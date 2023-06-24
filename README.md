# HostingCLR
HostingCLR For dotNet GUI/Console exe

- Console

		int		argc = 1;
		const	WCHAR* argv[3] = { L"", L"", L""};

		ZeroMemory(&vRet, sizeof(VARIANT));
		ZeroMemory(&vObj, sizeof(VARIANT));
		vObj.vt = VT_NULL;
		vPsa.vt = (VT_ARRAY | VT_BSTR);
		args = SafeArrayCreateVector(VT_VARIANT, 0, 1);

		if (argc > 1)
		{
			vPsa.parray = SafeArrayCreateVector(VT_BSTR, 0, argc);
			for (long i = 0; i < argc; i++)
			{
				SafeArrayPutElement(vPsa.parray, &i, SysAllocString(argv[i]));
			}

			long idx[1] = { 0 };
			SafeArrayPutElement(args, idx, &vPsa);
		}

		HRESULT hr = pMethodInfo->Invoke_3(vObj, args, &vRet);
- GUI 
  
		VARIANT ret_val;
		ZeroMemory(&ret_val, sizeof(VARIANT));
		VARIANT obj;
		ZeroMemory(&obj, sizeof(VARIANT));
		obj.vt = VT_NULL;
		const auto psa_static_method_args = SafeArrayCreateVector(VT_VARIANT, 0, 0);


		HRESULT hr = pMethodInfo->Invoke_3(obj, psa_static_method_args, &ret_val);
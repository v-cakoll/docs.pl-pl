---
title: IMetaDataEmit — Interfejs
ms.date: 03/30/2017
api_name:
- IMetaDataEmit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit
helpviewer_keywords:
- IMetaDataEmit interface [.NET Framework metadata]
ms.assetid: 3b48fd47-7397-4e2c-8bec-8157aa08978c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 10942541b781d367820301588656b2f1fc2fd006
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184421"
---
# <a name="imetadataemit-interface"></a>IMetaDataEmit — Interfejs
Dostarcza metody do tworzenia, modyfikacji i Zapisz metadane dotyczące zestawu w aktualnie zdefiniowanego zakresu. Metadane może być przechowywany w pamięci lub zapisywany na dysku.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ApplyEditAndContinue, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md)|Bieżący zakres zestawu zostaje zaktualizowana o zmiany wprowadzone w określonym `pImport`.|  
|[DefineCustomAttribute, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md)|Tworzy definicję atrybutu niestandardowego za pomocą podpisu określonych metadanych, dołączony do określonego obiektu, a następnie pobiera token do tej definicji atrybutu niestandardowego.|  
|[DefineEvent, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md)|Tworzy definicję na zdarzenie o sygnaturze określonych metadanych, a następnie pobiera token do tej definicji zdarzeń.|  
|[DefineField, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definefield-method.md)|Tworzy definicję dla pola przy użyciu podpisu określonych metadanych, a następnie pobiera token do tej definicji pola.|  
|[DefineImportMember, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md)|Tworzy definicję dla składowej typu, który jest zdefiniowany w module poza bieżącym zakresem, a następnie pobiera token dla tej definicji odwołania.|  
|[DefineImportType, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)|Tworzy definicję dla odwołania do typu, który jest zdefiniowany w module poza bieżącym zakresem, a następnie pobiera token do tej definicji odwołania.|  
|[DefineMemberRef, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)|Tworzy definicję dla odwołania do elementu członkowskiego modułu poza bieżącym zakresem, a następnie pobiera token do tej definicji odwołania.|  
|[DefineMethod, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)|Tworzy definicję metody o określonej sygnaturze i zwraca token do tej definicji metody.|  
|[DefineMethodImpl, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethodimpl-method.md)|Tworzy definicję dla implementacji metody dziedziczone z interfejsu, a następnie zwraca token do tej definicji implementacji metody.|  
|[DefineModuleRef, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md)|Tworzy podpisu metadanych dla modułu o określonej nazwie.|  
|[DefineNestedType, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definenestedtype-method.md)|Tworzy podpisu metadanych w definicji typu i zwraca `mdTypeDef` tokenu do typu, a ponadto określenie, że typ zdefiniowany jest elementem członkowskim typu odwołuje się `tdEncloser`.|  
|[DefineParam, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md)|Tworzy definicję parametrów o określonej sygnaturze metody odwołuje się określony token, a następnie pobiera token dla tej definicji parametru.|  
|[DefinePermissionSet, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md)|Tworzy definicję zestawu uprawnień o podpisu określonych metadanych, a następnie pobiera token do tej definicji zestaw uprawnień.|  
|[DefinePinvokeMap, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md)|Ustawia funkcji PInvoke podpis metody odwołuje się określony token.|  
|[DefineProperty, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md)|Utworzenie definicji właściwości dla określonego typu z określonego `get` i `set` metod dostępu do metody, a następnie pobiera token do tej definicji właściwości.|  
|[DefineSecurityAttributeSet, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definesecurityattributeset-method.md)|Tworzy zestaw uprawnień zabezpieczeń, aby dołączyć do obiektu odwołuje się określony token.|  
|[DefineTypeDef, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)|Tworzy definicję typu na typ środowiska uruchomieniowego języka wspólnego, a następnie pobiera token metadanych do tej definicji typu.|  
|[DefineTypeRefByName, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md)|Pobiera token metadanych dla typu, który jest zdefiniowany w innym module poza bieżącym zakresie.|  
|[DefineUserString, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md)|Pobiera metadane token dla określonego ciągu literału.|  
|[DeleteClassLayout, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deleteclasslayout-method.md)|Niszczy podpisu metadanych układ klasy dla danego typu odwołuje się określony token.|  
|[DeleteFieldMarshal, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletefieldmarshal-method.md)|Niszczy PInvoke marshaling podpisu metadanych dla obiektu odwołuje się określony token.|  
|[DeletePinvokeMap, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletepinvokemap-method.md)|Niszczy obiekt odwołuje się określony token metadanych mapowania funkcji PInvoke.|  
|[DeleteToken, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletetoken-method.md)|Usuwa określony token z bieżącego zakresu metadanych.|  
|[GetSaveSize, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-getsavesize-method.md)|Pobiera szacowany rozmiar binarne zestawu w bieżącym zakresie.|  
|[GetTokenFromSig, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md)|Pobiera token dla podpisu określonych metadanych.|  
|[GetTokenFromTypeSpec, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md)|Pobiera token metadanych dla typu za pomocą podpisu określonych metadanych.|  
|[Merge, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)|Dodaje określony zakres zaimportowane do listy zakresów do scalenia.|  
|[MergeEnd, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md)|Scala do bieżącego zakresu zakresy metadanych określone przez co najmniej jeden poprzedniego wywołania `IMetaDataEmit::Merge`.|  
|[Save, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-save-method.md)|Zapisuje wszystkie metadane w bieżącym zakresie pliku pod podanym adresem.|  
|[SaveToMemory, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md)|Zapisuje wszystkie metadane w bieżącym zakresie do określonego obszaru pamięci.|  
|[SaveToStream, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md)|Zapisuje wszystkie metadane w bieżącym zakresie określonej `IStream`.|  
|[SetClassLayout, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md)|Ustawia lub aktualizuje podpis układ klasy typu zdefiniowanego przez wcześniejsze wywołanie `IMetaDataEmit::DefineTypeDef`.|  
|[SetCustomAttributeValue, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setcustomattributevalue-method.md)|Ustawia lub aktualizuje wartość atrybutu niestandardowego, zdefiniowane przez wcześniejsze wywołanie `IMetaDataEmit::DefineCustomAttribute`.|  
|[SetEventProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-seteventprops-method.md)|Ustawia lub aktualizuje określoną funkcję zdarzenie zdefiniowane przez wcześniejsze wywołanie `IMetaDataEmit::DefineEvent`.|  
|[SetFieldMarshal, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldmarshal-method.md)|Ustawia PInvoke organizowanie informacji dla parametru pola, metody zwrotu lub metoda odwołuje się określony token.|  
|[SetFieldProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldprops-method.md)|Ustawia lub aktualizuje wartość domyślną dla pola przywoływane przez token określonego pola.|  
|[SetFieldRVA, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldrva-method.md)|Ustawia wartość zmiennej globalnej dla względne wirtualnego adresu pola przywoływane przez określony token.|  
|[SetHandler, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)|Ustawia metodę odwołuje się określony `IUnknown` wskaźnik jako wywołania zwrotnego dla tokenu ponowne mapowania.|  
|[SetMethodImplFlags, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md)|Ustawia lub aktualizuje podpis implementacji metody dziedziczonej, odwołuje się określony token metadanych.|  
|[SetMethodProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodprops-method.md)|Ustawia lub aktualizuje funkcji przechowywaną w określonej wirtualnej adres względny, zdefiniowane przez wcześniejsze wywołanie metody `IMetaDataEmit::DefineMethod`.|  
|[SetModuleProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md)|Aktualizuje odwołania do modułu zdefiniowane przez wcześniejsze wywołanie `IMetaDataEmit::DefineModuleRef`.|  
|[SetParamProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)|Ustawia lub zmienia funkcje parametru metody, która została zdefiniowana przez wcześniejsze wywołanie `IMetaDataEmit::DefineParam`.|  
|[SetParent, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparent-method.md)|Ustali, że określony element członkowski, zgodnie z definicją przez wcześniejsze wywołanie `IMetaDataEmit::DefineMemberRef`, jest członkiem określonego typu, zgodnie z wcześniejszym wywołaniu `IMetaDataEmit::DefineTypeDef`.|  
|[SetPermissionSetProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpermissionsetprops-method.md)|Ustawia lub aktualizuje funkcji podpisu metadanych zestawu uprawnień, zdefiniowane przez wcześniejsze wywołanie `IMetaDataEmit::DefinePermissionSet`.|  
|[SetPinvokeMap, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpinvokemap-method.md)|Ustawia lub zmienia funkcji PInvoke sygnatury metody, zgodnie z wcześniejszym wywołaniu `IMetaDataEmit::DefinePinvokeMap`.|  
|[SetPropertyProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpropertyprops-method.md)|Ustawia funkcje przechowywany w metadanych dla właściwości zdefiniowane przez wcześniejsze wywołanie `IMetaDataEmit::DefineProperty`.|  
|[SetRVA, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)|Ustawia adres względny wirtualnej określonej metody.|  
|[SetTypeDefProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-settypedefprops-method.md)|Ustawia typ zdefiniowany przez wcześniejsze wywołanie funkcji `IMetaDataEmit::DefineTypeDef`.|  
|[TranslateSigWithScope, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-translatesigwithscope-method.md)|Importuje zestawu do bieżącego zakresu, a następnie pobiera nowa sygnatura metadanych dla zakresu scalone.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataEmit2 — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

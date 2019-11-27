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
ms.openlocfilehash: b4ae599a0e5cdb604fd9a610728671b39c67af31
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440902"
---
# <a name="imetadataemit-interface"></a>IMetaDataEmit — Interfejs
Zapewnia metody tworzenia, modyfikowania i zapisywania metadanych dotyczących zestawu w aktualnie zdefiniowanym zakresie. Metadane mogą być przechowywane w pamięci lub zapisywane na dysku.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ApplyEditAndContinue, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md)|Aktualizuje bieżący zakres zestawu zmianami wprowadzonymi w określonym `pImport`.|  
|[DefineCustomAttribute, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md)|Tworzy definicję atrybutu niestandardowego z określonym podpisem metadanych do dołączenia do określonego obiektu i pobiera token do tej definicji atrybutu niestandardowego.|  
|[DefineEvent, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md)|Tworzy definicję zdarzenia z określonym podpisem metadanych i pobiera token do tej definicji zdarzenia.|  
|[DefineField, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definefield-method.md)|Tworzy definicję dla pola z określonym podpisem metadanych i pobiera token do tej definicji pola.|  
|[DefineImportMember, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md)|Tworzy definicję dla elementu członkowskiego typu, który jest zdefiniowany w module poza bieżącym zakresem, i pobiera token dla tej definicji odwołania.|  
|[DefineImportType, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)|Tworzy definicję odwołania do typu, który jest zdefiniowany w module poza bieżącym zakresem, i pobiera token do tej definicji odwołania.|  
|[DefineMemberRef, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)|Tworzy definicję odwołania do elementu członkowskiego modułu poza bieżącym zakresem i pobiera token do tej definicji odwołania.|  
|[DefineMethod, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)|Tworzy definicję metody z określonym podpisem i zwraca token do tej definicji metody.|  
|[DefineMethodImpl, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethodimpl-method.md)|Tworzy definicję dla implementacji metody dziedziczonej z interfejsu i zwraca token do tej definicji implementacji metody.|  
|[DefineModuleRef, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md)|Tworzy sygnaturę metadanych dla modułu o określonej nazwie.|  
|[DefineNestedType, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definenestedtype-method.md)|Tworzy sygnaturę metadanych definicji typu i zwraca token `mdTypeDef` dla tego typu, a także określa, że zdefiniowany typ jest członkiem typu, do którego odwołuje się `tdEncloser`.|  
|[DefineParam, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md)|Tworzy definicję parametru z określonym podpisem dla metody przywoływanej przez określony token i pobiera token dla tej definicji parametru.|  
|[DefinePermissionSet, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md)|Tworzy definicję zestawu uprawnień z określonym podpisem metadanych i pobiera token do tej definicji zestawu uprawnień.|  
|[DefinePinvokeMap, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md)|Ustawia funkcje podpisu PInvoke metody, do której odwołuje się określony token.|  
|[DefineProperty, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md)|Tworzy definicję właściwości określonego typu z określonym `get` i metodami dostępu do metody `set` i pobiera token do tej definicji właściwości.|  
|[DefineSecurityAttributeSet, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definesecurityattributeset-method.md)|Tworzy zestaw uprawnień zabezpieczeń do dołączenia do obiektu, do którego odwołuje się określony token.|  
|[DefineTypeDef, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)|Tworzy definicję typu dla typu środowiska uruchomieniowego języka wspólnego i pobiera token metadanych do tej definicji typu.|  
|[DefineTypeRefByName, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md)|Pobiera token metadanych dla typu, który jest zdefiniowany w innym module poza bieżącym zakresem.|  
|[DefineUserString, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md)|Pobiera token metadanych dla określonego ciągu literału.|  
|[DeleteClassLayout, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deleteclasslayout-method.md)|Niszczy sygnaturę metadanych układu klasy dla typu, do którego odwołuje się określony token.|  
|[DeleteFieldMarshal, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletefieldmarshal-method.md)|Niszczy sygnaturę metadanych kierowania PInvoke dla obiektu, do którego odwołuje się określony token.|  
|[DeletePinvokeMap, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletepinvokemap-method.md)|Niszczy metadane mapowania PInvoke dla obiektu, do którego odwołuje się określony token.|  
|[DeleteToken, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletetoken-method.md)|Usuwa określony token z bieżącego zakresu metadanych.|  
|[GetSaveSize, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-getsavesize-method.md)|Pobiera Szacowany rozmiar binarny zestawu w bieżącym zakresie.|  
|[GetTokenFromSig, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md)|Pobiera token dla określonej sygnatury metadanych.|  
|[GetTokenFromTypeSpec, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md)|Pobiera token metadanych dla typu z określonym podpisem metadanych.|  
|[Merge, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)|Dodaje określony zaimportowany zakres do listy zakresów, które mają zostać scalone.|  
|[MergeEnd, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md)|Scala do bieżącego zakresu wszystkich zakresów metadanych określonych przez jedno lub więcej wcześniejszych wywołań do `IMetaDataEmit::Merge`.|  
|[Save, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-save-method.md)|Zapisuje wszystkie metadane w bieżącym zakresie do pliku pod określonym adresem.|  
|[SaveToMemory, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md)|Zapisuje wszystkie metadane w bieżącym zakresie do określonego obszaru pamięci.|  
|[SaveToStream, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md)|Zapisuje wszystkie metadane w bieżącym zakresie do określonego `IStream`.|  
|[SetClassLayout, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md)|Ustawia lub aktualizuje sygnaturę układu klasy typu zdefiniowanego przez poprzednie wywołanie do `IMetaDataEmit::DefineTypeDef`.|  
|[SetCustomAttributeValue, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setcustomattributevalue-method.md)|Ustawia lub aktualizuje wartość atrybutu niestandardowego zdefiniowanego przez poprzednie wywołanie do `IMetaDataEmit::DefineCustomAttribute`.|  
|[SetEventProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-seteventprops-method.md)|Ustawia lub aktualizuje określoną funkcję zdarzenia zdefiniowaną przez poprzednie wywołanie do `IMetaDataEmit::DefineEvent`.|  
|[SetFieldMarshal, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldmarshal-method.md)|Ustawia informacje o kierowaniu PInvoke dla parametru, zwraca metodę lub parametr metody, do którego odwołuje się określony token.|  
|[SetFieldProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldprops-method.md)|Ustawia lub aktualizuje wartość domyślną dla pola, do którego odwołuje się określony token pola.|  
|[SetFieldRVA, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldrva-method.md)|Ustawia wartość zmiennej globalnej dla względnego adresu wirtualnego pola, do którego odwołuje się określony token.|  
|[SetHandler, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)|Ustawia metodę przywoływaną przez określony `IUnknown` wskaźnik jako wywołanie zwrotne powiadomienia o ponownym mapowaniu tokenu.|  
|[SetMethodImplFlags, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md)|Ustawia lub aktualizuje podpis metadanych dziedziczonej metody, do której odwołuje się określony token.|  
|[SetMethodProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodprops-method.md)|Ustawia lub aktualizuje funkcję przechowywaną w określonym względnym adresie wirtualnym metody zdefiniowanej przez poprzednie wywołanie do `IMetaDataEmit::DefineMethod`.|  
|[SetModuleProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md)|Aktualizuje odwołania do modułu zdefiniowanego przez poprzednie wywołanie do `IMetaDataEmit::DefineModuleRef`.|  
|[SetParamProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)|Ustawia lub zmienia funkcje parametru metody, który został zdefiniowany przez poprzednie wywołanie do `IMetaDataEmit::DefineParam`.|  
|[SetParent, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparent-method.md)|Określa, że określony element członkowski zdefiniowany przez poprzednie wywołanie do `IMetaDataEmit::DefineMemberRef`, jest elementem członkowskim określonego typu zdefiniowanym przez poprzednie wywołanie do `IMetaDataEmit::DefineTypeDef`.|  
|[SetPermissionSetProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpermissionsetprops-method.md)|Ustawia lub aktualizuje funkcje sygnatury metadanych zestawu uprawnień zdefiniowanego przez poprzednie wywołanie do `IMetaDataEmit::DefinePermissionSet`.|  
|[SetPinvokeMap, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpinvokemap-method.md)|Ustawia lub zmienia funkcje podpisu PInvoke metody, zgodnie z definicją w poprzednim wywołaniu do `IMetaDataEmit::DefinePinvokeMap`.|  
|[SetPropertyProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpropertyprops-method.md)|Ustawia funkcje przechowywane w metadanych dla właściwości zdefiniowanej przez poprzednie wywołanie do `IMetaDataEmit::DefineProperty`.|  
|[SetRVA, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)|Ustawia względny adres wirtualny określonej metody.|  
|[SetTypeDefProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-settypedefprops-method.md)|Ustawia funkcje typu zdefiniowanego przez poprzednie wywołanie do `IMetaDataEmit::DefineTypeDef`.|  
|[TranslateSigWithScope, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-translatesigwithscope-method.md)|Importuje zestaw do bieżącego zakresu i pobiera nowy podpis metadanych dla scalonego zakresu.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

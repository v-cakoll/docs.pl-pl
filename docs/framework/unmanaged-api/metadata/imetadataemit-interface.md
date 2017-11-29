---
title: "IMetaDataEmit — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit
helpviewer_keywords: IMetaDataEmit interface [.NET Framework metadata]
ms.assetid: 3b48fd47-7397-4e2c-8bec-8157aa08978c
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b62e11f8237330122ccd2bd8775f8d113545dd95
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemit-interface"></a>IMetaDataEmit — Interfejs
Udostępnia metody do tworzenia, modyfikacji i zapisać metadane dotyczące zestawu w aktualnie określonego zakresu. Metadane można przechowywane w pamięci lub zapisanej na dysku.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ApplyEditAndContinue — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md)|Aktualizuje bieżącego zakresu zestawu zmiany wprowadzone w określonym `pImport`.|  
|[DefineCustomAttribute — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md)|Tworzy definicji dla atrybutu niestandardowego o sygnaturze określonych metadanych, jest dołączony do określonego obiektu i pobiera token do tej definicji atrybutu niestandardowego.|  
|[DefineEvent — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md)|Tworzy definicję zdarzenie o sygnaturze określonych metadanych, a następnie pobiera token do tej definicji zdarzeń.|  
|[DefineField — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definefield-method.md)|Tworzy definicję pola z podpisem określonych metadanych i pobiera token do tej definicji pola.|  
|[DefineImportMember — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md)|Tworzy definicji dla elementu członkowskiego typu, który jest zdefiniowany w module spoza zakresu i pobiera token dla tej definicji odwołania.|  
|[DefineImportType — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)|Tworzy definicję dla odwołania do typu, który jest zdefiniowany w module poza bieżącym zakresem i pobiera token do tej definicji odwołania.|  
|[DefineMemberRef — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)|Tworzy definicję dla odwołania do elementu członkowskiego modułu poza bieżącym zakresem i pobiera token do tej definicji odwołania.|  
|[DefineMethod — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)|Tworzy definicję metody z określoną sygnaturą i zwraca token do tej definicji metody.|  
|[DefineMethodImpl — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethodimpl-method.md)|Tworzy definicję dla implementacji metody dziedziczone z interfejsem i zwraca token do tej definicji implementacji metody.|  
|[DefineModuleRef — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md)|Tworzy podpis metadane dla modułu o określonej nazwie.|  
|[DefineNestedType — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definenestedtype-method.md)|Tworzy podpisu metadanych definicją typu i zwraca `mdTypeDef` tokenu dla tego typu, który jest również określenie, że zdefiniowanego typu jest elementem członkowskim typu odwołuje się `tdEncloser`.|  
|[DefineParam — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md)|Tworzy definicję parametru z określoną sygnaturą dla metody odwołuje się określony token i pobiera token dla tej definicji parametru.|  
|[DefinePermissionSet — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md)|Tworzy definicji zestawu uprawnień o podpisu określonych metadanych, a następnie pobiera token do tej definicji zestawu uprawnień.|  
|[DefinePinvokeMap — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md)|Ustawia funkcje metody odwołuje się określony token podpisu funkcji PInvoke.|  
|[DefineProperty — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md)|Utworzenie definicji właściwości dla określonego typu z określonym `get` i `set` akcesorów — metoda i pobiera token do tej definicji właściwości.|  
|[DefineSecurityAttributeSet — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definesecurityattributeset-method.md)|Tworzy zestaw uprawnień zabezpieczeń, aby dołączyć do obiektu odwołuje się określony token.|  
|[DefineTypeDef — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)|Tworzy definicji typu dla typu środowiska uruchomieniowego języka wspólnego i pobiera token metadanych do tej definicji typu.|  
|[DefineTypeRefByName — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md)|Pobiera token metadanych dla typu, który jest zdefiniowany w innym module spoza zakresu.|  
|[DefineUserString — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md)|Pobiera metadane token dla określonego ciągu literału.|  
|[DeleteClassLayout — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deleteclasslayout-method.md)|Niszczy podpisu metadanych układ klasy dla typu odwołuje się określony token.|  
|[DeleteFieldMarshal — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletefieldmarshal-method.md)|Niszczy PInvoke organizowanie podpisu metadanych dla obiekt odwołuje się określony token.|  
|[DeletePinvokeMap — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletepinvokemap-method.md)|Niszczy metadanych mapowania PInvoke dla obiekt odwołuje się określony token.|  
|[DeleteToken — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletetoken-method.md)|Usuwa określony token z bieżącego zakresu metadanych.|  
|[GetSaveSize — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-getsavesize-method.md)|Pobiera szacowany rozmiar binarnych zestawu w bieżącym zakresie.|  
|[GetTokenFromSig — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md)|Pobiera token podpisu określonych metadanych.|  
|[GetTokenFromTypeSpec — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md)|Pobiera token metadanych dla typu o sygnaturze określonych metadanych.|  
|[Merge — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)|Dodaje określony zakres zaimportowane do listy zakresów do scalenia.|  
|[MergeEnd — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md)|Scalenia do bieżącego zakresu zakresy metadanych określonych przez jeden lub więcej poprzedniego wywołania `IMetaDataEmit::Merge`.|  
|[Save — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-save-method.md)|Zapisuje wszystkie metadane w bieżącym zakresie pliku pod określonym adresem.|  
|[SaveToMemory — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md)|Zapisuje wszystkie metadane w bieżącym zakresie do określonego obszaru pamięci.|  
|[SaveToStream — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md)|Zapisuje wszystkie metadane w bieżącym zakresie do określonego `IStream`.|  
|[SetClassLayout — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md)|Ustawia lub aktualizuje podpis układ klasy typ zdefiniowany przez poprzednie wywołanie `IMetaDataEmit::DefineTypeDef`.|  
|[SetCustomAttributeValue — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setcustomattributevalue-method.md)|Ustawia lub aktualizuje wartość atrybutu niestandardowego wynika z wcześniejszym wywołaniu `IMetaDataEmit::DefineCustomAttribute`.|  
|[SetEventProps — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-seteventprops-method.md)|Ustawia lub aktualizuje określoną funkcję wynika z wcześniejszym wywołaniu zdarzenia `IMetaDataEmit::DefineEvent`.|  
|[SetFieldMarshal — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldmarshal-method.md)|Ustawia PInvoke przekazywanie informacji dla parametru pola, zwracany — metoda lub metody odwołuje się określony token.|  
|[SetFieldProps — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldprops-method.md)|Ustawia lub aktualizuje wartość domyślna w polu odwołuje się token określonego pola.|  
|[SetFieldRVA — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldrva-method.md)|Ustawia wartość zmiennej globalnej względną wirtualnego adresu pola odwołuje się określony token.|  
|[SetHandler — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)|Ustawia metodę odwołuje się określony `IUnknown` wskaźnika jako wywołanie zwrotne powiadomienia dla tokenu ponowne mapowania.|  
|[SetMethodImplFlags — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md)|Ustawia lub aktualizuje podpis implementacji dziedziczonej metody odwołuje się określony token metadanych.|  
|[SetMethodProps — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodprops-method.md)|Ustawia lub aktualizuje funkcję przechowywane w określonej wirtualnej adres względny, zdefiniowany przez poprzednie wywołanie do metody `IMetaDataEmit::DefineMethod`.|  
|[SetModuleProps — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md)|Aktualizuje odwołania do modułu wynika z wcześniejszym wywołaniu `IMetaDataEmit::DefineModuleRef`.|  
|[SetParamProps — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)|Ustawia lub zmienia funkcje parametru metody, która została zdefiniowana przez poprzednie wywołanie `IMetaDataEmit::DefineParam`.|  
|[SetParent — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparent-method.md)|Ustali, że określony element członkowski, zdefiniowane przez poprzednie wywołanie `IMetaDataEmit::DefineMemberRef`, jest członkiem określonego typu, zgodnie z wcześniejszym wywołaniu `IMetaDataEmit::DefineTypeDef`.|  
|[SetPermissionSetProps — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpermissionsetprops-method.md)|Ustawia lub aktualizuje funkcje podpisu metadanych zestawu uprawnień wynika z wcześniejszym wywołaniu `IMetaDataEmit::DefinePermissionSet`.|  
|[SetPinvokeMap — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpinvokemap-method.md)|Ustawia lub zmienia funkcje podpisu funkcji PInvoke metody, zgodnie z wcześniejszym wywołaniu `IMetaDataEmit::DefinePinvokeMap`.|  
|[SetPropertyProps — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpropertyprops-method.md)|Ustawia przechowywane w metadanych dla właściwości zdefiniowane przez poprzednie wywołanie funkcji `IMetaDataEmit::DefineProperty`.|  
|[SetRVA — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)|Ustawia adres względny wirtualnego określonej metody.|  
|[SetTypeDefProps — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-settypedefprops-method.md)|Ustawia typ zdefiniowany przez poprzednie wywołanie funkcji `IMetaDataEmit::DefineTypeDef`.|  
|[TranslateSigWithScope — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-translatesigwithscope-method.md)|Importuje zestawu do bieżącego zakresu i pobiera nowego podpisu metadanych dla zakresu scalone.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [IMetaDataEmit2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

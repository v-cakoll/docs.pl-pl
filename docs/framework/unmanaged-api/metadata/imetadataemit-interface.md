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
ms.openlocfilehash: a2c2512abc28f0140fc261c5136c7e1255db96de
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009217"
---
# <a name="imetadataemit-interface"></a>IMetaDataEmit — Interfejs
Zapewnia metody tworzenia, modyfikowania i zapisywania metadanych dotyczących zestawu w aktualnie zdefiniowanym zakresie. Metadane mogą być przechowywane w pamięci lub zapisywane na dysku.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ApplyEditAndContinue — Metoda](imetadataemit-applyeditandcontinue-method.md)|Aktualizuje bieżący zakres zestawu zmianami wprowadzonymi w określonym `pImport` .|  
|[DefineCustomAttribute — Metoda](imetadataemit-definecustomattribute-method.md)|Tworzy definicję atrybutu niestandardowego z określonym podpisem metadanych do dołączenia do określonego obiektu i pobiera token do tej definicji atrybutu niestandardowego.|  
|[DefineEvent — Metoda](imetadataemit-defineevent-method.md)|Tworzy definicję zdarzenia z określonym podpisem metadanych i pobiera token do tej definicji zdarzenia.|  
|[DefineField — Metoda](imetadataemit-definefield-method.md)|Tworzy definicję dla pola z określonym podpisem metadanych i pobiera token do tej definicji pola.|  
|[DefineImportMember — Metoda](imetadataemit-defineimportmember-method.md)|Tworzy definicję dla elementu członkowskiego typu, który jest zdefiniowany w module poza bieżącym zakresem, i pobiera token dla tej definicji odwołania.|  
|[DefineImportType — Metoda](imetadataemit-defineimporttype-method.md)|Tworzy definicję odwołania do typu, który jest zdefiniowany w module poza bieżącym zakresem, i pobiera token do tej definicji odwołania.|  
|[DefineMemberRef — Metoda](imetadataemit-definememberref-method.md)|Tworzy definicję odwołania do elementu członkowskiego modułu poza bieżącym zakresem i pobiera token do tej definicji odwołania.|  
|[DefineMethod — Metoda](imetadataemit-definemethod-method.md)|Tworzy definicję metody z określonym podpisem i zwraca token do tej definicji metody.|  
|[DefineMethodImpl — Metoda](imetadataemit-definemethodimpl-method.md)|Tworzy definicję dla implementacji metody dziedziczonej z interfejsu i zwraca token do tej definicji implementacji metody.|  
|[DefineModuleRef — Metoda](imetadataemit-definemoduleref-method.md)|Tworzy sygnaturę metadanych dla modułu o określonej nazwie.|  
|[DefineNestedType — Metoda](imetadataemit-definenestedtype-method.md)|Tworzy sygnaturę metadanych definicji typu i zwraca `mdTypeDef` token dla tego typu, a także określa, że zdefiniowany typ jest członkiem typu, do którego odwołuje się `tdEncloser` .|  
|[DefineParam — Metoda](imetadataemit-defineparam-method.md)|Tworzy definicję parametru z określonym podpisem dla metody przywoływanej przez określony token i pobiera token dla tej definicji parametru.|  
|[DefinePermissionSet — Metoda](imetadataemit-definepermissionset-method.md)|Tworzy definicję zestawu uprawnień z określonym podpisem metadanych i pobiera token do tej definicji zestawu uprawnień.|  
|[DefinePinvokeMap — Metoda](imetadataemit-definepinvokemap-method.md)|Ustawia funkcje podpisu PInvoke metody, do której odwołuje się określony token.|  
|[DefineProperty — Metoda](imetadataemit-defineproperty-method.md)|Tworzy definicję właściwości określonego typu, z określonymi `get` `set` metodami dostępu, i pobiera token do tej definicji właściwości.|  
|[DefineSecurityAttributeSet — Metoda](imetadataemit-definesecurityattributeset-method.md)|Tworzy zestaw uprawnień zabezpieczeń do dołączenia do obiektu, do którego odwołuje się określony token.|  
|[DefineTypeDef — Metoda](imetadataemit-definetypedef-method.md)|Tworzy definicję typu dla typu środowiska uruchomieniowego języka wspólnego i pobiera token metadanych do tej definicji typu.|  
|[DefineTypeRefByName — Metoda](imetadataemit-definetyperefbyname-method.md)|Pobiera token metadanych dla typu, który jest zdefiniowany w innym module poza bieżącym zakresem.|  
|[DefineUserString — Metoda](imetadataemit-defineuserstring-method.md)|Pobiera token metadanych dla określonego ciągu literału.|  
|[DeleteClassLayout — Metoda](imetadataemit-deleteclasslayout-method.md)|Niszczy sygnaturę metadanych układu klasy dla typu, do którego odwołuje się określony token.|  
|[DeleteFieldMarshal — Metoda](imetadataemit-deletefieldmarshal-method.md)|Niszczy sygnaturę metadanych kierowania PInvoke dla obiektu, do którego odwołuje się określony token.|  
|[DeletePinvokeMap — Metoda](imetadataemit-deletepinvokemap-method.md)|Niszczy metadane mapowania PInvoke dla obiektu, do którego odwołuje się określony token.|  
|[DeleteToken — Metoda](imetadataemit-deletetoken-method.md)|Usuwa określony token z bieżącego zakresu metadanych.|  
|[GetSaveSize — Metoda](imetadataemit-getsavesize-method.md)|Pobiera Szacowany rozmiar binarny zestawu w bieżącym zakresie.|  
|[GetTokenFromSig — Metoda](imetadataemit-gettokenfromsig-method.md)|Pobiera token dla określonej sygnatury metadanych.|  
|[GetTokenFromTypeSpec — Metoda](imetadataemit-gettokenfromtypespec-method.md)|Pobiera token metadanych dla typu z określonym podpisem metadanych.|  
|[Merge — Metoda](imetadataemit-merge-method.md)|Dodaje określony zaimportowany zakres do listy zakresów, które mają zostać scalone.|  
|[MergeEnd — Metoda](imetadataemit-mergeend-method.md)|Scala do bieżącego zakresu wszystkich zakresów metadanych określonych przez jedno lub więcej wcześniejszych wywołań do `IMetaDataEmit::Merge` .|  
|[Save — Metoda](imetadataemit-save-method.md)|Zapisuje wszystkie metadane w bieżącym zakresie do pliku pod określonym adresem.|  
|[SaveToMemory — Metoda](imetadataemit-savetomemory-method.md)|Zapisuje wszystkie metadane w bieżącym zakresie do określonego obszaru pamięci.|  
|[SaveToStream — Metoda](imetadataemit-savetostream-method.md)|Zapisuje wszystkie metadane w bieżącym zakresie do określonego `IStream` .|  
|[SetClassLayout — Metoda](imetadataemit-setclasslayout-method.md)|Ustawia lub aktualizuje sygnaturę układu klasy typu zdefiniowanego przez poprzednie wywołanie do `IMetaDataEmit::DefineTypeDef` .|  
|[SetCustomAttributeValue — Metoda](imetadataemit-setcustomattributevalue-method.md)|Ustawia lub aktualizuje wartość atrybutu niestandardowego zdefiniowanego przez poprzednie wywołanie do `IMetaDataEmit::DefineCustomAttribute` .|  
|[SetEventProps — Metoda](imetadataemit-seteventprops-method.md)|Ustawia lub aktualizuje określoną funkcję zdarzenia zdefiniowaną przez poprzednie wywołanie do `IMetaDataEmit::DefineEvent` .|  
|[SetFieldMarshal — Metoda](imetadataemit-setfieldmarshal-method.md)|Ustawia informacje o kierowaniu PInvoke dla parametru, zwraca metodę lub parametr metody, do którego odwołuje się określony token.|  
|[SetFieldProps — Metoda](imetadataemit-setfieldprops-method.md)|Ustawia lub aktualizuje wartość domyślną dla pola, do którego odwołuje się określony token pola.|  
|[SetFieldRVA — Metoda](imetadataemit-setfieldrva-method.md)|Ustawia wartość zmiennej globalnej dla względnego adresu wirtualnego pola, do którego odwołuje się określony token.|  
|[SetHandler — Metoda](imetadataemit-sethandler-method.md)|Ustawia metodę przywoływaną przez określony `IUnknown` wskaźnik jako wywołanie zwrotne powiadomienia o ponownym mapowaniu tokenu.|  
|[SetMethodImplFlags — Metoda](imetadataemit-setmethodimplflags-method.md)|Ustawia lub aktualizuje podpis metadanych dziedziczonej metody, do której odwołuje się określony token.|  
|[SetMethodProps — Metoda](imetadataemit-setmethodprops-method.md)|Ustawia lub aktualizuje funkcję przechowywaną w określonym względnie wirtualnym adresie metody zdefiniowanej przez poprzednie wywołanie do `IMetaDataEmit::DefineMethod` .|  
|[SetModuleProps — Metoda](imetadataemit-setmoduleprops-method.md)|Aktualizuje odwołania do modułu zdefiniowanego przez poprzednie wywołanie do `IMetaDataEmit::DefineModuleRef` .|  
|[SetParamProps — Metoda](imetadataemit-setparamprops-method.md)|Ustawia lub zmienia funkcje parametru metody, który został zdefiniowany przez poprzednie wywołanie do `IMetaDataEmit::DefineParam` .|  
|[SetParent — Metoda](imetadataemit-setparent-method.md)|Określa, że określony element członkowski zdefiniowany przez poprzednie wywołanie do `IMetaDataEmit::DefineMemberRef` , jest składową określonego typu, zgodnie z wcześniejszym wywołaniem do `IMetaDataEmit::DefineTypeDef` .|  
|[SetPermissionSetProps — Metoda](imetadataemit-setpermissionsetprops-method.md)|Ustawia lub aktualizuje funkcje podpisu metadanych zestawu uprawnień zdefiniowanego przez poprzednie wywołanie do `IMetaDataEmit::DefinePermissionSet` .|  
|[SetPinvokeMap — Metoda](imetadataemit-setpinvokemap-method.md)|Ustawia lub zmienia funkcje podpisu PInvoke metody, zgodnie z definicją w poprzednim wywołaniu do `IMetaDataEmit::DefinePinvokeMap` .|  
|[SetPropertyProps — Metoda](imetadataemit-setpropertyprops-method.md)|Ustawia funkcje przechowywane w metadanych dla właściwości zdefiniowanej przez poprzednie wywołanie do `IMetaDataEmit::DefineProperty` .|  
|[SetRVA — Metoda](imetadataemit-setrva-method.md)|Ustawia względny adres wirtualny określonej metody.|  
|[SetTypeDefProps — Metoda](imetadataemit-settypedefprops-method.md)|Ustawia funkcje typu zdefiniowanego przez poprzednie wywołanie do `IMetaDataEmit::DefineTypeDef` .|  
|[TranslateSigWithScope — Metoda](imetadataemit-translatesigwithscope-method.md)|Importuje zestaw do bieżącego zakresu i pobiera nowy podpis metadanych dla scalonego zakresu.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Interfejsy metadanych](metadata-interfaces.md)
- [IMetaDataEmit2, interfejs](imetadataemit2-interface.md)

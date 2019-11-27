---
title: IMetaDataImport — Interfejs
ms.date: 03/30/2017
api_name:
- IMetaDataImport
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport
helpviewer_keywords:
- IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 0adbbd35-5e8d-4fec-8268-dc70a07c5975
topic_type:
- apiref
ms.openlocfilehash: 2d45a369def193b9c8d8f9a3aa954ede600a87dd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434735"
---
# <a name="imetadataimport-interface"></a>IMetaDataImport — Interfejs
Zapewnia metody importowania i manipulowania istniejącymi metadanymi z przenośnego pliku wykonywalnego (PE) lub innego źródła, takiego jak biblioteka typów lub autonomiczny plik binarny metadanych w czasie wykonywania.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CloseEnum, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-closeenum-method.md)|Zamyka moduł wyliczający z określonym dojściem.|  
|[CountEnum, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-countenum-method.md)|Pobiera liczbę elementów w module wyliczającym z określonym dojściem.|  
|[EnumCustomAttributes, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md)|Wylicza listę niestandardowych tokenów definicji atrybutów skojarzonych z określonym typem lub członkiem.|  
|[EnumEvents, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumevents-method.md)|Wylicza tokeny definicji zdarzeń dla określonego tokenu TypeDef.|  
|[EnumFields, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md)|Wylicza tokeny FieldDef dla typu, do którego odwołuje się określony token TypeDef.|  
|[EnumFieldsWithName, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfieldswithname-method.md)|Wylicza tokeny FieldDef określonego typu o określonej nazwie.|  
|[EnumInterfaceImpls, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enuminterfaceimpls-method.md)|Wylicza tokeny MethodDef reprezentujące implementacje interfejsu.|  
|[EnumMemberRefs, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummemberrefs-method.md)|Wylicza tokeny elementu MemberRef reprezentujące elementy członkowskie określonego typu.|  
|[EnumMembers, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md)|Wylicza tokeny MemberDef reprezentujące składowe określonego typu.|  
|[EnumMembersWithName, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummemberswithname-method.md)|Wylicza tokeny MemberDef reprezentujące elementy członkowskie określonego typu o określonej nazwie.|  
|[EnumMethodImpls, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodimpls-method.md)|Wylicza tokeny MethodBody i MethodDeclaration reprezentujące metody określonego typu.|  
|[EnumMethods, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md)|Wylicza tokeny MethodDef reprezentujące metody określonego typu.|  
|[EnumMethodSemantics, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodsemantics-method.md)|Wylicza właściwości i zdarzenia zmiany właściwości, z którymi powiązana jest określona metoda.|  
|[EnumMethodsWithName, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodswithname-method.md)|Wylicza metody, które mają określoną nazwę i które są definiowane przez typ, do którego odwołuje się określony token TypeDef.|  
|[EnumModuleRefs, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummodulerefs-method.md)|Wylicza tokeny ModuleRef reprezentujące importowane moduły.|  
|[EnumParams, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumparams-method.md)|Wylicza tokeny ParamDef reprezentujące parametry metody przywoływanej przez określony token MethodDef.|  
|[EnumPermissionSets, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumpermissionsets-method.md)|Wylicza uprawnienia dla obiektów w określonym zakresie metadanych.|  
|[EnumProperties, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumproperties-method.md)|Wylicza tokeny PropertyDef reprezentujące właściwości typu, do którego odwołuje się określony token TypeDef.|  
|[EnumSignatures, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumsignatures-method.md)|Wylicza tokeny podpisu reprezentujące podpisy autonomiczne w bieżącym zakresie.|  
|[EnumTypeDefs, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)|Wylicza tokeny TypeDef reprezentujące wszystkie typy w bieżącym zakresie.|  
|[EnumTypeRefs, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtyperefs-method.md)|Wylicza tokeny TypeRef zdefiniowane w bieżącym zakresie metadanych.|  
|[EnumTypeSpecs, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypespecs-method.md)|Wylicza tokeny elementu TypeSpec zdefiniowane w bieżącym zakresie metadanych.|  
|[EnumUnresolvedMethods, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumunresolvedmethods-method.md)|Wylicza tokeny MemberDef reprezentujące nierozpoznane metody w bieżącym zakresie metadanych.|  
|[EnumUserStrings, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumuserstrings-method.md)|Wylicza tokeny ciągów reprezentujące stałe ciągi w bieżącym zakresie metadanych.|  
|[FindField, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md)|Pobiera token FieldDef dla pola, które jest elementem członkowskim określonego typu i ma określoną nazwę i sygnaturę metadanych.|  
|[FindMember, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmember-method.md)|Pobiera wskaźnik do tokenu MemberDef dla elementu członkowskiego zdefiniowanego przez określony typ z określoną nazwą i sygnaturą metadanych.|  
|[FindMemberRef, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmemberref-method.md)|Pobiera wskaźnik do tokenu MemberRef dla elementu członkowskiego zdefiniowanego przez określony typ z określoną nazwą i sygnaturą metadanych.|  
|[FindMethod, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md)|Pobiera wskaźnik do tokenu MethodDef dla metody zdefiniowanej przez określony typ z określoną nazwą i sygnaturą metadanych.|  
|[FindTypeDefByName, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findtypedefbyname-method.md)|Pobiera wskaźnik do tokenu metadanych TypeDef dla typu o określonej nazwie.|  
|[FindTypeRef, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findtyperef-method.md)|Pobiera wskaźnik do tokenu metadanych elementu TypeRef, który odwołuje się do typu w określonym zakresie wyszukiwania o określonej nazwie.|  
|[GetClassLayout, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md)|Pobiera informacje o układzie dla klasy, do której odwołuje się określony token TypeDef.|  
|[GetCustomAttributeByName, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getcustomattributebyname-method.md)|Pobiera wartość atrybutu niestandardowego pod nazwą.|  
|[GetCustomAttributeProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getcustomattributeprops-method.md)|Pobiera wartość atrybutu niestandardowego z uwzględnieniem jego tokenu metadanych.|  
|[GetEventProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-geteventprops-method.md)|Pobiera informacje o metadanych (w tym typ deklarujący, metody dodawania i usuwania dla delegatów oraz wszelkie flagi i inne powiązane dane) dla zdarzenia reprezentowanego przez określony token zdarzenia.|  
|[GetFieldMarshal, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getfieldmarshal-method.md)|Pobiera wskaźnik do natywnego, niezarządzanego typu pola reprezentowanego przez określony token metadanych pola.|  
|[GetFieldProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getfieldprops-method.md)|Pobiera metadane skojarzone z polem, do którego odwołuje się określony token FieldDef.|  
|[GetInterfaceImplProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getinterfaceimplprops-method.md)|Pobiera wskaźnik do tokenów metadanych dla typu, który implementuje określoną metodę i dla interfejsu, który deklaruje tę metodę.|  
|[GetMemberProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmemberprops-method.md)|Pobiera informacje o metadanych (w tym nazwę, podpis binarny i względny adres wirtualny) elementu członkowskiego typu, do którego odwołuje się określony token metadanych.|  
|[GetMemberRefProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmemberrefprops-method.md)|Pobiera metadane skojarzone z elementem członkowskim, do którego odwołuje się określony token.|  
|[GetMethodProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmethodprops-method.md)|Pobiera metadane skojarzone z metodą przywoływaną przez określony token MethodDef.|  
|[GetMethodSemantics, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmethodsemantics-method.md)|Pobiera wskaźnik do relacji między metodą przywoływaną przez określony token MethodDef i sparowaną właściwością i zdarzeniem, do którego odwołuje się określony token EventProp.|  
|[GetModuleFromScope, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmodulefromscope-method.md)|Pobiera wskaźnik do tokenu metadanych dla modułu, do którego odwołuje się bieżący zakres metadanych.|  
|[GetModuleRefProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmodulerefprops-method.md)|Pobiera nazwę modułu, do którego odwołuje się określony token metadanych.|  
|[GetNameFromToken, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnamefromtoken-method.md)|Pobiera nazwę UTF-8 obiektu, do którego odwołuje się określony token metadanych.|  
|[GetNativeCallConvFromSig, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnativecallconvfromsig-method.md)|Pobiera natywną konwencję wywoływania dla metody reprezentowanej przez określony wskaźnik podpisu.|  
|[GetNestedClassProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnestedclassprops-method.md)|Pobiera token TypeDef dla otaczającego typu nadrzędnego określonego typu zagnieżdżonego.|  
|[GetParamForMethodIndex, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getparamformethodindex-method.md)|Pobiera wskaźnik do tokenu, który reprezentuje parametr w określonej pozycji porządkowej w sekwencji parametrów metody dla metody reprezentowanej przez określony token MethodDef.|  
|[GetParamProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getparamprops-method.md)|Pobiera wartości metadanych dla parametru, do którego odwołuje się określony token ParamDef.|  
|[GetPermissionSetProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpermissionsetprops-method.md)|Pobiera metadane skojarzone z System. Security. PermissionSet reprezentowane przez określony token uprawnień.|  
|[GetPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpinvokemap-method.md)|Pobiera token typu ModuleRef reprezentujący zestaw docelowy wywołania PInvoke.|  
|[GetPropertyProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpropertyprops-method.md)|Pobiera metadane skojarzone z właściwością reprezentowaną przez określony token.|  
|[GetRVA, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getrva-method.md)|Pobiera przesunięcie względnego adresu wirtualnego obiektu kodu reprezentowanego przez określony token.|  
|[GetScopeProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md)|Pobiera nazwę i opcjonalnie identyfikator wersji zestawu lub modułu w bieżącym zakresie metadanych.|  
|[GetSigFromToken, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getsigfromtoken-method.md)|Pobiera binarny podpis metadanych skojarzony z określonym tokenem.|  
|[GetTypeDefProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettypedefprops-method.md)|Zwraca informacje o metadanych dla typu reprezentowanego przez określony token TypeDef.|  
|[GetTypeRefProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettyperefprops-method.md)|Pobiera metadane skojarzone z typem przywoływanym przez określony token elementu TypeRef.|  
|[GetTypeSpecFromToken, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettypespecfromtoken-method.md)|Pobiera binarny podpis metadanych specyfikacji typu reprezentowanej przez określony token.|  
|[GetUserString, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getuserstring-method.md)|Pobiera ciąg literału reprezentowanego przez określony token metadanych.|  
|[IsGlobal, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-isglobal-method.md)|Pobiera wartość wskazującą, czy pole, metoda lub typ reprezentowane przez określony token metadanych ma zakres globalny.|  
|[IsValidToken, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-isvalidtoken-method.md)|Pobiera wartość wskazującą, czy określony token przechowuje prawidłowe odwołanie do obiektu kodu.|  
|[ResetEnum, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-resetenum-method.md)|Resetuje określony moduł wyliczający do określonego położenia.|  
|[ResolveTypeRef, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-resolvetyperef-method.md)|Pobiera informacje o typie dla typu, do którego odwołuje się określony token elementu TypeRef.|  
  
## <a name="remarks"></a>Uwagi  
 Projekt interfejsu `IMetaDataImport` jest przeznaczony głównie do użytku przez narzędzia i usługi, które będą importować informacje o typie (na przykład narzędzia programistyczne) lub zarządzać wdrożonymi składnikami (na przykład w usługach rozpoznawania/aktywacji). Metody w `IMetaDataImport` należą do następujących kategorii zadań:  
  
- Wyliczanie kolekcji elementów w zakresie metadanych.  
  
- Znajdowanie elementu, który ma określony zestaw właściwości.  
  
- Pobieranie właściwości określonego elementu.  
  
- Metody get są specjalnie zaprojektowane do zwracania właściwości jednowartościowych elementu metadanych. Gdy właściwość jest odwołaniem do innego elementu, zwracany jest token dla tego elementu. Dowolny typ wejściowy wskaźnika może mieć wartość NULL, aby wskazać, że określona wartość nie jest żądana. Aby uzyskać właściwości, które są zasadniczo obiektami kolekcji (na przykład kolekcje interfejsów, które implementuje Klasa), użyj metod wyliczania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

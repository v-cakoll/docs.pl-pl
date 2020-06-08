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
ms.openlocfilehash: 02d1ea1ef12fa158ce7ec94aeca4356ac54d4e5f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503487"
---
# <a name="imetadataimport-interface"></a>IMetaDataImport — Interfejs
Zapewnia metody importowania i manipulowania istniejącymi metadanymi z przenośnego pliku wykonywalnego (PE) lub innego źródła, takiego jak biblioteka typów lub autonomiczny plik binarny metadanych w czasie wykonywania.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CloseEnum, metoda](imetadataimport-closeenum-method.md)|Zamyka moduł wyliczający z określonym dojściem.|  
|[CountEnum — Metoda](imetadataimport-countenum-method.md)|Pobiera liczbę elementów w module wyliczającym z określonym dojściem.|  
|[EnumCustomAttributes — Metoda](imetadataimport-enumcustomattributes-method.md)|Wylicza listę niestandardowych tokenów definicji atrybutów skojarzonych z określonym typem lub członkiem.|  
|[EnumEvents — Metoda](imetadataimport-enumevents-method.md)|Wylicza tokeny definicji zdarzeń dla określonego tokenu TypeDef.|  
|[EnumFields — Metoda](imetadataimport-enumfields-method.md)|Wylicza tokeny FieldDef dla typu, do którego odwołuje się określony token TypeDef.|  
|[EnumFieldsWithName — Metoda](imetadataimport-enumfieldswithname-method.md)|Wylicza tokeny FieldDef określonego typu o określonej nazwie.|  
|[EnumInterfaceImpls — Metoda](imetadataimport-enuminterfaceimpls-method.md)|Wylicza tokeny MethodDef reprezentujące implementacje interfejsu.|  
|[EnumMemberRefs — Metoda](imetadataimport-enummemberrefs-method.md)|Wylicza tokeny elementu MemberRef reprezentujące elementy członkowskie określonego typu.|  
|[EnumMembers — Metoda](imetadataimport-enummembers-method.md)|Wylicza tokeny MemberDef reprezentujące składowe określonego typu.|  
|[EnumMembersWithName — Metoda](imetadataimport-enummemberswithname-method.md)|Wylicza tokeny MemberDef reprezentujące elementy członkowskie określonego typu o określonej nazwie.|  
|[EnumMethodImpls — Metoda](imetadataimport-enummethodimpls-method.md)|Wylicza tokeny MethodBody i MethodDeclaration reprezentujące metody określonego typu.|  
|[EnumMethods — Metoda](imetadataimport-enummethods-method.md)|Wylicza tokeny MethodDef reprezentujące metody określonego typu.|  
|[EnumMethodSemantics — Metoda](imetadataimport-enummethodsemantics-method.md)|Wylicza właściwości i zdarzenia zmiany właściwości, z którymi powiązana jest określona metoda.|  
|[EnumMethodsWithName — Metoda](imetadataimport-enummethodswithname-method.md)|Wylicza metody, które mają określoną nazwę i które są definiowane przez typ, do którego odwołuje się określony token TypeDef.|  
|[EnumModuleRefs — Metoda](imetadataimport-enummodulerefs-method.md)|Wylicza tokeny ModuleRef reprezentujące importowane moduły.|  
|[EnumParams — Metoda](imetadataimport-enumparams-method.md)|Wylicza tokeny ParamDef reprezentujące parametry metody przywoływanej przez określony token MethodDef.|  
|[EnumPermissionSets — Metoda](imetadataimport-enumpermissionsets-method.md)|Wylicza uprawnienia dla obiektów w określonym zakresie metadanych.|  
|[EnumProperties — Metoda](imetadataimport-enumproperties-method.md)|Wylicza tokeny PropertyDef reprezentujące właściwości typu, do którego odwołuje się określony token TypeDef.|  
|[EnumSignatures — Metoda](imetadataimport-enumsignatures-method.md)|Wylicza tokeny podpisu reprezentujące podpisy autonomiczne w bieżącym zakresie.|  
|[EnumTypeDefs — Metoda](imetadataimport-enumtypedefs-method.md)|Wylicza tokeny TypeDef reprezentujące wszystkie typy w bieżącym zakresie.|  
|[EnumTypeRefs — Metoda](imetadataimport-enumtyperefs-method.md)|Wylicza tokeny TypeRef zdefiniowane w bieżącym zakresie metadanych.|  
|[EnumTypeSpecs — Metoda](imetadataimport-enumtypespecs-method.md)|Wylicza tokeny elementu TypeSpec zdefiniowane w bieżącym zakresie metadanych.|  
|[EnumUnresolvedMethods — Metoda](imetadataimport-enumunresolvedmethods-method.md)|Wylicza tokeny MemberDef reprezentujące nierozpoznane metody w bieżącym zakresie metadanych.|  
|[EnumUserStrings — Metoda](imetadataimport-enumuserstrings-method.md)|Wylicza tokeny ciągów reprezentujące stałe ciągi w bieżącym zakresie metadanych.|  
|[FindField — Metoda](imetadataimport-findfield-method.md)|Pobiera token FieldDef dla pola, które jest elementem członkowskim określonego typu i ma określoną nazwę i sygnaturę metadanych.|  
|[FindMember — Metoda](imetadataimport-findmember-method.md)|Pobiera wskaźnik do tokenu MemberDef dla elementu członkowskiego zdefiniowanego przez określony typ z określoną nazwą i sygnaturą metadanych.|  
|[FindMemberRef — Metoda](imetadataimport-findmemberref-method.md)|Pobiera wskaźnik do tokenu MemberRef dla elementu członkowskiego zdefiniowanego przez określony typ z określoną nazwą i sygnaturą metadanych.|  
|[FindMethod — Metoda](imetadataimport-findmethod-method.md)|Pobiera wskaźnik do tokenu MethodDef dla metody zdefiniowanej przez określony typ z określoną nazwą i sygnaturą metadanych.|  
|[FindTypeDefByName — Metoda](imetadataimport-findtypedefbyname-method.md)|Pobiera wskaźnik do tokenu metadanych TypeDef dla typu o określonej nazwie.|  
|[FindTypeRef — Metoda](imetadataimport-findtyperef-method.md)|Pobiera wskaźnik do tokenu metadanych elementu TypeRef, który odwołuje się do typu w określonym zakresie wyszukiwania o określonej nazwie.|  
|[GetClassLayout — Metoda](imetadataimport-getclasslayout-method.md)|Pobiera informacje o układzie dla klasy, do której odwołuje się określony token TypeDef.|  
|[GetCustomAttributeByName — Metoda](imetadataimport-getcustomattributebyname-method.md)|Pobiera wartość atrybutu niestandardowego pod nazwą.|  
|[GetCustomAttributeProps — Metoda](imetadataimport-getcustomattributeprops-method.md)|Pobiera wartość atrybutu niestandardowego z uwzględnieniem jego tokenu metadanych.|  
|[GetEventProps — Metoda](imetadataimport-geteventprops-method.md)|Pobiera informacje o metadanych (w tym typ deklarujący, metody dodawania i usuwania dla delegatów oraz wszelkie flagi i inne powiązane dane) dla zdarzenia reprezentowanego przez określony token zdarzenia.|  
|[GetFieldMarshal — Metoda](imetadataimport-getfieldmarshal-method.md)|Pobiera wskaźnik do natywnego, niezarządzanego typu pola reprezentowanego przez określony token metadanych pola.|  
|[GetFieldProps — Metoda](imetadataimport-getfieldprops-method.md)|Pobiera metadane skojarzone z polem, do którego odwołuje się określony token FieldDef.|  
|[GetInterfaceImplProps — Metoda](imetadataimport-getinterfaceimplprops-method.md)|Pobiera wskaźnik do tokenów metadanych dla typu, który implementuje określoną metodę i dla interfejsu, który deklaruje tę metodę.|  
|[GetMemberProps — Metoda](imetadataimport-getmemberprops-method.md)|Pobiera informacje o metadanych (w tym nazwę, podpis binarny i względny adres wirtualny) elementu członkowskiego typu, do którego odwołuje się określony token metadanych.|  
|[GetMemberRefProps — Metoda](imetadataimport-getmemberrefprops-method.md)|Pobiera metadane skojarzone z elementem członkowskim, do którego odwołuje się określony token.|  
|[GetMethodProps, metoda](imetadataimport-getmethodprops-method.md)|Pobiera metadane skojarzone z metodą przywoływaną przez określony token MethodDef.|  
|[GetMethodSemantics — Metoda](imetadataimport-getmethodsemantics-method.md)|Pobiera wskaźnik do relacji między metodą przywoływaną przez określony token MethodDef i sparowaną właściwością i zdarzeniem, do którego odwołuje się określony token EventProp.|  
|[GetModuleFromScope — Metoda](imetadataimport-getmodulefromscope-method.md)|Pobiera wskaźnik do tokenu metadanych dla modułu, do którego odwołuje się bieżący zakres metadanych.|  
|[GetModuleRefProps — Metoda](imetadataimport-getmodulerefprops-method.md)|Pobiera nazwę modułu, do którego odwołuje się określony token metadanych.|  
|[GetNameFromToken — Metoda](imetadataimport-getnamefromtoken-method.md)|Pobiera nazwę UTF-8 obiektu, do którego odwołuje się określony token metadanych.|  
|[GetNativeCallConvFromSig — Metoda](imetadataimport-getnativecallconvfromsig-method.md)|Pobiera natywną konwencję wywoływania dla metody reprezentowanej przez określony wskaźnik podpisu.|  
|[GetNestedClassProps — Metoda](imetadataimport-getnestedclassprops-method.md)|Pobiera token TypeDef dla otaczającego typu nadrzędnego określonego typu zagnieżdżonego.|  
|[GetParamForMethodIndex — Metoda](imetadataimport-getparamformethodindex-method.md)|Pobiera wskaźnik do tokenu, który reprezentuje parametr w określonej pozycji porządkowej w sekwencji parametrów metody dla metody reprezentowanej przez określony token MethodDef.|  
|[GetParamProps — Metoda](imetadataimport-getparamprops-method.md)|Pobiera wartości metadanych dla parametru, do którego odwołuje się określony token ParamDef.|  
|[GetPermissionSetProps — Metoda](imetadataimport-getpermissionsetprops-method.md)|Pobiera metadane skojarzone z System. Security. PermissionSet reprezentowane przez określony token uprawnień.|  
|[GetPinvokeMap](imetadataimport-getpinvokemap-method.md)|Pobiera token typu ModuleRef reprezentujący zestaw docelowy wywołania PInvoke.|  
|[GetPropertyProps — Metoda](imetadataimport-getpropertyprops-method.md)|Pobiera metadane skojarzone z właściwością reprezentowaną przez określony token.|  
|[GetRVA — Metoda](imetadataimport-getrva-method.md)|Pobiera przesunięcie względnego adresu wirtualnego obiektu kodu reprezentowanego przez określony token.|  
|[GetScopeProps — Metoda](imetadataimport-getscopeprops-method.md)|Pobiera nazwę i opcjonalnie identyfikator wersji zestawu lub modułu w bieżącym zakresie metadanych.|  
|[GetSigFromToken — Metoda](imetadataimport-getsigfromtoken-method.md)|Pobiera binarny podpis metadanych skojarzony z określonym tokenem.|  
|[GetTypeDefProps — Metoda](imetadataimport-gettypedefprops-method.md)|Zwraca informacje o metadanych dla typu reprezentowanego przez określony token TypeDef.|  
|[GetTypeRefProps — Metoda](imetadataimport-gettyperefprops-method.md)|Pobiera metadane skojarzone z typem przywoływanym przez określony token elementu TypeRef.|  
|[GetTypeSpecFromToken — Metoda](imetadataimport-gettypespecfromtoken-method.md)|Pobiera binarny podpis metadanych specyfikacji typu reprezentowanej przez określony token.|  
|[GetUserString — Metoda](imetadataimport-getuserstring-method.md)|Pobiera ciąg literału reprezentowanego przez określony token metadanych.|  
|[IsGlobal — Metoda](imetadataimport-isglobal-method.md)|Pobiera wartość wskazującą, czy pole, metoda lub typ reprezentowane przez określony token metadanych ma zakres globalny.|  
|[IsValidToken — Metoda](imetadataimport-isvalidtoken-method.md)|Pobiera wartość wskazującą, czy określony token przechowuje prawidłowe odwołanie do obiektu kodu.|  
|[ResetEnum — Metoda](imetadataimport-resetenum-method.md)|Resetuje określony moduł wyliczający do określonego położenia.|  
|[ResolveTypeRef — Metoda](imetadataimport-resolvetyperef-method.md)|Pobiera informacje o typie dla typu, do którego odwołuje się określony token elementu TypeRef.|  
  
## <a name="remarks"></a>Uwagi  
 Projekt `IMetaDataImport` interfejsu jest przeznaczony głównie do użytku przez narzędzia i usługi, które będą importować informacje o typie (na przykład narzędzia programistyczne) lub zarządzać wdrożonymi składnikami (na przykład w przypadku usług rozpoznawania/aktywacji). Metody w `IMetaDataImport` należą do następujących kategorii zadań:  
  
- Wyliczanie kolekcji elementów w zakresie metadanych.  
  
- Znajdowanie elementu, który ma określony zestaw właściwości.  
  
- Pobieranie właściwości określonego elementu.  
  
- Metody get są specjalnie zaprojektowane do zwracania właściwości jednowartościowych elementu metadanych. Gdy właściwość jest odwołaniem do innego elementu, zwracany jest token dla tego elementu. Dowolny typ wejściowy wskaźnika może mieć wartość NULL, aby wskazać, że określona wartość nie jest żądana. Aby uzyskać właściwości, które są zasadniczo obiektami kolekcji (na przykład kolekcje interfejsów, które implementuje Klasa), użyj metod wyliczania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy metadanych](metadata-interfaces.md)
- [IMetaDataImport2, interfejs](imetadataimport2-interface.md)

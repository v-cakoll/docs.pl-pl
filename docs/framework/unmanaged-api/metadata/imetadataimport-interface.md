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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c6a65eae91bf3b44fc2b49588ead5ed178d7326f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777458"
---
# <a name="imetadataimport-interface"></a>IMetaDataImport — Interfejs
Zawiera metody służące do importowania i manipulowanie nimi istniejące metadane z plików przenośnych plików wykonywalnych (PE) lub innego źródła, takich jak biblioteka typów lub dane binarne autonomicznej, czasu wykonywania metadanych.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CloseEnum, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-closeenum-method.md)|Zamyka modułu wyliczającego z określonego dojścia.|  
|[CountEnum, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-countenum-method.md)|Pobiera liczbę elementów w moduł wyliczający z określonego dojścia.|  
|[EnumCustomAttributes, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md)|Wylicza listę tokeny niestandardowe definicja atrybutu skojarzone z określonego typu lub składowej.|  
|[EnumEvents, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumevents-method.md)|Wylicza tokenów definicji zdarzeń dla określonego tokenu TypeDef.|  
|[EnumFields, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md)|Wylicza FieldDef tokeny dla danego typu odwołuje się określony token TypeDef.|  
|[EnumFieldsWithName, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfieldswithname-method.md)|Wylicza tokenów FieldDef określonego typu o określonej nazwie.|  
|[EnumInterfaceImpls, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enuminterfaceimpls-method.md)|Wylicza tokenów MethodDef reprezentujący implementacje interfejsu.|  
|[EnumMemberRefs, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummemberrefs-method.md)|Wylicza tokenów MemberRef reprezentujących elementy określonego typu.|  
|[EnumMembers, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md)|Wylicza tokenów MemberDef reprezentujących elementy określonego typu.|  
|[EnumMembersWithName, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummemberswithname-method.md)|Wylicza tokenów MemberDef reprezentujących elementy członkowskie określonego typu o określonej nazwie.|  
|[EnumMethodImpls, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodimpls-method.md)|Wylicza MethodBody i MethodDeclaration tokenów reprezentujący metody określonego typu.|  
|[EnumMethods, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md)|Wylicza tokenów MethodDef reprezentujący metody określonego typu.|  
|[EnumMethodSemantics, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodsemantics-method.md)|Wylicza właściwości i zdarzenia zmiany właściwości, do których odnosi się określonej metody.|  
|[EnumMethodsWithName, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodswithname-method.md)|Wylicza metod, które mają określoną nazwą i które są definiowane przez typ odwołuje się określony token TypeDef.|  
|[EnumModuleRefs, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummodulerefs-method.md)|Wylicza element ModuleRef tokenów, które reprezentują zaimportowanych modułów.|  
|[EnumParams, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumparams-method.md)|Wylicza tokenów ParamDef reprezentującą parametry metody odwołuje się określony token MethodDef.|  
|[EnumPermissionSets, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumpermissionsets-method.md)|Wylicza uprawnienia dla obiektów w zakresie określonych metadanych.|  
|[EnumProperties, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumproperties-method.md)|Wylicza tokenów właściwości reprezentujących właściwości typu odwołuje się określony token TypeDef.|  
|[EnumSignatures, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumsignatures-method.md)|Wylicza tokenów sygnatur reprezentujący autonomicznej podpisów w bieżącym zakresie.|  
|[EnumTypeDefs, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)|Wylicza tokenów TypeDef reprezentujący wszystkie typy w bieżącym zakresie.|  
|[EnumTypeRefs, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtyperefs-method.md)|Wylicza tokeny TypeRef zdefiniowane w bieżącym zakresie metadanych.|  
|[EnumTypeSpecs, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypespecs-method.md)|Wylicza TypeSpec tokeny zdefiniowane w bieżącym zakresie metadanych.|  
|[EnumUnresolvedMethods, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumunresolvedmethods-method.md)|Wylicza tokenów MemberDef reprezentujący nierozwiązane metod w bieżącym zakresie metadanych.|  
|[EnumUserStrings, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumuserstrings-method.md)|Wylicza tokenów ciąg reprezentujący zakodowane sprzętowo ciągi w bieżącym zakresie metadanych.|  
|[FindField, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md)|Pobiera token FieldDef dla pola, które jest elementem członkowskim o określonym typie, a ma określoną nazwę i podpis metadanych.|  
|[FindMember, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmember-method.md)|Pobiera wskaźnik do MemberDef tokenu dla elementu członkowskiego zdefiniowane przez określony typ o określonej nazwie i sygnaturze metadanych.|  
|[FindMemberRef, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmemberref-method.md)|Pobiera wskaźnik do elementu MemberRef tokenu dla elementu członkowskiego zdefiniowane przez określony typ o określonej nazwie i sygnaturze metadanych.|  
|[FindMethod, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md)|Pobiera wskaźnik do MethodDef tokenu dla metody zdefiniowane przez określony typ o określonej nazwie i sygnaturze metadanych.|  
|[FindTypeDefByName, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findtypedefbyname-method.md)|Pobiera wskaźnik do metadanych TypeDef tokenu dla typu o określonej nazwie.|  
|[FindTypeRef, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findtyperef-method.md)|Pobiera wskaźnik do tokenu metadanych TypeRef, który odwołuje się do typu w zakresie wyszukiwania o określonej nazwie.|  
|[GetClassLayout, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md)|Pobiera informacje o układzie dla klasy odwołuje się określony element TypeDef token.|  
|[GetCustomAttributeByName, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getcustomattributebyname-method.md)|Pobiera wartość atrybutu niestandardowego nadać jej nazwę.|  
|[GetCustomAttributeProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getcustomattributeprops-method.md)|Pobiera wartość atrybutu niestandardowego, biorąc pod uwagę jego token metadanych.|  
|[GetEventProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-geteventprops-method.md)|Pobiera informacje o metadanych (w tym typ deklarujący Dodaj i Usuń metod dla obiektów delegowanych oraz flag i inne powiązane dane) dla zdarzeń, reprezentowane przez token określonego zdarzenia.|  
|[GetFieldMarshal, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getfieldmarshal-method.md)|Pobiera wskaźnik do typu macierzystego, niezarządzanych pola, reprezentowane przez określony token metadanych pola.|  
|[GetFieldProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getfieldprops-method.md)|Pobiera metadane skojarzone z polem odwołuje się określona FieldDef token.|  
|[GetInterfaceImplProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getinterfaceimplprops-method.md)|Pobiera wskaźnik do tokenów metadanych dla typu, który implementuje określonej metody i interfejsu, który deklaruje tej metody.|  
|[GetMemberProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmemberprops-method.md)|Pobiera informacje o metadanych (w tym nazwę, podpis binarny i względny adres wirtualny) elementu członkowskiego typu odwołuje się token określonych metadanych.|  
|[GetMemberRefProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmemberrefprops-method.md)|Pobiera metadane skojarzone z elementem członkowskim odwołuje się określony token.|  
|[GetMethodProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmethodprops-method.md)|Pobiera metadane skojarzone z metody odwołuje się określona MethodDef token.|  
|[GetMethodSemantics, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmethodsemantics-method.md)|Pobiera wskaźnik do relacji między odwołuje się określony token MethodDef oraz sparowany właściwości, metody i zdarzenia odwołuje się określona EventProp tokenu.|  
|[GetModuleFromScope, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmodulefromscope-method.md)|Pobiera wskaźnik do metadanych tokenu dla modułu odwołania w bieżącym zakresie metadanych.|  
|[GetModuleRefProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmodulerefprops-method.md)|Pobiera nazwę modułu odwołuje się token określonych metadanych.|  
|[GetNameFromToken, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnamefromtoken-method.md)|Pobiera nazwę UTF-8 zawiera odwołanie do tokenu metadanych określonego obiektu.|  
|[GetNativeCallConvFromSig, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnativecallconvfromsig-method.md)|Pobiera natywnych konwencja wywołania dla metody, która jest reprezentowana przez wskaźnik określonej sygnaturze.|  
|[GetNestedClassProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnestedclassprops-method.md)|Pobiera token definicji typu otaczającego typu nadrzędny określonego typu zagnieżdżonego.|  
|[GetParamForMethodIndex, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getparamformethodindex-method.md)|Pobiera wskaźnik do tokenu, który reprezentuje parametr w określonej pozycji numer porządkowy w sekwencji parametry metody do metody reprezentowanej przez określony token MethodDef.|  
|[GetParamProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getparamprops-method.md)|Pobiera metadane wartości dla parametru odwołuje się określona ParamDef token.|  
|[GetPermissionSetProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpermissionsetprops-method.md)|Pobiera metadane skojarzone z System.Security.PermissionSet reprezentowany przez określony token uprawnień.|  
|[GetPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpinvokemap-method.md)|Pobiera element ModuleRef jest token reprezentujący zestaw docelowy wywołania funkcji PInvoke.|  
|[GetPropertyProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpropertyprops-method.md)|Pobiera metadane skojarzone z właściwością, reprezentowane przez określony token.|  
|[GetRVA, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getrva-method.md)|Pobiera przesunięcie względne wirtualny adres obiektu kodu, reprezentowane przez określony token.|  
|[GetScopeProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md)|Pobiera nazwę i opcjonalnie identyfikator wersji zestaw lub moduł w bieżącym zakresie metadanych.|  
|[GetSigFromToken, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getsigfromtoken-method.md)|Pobiera podpisu binarne metadane skojarzone z określonym tokenem.|  
|[GetTypeDefProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettypedefprops-method.md)|Zwraca informacje o metadanych dla typu reprezentowanego przez określony token TypeDef.|  
|[GetTypeRefProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettyperefprops-method.md)|Pobiera metadane skojarzone z typem odwołuje się określona TypeRef token.|  
|[GetTypeSpecFromToken, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettypespecfromtoken-method.md)|Pobiera podpisu metadanych binarne specyfikacji typu reprezentowanego przez określony token.|  
|[GetUserString, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getuserstring-method.md)|Pobiera ciąg literału, reprezentowane przez token określonych metadanych.|  
|[IsGlobal, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-isglobal-method.md)|Pobiera wartość wskazującą, czy pola, metody lub typu reprezentowanego przez token metadanych w określonym zakresie globalnym.|  
|[IsValidToken, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-isvalidtoken-method.md)|Pobiera wartość wskazującą, czy określony token zawiera prawidłowe odwołanie do obiektu kodu.|  
|[ResetEnum, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-resetenum-method.md)|Resetuje określonego modułu wyliczającego do określonej pozycji.|  
|[ResolveTypeRef, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-resolvetyperef-method.md)|Pobiera typ informacje dotyczące danego typu odwołuje się określony token TypeRef.|  
  
## <a name="remarks"></a>Uwagi  
 Projekt `IMetaDataImport` interfejsu zasadniczo mają być wykorzystywane przez narzędzia i usługi, które będą importowanie informacji o typie (na przykład, narzędzia programistyczne) i zarządzaniu nim wdrożone składniki (na przykład rozpoznawanie/aktywacji usługi). Metody w `IMetaDataImport` można podzielić na następujące kategorie zadań:  
  
- Wyliczanie kolekcji elementów w zakresie metadanych.  
  
- Znajdowanie elementu, który ma określony zbiór właściwości.  
  
- Pobieranie właściwości określonego elementu.  
  
- Metody Get zostały zaprojektowane specjalnie do zwrócenia pojedynczej wartości właściwości elementu metadanych. Gdy właściwość jest odwołaniem do innego elementu, zwracany jest token dla tego elementu. Dowolny typ danych wejściowych wskaźnik może mieć wartość NULL, aby wskazać, że określonej wartości nie jest wymagany. Aby uzyskać właściwości, które są zasadniczo kolekcji obiektów (na przykład zbiór interfejsów, które implementuje klasa), należy użyć metod wyliczenia.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

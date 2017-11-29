---
title: "IMetaDataImport — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport
helpviewer_keywords: IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 0adbbd35-5e8d-4fec-8268-dc70a07c5975
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6c7f1c7e99df61cc0cd33e1697de52a039d412df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport-interface"></a>IMetaDataImport — Interfejs
Udostępnia metody do importowania i manipulowanie istniejących metadanych z pliku przenośny plik wykonywalny (PE) lub innego źródła, takich jak biblioteki typów lub binary metadanych autonomicznej, czasu wykonywania.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CloseEnum — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-closeenum-method.md)|Zamyka modułu wyliczającego z określonego dojścia.|  
|[CountEnum — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-countenum-method.md)|Pobiera liczbę elementów w moduł wyliczający z określonego dojścia.|  
|[EnumCustomAttributes — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md)|Wylicza listę tokenów niestandardowych definicja atrybutu skojarzone z określonego typu lub elementu członkowskiego.|  
|[EnumEvents — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumevents-method.md)|Wylicza tokeny definicji zdarzenia dla określony token TypeDef.|  
|[EnumFields — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md)|Wylicza FieldDef tokeny dla typu odwołuje się określony token TypeDef.|  
|[EnumFieldsWithName — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfieldswithname-method.md)|Wylicza tokenów FieldDef określonego typu o określonej nazwie.|  
|[EnumInterfaceImpls — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enuminterfaceimpls-method.md)|Wylicza tokeny MethodDef reprezentujący implementacji interfejsu.|  
|[EnumMemberRefs — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummemberrefs-method.md)|Wylicza tokenów elementu MemberRef reprezentujący elementy członkowskie określonego typu.|  
|[EnumMembers — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md)|Wylicza tokenów MemberDef reprezentujący elementy członkowskie określonego typu.|  
|[EnumMembersWithName — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummemberswithname-method.md)|Wylicza tokenów MemberDef reprezentujący elementy członkowskie określonego typu o określonej nazwie.|  
|[EnumMethodImpls — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodimpls-method.md)|Wylicza MethodBody i MethodDeclaration tokeny reprezentujący metody określonego typu.|  
|[EnumMethods — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md)|Wylicza tokeny MethodDef reprezentujący metody określonego typu.|  
|[EnumMethodSemantics — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodsemantics-method.md)|Wylicza właściwości i zdarzenia zmiany właściwości, których dotyczy określonej metody.|  
|[EnumMethodsWithName — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodswithname-method.md)|Wylicza metody tym, które są definiowane przez typ odwołuje się określony token TypeDef określonej nazwy.|  
|[EnumModuleRefs — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummodulerefs-method.md)|Wylicza tokeny element ModuleRef, które reprezentują zaimportowanych modułów.|  
|[EnumParams — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumparams-method.md)|Wylicza tokenów ParamDef reprezentujący parametry metody odwołuje się określony token MethodDef.|  
|[EnumPermissionSets — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumpermissionsets-method.md)|Wylicza uprawnienia dla obiektów w zakresie określonych metadanych.|  
|[EnumProperties — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumproperties-method.md)|Wylicza tokeny właściwości reprezentujący właściwości typu odwołuje się określony token TypeDef.|  
|[EnumSignatures — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumsignatures-method.md)|Wylicza tokeny sygnatury reprezentujący autonomicznej podpisów w bieżącym zakresie.|  
|[EnumTypeDefs — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)|Wylicza tokeny TypeDef reprezentujący wszystkie typy w bieżącym zakresie.|  
|[EnumTypeRefs — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtyperefs-method.md)|Wylicza tokeny TypeRef zdefiniowane w bieżącym zakresie metadanych.|  
|[EnumTypeSpecs — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypespecs-method.md)|Wylicza tokenów elementu TypeSpec zdefiniowany w bieżącym zakresie metadanych.|  
|[EnumUnresolvedMethods — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumunresolvedmethods-method.md)|Wylicza tokenów MemberDef reprezentujący nierozwiązane metod w bieżącym zakresie metadanych.|  
|[EnumUserStrings — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumuserstrings-method.md)|Wylicza tokeny ciąg reprezentujący ustalony ciągów w bieżącym zakresie metadanych.|  
|[FindField — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md)|Pobiera token FieldDef pola, które jest członkiem określonego typu i ma określoną nazwę i sygnaturę metadanych.|  
|[FindMember — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmember-method.md)|Pobiera wskaźnik do MemberDef token elementu członkowskiego zdefiniowane przez określony typ o określonej nazwie i podpisie metadanych.|  
|[FindMemberRef — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmemberref-method.md)|Pobiera wskaźnik do elementu MemberRef token elementu członkowskiego zdefiniowane przez określony typ o określonej nazwie i podpisie metadanych.|  
|[FindMethod — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md)|Pobiera wskaźnik do elementu MethodDef token metody zdefiniowane przez określony typ o określonej nazwie i podpisie metadanych.|  
|[FindTypeDefByName — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findtypedefbyname-method.md)|Pobiera wskaźnik do metadanych elementu TypeDef token dla typu o określonej nazwie.|  
|[FindTypeRef — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findtyperef-method.md)|Pobiera wskaźnik do tokenu metadanych elementu TypeRef, który odwołuje się do typu w zakresie określonym wyszukiwania o określonej nazwie.|  
|[GetClassLayout — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md)|Pobiera informacje o układzie dla klasy odwołuje się określony element TypeDef token.|  
|[GetCustomAttributeByName — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getcustomattributebyname-method.md)|Pobiera wartość atrybutu niestandardowego, jego nazwę.|  
|[GetCustomAttributeProps — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getcustomattributeprops-method.md)|Pobiera wartość atrybutu niestandardowego, podane jego token metadanych.|  
|[GetEventProps — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-geteventprops-method.md)|Pobiera informacje o metadanych (w tym typ deklarujący, Dodaj i Usuń metody delegatów oraz wszystkie flagi i inne powiązane dane) dla zdarzenia reprezentowany przez token określonego zdarzenia.|  
|[GetFieldMarshal — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getfieldmarshal-method.md)|Pobiera wskaźnik do typu macierzystego, niezarządzanych pola reprezentowany przez określony token pola w metadanych.|  
|[GetFieldProps — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getfieldprops-method.md)|Pobiera metadane skojarzone z polem odwołuje się określony FieldDef token.|  
|[GetInterfaceImplProps — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getinterfaceimplprops-method.md)|Pobiera wskaźnik do tokenów metadanych dla typu, który implementuje określonej metody i interfejsie, który deklaruje, że metoda.|  
|[GetMemberProps — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmemberprops-method.md)|Pobiera informacje o metadanych (w tym nazwę, podpis binarny i adres względny wirtualnego) elementu członkowskiego typu odwołuje się token określonych metadanych.|  
|[GetMemberRefProps — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmemberrefprops-method.md)|Pobiera metadane skojarzone z elementem członkowskim odwołuje się określony token.|  
|[GetMethodProps — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmethodprops-method.md)|Pobiera metadane skojarzone z metody odwołuje się określony MethodDef token.|  
|[GetMethodSemantics — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmethodsemantics-method.md)|Pobiera wskaźnik do relacji między metody odwołuje się określony token MethodDef i sparowanego właściwości i zdarzenia odwołuje się określony EventProp token.|  
|[GetModuleFromScope — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmodulefromscope-method.md)|Pobiera wskaźnik do metadanych token występujący w odwołaniu w bieżącym zakresie metadane modułu.|  
|[GetModuleRefProps — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmodulerefprops-method.md)|Pobiera nazwę modułu odwołuje się token określonych metadanych.|  
|[GetNameFromToken — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnamefromtoken-method.md)|Pobiera nazwę UTF-8 obiektu odwołuje się token określonych metadanych.|  
|[GetNativeCallConvFromSig — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnativecallconvfromsig-method.md)|Pobiera natywnego Konwencję wywoływania dla metody, która jest reprezentowana przez wskaźnik określoną sygnaturą.|  
|[GetNestedClassProps — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnestedclassprops-method.md)|Pobiera token TypeDef dla typu otaczającego nadrzędnego dla określonego typu zagnieżdżonego.|  
|[GetParamForMethodIndex — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getparamformethodindex-method.md)|Pobiera wskaźnik do tokenu, który reprezentuje parametr w określonej pozycji porządkowej w sekwencji parametrów metody metodę reprezentowaną przez określony token MethodDef.|  
|[GetParamProps — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getparamprops-method.md)|Pobiera wartości metadanych dla parametru odwołuje się określony ParamDef token.|  
|[GetPermissionSetProps — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpermissionsetprops-method.md)|Pobiera metadane skojarzone z System.Security.PermissionSet reprezentowany przez określony token uprawnień.|  
|[GetPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpinvokemap-method.md)|Pobiera element ModuleRef token reprezentujący zestaw docelowy wywołania funkcji PInvoke.|  
|[GetPropertyProps — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpropertyprops-method.md)|Pobiera metadane skojarzone z właściwości reprezentowanej przez określony token.|  
|[GetRVA — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getrva-method.md)|Pobiera przesunięcie wirtualny adres względny kod obiektu reprezentowanego przez określony token.|  
|[GetScopeProps — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md)|Pobiera nazwę i opcjonalnie identyfikator wersji zestawu lub modułu w bieżącym zakresie metadanych.|  
|[GetSigFromToken — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getsigfromtoken-method.md)|Pobiera podpisu binarne metadane skojarzone z określonym tokenem.|  
|[GetTypeDefProps — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettypedefprops-method.md)|Zwraca informacje o metadanych dla typu reprezentowanego przez określony token TypeDef.|  
|[GetTypeRefProps — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettyperefprops-method.md)|Pobiera metadane skojarzone z typem odwołuje się określony element TypeRef token.|  
|[GetTypeSpecFromToken — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettypespecfromtoken-method.md)|Pobiera podpisu metadanych binarne specyfikacji typu reprezentowanego przez określony token.|  
|[GetUserString — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getuserstring-method.md)|Pobiera ciąg literału reprezentowany przez token określonych metadanych.|  
|[IsGlobal — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-isglobal-method.md)|Pobiera wartość wskazującą, czy pola, metody lub typu reprezentowanego przez token określonych metadanych, ma zasięg globalny.|  
|[IsValidToken — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-isvalidtoken-method.md)|Pobiera wartość wskazującą, czy określony token jest prawidłowym odwołaniem do obiektu kodu.|  
|[ResetEnum — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-resetenum-method.md)|Resetuje określonego modułu wyliczającego do określonej pozycji.|  
|[ResolveTypeRef — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-resolvetyperef-method.md)|Pobiera typ informacje dotyczące typu odwołuje się określony token TypeRef.|  
  
## <a name="remarks"></a>Uwagi  
 Projekt `IMetaDataImport` interfejsu jest przeznaczony głównie do użycia przez narzędzia i usługi, które będą importowanie informacji o typie (na przykład narzędzia deweloperskie) lub zarządzania wdrożeniu składników (na przykład rozwiązania/aktywacji usługi). Metody w `IMetaDataImport` można podzielić na następujące kategorie zadań:  
  
-   Wyliczanie kolekcji elementów w zakresie metadanych.  
  
-   Wyszukiwanie elementu, który ma określony zbiór właściwości.  
  
-   Pobieranie właściwości określonego elementu.  
  
-   Metody Get są zaprojektowane specjalnie do zwrócenia pojedynczej wartości właściwości elementu metadanych. Gdy właściwość jest odwołaniem do innego elementu, jest zwracany token dla tego elementu. Typ danych wejściowych żadnych wskaźnika może być NULL, aby wskazać, że określonej wartości nie jest wymagany. Aby uzyskać właściwości, które są zasadniczo kolekcji obiektów (na przykład kolekcja interfejsów, które implementuje klasy), należy użyć metody wyliczania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [IMetaDataImport2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

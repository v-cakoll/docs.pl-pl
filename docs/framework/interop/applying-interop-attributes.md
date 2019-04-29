---
title: Stosowanie atrybutów międzyoperacyjności
ms.date: 03/30/2017
helpviewer_keywords:
- design-time attributes
- .NET Framework, exposing components to COM
- attributes [.NET Framework], design-time functionality
- conversion-tool attributes
- attributes [.NET Framework], interop-specific
- attributes [.NET Framework], conversion-tool
- interoperation with unmanaged code, applying attributes
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
- COM interop, applying attributes
ms.assetid: b6014613-641c-4912-9e2f-83a99210a037
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83afabf58048620b3b9936560f2b3fdf1e2039d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61643676"
---
# <a name="applying-interop-attributes"></a>Stosowanie atrybutów międzyoperacyjności
<xref:System.Runtime.InteropServices> Przestrzeń nazw zawiera trzy kategorie atrybuty specyficzne dla współdziałania: stosowane przez użytkownika w czasie projektowania, stosowane przez narzędzia międzyoperacyjności modelu COM i interfejsów API w procesie konwersji i stosowane przez współdziałania z modelem COM.  
  
 Jeśli nie jesteś zaznajomiony z zadaniem stosowanie atrybutów do zarządzanego kodu, zobacz [Extending Metadata Using Attributes](../../../docs/standard/attributes/index.md). Podobnie jak inne atrybuty niestandardowe można zastosować atrybuty specyficzne dla międzyoperacyjności na typy, metody, właściwości, parametry, pól i innych członków.  
  
## <a name="design-time-attributes"></a>Atrybuty czasu projektowania  
 Można dostosować wynik procesu konwersji, wykonywane przez narzędzia międzyoperacyjności modelu COM i interfejsów API za pomocą atrybutów w czasie projektowania. W poniższej tabeli opisano atrybuty, które można zastosować do Twojej zarządzanym kodzie źródłowym. Narzędzia międzyoperacyjności modelu COM, czasem może mają zastosowanie również atrybutów opisanych w tej tabeli.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|<xref:System.Runtime.InteropServices.AutomationProxyAttribute>|Określa, czy typ powinny być wprowadzane za pomocą organizatora automatyzacji lub niestandardowy serwer proxy i wycinka.|  
|<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>|Określa typ interfejsu generowana dla klasy.|  
|<xref:System.Runtime.InteropServices.CoClassAttribute>|Określa identyfikator CLSID oryginalnej klasy coclass zaimportowano z biblioteki typów.<br /><br /> Narzędzia międzyoperacyjności COM zazwyczaj stosuje się ten atrybut.|  
|<xref:System.Runtime.InteropServices.ComImportAttribute>|Wskazuje, że definicję klasy coclass lub interfejs został zaimportowany z biblioteki typów COM. Środowisko wykonawcze używa tej flagi, aby wiedzieć, jak aktywować i organizowania typu. Tego atrybutu uniemożliwia typ eksportowany do biblioteki typów.<br /><br /> Narzędzia międzyoperacyjności COM zazwyczaj stosuje się ten atrybut.|  
|<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>|Wskazuje, że metoda powinna być wywoływana, gdy zestaw jest zarejestrowana w celu korzystania z modelu COM, tak, aby kod napisany przez użytkownika mogą być wykonywane podczas procesu rejestracji.|  
|<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>|Identyfikuje interfejsy, które są źródła zdarzeń dla tej klasy.<br /><br /> Narzędzia międzyoperacyjności COM można zastosować ten atrybut.|  
|<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>|Wskazuje, że metoda powinna być wywoływana, gdy zestaw jest wyrejestrowywany z modelu COM, tak, aby kod napisany przez użytkownika można wykonywać w procesie.|  
|<xref:System.Runtime.InteropServices.ComVisibleAttribute>|Renderuje typy niewidoczne dla modelu COM, gdy wartość atrybutu jest równa **false**. Ten atrybut można stosować do poszczególnych typu lub do całego zestawu, aby ustawić widoczność COM. Domyślnie wszystkie typy zarządzane, publiczne są widoczne; Ten atrybut nie jest wymagana, aby stały się widoczne.|  
|<xref:System.Runtime.InteropServices.DispIdAttribute>|Określa identyfikatora wysyłania COM (identyfikator DISPID) pola lub metody. Ten atrybut zawiera identyfikator DISPID dla metody, pola lub właściwości, które opisano w nim.<br /><br /> Narzędzia międzyoperacyjności COM można zastosować ten atrybut.|  
|<xref:System.Runtime.InteropServices.FieldOffsetAttribute>|Wskazuje fizyczne położenie każdego pola w obrębie klasy, gdy jest używane z **structlayoutattribute —** i **LayoutKind** jest ustawiona na jawne.|  
|<xref:System.Runtime.InteropServices.GuidAttribute>|Określa unikatowy identyfikator globalny (GUID), z klasą, interfejsem lub całej biblioteki typów. Ciąg przekazywany do atrybutu musi być w formacie, który jest argumentem dopuszczalne konstruktora dla typu **System.Guid**.<br /><br /> Narzędzia międzyoperacyjności COM można zastosować ten atrybut.|  
|<xref:System.Runtime.InteropServices.IDispatchImplAttribute>|Wskazuje, które **IDispatch** interfejsu implementacji środowiska uruchomieniowego języka wspólnego używa podczas udostępniania podwójne interfejsy i dispinterfaces dla modelu COM.|  
|<xref:System.Runtime.InteropServices.InAttribute>|Wskazuje, że dane powinny być wprowadzane w do obiektu wywołującego. Może służyć do parametrów atrybutu.|  
|<xref:System.Runtime.InteropServices.InterfaceTypeAttribute>|Określa, jak zarządzanego interfejsu jest narażony na klientów modelu COM (podwójne, IUnknown derived, lub tylko IDispatch).<br /><br /> Narzędzia międzyoperacyjności COM można zastosować ten atrybut.|  
|<xref:System.Runtime.InteropServices.LCIDConversionAttribute>|Wskazuje, że podpis metody niezarządzanego parametr LCID.<br /><br /> Narzędzia międzyoperacyjności COM można zastosować ten atrybut.|  
|<xref:System.Runtime.InteropServices.MarshalAsAttribute>|Wskazuje, jak dane w polach lub parametry powinny być wprowadzane między kodem zarządzanym i niezarządzanym. Ten atrybut jest opcjonalny zawsze w przypadku, ponieważ każdy typ danych ma domyślne zachowanie marshalingu.<br /><br /> Narzędzia międzyoperacyjności COM można zastosować ten atrybut.|  
|<xref:System.Runtime.InteropServices.OptionalAttribute>|Wskazuje, że parametr jest opcjonalny.<br /><br /> Narzędzia międzyoperacyjności COM można zastosować ten atrybut.|  
|<xref:System.Runtime.InteropServices.OutAttribute>|Wskazuje, czy dane w polu lub parametr musi być organizowany z obiektu o nazwie do obiektu wywołującego.|  
|<xref:System.Runtime.InteropServices.PreserveSigAttribute>|Pomija HRESULT lub retval przekształcenie podpisu, zwykle odbywa się podczas współdziałanie wywołań. Ten atrybut ma wpływ na przekazywanie oraz eksportowanie biblioteki typów.<br /><br /> Narzędzia międzyoperacyjności COM można zastosować ten atrybut.|  
|<xref:System.Runtime.InteropServices.ProgIdAttribute>|Określa identyfikator ProgID klasy .NET Framework. Może służyć do klas atrybutów.|  
|<xref:System.Runtime.InteropServices.StructLayoutAttribute>|Steruje fizyczny układ pól klasy.<br /><br /> Narzędzia międzyoperacyjności COM można zastosować ten atrybut.|  
  
## <a name="conversion-tool-attributes"></a>Atrybuty narzędzia konwersji  
 W poniższej tabeli opisano atrybuty, które narzędzia międzyoperacyjności modelu COM, mają zastosowanie w procesie konwersji. Te atrybuty nie są stosowane w czasie projektowania.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|<xref:System.Runtime.InteropServices.ComAliasNameAttribute>|Wskazuje alias COM dla typu parametru lub pola. Może służyć do parametrów atrybutu, pola, lub zwracanych wartości.|  
|<xref:System.Runtime.InteropServices.ComConversionLossAttribute>|Wskazuje, że informacji na temat klasy lub interfejsu została utracona został zaimportowany z biblioteki typów, do zestawu.|  
|<xref:System.Runtime.InteropServices.ComEventInterfaceAttribute>|Identyfikuje interfejs źródłowy, a klasa, która implementuje metody interfejsu zdarzenia.|  
|<xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute>|Wskazuje, że zestaw pierwotnie został zaimportowany z biblioteki typów COM. Ten atrybut zawiera definicję typu biblioteki oryginalnej biblioteki typów.|  
|<xref:System.Runtime.InteropServices.TypeLibFuncAttribute>|Zawiera **FUNCFLAGS** , zostały pierwotnie zaimportowane dla tej funkcji z biblioteki typów COM.|  
|<xref:System.Runtime.InteropServices.TypeLibTypeAttribute>|Zawiera **TYPEFLAGS** , zostały pierwotnie zaimportowane dla tego typu z biblioteki typów COM.|  
|<xref:System.Runtime.InteropServices.TypeLibVarAttribute>|Zawiera **VARFLAGS** , zostały pierwotnie zaimportowane dla tej zmiennej w bibliotece typów modelu COM.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices>
- [Udostępnianie składników .NET Framework modelowi COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)
- [Atrybuty](../../../docs/standard/attributes/index.md)
- [Kwalifikowanie typów .NET do międzyoperacyjności](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md)
- [Pakowanie zestawu dla modelu COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md)

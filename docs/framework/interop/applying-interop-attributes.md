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
ms.openlocfilehash: 554ea7c54973852510e539000baf03bdce8e7bcf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392567"
---
# <a name="applying-interop-attributes"></a>Stosowanie atrybutów międzyoperacyjności
<xref:System.Runtime.InteropServices> Przestrzeń nazw zawiera trzy kategorie atrybutów specyficzny dla międzyoperacyjności: stosowanych przez użytkownika w czasie projektowania, stosowane przez COM interop narzędzia i interfejsy API w procesie konwersji i stosowane przez COM interop.  
  
 Jeśli znasz zadanie stosowanie atrybutów do kodu zarządzanego, zobacz [rozszerzanie metadanych za pomocą atrybutów](../../../docs/standard/attributes/index.md). Podobnie jak inne atrybuty niestandardowe można stosować atrybutów specyficzny dla międzyoperacyjności do typów, metody, właściwości, parametry, pól i innych członków.  
  
## <a name="design-time-attributes"></a>Atrybuty czasu projektowania  
 Można dostosować wyniki procesu konwersji z zastosowaniem modelu COM interop narzędzia i interfejsy API za pomocą atrybutów czasu projektowania. W poniższej tabeli opisano atrybuty, które można zastosować do kodu źródłowego zarządzanych. COM interop narzędzia, czasem może mieć zastosowanie także atrybuty opisane w tej tabeli.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|<xref:System.Runtime.InteropServices.AutomationProxyAttribute>|Określa, czy należy zorganizować typu przy użyciu automatyzacji organizatora niestandardowego serwera proxy i stub.|  
|<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>|Określa typ interfejsu wygenerowane klasy.|  
|<xref:System.Runtime.InteropServices.CoClassAttribute>|Określa identyfikator CLSID oryginalnej klasy coclass zaimportowany z biblioteki typów.<br /><br /> COM interop narzędzia zazwyczaj zastosowaniu tego atrybutu.|  
|<xref:System.Runtime.InteropServices.ComImportAttribute>|Wskazuje, że definicja klasy coclass lub interfejs został zaimportowany z biblioteki typów COM. Środowisko uruchomieniowe używa tej flagi wiedzieć, jak aktywować i organizowania typu. Ten atrybut uniemożliwia używanie typu są eksportowane do biblioteki typów.<br /><br /> COM interop narzędzia zazwyczaj zastosowaniu tego atrybutu.|  
|<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>|Wskazuje, że metoda powinna być wywoływana podczas zestawu jest zarejestrowany do użytkowania z modelu COM, tak, aby kodu napisanego przez użytkownika mogą być wykonywane podczas procesu rejestracji.|  
|<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>|Identyfikuje interfejsów, które są źródła zdarzeń dla tej klasy.<br /><br /> COM interop narzędzia można zastosować tego atrybutu.|  
|<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>|Wskazuje, czy metoda powinna być wywoływana gdy zestaw jest zarejestrowany z modelu COM, dzięki czemu możliwe wykonanie kodu napisanego przez użytkownika, podczas procesu.|  
|<xref:System.Runtime.InteropServices.ComVisibleAttribute>|Renderuje typy niewidocznej dla modelu COM gdy jest równa wartości atrybutu **false**. Ten atrybut można stosować do poszczególnych typów lub całego zestawu do kontrolowania widoczność COM. Domyślnie wszystkie typy zarządzane, public są widoczne; Ten atrybut nie jest potrzebna, aby je wyświetlić.|  
|<xref:System.Runtime.InteropServices.DispIdAttribute>|Określa identyfikator wysyłania COM (identyfikator DISPID) metody lub pola. Ten atrybut zawiera identyfikator DISPID dla metody, pole lub właściwość, którą opisuje.<br /><br /> COM interop narzędzia można zastosować tego atrybutu.|  
|<xref:System.Runtime.InteropServices.FieldOffsetAttribute>|Wskazuje położenie fizycznych każde pole w klasie, gdy jest używany z **structlayoutattribute —** i **LayoutKind** ma ustawioną wartość Explicit.|  
|<xref:System.Runtime.InteropServices.GuidAttribute>|Określa unikatowy identyfikator globalny (GUID) z klasą, interfejsem lub biblioteki typów całego. Ciąg przekazany do atrybutu musi być w formacie, który jest argumentem dopuszczalne konstruktora dla typu **System.Guid**.<br /><br /> COM interop narzędzia można zastosować tego atrybutu.|  
|<xref:System.Runtime.InteropServices.IDispatchImplAttribute>|Wskazuje, które **IDispatch** środowisko uruchomieniowe języka wspólnego używa podczas udostępnianie podwójne interfejsy i dispinterfaces do modelu COM. implementacja interfejsu|  
|<xref:System.Runtime.InteropServices.InAttribute>|Wskazuje, dane powinny być przekazywane w do obiektu wywołującego. Może służyć do parametrów atrybutu.|  
|<xref:System.Runtime.InteropServices.InterfaceTypeAttribute>|Określa, jak zarządzanego interfejsu jest ujawnione klientom modelu COM (procesory pochodnych IUnknown lub IDispatch tylko).<br /><br /> COM interop narzędzia można zastosować tego atrybutu.|  
|<xref:System.Runtime.InteropServices.LCIDConversionAttribute>|Wskazuje, że podpis metody niezarządzane oczekuje, że parametr LCID.<br /><br /> COM interop narzędzia można zastosować tego atrybutu.|  
|<xref:System.Runtime.InteropServices.MarshalAsAttribute>|Wskazuje, jak dane w polach lub parametry powinien być przekazywane między zarządzanymi i niezarządzanymi kodu. Atrybut zawsze jest opcjonalny, ponieważ każdy typ danych ma domyślne zachowanie marshalingu.<br /><br /> COM interop narzędzia można zastosować tego atrybutu.|  
|<xref:System.Runtime.InteropServices.OptionalAttribute>|Wskazuje, że parametr jest opcjonalny.<br /><br /> COM interop narzędzia można zastosować tego atrybutu.|  
|<xref:System.Runtime.InteropServices.OutAttribute>|Wskazuje, czy dane w polu lub parametr musi być organizowany z wywołany obiekt do swojego obiektu wywołującego.|  
|<xref:System.Runtime.InteropServices.PreserveSigAttribute>|Pomija przekształcania podpisu HRESULT lub retval czy zwykle odbywa się podczas wywołania współdziałanie. Ten atrybut ma wpływ na przekazywanie oraz eksportowanie biblioteki typów.<br /><br /> COM interop narzędzia można zastosować tego atrybutu.|  
|<xref:System.Runtime.InteropServices.ProgIdAttribute>|Określa identyfikator ProgID klasy .NET Framework. Może służyć do klas atrybutów.|  
|<xref:System.Runtime.InteropServices.StructLayoutAttribute>|Określa fizyczny układ pól klasy.<br /><br /> COM interop narzędzia można zastosować tego atrybutu.|  
  
## <a name="conversion-tool-attributes"></a>Atrybuty narzędzia konwersji  
 W poniższej tabeli opisano atrybuty stosowane narzędzia międzyoperacyjnego modelu COM w procesie konwersji. Te atrybuty nie są stosowane w czasie projektowania.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|<xref:System.Runtime.InteropServices.ComAliasNameAttribute>|Wskazuje alias COM dla typu parametru lub pola. Może służyć do parametrów atrybutu, pól, lub wartości zwracane.|  
|<xref:System.Runtime.InteropServices.ComConversionLossAttribute>|Wskazuje informacji na temat klasy lub interfejsu zostało utracone, jeśli został zaimportowany z biblioteki typów, do zestawu.|  
|<xref:System.Runtime.InteropServices.ComEventInterfaceAttribute>|Identyfikuje interfejsu źródłowego i klasy, która implementuje metody interfejsu zdarzenia.|  
|<xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute>|Wskazuje, że zestaw pierwotnie został zaimportowany z biblioteki typów COM. Ten atrybut zawiera definicję typu biblioteki oryginalnej biblioteki typów.|  
|<xref:System.Runtime.InteropServices.TypeLibFuncAttribute>|Zawiera **FUNCFLAGS** które pierwotnie zostały zaimportowane dla tej funkcji z biblioteki typów COM.|  
|<xref:System.Runtime.InteropServices.TypeLibTypeAttribute>|Zawiera **TYPEFLAGS** które pierwotnie zostały zaimportowane dla tego typu z biblioteki typów COM.|  
|<xref:System.Runtime.InteropServices.TypeLibVarAttribute>|Zawiera **VARFLAGS** które pierwotnie zostały zaimportowane dla tej zmiennej z biblioteki typów COM.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices>  
 [Udostępnianie składników .NET Framework modelowi COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [Atrybuty](../../../docs/standard/attributes/index.md)  
 [Kwalifikowanie typów .NET do międzyoperacyjności](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md)  
 [Pakowanie zestawu dla modelu COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md)

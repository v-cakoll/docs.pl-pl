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
ms.openlocfilehash: 78f89c3c8784467d3ec396106de7bbb34a2022f6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121949"
---
# <a name="applying-interop-attributes"></a>Stosowanie atrybutów międzyoperacyjności
Przestrzeń nazw <xref:System.Runtime.InteropServices> zawiera trzy kategorie atrybutów specyficznych dla współdziałania: te stosowane w czasie projektowania, które są stosowane przez narzędzia i interfejsy API międzyoperacyjności modelu COM w procesie konwersji i są stosowane przez użytkownika lub międzyoperacyjność modelu COM.  
  
 Jeśli nie znasz zadania dotyczącego stosowania atrybutów do kodu zarządzanego, zobacz [Rozszerzanie metadanych przy użyciu atrybutów](../../../docs/standard/attributes/index.md). Podobnie jak w przypadku innych atrybutów niestandardowych, można zastosować atrybuty dotyczące międzyoperacyjności do typów, metod, właściwości, parametrów, pól i innych elementów członkowskich.  
  
## <a name="design-time-attributes"></a>Atrybuty czasu projektowania  
 Można dostosować wynik procesu konwersji wykonywanego przez narzędzia i interfejsy API międzyoperacyjności modelu COM przy użyciu atrybutów czasu projektowania. W poniższej tabeli opisano atrybuty, które można zastosować do zarządzanego kodu źródłowego. Narzędzia międzyoperacyjności modelu COM mogą również zastosować atrybuty opisane w tej tabeli.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|<xref:System.Runtime.InteropServices.AutomationProxyAttribute>|Określa, czy typ powinien być zorganizowany przy użyciu Organizatora automatyzacji, czy niestandardowego serwera proxy i szczątkowego.|  
|<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>|Kontroluje typ interfejsu wygenerowanego dla klasy.|  
|<xref:System.Runtime.InteropServices.CoClassAttribute>|Identyfikuje identyfikator CLSID oryginalnej klasy coclass zaimportowanej z biblioteki typów.<br /><br /> Narzędzia międzyoperacyjności modelu COM zwykle stosują ten atrybut.|  
|<xref:System.Runtime.InteropServices.ComImportAttribute>|Wskazuje, że definicja klasy coclass lub interfejsu została zaimportowana z biblioteki typów COM. Środowisko uruchomieniowe używa tej flagi, aby dowiedzieć się, jak aktywować i zorganizować typ. Ten atrybut zabrania eksportowania typu z powrotem do biblioteki typów.<br /><br /> Narzędzia międzyoperacyjności modelu COM zwykle stosują ten atrybut.|  
|<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>|Wskazuje, że metoda powinna być wywoływana, gdy zestaw jest zarejestrowany do użycia z modelu COM, dzięki czemu kod może być wykonywany podczas procesu rejestracji.|  
|<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>|Identyfikuje interfejsy, które są źródła zdarzeń dla klasy.<br /><br /> Narzędzia międzyoperacyjności modelu COM mogą zastosować ten atrybut.|  
|<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>|Wskazuje, że metoda powinna być wywoływana, gdy zestaw jest wyrejestrowany z modelu COM, dzięki czemu kod zapisany przez użytkownika może być wykonywany podczas procesu.|  
|<xref:System.Runtime.InteropServices.ComVisibleAttribute>|Renderuje typy niewidoczne do modelu COM, gdy wartość atrybutu jest równa **false**. Ten atrybut może być stosowany do pojedynczego typu lub do całego zestawu, aby kontrolować widoczność modelu COM. Domyślnie widoczne są wszystkie typy zarządzane, publiczne. Ten atrybut nie jest wymagany, aby były widoczne.|  
|<xref:System.Runtime.InteropServices.DispIdAttribute>|Określa identyfikator wysyłania COM (DISPID) metody lub pola. Ten atrybut zawiera identyfikator DISPID dla metody, pola lub właściwości, która opisuje.<br /><br /> Narzędzia międzyoperacyjności modelu COM mogą zastosować ten atrybut.| 
|<xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute>|Wskazuje domyślny interfejs dla klasy COM wdrożony w środowisku .NET.<br /><br /> Narzędzia międzyoperacyjności modelu COM mogą zastosować ten atrybut.|
|<xref:System.Runtime.InteropServices.FieldOffsetAttribute>|Wskazuje fizyczną pozycję każdego pola w klasie, gdy jest używany z **StructLayoutAttribute**, a **LayoutKind** jest ustawiona na wartość explicit.|  
|<xref:System.Runtime.InteropServices.GuidAttribute>|Określa unikatowy identyfikator globalny (GUID) klasy, interfejsu lub całej biblioteki typów. Ciąg przesłany do atrybutu musi być formatem, który jest akceptowalnym argumentem konstruktora dla typu **System. GUID**.<br /><br /> Narzędzia międzyoperacyjności modelu COM mogą zastosować ten atrybut.|  
|<xref:System.Runtime.InteropServices.IDispatchImplAttribute>|Wskazuje, która implementacja interfejsu **IDispatch** używa środowiska uruchomieniowego języka wspólnego podczas udostępniania podwójnych interfejsów i dispinterfaces do modelu com.|  
|<xref:System.Runtime.InteropServices.InAttribute>|Wskazuje, że dane powinny być przekazywane do obiektu wywołującego. Może służyć do atrybutów parametrów.|  
|<xref:System.Runtime.InteropServices.InterfaceTypeAttribute>|Steruje sposobem ujawniania interfejsu zarządzanego klientom modelu COM (tylko dla podwójnych elementów IUnknown lub IDispatch).<br /><br /> Narzędzia międzyoperacyjności modelu COM mogą zastosować ten atrybut.|  
|<xref:System.Runtime.InteropServices.LCIDConversionAttribute>|Wskazuje, że niezarządzany podpis metody oczekuje parametru LCID.<br /><br /> Narzędzia międzyoperacyjności modelu COM mogą zastosować ten atrybut.|  
|<xref:System.Runtime.InteropServices.MarshalAsAttribute>|Wskazuje, w jaki sposób dane w polach lub parametrach powinny być organizowane między zarządzanym i niezarządzanym kodem. Atrybut jest zawsze opcjonalny, ponieważ każdy typ danych ma domyślne zachowanie organizowania.<br /><br /> Narzędzia międzyoperacyjności modelu COM mogą zastosować ten atrybut.|  
|<xref:System.Runtime.InteropServices.OptionalAttribute>|Wskazuje, że parametr jest opcjonalny.<br /><br /> Narzędzia międzyoperacyjności modelu COM mogą zastosować ten atrybut.|  
|<xref:System.Runtime.InteropServices.OutAttribute>|Wskazuje, że dane w polu lub parametrze muszą być organizowane z wywoływanego obiektu z powrotem do obiektu wywołującego.|  
|<xref:System.Runtime.InteropServices.PreserveSigAttribute>|Pomija transformację sygnatury HRESULT lub retval, która zwykle odbywa się podczas wywołań międzyoperacyjnych. Ten atrybut ma wpływ na kierowanie oraz eksportowanie biblioteki typów.<br /><br /> Narzędzia międzyoperacyjności modelu COM mogą zastosować ten atrybut.|  
|<xref:System.Runtime.InteropServices.ProgIdAttribute>|Określa identyfikator ProgID klasy .NET Framework. Może służyć do atrybutów klas.|  
|<xref:System.Runtime.InteropServices.StructLayoutAttribute>|Kontroluje układ fizyczny pól klasy.<br /><br /> Narzędzia międzyoperacyjności modelu COM mogą zastosować ten atrybut.|  
  
## <a name="conversion-tool-attributes"></a>Atrybuty narzędzia konwersji  
 W poniższej tabeli opisano atrybuty stosowane przez narzędzia modelu COM Interop w procesie konwersji. Te atrybuty nie są stosowane w czasie projektowania.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|<xref:System.Runtime.InteropServices.ComAliasNameAttribute>|Wskazuje alias COM dla parametru lub typu pola. Może służyć do atrybutów parametrów, pól lub wartości zwracanych.|  
|<xref:System.Runtime.InteropServices.ComConversionLossAttribute>|Wskazuje, że informacje o klasie lub interfejsie zostały utracone podczas importowania z biblioteki typów do zestawu.|  
|<xref:System.Runtime.InteropServices.ComEventInterfaceAttribute>|Identyfikuje interfejs źródłowy i klasę, która implementuje metody interfejsu zdarzenia.|  
|<xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute>|Wskazuje, że zestaw został pierwotnie zaimportowany z biblioteki typów COM. Ten atrybut zawiera definicję biblioteki typów oryginalnej biblioteki typów.|  
|<xref:System.Runtime.InteropServices.TypeLibFuncAttribute>|Zawiera **FUNCFLAGS** , które zostały pierwotnie zaimportowane do tej funkcji z biblioteki typów com.|  
|<xref:System.Runtime.InteropServices.TypeLibTypeAttribute>|Zawiera **TYPEFLAGS** , które zostały pierwotnie zaimportowane dla tego typu z biblioteki typów com.|  
|<xref:System.Runtime.InteropServices.TypeLibVarAttribute>|Zawiera **VARFLAGS** , które zostały pierwotnie zaimportowane dla tej zmiennej z biblioteki typów com.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices>
- [Udostępnianie składników .NET Framework modelowi COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)
- [Atrybuty](../../../docs/standard/attributes/index.md)
- [Kwalifikowanie typów .NET do międzyoperacyjności](../../../docs/standard/native-interop/qualify-net-types-for-interoperation.md)
- [Pakowanie zestawu .NET Framework dla modelu COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md)

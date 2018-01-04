---
title: "Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie klienta"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, client-side provider implementation
- client-side UI Automation provider, implementation
- provider implementation, UI Automation
ms.assetid: 3584c0a1-9cd0-4968-8b63-b06390890ef6
caps.latest.revision: "14"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 50335994fab424b3100c91a202a7ea53643db551
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="client-side-ui-automation-provider-implementation"></a>Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie klienta
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Kilka różnych [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] struktury są używane w ramach [!INCLUDE[TLA#tla_ms](../../../includes/tlasharptla-ms-md.md)] systemy operacyjne, w tym [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)], i [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]przedstawia informacje o elementach interfejsu użytkownika na klientach. Jednak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sam nie ma pogłębianie wiedzy na temat różnych typów formantów, które istnieją w tych platform i techniki, które są niezbędne do wyodrębnienia informacji z nich. Zamiast tego pozostawia to zadanie do obiektów nazywanych dostawcami. Dostawca wyodrębnia dane z określonego formantu i przekazuje informacje do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], który następnie prezentuje je do klienta w sposób ciągły.  
  
 Dostawcy mogą się znajdować po stronie serwera lub po stronie klienta. Dostawcy po stronie serwera jest implementowany przez samego formantu. [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]elementy zaimplementować dostawców, jak wszystkie formanty innych firm napisany za pomocą [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pamiętać.  
  
 Jednak starsza formanty, takie jak te w [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] i [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] bezpośrednio czy obsługa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Formanty te są udostępniane zamiast tego przez dostawców, które istnieją w procesie klienta i uzyskaj informacje na temat kontroli komunikacji między procesami; na przykład monitorując komunikaty systemu windows z kontrolki. Takie dostawcy po stronie klienta są czasami nazywane serwerami proxy.  
  
 [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)]dostarcza dostawców dla standardowej [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] i [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)] kontrolki. Ponadto zapewnia częściowe rezerwowy dostawcy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsługiwać żadnego formantu, który nie jest obsługiwana przez innego dostawcy po stronie serwera lub serwera proxy, lecz jest [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)] implementacji. Ci dostawcy są automatycznie załadowany i dostępne dla aplikacji klienckich.  
  
 Aby uzyskać więcej informacji na temat obsługi [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] i [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)] formantów, zobacz [Obsługa automatyzacji interfejsu użytkownika standardowych formantów](../../../docs/framework/ui-automation/ui-automation-support-for-standard-controls.md).  
  
 Aplikacje można również zarejestrować inni dostawcy po stronie klienta.  
  
<a name="Distributing_Client-Side_Providers"></a>   
## <a name="distributing-client-side-providers"></a>Dystrybucja dostawcy po stronie klienta  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]oczekuje, że można znaleźć w zestawie kodu zarządzanego dostawcy po stronie klienta. Przestrzeń nazw w tym zestawie powinny mieć taką samą nazwę jak zestawu. Na przykład zestawu o nazwie ContosoProxies.dll zawierałoby ContosoProxies przestrzeni nazw. W obszarze nazw, należy utworzyć <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders> klasy. W implementacji statycznych <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders.ClientSideProviderDescriptionTable> pola, Utwórz tablicę <xref:System.Windows.Automation.ClientSideProviderDescription> struktury opisujące dostawców.  
  
<a name="Registering_and_Configuring_Client-Side_Providers"></a>   
## <a name="registering-and-configuring-client-side-providers"></a>Rejestrowanie i Konfigurowanie dostawcy po stronie klienta  
 Dostawcy po stronie klienta w [!INCLUDE[TLA#tla_dll](../../../includes/tlasharptla-dll-md.md)] są ładowane przez wywołanie metody <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviderAssembly%2A>. Żadne dalsze akcje nie jest wymagane przez aplikację klienta, aby korzystać z dostawców.  
  
 Zarejestrowanych dostawców zaimplementowano w kodzie przez klienta za pomocą <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>. Ta metoda przyjmuje jako argument tablicy <xref:System.Windows.Automation.ClientSideProviderDescription> struktury, z których każdy określa następujące właściwości:  
  
-   Funkcja wywołania zwrotnego, która tworzy obiekt dostawcy.  
  
-   Nazwa klasy formantów, które będą obsługiwać dostawcę.  
  
-   Nazwa obrazu aplikacji (zwykle Pełna nazwa pliku wykonywalnego), która posłuży dostawcy.  
  
-   Flagi określające, jak nazwa klasy jest dopasowywana klasy okien w aplikacji docelowej.  
  
 Ostatnie dwa parametry są opcjonalne. Klient może określić nazwę obrazu w aplikacji docelowej, gdy chce używać różnych dostawców dla różnych aplikacji. Na przykład klient może używać jednego dostawcę dla [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] formant widoku w znanych aplikacji, która obsługuje wzorzec wielu widoku, a druga podobne kontrolki w innej aplikacji znane, która nie listy.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie dostawcy automatyzacji interfejsu użytkownika po stronie klienta](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)  
 [Implementacja dostawców automatyzacji interfejsu użytkownika w aplikacji klienta](../../../docs/framework/ui-automation/implement-ui-automation-providers-in-a-client-application.md)

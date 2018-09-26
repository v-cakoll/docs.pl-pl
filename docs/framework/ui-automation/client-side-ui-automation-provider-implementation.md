---
title: Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie klienta
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, client-side provider implementation
- client-side UI Automation provider, implementation
- provider implementation, UI Automation
ms.assetid: 3584c0a1-9cd0-4968-8b63-b06390890ef6
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 53773c51aef6b9530ed0b2cfaf0ef08cdb340ec2
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47205454"
---
# <a name="client-side-ui-automation-provider-implementation"></a>Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie klienta
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Kilka różnych [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] struktur są używane w ramach [!INCLUDE[TLA#tla_ms](../../../includes/tlasharptla-ms-md.md)] systemy operacyjne, w tym [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)], i [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] przedstawia informacje o elementach interfejsu użytkownika na klientach. Jednak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sam nie ma świadomości różne typy kontrolek, które istnieją w tych struktur i technik, które są niezbędne do wyodrębnienia informacji z nich. Zamiast tego instalacja pozostawia to zadanie do obiektów, nazywanych dostawcami. Dostawca wyodrębnia informacje z określonego formantu i przekazuje te informacje do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], który następnie prezentuje je do klienta w sposób ciągły.  
  
 Dostawców może znajdować się po stronie serwera lub po stronie klienta. Dostawcy po stronie serwera jest implementowany przez sam formant. [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] elementy implementacja dostawców, jak wszystkie formanty innych firm, napisany w języku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] na uwadze.  
  
 Jednak starsze formanty, takie jak te w [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] i [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] bezpośrednio czy obsługa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Te kontrolki zamiast obsługiwanych przez dostawców, które istnieją w procesie klienta i uzyskać informacje na temat kontrolek przy użyciu komunikacji między procesami; na przykład przez monitorowanie komunikatów systemu windows do i z kontrolki. Taki dostawcy po stronie klienta są czasami nazywane serwerami proxy.  
  
 [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] dostarcza dostawców dla warstwy standardowej [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] i formanty Windows Forms. Ponadto zapewnia częściowe rezerwowego dostawcy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsługiwać dowolną kontrolkę, która nie jest obsługiwana przez innego dostawcę po stronie serwera lub serwer proxy, lecz jest [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)] implementacji. Ci dostawcy są automatycznie załadowany i dostępne dla aplikacji klienckich.  
  
 Aby uzyskać więcej informacji na temat obsługi [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] i kontrolek Windows Forms, zobacz [UI Automation obsługi dla standardowych kontrolek](../../../docs/framework/ui-automation/ui-automation-support-for-standard-controls.md).  
  
 Aplikacje można również zarejestrować inni dostawcy po stronie klienta.  
  
<a name="Distributing_Client-Side_Providers"></a>   
## <a name="distributing-client-side-providers"></a>Dystrybucja dostawcy po stronie klienta  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] spodziewa się znaleźć dostawcy po stronie klienta w zestawie kodu zarządzanego. Przestrzeń nazw, w tym zestawie mają taką samą nazwę jak zestawu. Na przykład zestaw o nazwie ContosoProxies.dll zawierałoby ContosoProxies przestrzeni nazw. W ramach przestrzeni nazw, należy utworzyć <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders> klasy. W implementacji statycznych <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders.ClientSideProviderDescriptionTable> pola, Utwórz tablicę <xref:System.Windows.Automation.ClientSideProviderDescription> struktury zawierająca opis dostawcy.  
  
<a name="Registering_and_Configuring_Client-Side_Providers"></a>   
## <a name="registering-and-configuring-client-side-providers"></a>Rejestrowanie i Konfigurowanie dostawcy po stronie klienta  
 Dostawcy po stronie klienta w [!INCLUDE[TLA#tla_dll](../../../includes/tlasharptla-dll-md.md)] są ładowane przez wywołanie metody <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviderAssembly%2A>. Żadne dalsze działania jest wymagany przez aplikację kliencką, aby korzystać z dostawców.  
  
 Zarejestrowano dostawców zaimplementowany w kodzie przez klienta za pomocą <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>. Ta metoda przyjmuje jako argument tablicę <xref:System.Windows.Automation.ClientSideProviderDescription> struktur, z których każdy określa następujące właściwości:  
  
-   Funkcja wywołania zwrotnego, która tworzy obiekt dostawcy.  
  
-   Nazwa klasy kontrolki, które będą obsługiwać dostawcę.  
  
-   Nazwa obrazu aplikacji (zwykle Pełna nazwa pliku wykonywalnego), która posłuży dostawcy.  
  
-   Flagi określające, jak nazwa klasy jest dopasowywana klas okien w aplikacji docelowej.  
  
 Ostatnie dwa parametry są opcjonalne. Klient może określić nazwę obrazu aplikacji docelowej, gdy chce korzystać z różnych dostawców dla różnych aplikacji. Na przykład, klient może używać jednego dostawcę dla [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] kontrolka widoku w znanych aplikacji, która obsługuje wzorzec wielu widoku, a druga podobne kontrolki w innej aplikacji znane, która nie ma listy.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie dostawcy automatyzacji interfejsu użytkownika po stronie klienta](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)  
 [Implementacja dostawców automatyzacji interfejsu użytkownika w aplikacji klienta](../../../docs/framework/ui-automation/implement-ui-automation-providers-in-a-client-application.md)

---
title: Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie klienta
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, client-side provider implementation
- client-side UI Automation provider, implementation
- provider implementation, UI Automation
ms.assetid: 3584c0a1-9cd0-4968-8b63-b06390890ef6
ms.openlocfilehash: 9079dfa03ab81bfa6875e43bfa8a6e5351e0a35d
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015115"
---
# <a name="client-side-ui-automation-provider-implementation"></a>Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie klienta
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 Niektóre różne [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] platformy są używane w systemach operacyjnych firmy Microsoft, w tym [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]i [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]przedstawia informacje o elementach interfejsu użytkownika dla klientów programu. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Jednakże nie jest to jednak świadomość różnych typów formantów, które istnieją w tych strukturach, oraz technik, które są potrzebne do wyodrębnienia z nich informacji. Zamiast tego pozostawi to zadanie w obiektach o nazwie Providers. Dostawca wyodrębnia informacje z konkretnej kontrolki i udostępnia te informacje [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], które przedstawiają go klientowi w spójny sposób.  
  
 Dostawcy mogą istnieć zarówno po stronie serwera, jak i po stronie klienta. Dostawca po stronie serwera jest implementowany przez sam formant. [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]elementy implementujące dostawców, jak mogą dowolnie dowolnych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontrolek innych firm.  
  
 Jednak starsze kontrolki, takie jak te [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] w [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] i nie są bezpośrednio [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]obsługiwane. Te kontrolki są obsługiwane zamiast dostawców, którzy istnieją w procesie klienta i uzyskują informacje o kontrolkach korzystających z komunikacji między procesami; na przykład przez monitorowanie komunikatów systemu Windows do i z kontrolek. Tacy dostawcy po stronie klienta są czasami nazywane serwerami proxy.  
  
 [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)]dostarcza dostawców dla kontrolek standardowych [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] i Windows Formsowych. Dodatkowo dostawca rezerwowy zapewnia częściową [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsługę każdej kontroli, która nie jest obsługiwana przez innego dostawcę po stronie serwera lub serwer proxy, ale ma implementację Microsoft Active Accessibility. Wszyscy dostawcy są automatycznie załadowana i dostępni dla aplikacji klienckich.  
  
 Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] obsługi formantów i Windows Forms, zobacz [Obsługa automatyzacji interfejsu użytkownika dla standardowych kontrolek](../../../docs/framework/ui-automation/ui-automation-support-for-standard-controls.md).  
  
 Aplikacje mogą także rejestrować innych dostawców po stronie klienta.  
  
<a name="Distributing_Client-Side_Providers"></a>   
## <a name="distributing-client-side-providers"></a>Dystrybuowanie dostawców po stronie klienta  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]oczekuje, że dostawcy po stronie klienta mają znajdować się w zestawie kodu zarządzanego. Przestrzeń nazw w tym zestawie powinna mieć taką samą nazwę jak zestaw. Na przykład zestaw o nazwie ContosoProxies. dll będzie zawierać przestrzeń nazw ContosoProxies. W przestrzeni nazw Utwórz <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders> klasę. W implementacji pola statycznego <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders.ClientSideProviderDescriptionTable> Utwórz <xref:System.Windows.Automation.ClientSideProviderDescription> tablicę struktur opisującą dostawców.  
  
<a name="Registering_and_Configuring_Client-Side_Providers"></a>   
## <a name="registering-and-configuring-client-side-providers"></a>Rejestrowanie i Konfigurowanie dostawców po stronie klienta  
 Dostawcy po stronie klienta w bibliotece dołączanej dynamicznie (DLL) są załadowane przez <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviderAssembly%2A>wywołanie. Żadna dodatkowa akcja nie jest wymagana przez aplikację kliencką do korzystania z dostawców.  
  
 Dostawcy zaimplementowani w własnym kodzie klienta są rejestrowani przy użyciu <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>. Ta metoda przyjmuje jako argument tablicę <xref:System.Windows.Automation.ClientSideProviderDescription> struktur, z których każdy określa następujące właściwości:  
  
- Funkcja wywołania zwrotnego, która tworzy obiekt dostawcy.  
  
- Nazwa klasy kontrolek, która będzie obsługiwała dostawca.  
  
- Nazwa obrazu aplikacji (zazwyczaj pełna nazwa pliku wykonywalnego), który będzie obsługiwany przez dostawcę.  
  
- Flagi określające sposób dopasowania nazwy klasy do klas okien znalezionych w aplikacji docelowej.  
  
 Ostatnie dwa parametry są opcjonalne. Klient może określić nazwę obrazu aplikacji docelowej, gdy chce używać różnych dostawców dla różnych aplikacji. Na przykład klient może użyć jednego dostawcy dla [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] kontrolki widok listy w znanej aplikacji, która obsługuje wzorzec wielu widoków i drugi dla podobnej kontroli w innej znanej aplikacji, która nie.  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie dostawcy automatyzacji interfejsu użytkownika po stronie klienta](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)
- [Implementacja dostawców automatyzacji interfejsu użytkownika w aplikacji klienta](../../../docs/framework/ui-automation/implement-ui-automation-providers-in-a-client-application.md)

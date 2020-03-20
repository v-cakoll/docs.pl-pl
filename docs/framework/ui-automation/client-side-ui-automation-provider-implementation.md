---
title: Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie klienta
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, client-side provider implementation
- client-side UI Automation provider, implementation
- provider implementation, UI Automation
ms.assetid: 3584c0a1-9cd0-4968-8b63-b06390890ef6
ms.openlocfilehash: 50d7921f1c63580248b562864f9c1f398d41c9bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180257"
---
# <a name="client-side-ui-automation-provider-implementation"></a>Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie klienta
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] systemach operacyjnych firmy Microsoft jest używanych kilka różnych [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]struktur, w tym Win32, Windows Forms i . [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]udostępnia klientom informacje o elementach interfejsu użytkownika. Jednak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sama nie ma świadomości różnych typów formantów, które istnieją w tych ramach i technik, które są potrzebne do wyodrębniania informacji z nich. Zamiast tego pozostawia to zadanie do obiektów o nazwie dostawców. Dostawca wyodrębnia informacje z określonej kontroli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]i przekazuje te informacje do , który następnie przedstawia go klientowi w spójny sposób.  
  
 Dostawcy mogą istnieć po stronie serwera lub po stronie klienta. Dostawca po stronie serwera jest implementowany przez sam formant. [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]elementy implementują dostawców, podobnie jak wszelkie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontrole innych firm napisane z myślą.  
  
 Jednak starsze formanty, takie jak te w środowiskach [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Win32 i Windows Forms, nie obsługują bezpośrednio . Te formanty są obsługiwane zamiast przez dostawców, którzy istnieją w procesie klienta i uzyskać informacje o formantów za pomocą komunikacji między procesami; na przykład przez monitorowanie wiadomości systemu Windows do i z formantów. Tacy dostawcy po stronie klienta są czasami nazywane serwerami proxy.  
  
 System Windows Vista dostarcza dostawcom standardowych formantów Win32 i Windows Forms. Ponadto dostawca rezerwowy zapewnia częściową [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsługę dowolnej kontroli, która nie jest obsługiwana przez innego dostawcę po stronie serwera lub serwer proxy, ale ma implementację microsoft active accessibility. Wszyscy ci dostawcy są automatycznie ładowane i dostępne dla aplikacji klienckich.  
  
 Aby uzyskać więcej informacji na temat obsługi formantów Win32 i Windows Forms, zobacz [Obsługa automatyzacji interfejsu użytkownika dla standardowych formantów](ui-automation-support-for-standard-controls.md).  
  
 Aplikacje mogą również rejestrować innych dostawców po stronie klienta.  
  
<a name="Distributing_Client-Side_Providers"></a>
## <a name="distributing-client-side-providers"></a>Dystrybucja dostawców po stronie klienta  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]oczekuje, że znajdzie dostawców po stronie klienta w zestawie kodu zarządzanego. Obszar nazw w tym zestawie powinien mieć taką samą nazwę jak zestaw. Na przykład zestaw o nazwie ContosoProxies.dll będzie zawierać ContosoProxies przestrzeni nazw. W obszarze nazw utwórz <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders> klasę. W implementacji pola <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders.ClientSideProviderDescriptionTable> statycznego utwórz <xref:System.Windows.Automation.ClientSideProviderDescription> tablicę struktur opisujących dostawców.  
  
<a name="Registering_and_Configuring_Client-Side_Providers"></a>
## <a name="registering-and-configuring-client-side-providers"></a>Rejestrowanie i konfigurowanie dostawców po stronie klienta  
 Dostawcy po stronie klienta w bibliotece łączy dynamicznych <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviderAssembly%2A>(DLL) są ładowane przez wywołanie . Żadne dalsze działania nie są wymagane przez aplikację kliencką, aby korzystać z dostawców.  
  
 Dostawcy zaimplementowani we własnym kodzie <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>klienta są rejestrowani za pomocą programu . Ta metoda przyjmuje jako argument <xref:System.Windows.Automation.ClientSideProviderDescription> tablicę struktur, z których każda określa następujące właściwości:  
  
- Funkcja wywołania zwrotnego, która tworzy obiekt dostawcy.  
  
- Nazwa klasy formantów, które dostawca będzie służyć.  
  
- Nazwa obrazu aplikacji (zwykle pełna nazwa pliku wykonywalnego), który dostawca będzie służyć.  
  
- Flagi, które regulują, jak nazwa klasy jest dopasowywała się do klas okien znalezionych w aplikacji docelowej.  
  
 Ostatnie dwa parametry są opcjonalne. Klient może określić nazwę obrazu aplikacji docelowej, gdy chce używać różnych dostawców dla różnych aplikacji. Na przykład klient może użyć jednego dostawcy dla formantu widoku listy Win32 w znanej aplikacji, która obsługuje wzorzec wielu widoków, a drugi dla podobnego formantu w innej znanej aplikacji, która nie.  
  
## <a name="see-also"></a>Zobacz też

- [Tworzenie dostawcy automatyzacji interfejsu użytkownika po stronie klienta](create-a-client-side-ui-automation-provider.md)
- [Implementacja dostawców automatyzacji interfejsu użytkownika w aplikacji klienta](implement-ui-automation-providers-in-a-client-application.md)

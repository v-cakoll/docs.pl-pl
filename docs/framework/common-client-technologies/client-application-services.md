---
title: Usługi aplikacji klienta
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- role-based security [.NET Framework], client application services
- client application services
- credentials [.NET Framework]
- Windows-based applications, client application services
- application settings, client application services
- profiles [ASP.NET], client application services
- logins [client application services]
- sharing information and functionality [client application services]
- Web settings [client application services]
- authentication [ASP.NET], client application services
- ASP.NET services, client application services
- client applications, ASP.NET services
- roles [.NET Framework], client application services
- client application services, about client application services
ms.assetid: 1487d8df-089e-4f21-abfb-a791a652b58e
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9532594f5f243faed28229388b9a6d597be57a7d
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="client-application-services"></a>Usługi aplikacji klienta
Usługi aplikacji klienta ułatwiają tworzenie aplikacji systemu Windows, które używają [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] logowania, ról i usług aplikacji profil w ramach rozszerzenia AJAX Microsoft ASP.NET 2.0. Te usługi umożliwiają wielu sieci Web i aplikacji do udostępniania informacji o użytkowniku i funkcje z zakresu zarządzania użytkownika z jednego serwera systemu Windows. Można na przykład korzystania z tych usług do wykonywania następujących zadań:  
  
-   Uwierzytelnianie użytkownika. Usługa uwierzytelniania służy do sprawdzenia tożsamości użytkownika.  
  
-   Określ rolę lub role uwierzytelnionego użytkownika. Usługi ról można użyć do zmiany interfejsu użytkownika aplikacji w zależności od roli użytkownika. Na przykład możesz podać dodatkowe funkcje dla użytkowników, którzy znajdują się w roli administratora.  
  
-   Magazyn i dostęp użytkownika ustawienia aplikacji znajduje się na serwerze. Ustawienia usługi sieci Web (znaną również jako usługa profilu) umożliwia współużytkowanie ustawień przez wiele aplikacji i lokalizacji.  
  
 Usługi aplikacji klienta korzystać z modelu rozszerzeń usługi sieci Web za pośrednictwem dostawcy usług klienta, które można określić w plikach konfiguracji aplikacji. Ci dostawcy usług obejmują funkcje w trybie offline, które używa lokalnej pamięci podręcznej dla uwierzytelniania, ról i ustawienia danych, gdy połączenie sieciowe jest niedostępne.  
  
 Aby uzyskać więcej informacji na temat [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] usług aplikacji, zobacz [przegląd usług aplikacji ASP.NET](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Omówienie usług aplikacji klienckich](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 Zawiera opis funkcji dostępnych za pośrednictwem dostawcy usług aplikacji klienta.  
  
 [Instrukcje: konfigurowanie usług aplikacji klienckich](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 Informacje dotyczące używania projektanta projektu programu Visual Studio, aby włączyć i konfiguracji aplikacji usługi. Opisano również odpowiednie zmiany w pliku App.config.  
  
 [Instrukcje: implementowanie logowania użytkownika przy użyciu usług aplikacji klienckich](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)  
 Opisuje sposób sprawdzania poprawności użytkownika, gdy aplikacja jest skonfigurowana do używania dostawcy usługi uwierzytelniania klienta.  
  
 [Przewodnik: używanie usług aplikacji klienckich](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 Zawiera opis sposobu łączenia wszystkich funkcji usług aplikacji klienta w pojedynczej aplikacji. Ten przewodnik zawiera wskazówki dotyczące end-to-end. Na przykład zawiera instrukcje dotyczące tworzenia aplikacji usługi sieci Web ASP.NET, którego można używać do testowania usługi aplikacji klienta.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Web.ClientServices.ClientFormsIdentity>  
 <xref:System.Web.ClientServices.ClientRolePrincipal>  
 <xref:System.Web.ClientServices.ConnectivityStatus>  
 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials>  
 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider>  
 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider>  
 <xref:System.Web.ClientServices.Providers.ClientWindowsAuthenticationMembershipProvider>  
 <xref:System.Web.ClientServices.Providers.ClientRoleProvider>  
 <xref:System.Web.ClientServices.Providers.ClientSettingsProvider>  
 <xref:System.Web.ClientServices.Providers.SettingsSavedEventArgs>  
 <xref:System.Web.ClientServices.Providers.UserValidatedEventArgs>  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd usług aplikacji ASP.NET](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013)  
 [Korzystanie z uwierzytelniania formularzy z Microsoft Ajax](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)  
 [Przy użyciu ról informacji o Microsoft Ajax](http://msdn.microsoft.com/library/280f6ad9-ba1a-4fc9-b0cc-22e39e54a82d)  
 [Przy użyciu informacji o profilu z Microsoft Ajax](http://msdn.microsoft.com/library/91239ae6-d01c-4f4e-a433-eb9040dbed61)  
 [Uwierzytelnianie ASP.NET](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1)  
 [Zarządzanie autoryzację za pomocą ról](http://msdn.microsoft.com/library/01954ce4-39a2-487f-8153-a69f6f6f3195)    
 [Przegląd ustawień aplikacji](../../../docs/framework/winforms/advanced/application-settings-overview.md)

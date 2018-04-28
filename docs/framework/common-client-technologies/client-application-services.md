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
# <a name="client-application-services"></a><span data-ttu-id="b28f7-102">Usługi aplikacji klienta</span><span class="sxs-lookup"><span data-stu-id="b28f7-102">Client Application Services</span></span>
<span data-ttu-id="b28f7-103">Usługi aplikacji klienta ułatwiają tworzenie aplikacji systemu Windows, które używają [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] logowania, ról i usług aplikacji profil w ramach rozszerzenia AJAX Microsoft ASP.NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="b28f7-103">Client application services make it easy for you to create Windows-based applications that use the [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] login, roles, and profile application services included in the Microsoft ASP.NET 2.0 AJAX Extensions.</span></span> <span data-ttu-id="b28f7-104">Te usługi umożliwiają wielu sieci Web i aplikacji do udostępniania informacji o użytkowniku i funkcje z zakresu zarządzania użytkownika z jednego serwera systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="b28f7-104">These services enable multiple Web and Windows-based applications to share user information and user-management functionality from a single server.</span></span> <span data-ttu-id="b28f7-105">Można na przykład korzystania z tych usług do wykonywania następujących zadań:</span><span class="sxs-lookup"><span data-stu-id="b28f7-105">For example, you can use these services to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="b28f7-106">Uwierzytelnianie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b28f7-106">Authenticate a user.</span></span> <span data-ttu-id="b28f7-107">Usługa uwierzytelniania służy do sprawdzenia tożsamości użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b28f7-107">You can use the authentication service to verify a user's identity.</span></span>  
  
-   <span data-ttu-id="b28f7-108">Określ rolę lub role uwierzytelnionego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b28f7-108">Determine the role or roles of an authenticated user.</span></span> <span data-ttu-id="b28f7-109">Usługi ról można użyć do zmiany interfejsu użytkownika aplikacji w zależności od roli użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b28f7-109">You can use the roles service to change the user interface of your application depending on the user's role.</span></span> <span data-ttu-id="b28f7-110">Na przykład możesz podać dodatkowe funkcje dla użytkowników, którzy znajdują się w roli administratora.</span><span class="sxs-lookup"><span data-stu-id="b28f7-110">For example, you can provide additional features for users who are in an administrator role.</span></span>  
  
-   <span data-ttu-id="b28f7-111">Magazyn i dostęp użytkownika ustawienia aplikacji znajduje się na serwerze.</span><span class="sxs-lookup"><span data-stu-id="b28f7-111">Store and access per-user application settings located on the server.</span></span> <span data-ttu-id="b28f7-112">Ustawienia usługi sieci Web (znaną również jako usługa profilu) umożliwia współużytkowanie ustawień przez wiele aplikacji i lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="b28f7-112">You can use the Web settings service (also known as the profile service) to share settings across multiple applications and locations.</span></span>  
  
 <span data-ttu-id="b28f7-113">Usługi aplikacji klienta korzystać z modelu rozszerzeń usługi sieci Web za pośrednictwem dostawcy usług klienta, które można określić w plikach konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b28f7-113">Client application services take advantage of the Web services extensibility model through client service providers that you can specify in your application configuration files.</span></span> <span data-ttu-id="b28f7-114">Ci dostawcy usług obejmują funkcje w trybie offline, które używa lokalnej pamięci podręcznej dla uwierzytelniania, ról i ustawienia danych, gdy połączenie sieciowe jest niedostępne.</span><span class="sxs-lookup"><span data-stu-id="b28f7-114">These service providers include offline functionality that uses a local cache for authentication, roles, and settings data when a network connection is unavailable.</span></span>  
  
 <span data-ttu-id="b28f7-115">Aby uzyskać więcej informacji na temat [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] usług aplikacji, zobacz [przegląd usług aplikacji ASP.NET](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013).</span><span class="sxs-lookup"><span data-stu-id="b28f7-115">For more information about the [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] application services, see [ASP.NET Application Services Overview](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b28f7-116">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="b28f7-116">In This Section</span></span>  
 [<span data-ttu-id="b28f7-117">Omówienie usług aplikacji klienckich</span><span class="sxs-lookup"><span data-stu-id="b28f7-117">Client Application Services Overview</span></span>](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 <span data-ttu-id="b28f7-118">Zawiera opis funkcji dostępnych za pośrednictwem dostawcy usług aplikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="b28f7-118">Describes the features available through the client application service providers.</span></span>  
  
 [<span data-ttu-id="b28f7-119">Instrukcje: konfigurowanie usług aplikacji klienckich</span><span class="sxs-lookup"><span data-stu-id="b28f7-119">How to: Configure Client Application Services</span></span>](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 <span data-ttu-id="b28f7-120">Informacje dotyczące używania projektanta projektu programu Visual Studio, aby włączyć i konfiguracji aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="b28f7-120">Describes how to use the Visual Studio project designer to enable and configuration application services.</span></span> <span data-ttu-id="b28f7-121">Opisano również odpowiednie zmiany w pliku App.config.</span><span class="sxs-lookup"><span data-stu-id="b28f7-121">Also describes the corresponding changes to your App.config file.</span></span>  
  
 [<span data-ttu-id="b28f7-122">Instrukcje: implementowanie logowania użytkownika przy użyciu usług aplikacji klienckich</span><span class="sxs-lookup"><span data-stu-id="b28f7-122">How to: Implement User Login with Client Application Services</span></span>](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)  
 <span data-ttu-id="b28f7-123">Opisuje sposób sprawdzania poprawności użytkownika, gdy aplikacja jest skonfigurowana do używania dostawcy usługi uwierzytelniania klienta.</span><span class="sxs-lookup"><span data-stu-id="b28f7-123">Describes how to validate a user when your application is configured to use a client authentication service provider.</span></span>  
  
 [<span data-ttu-id="b28f7-124">Przewodnik: używanie usług aplikacji klienckich</span><span class="sxs-lookup"><span data-stu-id="b28f7-124">Walkthrough: Using Client Application Services</span></span>](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 <span data-ttu-id="b28f7-125">Zawiera opis sposobu łączenia wszystkich funkcji usług aplikacji klienta w pojedynczej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b28f7-125">Describes how to combine all client application services features in a single application.</span></span> <span data-ttu-id="b28f7-126">Ten przewodnik zawiera wskazówki dotyczące end-to-end.</span><span class="sxs-lookup"><span data-stu-id="b28f7-126">This walkthrough provides end-to-end guidance.</span></span> <span data-ttu-id="b28f7-127">Na przykład zawiera instrukcje dotyczące tworzenia aplikacji usługi sieci Web ASP.NET, którego można używać do testowania usługi aplikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="b28f7-127">For example, it includes instructions on how to create an ASP.NET Web Service Application that you can use to test client application services.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b28f7-128">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="b28f7-128">Reference</span></span>  
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
  
## <a name="see-also"></a><span data-ttu-id="b28f7-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b28f7-129">See Also</span></span>  
 [<span data-ttu-id="b28f7-130">Przegląd usług aplikacji ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b28f7-130">ASP.NET Application Services Overview</span></span>](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013)  
 [<span data-ttu-id="b28f7-131">Korzystanie z uwierzytelniania formularzy z Microsoft Ajax</span><span class="sxs-lookup"><span data-stu-id="b28f7-131">Using Forms Authentication with Microsoft Ajax</span></span>](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)  
 [<span data-ttu-id="b28f7-132">Przy użyciu ról informacji o Microsoft Ajax</span><span class="sxs-lookup"><span data-stu-id="b28f7-132">Using Roles Information with Microsoft Ajax</span></span>](http://msdn.microsoft.com/library/280f6ad9-ba1a-4fc9-b0cc-22e39e54a82d)  
 [<span data-ttu-id="b28f7-133">Przy użyciu informacji o profilu z Microsoft Ajax</span><span class="sxs-lookup"><span data-stu-id="b28f7-133">Using Profile Information with Microsoft Ajax</span></span>](http://msdn.microsoft.com/library/91239ae6-d01c-4f4e-a433-eb9040dbed61)  
 [<span data-ttu-id="b28f7-134">Uwierzytelnianie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b28f7-134">ASP.NET Authentication</span></span>](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1)  
 <span data-ttu-id="b28f7-135">[Zarządzanie autoryzację za pomocą ról](http://msdn.microsoft.com/library/01954ce4-39a2-487f-8153-a69f6f6f3195)  </span><span class="sxs-lookup"><span data-stu-id="b28f7-135">[Managing Authorization Using Roles](http://msdn.microsoft.com/library/01954ce4-39a2-487f-8153-a69f6f6f3195)  </span></span>  
 [<span data-ttu-id="b28f7-136">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="b28f7-136">Application Settings Overview</span></span>](../../../docs/framework/winforms/advanced/application-settings-overview.md)

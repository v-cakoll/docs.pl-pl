---
title: "Porady: określanie kontekstu zabezpieczeń dla usług"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, security
- security [Visual Studio], contexts
- contexts, Visual Studio security
- security [Visual Studio], service applications
- ServiceProcessInstaller class, security context
- services, security
- ServiceInstaller class, security context
ms.assetid: 02187c7b-dbf2-45f2-96c2-e11010225a22
caps.latest.revision: "10"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: 50a9c6ff7f02cda4475aa5390181fa5d410af161
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-the-security-context-for-services"></a><span data-ttu-id="d40ae-102">Porady: określanie kontekstu zabezpieczeń dla usług</span><span class="sxs-lookup"><span data-stu-id="d40ae-102">How to: Specify the Security Context for Services</span></span>
<span data-ttu-id="d40ae-103">Domyślnie usługi uruchamiane w kontekście zabezpieczeń inną niż zalogowanego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d40ae-103">By default, services run in a different security context than that of the logged-in user.</span></span> <span data-ttu-id="d40ae-104">Usługi uruchamiane w kontekście domyślnego konta systemu o nazwie `LocalSystem`, która umożliwi im różne przywileje dostępu do zasobów systemowych od użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d40ae-104">Services run in the context of the default system account, called `LocalSystem`, which gives them different access privileges to system resources than the user.</span></span> <span data-ttu-id="d40ae-105">Można zmienić to zachowanie, aby określić inne konto użytkownika usługi powinny uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="d40ae-105">You can change this behavior to specify a different user account under which your service should run.</span></span>  
  
 <span data-ttu-id="d40ae-106">Ustaw kontekst zabezpieczeń przez manipulowanie <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> właściwości dla procesu, w którym jest uruchamiana usługa.</span><span class="sxs-lookup"><span data-stu-id="d40ae-106">You set the security context by manipulating the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property for the process within which the service runs.</span></span> <span data-ttu-id="d40ae-107">Ta właściwość pozwala ustawić jedną z czterech typy kont usługi:</span><span class="sxs-lookup"><span data-stu-id="d40ae-107">This property allows you to set the service to one of four account types:</span></span>  
  
-   <span data-ttu-id="d40ae-108">`User`, co powoduje, że system z monitem o prawidłowej nazwy użytkownika i hasła, gdy usługa jest zainstalowana i działa w kontekście konta określonego przez pojedynczego użytkownika w sieci, a</span><span class="sxs-lookup"><span data-stu-id="d40ae-108">`User`, which causes the system to prompt for a valid user name and password when the service is installed and runs in the context of an account specified by a single user on the network;</span></span>  
  
-   <span data-ttu-id="d40ae-109">`LocalService`, które są uruchamiane w kontekście konta działa jako użytkownik bez uprawnień na komputerze lokalnym, przedstawiając poświadczeń anonimowego do dowolnego serwera zdalnego;</span><span class="sxs-lookup"><span data-stu-id="d40ae-109">`LocalService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents anonymous credentials to any remote server;</span></span>  
  
-   <span data-ttu-id="d40ae-110">`LocalSystem`, które są uruchamiane w kontekście konta, które udostępnia szerokie uprawnienia lokalnego, przedstawiając poświadczeń komputera do dowolnego serwera zdalnego;</span><span class="sxs-lookup"><span data-stu-id="d40ae-110">`LocalSystem`, which runs in the context of an account that provides extensive local privileges, and presents the computer's credentials to any remote server;</span></span>  
  
-   <span data-ttu-id="d40ae-111">`NetworkService`, które są uruchamiane w kontekście konta działa jako użytkownik bez uprawnień na komputerze lokalnym, przedstawiając poświadczeń komputera do dowolnego serwera zdalnego.</span><span class="sxs-lookup"><span data-stu-id="d40ae-111">`NetworkService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents the computer's credentials to any remote server.</span></span>  
  
 <span data-ttu-id="d40ae-112">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceProcess.ServiceAccount> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d40ae-112">For more information, see the <xref:System.ServiceProcess.ServiceAccount> enumeration.</span></span>  
  
### <a name="to-specify-the-security-context-for-a-service"></a><span data-ttu-id="d40ae-113">Aby określić kontekstu zabezpieczeń dla usługi</span><span class="sxs-lookup"><span data-stu-id="d40ae-113">To specify the security context for a service</span></span>  
  
1.  <span data-ttu-id="d40ae-114">Po utworzeniu usługi, należy dodać wymagane pliki instalacyjne dla niego.</span><span class="sxs-lookup"><span data-stu-id="d40ae-114">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="d40ae-115">Aby uzyskać więcej informacji, zobacz [porady: Dodawanie instalatorów do Twojej aplikacji usługi](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="d40ae-115">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
2.  <span data-ttu-id="d40ae-116">W Projektancie dostępu `ProjectInstaller` klasy, a następnie kliknij przycisk Instalatora procesu usługi dla usługi pracujesz.</span><span class="sxs-lookup"><span data-stu-id="d40ae-116">In the designer, access the `ProjectInstaller` class and click the service process installer for the service you are working with.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d40ae-117">Dla każdej aplikacji usługi istnieją co najmniej dwa składniki instalacji w `ProjectInstaller` klasy —, który instaluje procesy dla wszystkich usług w projekcie oraz jednego Instalatora dla każdej usługi, ta aplikacja zawiera.</span><span class="sxs-lookup"><span data-stu-id="d40ae-117">For every service application, there are at least two installation components in the `ProjectInstaller` class — one that installs the processes for all services in the project, and one installer for each service the application contains.</span></span> <span data-ttu-id="d40ae-118">W tym wystąpieniu chcesz wybrać <xref:System.ServiceProcess.ServiceProcessInstaller>.</span><span class="sxs-lookup"><span data-stu-id="d40ae-118">In this instance, you want to select <xref:System.ServiceProcess.ServiceProcessInstaller>.</span></span>  
  
3.  <span data-ttu-id="d40ae-119">W **właściwości** ustaw <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="d40ae-119">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> to the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d40ae-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d40ae-120">See Also</span></span>  
 [<span data-ttu-id="d40ae-121">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d40ae-121">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="d40ae-122">Porady: Dodawanie instalatorów od aplikacji usług</span><span class="sxs-lookup"><span data-stu-id="d40ae-122">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [<span data-ttu-id="d40ae-123">Porady: tworzenie usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d40ae-123">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)

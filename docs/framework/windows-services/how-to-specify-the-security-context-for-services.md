---
title: 'Instrukcje: Określanie kontekstu zabezpieczeń dla usług'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, security
- security [Visual Studio], contexts
- contexts, Visual Studio security
- security [Visual Studio], service applications
- ServiceProcessInstaller class, security context
- services, security
- ServiceInstaller class, security context
ms.assetid: 02187c7b-dbf2-45f2-96c2-e11010225a22
author: ghogen
ms.openlocfilehash: 633d378b2336b3ee166375a923252e0477e75127
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591667"
---
# <a name="how-to-specify-the-security-context-for-services"></a><span data-ttu-id="b6923-102">Instrukcje: Określanie kontekstu zabezpieczeń dla usług</span><span class="sxs-lookup"><span data-stu-id="b6923-102">How to: Specify the Security Context for Services</span></span>
<span data-ttu-id="b6923-103">Domyślnie usługi uruchamiane w kontekście zabezpieczeń inny niż zalogowany użytkownik.</span><span class="sxs-lookup"><span data-stu-id="b6923-103">By default, services run in a different security context than that of the logged-in user.</span></span> <span data-ttu-id="b6923-104">Usługi uruchamiane w kontekście domyślnego konta systemu o nazwie `LocalSystem`, która umożliwi im różne przywileje dostępu do zasobów systemowych, nie użytkownik.</span><span class="sxs-lookup"><span data-stu-id="b6923-104">Services run in the context of the default system account, called `LocalSystem`, which gives them different access privileges to system resources than the user.</span></span> <span data-ttu-id="b6923-105">Możesz zmienić to zachowanie, aby określić inne konto użytkownika na którym jest uruchamiany z usługą.</span><span class="sxs-lookup"><span data-stu-id="b6923-105">You can change this behavior to specify a different user account under which your service should run.</span></span>  
  
 <span data-ttu-id="b6923-106">Ustaw kontekst zabezpieczeń, manipulowanie <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> właściwości dla procesu, w którym usługa jest uruchamiana.</span><span class="sxs-lookup"><span data-stu-id="b6923-106">You set the security context by manipulating the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property for the process within which the service runs.</span></span> <span data-ttu-id="b6923-107">Ta właściwość umożliwia ustawianie usługi do zestawu obejmującego cztery typy konta:</span><span class="sxs-lookup"><span data-stu-id="b6923-107">This property allows you to set the service to one of four account types:</span></span>  
  
- <span data-ttu-id="b6923-108">`User`, która sprawia, że system wyświetla monit o podanie prawidłowej nazwy użytkownika i hasła, gdy usługa jest zainstalowana i działa w kontekście konta określonego przez pojedynczego użytkownika w sieci.</span><span class="sxs-lookup"><span data-stu-id="b6923-108">`User`, which causes the system to prompt for a valid user name and password when the service is installed and runs in the context of an account specified by a single user on the network;</span></span>  
  
- <span data-ttu-id="b6923-109">`LocalService`, które są uruchamiane w kontekście konta, który działa jako użytkownik bez uprawnień na komputerze lokalnym i przedstawia poświadczenia anonimowe każdemu zdalnemu serwerowi;</span><span class="sxs-lookup"><span data-stu-id="b6923-109">`LocalService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents anonymous credentials to any remote server;</span></span>  
  
- <span data-ttu-id="b6923-110">`LocalSystem`, które są uruchamiane w kontekście konta, które zapewnia szerokie uprawnienia lokalnego i przedstawia poświadczenia komputera każdemu zdalnemu serwerowi;</span><span class="sxs-lookup"><span data-stu-id="b6923-110">`LocalSystem`, which runs in the context of an account that provides extensive local privileges, and presents the computer's credentials to any remote server;</span></span>  
  
- <span data-ttu-id="b6923-111">`NetworkService`, które są uruchamiane w kontekście konta, który działa jako użytkownik bez uprawnień na komputerze lokalnym, a poświadczenia komputera każdemu zdalnemu serwerowi przedstawia.</span><span class="sxs-lookup"><span data-stu-id="b6923-111">`NetworkService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents the computer's credentials to any remote server.</span></span>  
  
 <span data-ttu-id="b6923-112">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceProcess.ServiceAccount> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="b6923-112">For more information, see the <xref:System.ServiceProcess.ServiceAccount> enumeration.</span></span>  
  
### <a name="to-specify-the-security-context-for-a-service"></a><span data-ttu-id="b6923-113">Do określenia kontekstu zabezpieczeń dla usługi</span><span class="sxs-lookup"><span data-stu-id="b6923-113">To specify the security context for a service</span></span>  
  
1. <span data-ttu-id="b6923-114">Po utworzeniu usługi, dodanie niezbędnych instalatorów dla niego.</span><span class="sxs-lookup"><span data-stu-id="b6923-114">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="b6923-115">Aby uzyskać więcej informacji, zobacz [jak: Dodawanie instalatorów od aplikacji usług](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="b6923-115">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
2. <span data-ttu-id="b6923-116">W Projektancie dostępu `ProjectInstaller` klasy, a następnie kliknij przycisk Instalatora procesu usługi dla usługi, którymi pracujesz.</span><span class="sxs-lookup"><span data-stu-id="b6923-116">In the designer, access the `ProjectInstaller` class and click the service process installer for the service you are working with.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b6923-117">Dla każdej aplikacji usługi są co najmniej dwa składniki instalacyjne w `ProjectInstaller` klasy — taki, który instaluje procesów dla wszystkich usług w projekcie i jednego Instalatora dla każdej usługi, które zawiera aplikację.</span><span class="sxs-lookup"><span data-stu-id="b6923-117">For every service application, there are at least two installation components in the `ProjectInstaller` class — one that installs the processes for all services in the project, and one installer for each service the application contains.</span></span> <span data-ttu-id="b6923-118">W tym przypadku chcesz wybrać <xref:System.ServiceProcess.ServiceProcessInstaller>.</span><span class="sxs-lookup"><span data-stu-id="b6923-118">In this instance, you want to select <xref:System.ServiceProcess.ServiceProcessInstaller>.</span></span>  
  
3. <span data-ttu-id="b6923-119">W **właściwości** oknie <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="b6923-119">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> to the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6923-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6923-120">See also</span></span>

- [<span data-ttu-id="b6923-121">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b6923-121">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="b6923-122">Instrukcje: Dodawanie instalatorów od aplikacji usług</span><span class="sxs-lookup"><span data-stu-id="b6923-122">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="b6923-123">Instrukcje: Tworzenie usług Windows</span><span class="sxs-lookup"><span data-stu-id="b6923-123">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)

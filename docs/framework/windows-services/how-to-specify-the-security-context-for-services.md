---
title: 'Instrukcje: Określanie kontekstu zabezpieczeń dla usług'
description: Określ kontekst zabezpieczeń usług. Usługi są uruchamiane w domyślnym kontekście konta systemowego mają inne prawa dostępu do zasobów systemowych niż zalogowany użytkownik.
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
ms.openlocfilehash: 4ed531cb520a781fd38f8bf5491da6948901a1d5
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925738"
---
# <a name="how-to-specify-the-security-context-for-services"></a><span data-ttu-id="c9c3d-104">Instrukcje: Określanie kontekstu zabezpieczeń dla usług</span><span class="sxs-lookup"><span data-stu-id="c9c3d-104">How to: Specify the Security Context for Services</span></span>
<span data-ttu-id="c9c3d-105">Domyślnie usługi są uruchamiane w innym kontekście zabezpieczeń niż zalogowany użytkownik.</span><span class="sxs-lookup"><span data-stu-id="c9c3d-105">By default, services run in a different security context than that of the logged-in user.</span></span> <span data-ttu-id="c9c3d-106">Usługi są uruchamiane w kontekście domyślnego konta systemowego o nazwie `LocalSystem` , które daje im różne uprawnienia dostępu do zasobów systemowych niż użytkownik.</span><span class="sxs-lookup"><span data-stu-id="c9c3d-106">Services run in the context of the default system account, called `LocalSystem`, which gives them different access privileges to system resources than the user.</span></span> <span data-ttu-id="c9c3d-107">Możesz zmienić to zachowanie, aby określić inne konto użytkownika, w ramach którego ma zostać uruchomiona usługa.</span><span class="sxs-lookup"><span data-stu-id="c9c3d-107">You can change this behavior to specify a different user account under which your service should run.</span></span>  
  
 <span data-ttu-id="c9c3d-108">Kontekst zabezpieczeń jest ustawiany przez manipulowanie <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> właściwością procesu, w którym działa usługa.</span><span class="sxs-lookup"><span data-stu-id="c9c3d-108">You set the security context by manipulating the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property for the process within which the service runs.</span></span> <span data-ttu-id="c9c3d-109">Ta właściwość umożliwia ustawienie jednego z czterech typów kont:</span><span class="sxs-lookup"><span data-stu-id="c9c3d-109">This property allows you to set the service to one of four account types:</span></span>  
  
- <span data-ttu-id="c9c3d-110">`User`, co powoduje, że system monituje o podanie prawidłowej nazwy użytkownika i hasła podczas instalacji usługi i jest uruchamiany w kontekście konta określonego przez pojedynczego użytkownika w sieci;</span><span class="sxs-lookup"><span data-stu-id="c9c3d-110">`User`, which causes the system to prompt for a valid user name and password when the service is installed and runs in the context of an account specified by a single user on the network;</span></span>  
  
- <span data-ttu-id="c9c3d-111">`LocalService`, który działa w kontekście konta, które działa jako użytkownik nieuprzywilejowany na komputerze lokalnym i przedstawia anonimowe poświadczenia na dowolnym serwerze zdalnym;</span><span class="sxs-lookup"><span data-stu-id="c9c3d-111">`LocalService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents anonymous credentials to any remote server;</span></span>  
  
- <span data-ttu-id="c9c3d-112">`LocalSystem`, który działa w kontekście konta, które zapewnia szerokie uprawnienia lokalne, i przedstawia poświadczenia komputera na dowolnym serwerze zdalnym;</span><span class="sxs-lookup"><span data-stu-id="c9c3d-112">`LocalSystem`, which runs in the context of an account that provides extensive local privileges, and presents the computer's credentials to any remote server;</span></span>  
  
- <span data-ttu-id="c9c3d-113">`NetworkService`, który działa w kontekście konta, które działa jako użytkownik nieuprzywilejowany na komputerze lokalnym i przedstawia poświadczenia komputera na dowolnym serwerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="c9c3d-113">`NetworkService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents the computer's credentials to any remote server.</span></span>  
  
 <span data-ttu-id="c9c3d-114">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceProcess.ServiceAccount> Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="c9c3d-114">For more information, see the <xref:System.ServiceProcess.ServiceAccount> enumeration.</span></span>  
  
### <a name="to-specify-the-security-context-for-a-service"></a><span data-ttu-id="c9c3d-115">Aby określić kontekst zabezpieczeń dla usługi</span><span class="sxs-lookup"><span data-stu-id="c9c3d-115">To specify the security context for a service</span></span>  
  
1. <span data-ttu-id="c9c3d-116">Po utworzeniu usługi należy dodać do niej niezbędne Instalatory.</span><span class="sxs-lookup"><span data-stu-id="c9c3d-116">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="c9c3d-117">Aby uzyskać więcej informacji, zobacz [jak: Dodawanie instalatorów do aplikacji usługi](how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="c9c3d-117">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>  
  
2. <span data-ttu-id="c9c3d-118">W projektancie uzyskaj dostęp do `ProjectInstaller` klasy i kliknij Instalatora procesów usługi dla usługi, z którą pracujesz.</span><span class="sxs-lookup"><span data-stu-id="c9c3d-118">In the designer, access the `ProjectInstaller` class and click the service process installer for the service you are working with.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c9c3d-119">Dla każdej aplikacji usługi w klasie istnieją co najmniej dwa składniki instalacyjne `ProjectInstaller` — jedną, która instaluje procesy dla wszystkich usług w projekcie, oraz jeden Instalator dla każdej usługi zawierającej daną aplikację.</span><span class="sxs-lookup"><span data-stu-id="c9c3d-119">For every service application, there are at least two installation components in the `ProjectInstaller` class — one that installs the processes for all services in the project, and one installer for each service the application contains.</span></span> <span data-ttu-id="c9c3d-120">W tym przypadku należy wybrać opcję <xref:System.ServiceProcess.ServiceProcessInstaller> .</span><span class="sxs-lookup"><span data-stu-id="c9c3d-120">In this instance, you want to select <xref:System.ServiceProcess.ServiceProcessInstaller>.</span></span>  
  
3. <span data-ttu-id="c9c3d-121">W oknie **Właściwości** Ustaw <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="c9c3d-121">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> to the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9c3d-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c9c3d-122">See also</span></span>

- [<span data-ttu-id="c9c3d-123">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c9c3d-123">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="c9c3d-124">Instrukcje: Dodawanie instalatorów od aplikacji usług</span><span class="sxs-lookup"><span data-stu-id="c9c3d-124">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="c9c3d-125">Instrukcje: Tworzenie usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c9c3d-125">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)

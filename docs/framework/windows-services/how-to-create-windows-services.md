---
title: 'Porady: tworzenie usług systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
author: ghogen
manager: douge
ms.openlocfilehash: 7719af9393bee816665040d6e4ced191419d0855
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517865"
---
# <a name="how-to-create-windows-services"></a><span data-ttu-id="26a8b-102">Porady: tworzenie usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="26a8b-102">How to: Create Windows Services</span></span>
<span data-ttu-id="26a8b-103">Podczas tworzenia usługi za pomocą szablonu projektu programu Visual Studio o nazwie **usługi systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="26a8b-103">When you create a service, you can use a Visual Studio project template called **Windows Service**.</span></span> <span data-ttu-id="26a8b-104">Ten szablon automatycznie nie większość zadań można za pomocą odwołań do odpowiednich klas i przestrzenie nazw, konfigurowanie dziedziczenia z klasy podstawowej dla usług, i zastępowanie kilka metod prawdopodobnie do zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="26a8b-104">This template automatically does much of the work for you by referencing the appropriate classes and namespaces, setting up the inheritance from the base class for services, and overriding several of the methods you're likely to want to override.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="26a8b-105">Szablon projektu usług systemu Windows nie jest dostępna w wersji Express programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="26a8b-105">The Windows Services project template is not available in the Express edition of Visual Studio.</span></span>  
  
 <span data-ttu-id="26a8b-106">Co najmniej Aby utworzyć usługę funkcjonalną należy:</span><span class="sxs-lookup"><span data-stu-id="26a8b-106">At a minimum, to create a functional service you must:</span></span>  
  
-   <span data-ttu-id="26a8b-107">Ustaw <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="26a8b-107">Set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property.</span></span>  
  
-   <span data-ttu-id="26a8b-108">Utwórz niezbędne pliki instalacyjne aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="26a8b-108">Create the necessary installers for your service application.</span></span>  
  
-   <span data-ttu-id="26a8b-109">Zastąpienia i określ kod <xref:System.ServiceProcess.ServiceBase.OnStart%2A> i <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody dostosowania sposoby, w którym działa usługa.</span><span class="sxs-lookup"><span data-stu-id="26a8b-109">Override and specify code for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods to customize the ways in which your service behaves.</span></span>  
  
### <a name="to-create-a-windows-service-application"></a><span data-ttu-id="26a8b-110">Aby utworzyć aplikację usługi systemu Windows</span><span class="sxs-lookup"><span data-stu-id="26a8b-110">To create a Windows Service application</span></span>  
  
1.  <span data-ttu-id="26a8b-111">Utwórz **usługi systemu Windows** projektu.</span><span class="sxs-lookup"><span data-stu-id="26a8b-111">Create a **Windows Service** project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="26a8b-112">Aby uzyskać instrukcje dotyczące zapisywania usługi bez użycia szablonu, zobacz [porady: programowane pisanie usług](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).</span><span class="sxs-lookup"><span data-stu-id="26a8b-112">For instructions on writing a service without using the template, see [How to: Write Services Programmatically](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).</span></span>  
  
2.  <span data-ttu-id="26a8b-113">W **właściwości** ustaw <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwości usługi.</span><span class="sxs-lookup"><span data-stu-id="26a8b-113">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for your service.</span></span>  
  
     <span data-ttu-id="26a8b-114">![Ustaw właściwość ServiceName. ] (../../../docs/framework/windows-services/media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span><span class="sxs-lookup"><span data-stu-id="26a8b-114">![Set the ServiceName property.](../../../docs/framework/windows-services/media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="26a8b-115">Wartość <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwość zawsze musi odpowiadać nazwie rejestrowane w klasach Instalatora.</span><span class="sxs-lookup"><span data-stu-id="26a8b-115">The value of the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property must always match the name recorded in the installer classes.</span></span> <span data-ttu-id="26a8b-116">Jeśli zmienisz tę właściwość, należy zaktualizować <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwość również klas Instalatora.</span><span class="sxs-lookup"><span data-stu-id="26a8b-116">If you change this property, you must update the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property of installer classes as well.</span></span>  
  
3.  <span data-ttu-id="26a8b-117">Ustaw dowolne z poniższych właściwości, aby określić, jak działają usługi.</span><span class="sxs-lookup"><span data-stu-id="26a8b-117">Set any of the following properties to determine how your service will function.</span></span>  
  
    |<span data-ttu-id="26a8b-118">Właściwość</span><span class="sxs-lookup"><span data-stu-id="26a8b-118">Property</span></span>|<span data-ttu-id="26a8b-119">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="26a8b-119">Setting</span></span>|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|<span data-ttu-id="26a8b-120">`True` Aby wskazać, że usługa będzie akceptować żądania przestanie działać; `false` aby zapobiec zatrzymania usługi.</span><span class="sxs-lookup"><span data-stu-id="26a8b-120">`True` to indicate that the service will accept requests to stop running; `false` to prevent the service from being stopped.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|<span data-ttu-id="26a8b-121">`True` Aby wskazać, że chce otrzymywać powiadomienia, gdy komputer, na którym mieszka wyłączany, co go do wywołania usługi <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> procedury.</span><span class="sxs-lookup"><span data-stu-id="26a8b-121">`True` to indicate that the service wants to receive notification when the computer on which it lives shuts down, enabling it to call the <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> procedure.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|<span data-ttu-id="26a8b-122">`True` Aby wskazać, że usługa będzie akceptować żądania, aby wstrzymać lub wznowić uruchomiony; `false` zapobiegające usługi wstrzymać i wznowić.</span><span class="sxs-lookup"><span data-stu-id="26a8b-122">`True` to indicate that the service will accept requests to pause or to resume running; `false` to prevent the service from being paused and resumed.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|<span data-ttu-id="26a8b-123">`True` Aby wskazać, że usługa może obsługiwać powiadomień o zmianach stanu zasilania komputera; `false` aby zapobiec powiadomienia o tych zmianach usługi.</span><span class="sxs-lookup"><span data-stu-id="26a8b-123">`True` to indicate that the service can handle notification of changes to the computer's power status; `false` to prevent the service from being notified of these changes.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|<span data-ttu-id="26a8b-124">`True` na zapisywanie wpisów informacyjny w dzienniku zdarzeń aplikacji, gdy usługa wykonuje akcję; `false` wyłączenie tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="26a8b-124">`True` to write informational entries to the Application event log when your service performs an action; `false` to disable this functionality.</span></span> <span data-ttu-id="26a8b-125">Aby uzyskać więcej informacji, zobacz [porady: dziennika informacji o usługach](../../../docs/framework/windows-services/how-to-log-information-about-services.md).</span><span class="sxs-lookup"><span data-stu-id="26a8b-125">For more information, see [How to: Log Information About Services](../../../docs/framework/windows-services/how-to-log-information-about-services.md).</span></span> <span data-ttu-id="26a8b-126">**Uwaga:** domyślnie <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> ma ustawioną wartość `true`.</span><span class="sxs-lookup"><span data-stu-id="26a8b-126">**Note:**  By default, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> is set to `true`.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="26a8b-127">Gdy <xref:System.ServiceProcess.ServiceBase.CanStop%2A> lub <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> ustawiono `false`, **Menedżera sterowania usługami** spowoduje wyłączenie odpowiednich opcji menu, aby zatrzymać, wstrzymać lub kontynuować korzystanie z usługi.</span><span class="sxs-lookup"><span data-stu-id="26a8b-127">When <xref:System.ServiceProcess.ServiceBase.CanStop%2A> or <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> are set to `false`, the **Service Control Manager** will disable the corresponding menu options to stop, pause, or continue the service.</span></span>  
  
4.  <span data-ttu-id="26a8b-128">Edytor kodu dostępu, a następnie wypełnij przetwarzania dla <xref:System.ServiceProcess.ServiceBase.OnStart%2A> i <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedur.</span><span class="sxs-lookup"><span data-stu-id="26a8b-128">Access the Code Editor and fill in the processing you want for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures.</span></span>  
  
5.  <span data-ttu-id="26a8b-129">Zastąpienie innych metod, dla których chcesz zdefiniować funkcji.</span><span class="sxs-lookup"><span data-stu-id="26a8b-129">Override any other methods for which you want to define functionality.</span></span>  
  
6.  <span data-ttu-id="26a8b-130">Dodanie niezbędnych instalatorów dla aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="26a8b-130">Add the necessary installers for your service application.</span></span> <span data-ttu-id="26a8b-131">Aby uzyskać więcej informacji, zobacz [porady: Dodawanie instalatorów do Twojej aplikacji usługi](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="26a8b-131">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
7.  <span data-ttu-id="26a8b-132">Tworzenie projektu, wybierając **Kompiluj rozwiązanie** z **kompilacji** menu.</span><span class="sxs-lookup"><span data-stu-id="26a8b-132">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="26a8b-133">Nie naciśnij klawisz F5, aby uruchomić projekt — nie można uruchomić projekt usługi w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="26a8b-133">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
8.  <span data-ttu-id="26a8b-134">Zainstaluj usługę.</span><span class="sxs-lookup"><span data-stu-id="26a8b-134">Install the service.</span></span> <span data-ttu-id="26a8b-135">Aby uzyskać więcej informacji, zobacz [porady: Instalowanie i odinstalowywanie usług](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="26a8b-135">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26a8b-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="26a8b-136">See Also</span></span>  
 [<span data-ttu-id="26a8b-137">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="26a8b-137">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="26a8b-138">Instrukcje: programowane pisanie usług</span><span class="sxs-lookup"><span data-stu-id="26a8b-138">How to: Write Services Programmatically</span></span>](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)  
 [<span data-ttu-id="26a8b-139">Instrukcje: dodawanie instalatorów od aplikacji usług</span><span class="sxs-lookup"><span data-stu-id="26a8b-139">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [<span data-ttu-id="26a8b-140">Instrukcje: rejestrowanie informacji o usługach</span><span class="sxs-lookup"><span data-stu-id="26a8b-140">How to: Log Information About Services</span></span>](../../../docs/framework/windows-services/how-to-log-information-about-services.md)  
 [<span data-ttu-id="26a8b-141">Instrukcje: uruchamianie usług</span><span class="sxs-lookup"><span data-stu-id="26a8b-141">How to: Start Services</span></span>](../../../docs/framework/windows-services/how-to-start-services.md)  
 [<span data-ttu-id="26a8b-142">Instrukcje: określanie kontekstu zabezpieczeń dla usług</span><span class="sxs-lookup"><span data-stu-id="26a8b-142">How to: Specify the Security Context for Services</span></span>](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)  
 [<span data-ttu-id="26a8b-143">Instrukcje: instalowanie i odinstalowywanie usług</span><span class="sxs-lookup"><span data-stu-id="26a8b-143">How to: Install and Uninstall Services</span></span>](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [<span data-ttu-id="26a8b-144">Przewodnik: tworzenie aplikacji usługowej systemu Windows w Projektancie składników</span><span class="sxs-lookup"><span data-stu-id="26a8b-144">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

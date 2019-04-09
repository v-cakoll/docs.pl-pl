---
title: 'Instrukcje: Tworzenie usług systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
author: ghogen
ms.openlocfilehash: 26c903379afcab3d2d534272912c046cdffb6fed
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132499"
---
# <a name="how-to-create-windows-services"></a><span data-ttu-id="d9fd3-102">Instrukcje: Tworzenie usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d9fd3-102">How to: Create Windows Services</span></span>
<span data-ttu-id="d9fd3-103">Podczas tworzenia usługi można użyć szablonu projektu programu Visual Studio o nazwie **usługi Windows**.</span><span class="sxs-lookup"><span data-stu-id="d9fd3-103">When you create a service, you can use a Visual Studio project template called **Windows Service**.</span></span> <span data-ttu-id="d9fd3-104">Ten szablon automatycznie wykonuje znaczną część pracy za Ciebie, odwołując się do odpowiednich klas i przestrzenie nazw, konfigurując ustawienia dziedziczenia z klasy bazowej dla usług oraz zastępując kilka metod prawdopodobnie chcesz zastąpić.</span><span class="sxs-lookup"><span data-stu-id="d9fd3-104">This template automatically does much of the work for you by referencing the appropriate classes and namespaces, setting up the inheritance from the base class for services, and overriding several of the methods you're likely to want to override.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="d9fd3-105">Szablon projektu usług Windows nie jest dostępna w wersji Express programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d9fd3-105">The Windows Services project template is not available in the Express edition of Visual Studio.</span></span>  
  
 <span data-ttu-id="d9fd3-106">Jako minimum Aby utworzyć usługę funkcjonalną należy:</span><span class="sxs-lookup"><span data-stu-id="d9fd3-106">At a minimum, to create a functional service you must:</span></span>  
  
-   <span data-ttu-id="d9fd3-107">Ustaw <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="d9fd3-107">Set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property.</span></span>  
  
-   <span data-ttu-id="d9fd3-108">Utwórz niezbędne pliki instalacyjne dla aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="d9fd3-108">Create the necessary installers for your service application.</span></span>  
  
-   <span data-ttu-id="d9fd3-109">Zastąpienia i określ kod <xref:System.ServiceProcess.ServiceBase.OnStart%2A> i <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody dostosowania sposobów, w którym działa usługa.</span><span class="sxs-lookup"><span data-stu-id="d9fd3-109">Override and specify code for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods to customize the ways in which your service behaves.</span></span>  
  
### <a name="to-create-a-windows-service-application"></a><span data-ttu-id="d9fd3-110">Aby utworzyć aplikację Windows Service</span><span class="sxs-lookup"><span data-stu-id="d9fd3-110">To create a Windows Service application</span></span>  
  
1.  <span data-ttu-id="d9fd3-111">Tworzenie **usługi Windows** projektu.</span><span class="sxs-lookup"><span data-stu-id="d9fd3-111">Create a **Windows Service** project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d9fd3-112">Aby uzyskać instrukcje dotyczące pisania usługi bez użycia szablonu, zobacz [jak: Programowane pisanie usług](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).</span><span class="sxs-lookup"><span data-stu-id="d9fd3-112">For instructions on writing a service without using the template, see [How to: Write Services Programmatically](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).</span></span>  
  
2.  <span data-ttu-id="d9fd3-113">W **właściwości** oknie <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwości dla Twojej usługi.</span><span class="sxs-lookup"><span data-stu-id="d9fd3-113">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for your service.</span></span>  
  
     <span data-ttu-id="d9fd3-114">![Ustaw właściwość ServiceName. ](../../../docs/framework/windows-services/media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span><span class="sxs-lookup"><span data-stu-id="d9fd3-114">![Set the ServiceName property.](../../../docs/framework/windows-services/media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d9fd3-115">Wartość <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwość musi zawsze odpowiadać nazwie zarejestrowanej w klasach Instalatora.</span><span class="sxs-lookup"><span data-stu-id="d9fd3-115">The value of the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property must always match the name recorded in the installer classes.</span></span> <span data-ttu-id="d9fd3-116">Jeśli zmienisz tę właściwość, należy zaktualizować <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwości również w klasach Instalatora.</span><span class="sxs-lookup"><span data-stu-id="d9fd3-116">If you change this property, you must update the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property of installer classes as well.</span></span>  
  
3.  <span data-ttu-id="d9fd3-117">Ustaw dowolne z następujących właściwości, aby określić, jak będzie działać usługa.</span><span class="sxs-lookup"><span data-stu-id="d9fd3-117">Set any of the following properties to determine how your service will function.</span></span>  
  
    |<span data-ttu-id="d9fd3-118">Właściwość</span><span class="sxs-lookup"><span data-stu-id="d9fd3-118">Property</span></span>|<span data-ttu-id="d9fd3-119">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="d9fd3-119">Setting</span></span>|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|`True` <span data-ttu-id="d9fd3-120">Aby wskazać, że usługa akceptuje żądania zatrzymania działania; `false` zapobiega zatrzymanie usługi.</span><span class="sxs-lookup"><span data-stu-id="d9fd3-120">to indicate that the service will accept requests to stop running; `false` to prevent the service from being stopped.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|`True` <span data-ttu-id="d9fd3-121">Aby wskazać, że usługa chce otrzymywać powiadomienia o wyłączaniu komputera, na którym ją umieszczono, dzięki czemu może wywołać <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> procedury.</span><span class="sxs-lookup"><span data-stu-id="d9fd3-121">to indicate that the service wants to receive notification when the computer on which it lives shuts down, enabling it to call the <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> procedure.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|`True` <span data-ttu-id="d9fd3-122">Aby wskazać, że usługa akceptuje żądania wstrzymania lub wznowienia działania; `false` aby uniemożliwić wstrzymywanie i wznawianie przez usługę.</span><span class="sxs-lookup"><span data-stu-id="d9fd3-122">to indicate that the service will accept requests to pause or to resume running; `false` to prevent the service from being paused and resumed.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|`True` <span data-ttu-id="d9fd3-123">Aby wskazać, że usługa może obsługiwać powiadomienia o zmianach stanu zasilania komputera `false` zapobiega bycia powiadamianym o tych zmianach usługi.</span><span class="sxs-lookup"><span data-stu-id="d9fd3-123">to indicate that the service can handle notification of changes to the computer's power status; `false` to prevent the service from being notified of these changes.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|`True` <span data-ttu-id="d9fd3-124">Aby zapisywać wpisy informacyjne w dzienniku zdarzeń aplikacji, gdy usługa wykonuje akcję; `false` Aby wyłączyć tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="d9fd3-124">to write informational entries to the Application event log when your service performs an action; `false` to disable this functionality.</span></span> <span data-ttu-id="d9fd3-125">Aby uzyskać więcej informacji, zobacz [jak: Rejestrowanie informacji o usługach](../../../docs/framework/windows-services/how-to-log-information-about-services.md).</span><span class="sxs-lookup"><span data-stu-id="d9fd3-125">For more information, see [How to: Log Information About Services](../../../docs/framework/windows-services/how-to-log-information-about-services.md).</span></span> <span data-ttu-id="d9fd3-126">**Uwaga:**  Domyślnie <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> ustawiono `true`.</span><span class="sxs-lookup"><span data-stu-id="d9fd3-126">**Note:**  By default, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> is set to `true`.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="d9fd3-127">Gdy <xref:System.ServiceProcess.ServiceBase.CanStop%2A> lub <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> są ustawione na `false`, **Menedżera sterowania usługami** spowoduje wyłączenie odpowiednich opcji menu, aby zatrzymać, wstrzymać lub kontynuować usługę.</span><span class="sxs-lookup"><span data-stu-id="d9fd3-127">When <xref:System.ServiceProcess.ServiceBase.CanStop%2A> or <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> are set to `false`, the **Service Control Manager** will disable the corresponding menu options to stop, pause, or continue the service.</span></span>  
  
4.  <span data-ttu-id="d9fd3-128">Wejdź do edytora kodu, a następnie wypełnij przetwarzania dla <xref:System.ServiceProcess.ServiceBase.OnStart%2A> i <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedur.</span><span class="sxs-lookup"><span data-stu-id="d9fd3-128">Access the Code Editor and fill in the processing you want for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures.</span></span>  
  
5.  <span data-ttu-id="d9fd3-129">Zastąpienie wszelkich innych metod, które mają zostać zdefiniowane funkcje.</span><span class="sxs-lookup"><span data-stu-id="d9fd3-129">Override any other methods for which you want to define functionality.</span></span>  
  
6.  <span data-ttu-id="d9fd3-130">Dodanie niezbędnych instalatorów dla aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="d9fd3-130">Add the necessary installers for your service application.</span></span> <span data-ttu-id="d9fd3-131">Aby uzyskać więcej informacji, zobacz [jak: Dodawanie instalatorów od aplikacji usług](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="d9fd3-131">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
7.  <span data-ttu-id="d9fd3-132">Kompilowanie projektu przez wybranie **Kompiluj rozwiązanie** z **kompilacji** menu.</span><span class="sxs-lookup"><span data-stu-id="d9fd3-132">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d9fd3-133">Nie wciskaj F5, aby uruchomić projekt — nie można uruchomić projektu usługi w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="d9fd3-133">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
8.  <span data-ttu-id="d9fd3-134">Zainstaluj usługę.</span><span class="sxs-lookup"><span data-stu-id="d9fd3-134">Install the service.</span></span> <span data-ttu-id="d9fd3-135">Aby uzyskać więcej informacji, zobacz [jak: Instalowanie i odinstalowywanie usług](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="d9fd3-135">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9fd3-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d9fd3-136">See also</span></span>

- [<span data-ttu-id="d9fd3-137">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d9fd3-137">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="d9fd3-138">Instrukcje: Programowane pisanie usług</span><span class="sxs-lookup"><span data-stu-id="d9fd3-138">How to: Write Services Programmatically</span></span>](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)
- [<span data-ttu-id="d9fd3-139">Instrukcje: Dodawanie instalatorów od aplikacji usług</span><span class="sxs-lookup"><span data-stu-id="d9fd3-139">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="d9fd3-140">Instrukcje: Rejestrowanie informacji o usługach</span><span class="sxs-lookup"><span data-stu-id="d9fd3-140">How to: Log Information About Services</span></span>](../../../docs/framework/windows-services/how-to-log-information-about-services.md)
- [<span data-ttu-id="d9fd3-141">Instrukcje: Uruchamianie usług</span><span class="sxs-lookup"><span data-stu-id="d9fd3-141">How to: Start Services</span></span>](../../../docs/framework/windows-services/how-to-start-services.md)
- [<span data-ttu-id="d9fd3-142">Instrukcje: Określanie kontekstu zabezpieczeń dla usług</span><span class="sxs-lookup"><span data-stu-id="d9fd3-142">How to: Specify the Security Context for Services</span></span>](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)
- [<span data-ttu-id="d9fd3-143">Instrukcje: Instalowanie i odinstalowywanie usług</span><span class="sxs-lookup"><span data-stu-id="d9fd3-143">How to: Install and Uninstall Services</span></span>](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)
- [<span data-ttu-id="d9fd3-144">Przewodnik: Tworzenie aplikacji usługi Windows w Projektancie składników</span><span class="sxs-lookup"><span data-stu-id="d9fd3-144">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

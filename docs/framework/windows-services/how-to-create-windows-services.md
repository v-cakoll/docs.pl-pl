---
title: 'Porady: tworzenie usług systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
author: ghogen
ms.openlocfilehash: 514675b3c3ce1f6701dff571361df672fb520c6a
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053660"
---
# <a name="how-to-create-windows-services"></a><span data-ttu-id="942c5-102">Porady: tworzenie usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="942c5-102">How to: Create Windows Services</span></span>
<span data-ttu-id="942c5-103">Podczas tworzenia usługi można użyć szablonu projektu programu Visual Studio o nazwie **Usługa systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="942c5-103">When you create a service, you can use a Visual Studio project template called **Windows Service**.</span></span> <span data-ttu-id="942c5-104">Ten szablon automatycznie wykonuje większość pracy za Ciebie, odwołując się do odpowiednich klas i przestrzeni nazw, konfigurując dziedziczenie z klasy podstawowej dla usług i zastępując kilka metod, które mogą zostać przesłonięte.</span><span class="sxs-lookup"><span data-stu-id="942c5-104">This template automatically does much of the work for you by referencing the appropriate classes and namespaces, setting up the inheritance from the base class for services, and overriding several of the methods you're likely to want to override.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="942c5-105">Szablon projektu usług systemu Windows nie jest dostępny w wersji Express programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="942c5-105">The Windows Services project template is not available in the Express edition of Visual Studio.</span></span>  
  
 <span data-ttu-id="942c5-106">Aby utworzyć usługę funkcjonalną, należy co najmniej:</span><span class="sxs-lookup"><span data-stu-id="942c5-106">At a minimum, to create a functional service you must:</span></span>  
  
- <span data-ttu-id="942c5-107">Ustaw <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwość.</span><span class="sxs-lookup"><span data-stu-id="942c5-107">Set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property.</span></span>  
  
- <span data-ttu-id="942c5-108">Utwórz niezbędne Instalatory dla aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="942c5-108">Create the necessary installers for your service application.</span></span>  
  
- <span data-ttu-id="942c5-109">Przesłoń i określ kod dla <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metod <xref:System.ServiceProcess.ServiceBase.OnStop%2A> i, aby dostosować sposób zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="942c5-109">Override and specify code for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods to customize the ways in which your service behaves.</span></span>  
  
### <a name="to-create-a-windows-service-application"></a><span data-ttu-id="942c5-110">Aby utworzyć aplikację usługi systemu Windows</span><span class="sxs-lookup"><span data-stu-id="942c5-110">To create a Windows Service application</span></span>  
  
1. <span data-ttu-id="942c5-111">Utwórz projekt **usługi systemu Windows** .</span><span class="sxs-lookup"><span data-stu-id="942c5-111">Create a **Windows Service** project.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="942c5-112">Aby uzyskać instrukcje dotyczące pisania usługi bez użycia szablonu, zobacz [jak: programowe pisanie usług](how-to-write-services-programmatically.md).</span><span class="sxs-lookup"><span data-stu-id="942c5-112">For instructions on writing a service without using the template, see [How to: Write Services Programmatically](how-to-write-services-programmatically.md).</span></span>  
  
2. <span data-ttu-id="942c5-113">W oknie **Właściwości** Ustaw <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwość usługi.</span><span class="sxs-lookup"><span data-stu-id="942c5-113">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for your service.</span></span>  
  
     <span data-ttu-id="942c5-114">![Ustaw właściwość ServiceName.] (./media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span><span class="sxs-lookup"><span data-stu-id="942c5-114">![Set the ServiceName property.](./media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="942c5-115">Wartość <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwości musi zawsze odpowiadać nazwie zarejestrowanej w klasach Instalatora.</span><span class="sxs-lookup"><span data-stu-id="942c5-115">The value of the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property must always match the name recorded in the installer classes.</span></span> <span data-ttu-id="942c5-116">W przypadku zmiany tej właściwości należy również zaktualizować <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> Właściwość klas Instalatora.</span><span class="sxs-lookup"><span data-stu-id="942c5-116">If you change this property, you must update the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property of installer classes as well.</span></span>  
  
3. <span data-ttu-id="942c5-117">Ustaw dowolne z następujących właściwości, aby określić, jak będzie działać usługa.</span><span class="sxs-lookup"><span data-stu-id="942c5-117">Set any of the following properties to determine how your service will function.</span></span>  
  
    |<span data-ttu-id="942c5-118">Właściwość</span><span class="sxs-lookup"><span data-stu-id="942c5-118">Property</span></span>|<span data-ttu-id="942c5-119">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="942c5-119">Setting</span></span>|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|<span data-ttu-id="942c5-120">`True`, aby wskazać, że usługa będzie akceptować żądania zatrzymania działania; `false` , aby zapobiec zatrzymaniu usługi.</span><span class="sxs-lookup"><span data-stu-id="942c5-120">`True` to indicate that the service will accept requests to stop running; `false` to prevent the service from being stopped.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|<span data-ttu-id="942c5-121">`True`, aby wskazać, że usługa chce otrzymywać powiadomienie, gdy komputer, na którym się znajduje, jest zamykana, umożliwiając mu wywołanie <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> procedury.</span><span class="sxs-lookup"><span data-stu-id="942c5-121">`True` to indicate that the service wants to receive notification when the computer on which it lives shuts down, enabling it to call the <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> procedure.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|<span data-ttu-id="942c5-122">`True`, aby wskazać, że usługa będzie akceptować żądania wstrzymania lub wznowienia działania. `false` aby zapobiec wstrzymaniu i wznowieniu usługi.</span><span class="sxs-lookup"><span data-stu-id="942c5-122">`True` to indicate that the service will accept requests to pause or to resume running; `false` to prevent the service from being paused and resumed.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|<span data-ttu-id="942c5-123">`True`Aby wskazać, że usługa może obsługiwać powiadomienia o zmianach stanu zasilacza komputera; `false` aby zapobiec powiadamianiu usługi o tych zmianach.</span><span class="sxs-lookup"><span data-stu-id="942c5-123">`True` to indicate that the service can handle notification of changes to the computer's power status; `false` to prevent the service from being notified of these changes.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|<span data-ttu-id="942c5-124">`True`w celu zapisania wpisów informacyjnych w dzienniku zdarzeń aplikacji, gdy usługa wykonuje akcję; `false` aby wyłączyć tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="942c5-124">`True` to write informational entries to the Application event log when your service performs an action; `false` to disable this functionality.</span></span> <span data-ttu-id="942c5-125">Aby uzyskać więcej informacji, zobacz [jak: rejestrować informacje o usługach](how-to-log-information-about-services.md).</span><span class="sxs-lookup"><span data-stu-id="942c5-125">For more information, see [How to: Log Information About Services](how-to-log-information-about-services.md).</span></span> <span data-ttu-id="942c5-126">**Uwaga:**  Domyślnie <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> jest ustawiony na `true`.</span><span class="sxs-lookup"><span data-stu-id="942c5-126">**Note:**  By default, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> is set to `true`.</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="942c5-127">Gdy <xref:System.ServiceProcess.ServiceBase.CanStop%2A> lub <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> jest ustawiona na `false`, **Menedżer sterowania usługami** wyłącza odpowiednie opcje menu, aby zatrzymać, wstrzymać lub kontynuować usługę.</span><span class="sxs-lookup"><span data-stu-id="942c5-127">When <xref:System.ServiceProcess.ServiceBase.CanStop%2A> or <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> are set to `false`, the **Service Control Manager** will disable the corresponding menu options to stop, pause, or continue the service.</span></span>  
  
4. <span data-ttu-id="942c5-128">Uzyskaj dostęp do edytora kodu i Wypełnij odpowiednie przetwarzanie dla procedur <xref:System.ServiceProcess.ServiceBase.OnStart%2A> i. <xref:System.ServiceProcess.ServiceBase.OnStop%2A></span><span class="sxs-lookup"><span data-stu-id="942c5-128">Access the Code Editor and fill in the processing you want for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures.</span></span>  
  
5. <span data-ttu-id="942c5-129">Zastąp wszystkie inne metody, dla których chcesz zdefiniować funkcję.</span><span class="sxs-lookup"><span data-stu-id="942c5-129">Override any other methods for which you want to define functionality.</span></span>  
  
6. <span data-ttu-id="942c5-130">Dodanie niezbędnych instalatorów dla aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="942c5-130">Add the necessary installers for your service application.</span></span> <span data-ttu-id="942c5-131">Aby uzyskać więcej informacji, zobacz [jak: Dodawanie instalatorów do aplikacji usługi](how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="942c5-131">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>  
  
7. <span data-ttu-id="942c5-132">Skompiluj projekt, wybierając opcję **Kompiluj rozwiązanie** w menu **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="942c5-132">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="942c5-133">Nie należy naciskać klawisza F5, aby uruchomić projekt — nie można uruchomić projektu usługi w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="942c5-133">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
8. <span data-ttu-id="942c5-134">Zainstaluj usługę.</span><span class="sxs-lookup"><span data-stu-id="942c5-134">Install the service.</span></span> <span data-ttu-id="942c5-135">Aby uzyskać więcej informacji, zobacz [jak: Instalowanie i odinstalowywanie usług](how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="942c5-135">For more information, see [How to: Install and Uninstall Services](how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="942c5-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="942c5-136">See also</span></span>

- [<span data-ttu-id="942c5-137">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="942c5-137">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="942c5-138">Porady: programowane pisanie usług</span><span class="sxs-lookup"><span data-stu-id="942c5-138">How to: Write Services Programmatically</span></span>](how-to-write-services-programmatically.md)
- [<span data-ttu-id="942c5-139">Porady: dodawanie instalatorów od aplikacji usług</span><span class="sxs-lookup"><span data-stu-id="942c5-139">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="942c5-140">Porady: rejestrowanie informacji o usługach</span><span class="sxs-lookup"><span data-stu-id="942c5-140">How to: Log Information About Services</span></span>](how-to-log-information-about-services.md)
- [<span data-ttu-id="942c5-141">Instrukcje: uruchamianie usług</span><span class="sxs-lookup"><span data-stu-id="942c5-141">How to: Start Services</span></span>](how-to-start-services.md)
- [<span data-ttu-id="942c5-142">Porady: określanie kontekstu zabezpieczeń dla usług</span><span class="sxs-lookup"><span data-stu-id="942c5-142">How to: Specify the Security Context for Services</span></span>](how-to-specify-the-security-context-for-services.md)
- [<span data-ttu-id="942c5-143">Instrukcje: instalowanie i odinstalowywanie usług</span><span class="sxs-lookup"><span data-stu-id="942c5-143">How to: Install and Uninstall Services</span></span>](how-to-install-and-uninstall-services.md)
- [<span data-ttu-id="942c5-144">Przewodnik: tworzenie aplikacji usługowej systemu Windows w Projektancie składników</span><span class="sxs-lookup"><span data-stu-id="942c5-144">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

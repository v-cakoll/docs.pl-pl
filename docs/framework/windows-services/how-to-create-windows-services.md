---
title: 'Instrukcje: Tworzenie usług systemu Windows'
description: Aby utworzyć usługę, użyj szablonu projektu usługi systemu Windows. Ustaw właściwość ServiceName, Utwórz Instalatory i Zastąp metody OnStart i OnStop.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
author: ghogen
ms.openlocfilehash: 6918225e39c15a52710fd0d56342aae869b42325
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925777"
---
# <a name="how-to-create-windows-services"></a><span data-ttu-id="308bc-104">Instrukcje: Tworzenie usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="308bc-104">How to: Create Windows Services</span></span>
<span data-ttu-id="308bc-105">Podczas tworzenia usługi można użyć szablonu projektu programu Visual Studio o nazwie **Usługa systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="308bc-105">When you create a service, you can use a Visual Studio project template called **Windows Service**.</span></span> <span data-ttu-id="308bc-106">Ten szablon automatycznie wykonuje większość pracy za Ciebie, odwołując się do odpowiednich klas i przestrzeni nazw, konfigurując dziedziczenie z klasy podstawowej dla usług i zastępując kilka metod, które mogą zostać przesłonięte.</span><span class="sxs-lookup"><span data-stu-id="308bc-106">This template automatically does much of the work for you by referencing the appropriate classes and namespaces, setting up the inheritance from the base class for services, and overriding several of the methods you're likely to want to override.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="308bc-107">Szablon projektu usług systemu Windows nie jest dostępny w wersji Express programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="308bc-107">The Windows Services project template is not available in the Express edition of Visual Studio.</span></span>  
  
 <span data-ttu-id="308bc-108">Aby utworzyć usługę funkcjonalną, należy co najmniej:</span><span class="sxs-lookup"><span data-stu-id="308bc-108">At a minimum, to create a functional service you must:</span></span>  
  
- <span data-ttu-id="308bc-109">Ustaw <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> Właściwość.</span><span class="sxs-lookup"><span data-stu-id="308bc-109">Set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property.</span></span>  
  
- <span data-ttu-id="308bc-110">Utwórz niezbędne Instalatory dla aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="308bc-110">Create the necessary installers for your service application.</span></span>  
  
- <span data-ttu-id="308bc-111">Przesłoń i określ kod dla <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metod i, <xref:System.ServiceProcess.ServiceBase.OnStop%2A> Aby dostosować sposób zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="308bc-111">Override and specify code for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods to customize the ways in which your service behaves.</span></span>  
  
### <a name="to-create-a-windows-service-application"></a><span data-ttu-id="308bc-112">Aby utworzyć aplikację usługi systemu Windows</span><span class="sxs-lookup"><span data-stu-id="308bc-112">To create a Windows Service application</span></span>  
  
1. <span data-ttu-id="308bc-113">Utwórz projekt **usługi systemu Windows** .</span><span class="sxs-lookup"><span data-stu-id="308bc-113">Create a **Windows Service** project.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="308bc-114">Aby uzyskać instrukcje dotyczące pisania usługi bez użycia szablonu, zobacz [jak: programowe pisanie usług](how-to-write-services-programmatically.md).</span><span class="sxs-lookup"><span data-stu-id="308bc-114">For instructions on writing a service without using the template, see [How to: Write Services Programmatically](how-to-write-services-programmatically.md).</span></span>  
  
2. <span data-ttu-id="308bc-115">W oknie **Właściwości** Ustaw <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> Właściwość usługi.</span><span class="sxs-lookup"><span data-stu-id="308bc-115">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for your service.</span></span>  
  
     <span data-ttu-id="308bc-116">![Ustaw właściwość ServiceName.](./media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span><span class="sxs-lookup"><span data-stu-id="308bc-116">![Set the ServiceName property.](./media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="308bc-117">Wartość <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwości musi zawsze odpowiadać nazwie zarejestrowanej w klasach Instalatora.</span><span class="sxs-lookup"><span data-stu-id="308bc-117">The value of the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property must always match the name recorded in the installer classes.</span></span> <span data-ttu-id="308bc-118">W przypadku zmiany tej właściwości należy <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> również zaktualizować Właściwość klas Instalatora.</span><span class="sxs-lookup"><span data-stu-id="308bc-118">If you change this property, you must update the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property of installer classes as well.</span></span>  
  
3. <span data-ttu-id="308bc-119">Ustaw dowolne z następujących właściwości, aby określić, jak będzie działać usługa.</span><span class="sxs-lookup"><span data-stu-id="308bc-119">Set any of the following properties to determine how your service will function.</span></span>  
  
    |<span data-ttu-id="308bc-120">Właściwość</span><span class="sxs-lookup"><span data-stu-id="308bc-120">Property</span></span>|<span data-ttu-id="308bc-121">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="308bc-121">Setting</span></span>|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|<span data-ttu-id="308bc-122">`True`, aby wskazać, że usługa będzie akceptować żądania zatrzymania działania; `false`, aby zapobiec zatrzymaniu usługi.</span><span class="sxs-lookup"><span data-stu-id="308bc-122">`True` to indicate that the service will accept requests to stop running; `false` to prevent the service from being stopped.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|<span data-ttu-id="308bc-123">`True`, aby wskazać, że usługa chce otrzymywać powiadomienie, gdy komputer, na którym się znajduje, jest zamykana, umożliwiając mu wywołanie <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> procedury.</span><span class="sxs-lookup"><span data-stu-id="308bc-123">`True` to indicate that the service wants to receive notification when the computer on which it lives shuts down, enabling it to call the <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> procedure.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|<span data-ttu-id="308bc-124">`True`, aby wskazać, że usługa będzie akceptować żądania wstrzymania lub wznowienia działania. `false`Aby zapobiec wstrzymaniu i wznowieniu usługi.</span><span class="sxs-lookup"><span data-stu-id="308bc-124">`True` to indicate that the service will accept requests to pause or to resume running; `false` to prevent the service from being paused and resumed.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|<span data-ttu-id="308bc-125">`True`Aby wskazać, że usługa może obsługiwać powiadomienia o zmianach stanu zasilacza komputera; `false`Aby zapobiec powiadamianiu usługi o tych zmianach.</span><span class="sxs-lookup"><span data-stu-id="308bc-125">`True` to indicate that the service can handle notification of changes to the computer's power status; `false` to prevent the service from being notified of these changes.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|<span data-ttu-id="308bc-126">`True`w celu zapisania wpisów informacyjnych w dzienniku zdarzeń aplikacji, gdy usługa wykonuje akcję; `false`Aby wyłączyć tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="308bc-126">`True` to write informational entries to the Application event log when your service performs an action; `false` to disable this functionality.</span></span> <span data-ttu-id="308bc-127">Aby uzyskać więcej informacji, zobacz [jak: rejestrować informacje o usługach](how-to-log-information-about-services.md).</span><span class="sxs-lookup"><span data-stu-id="308bc-127">For more information, see [How to: Log Information About Services](how-to-log-information-about-services.md).</span></span> <span data-ttu-id="308bc-128">**Uwaga:**  Domyślnie <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> jest ustawiony na `true` .</span><span class="sxs-lookup"><span data-stu-id="308bc-128">**Note:**  By default, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> is set to `true`.</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="308bc-129">Gdy <xref:System.ServiceProcess.ServiceBase.CanStop%2A> lub <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> jest ustawiona na `false` , **Menedżer sterowania usługami** wyłącza odpowiednie opcje menu, aby zatrzymać, wstrzymać lub kontynuować usługę.</span><span class="sxs-lookup"><span data-stu-id="308bc-129">When <xref:System.ServiceProcess.ServiceBase.CanStop%2A> or <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> are set to `false`, the **Service Control Manager** will disable the corresponding menu options to stop, pause, or continue the service.</span></span>  
  
4. <span data-ttu-id="308bc-130">Uzyskaj dostęp do edytora kodu i Wypełnij odpowiednie przetwarzanie dla <xref:System.ServiceProcess.ServiceBase.OnStart%2A> <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedur i.</span><span class="sxs-lookup"><span data-stu-id="308bc-130">Access the Code Editor and fill in the processing you want for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures.</span></span>  
  
5. <span data-ttu-id="308bc-131">Zastąp wszystkie inne metody, dla których chcesz zdefiniować funkcję.</span><span class="sxs-lookup"><span data-stu-id="308bc-131">Override any other methods for which you want to define functionality.</span></span>  
  
6. <span data-ttu-id="308bc-132">Dodanie niezbędnych instalatorów dla aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="308bc-132">Add the necessary installers for your service application.</span></span> <span data-ttu-id="308bc-133">Aby uzyskać więcej informacji, zobacz [jak: Dodawanie instalatorów do aplikacji usługi](how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="308bc-133">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>  
  
7. <span data-ttu-id="308bc-134">Skompiluj projekt, wybierając opcję **Kompiluj rozwiązanie** w menu **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="308bc-134">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="308bc-135">Nie należy naciskać klawisza F5, aby uruchomić projekt — nie można uruchomić projektu usługi w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="308bc-135">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
8. <span data-ttu-id="308bc-136">Zainstaluj usługę.</span><span class="sxs-lookup"><span data-stu-id="308bc-136">Install the service.</span></span> <span data-ttu-id="308bc-137">Aby uzyskać więcej informacji, zobacz [jak: Instalowanie i odinstalowywanie usług](how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="308bc-137">For more information, see [How to: Install and Uninstall Services](how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="308bc-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="308bc-138">See also</span></span>

- [<span data-ttu-id="308bc-139">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="308bc-139">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="308bc-140">Instrukcje: Programowane pisanie usług</span><span class="sxs-lookup"><span data-stu-id="308bc-140">How to: Write Services Programmatically</span></span>](how-to-write-services-programmatically.md)
- [<span data-ttu-id="308bc-141">Instrukcje: Dodawanie instalatorów od aplikacji usług</span><span class="sxs-lookup"><span data-stu-id="308bc-141">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="308bc-142">Instrukcje: Rejestrowanie informacji o usługach</span><span class="sxs-lookup"><span data-stu-id="308bc-142">How to: Log Information About Services</span></span>](how-to-log-information-about-services.md)
- [<span data-ttu-id="308bc-143">Instrukcje: Uruchamianie usług</span><span class="sxs-lookup"><span data-stu-id="308bc-143">How to: Start Services</span></span>](how-to-start-services.md)
- [<span data-ttu-id="308bc-144">Instrukcje: Określanie kontekstu zabezpieczeń dla usług</span><span class="sxs-lookup"><span data-stu-id="308bc-144">How to: Specify the Security Context for Services</span></span>](how-to-specify-the-security-context-for-services.md)
- [<span data-ttu-id="308bc-145">Instrukcje: Instalowanie i odinstalowywanie usług</span><span class="sxs-lookup"><span data-stu-id="308bc-145">How to: Install and Uninstall Services</span></span>](how-to-install-and-uninstall-services.md)
- [<span data-ttu-id="308bc-146">Przewodnik: tworzenie aplikacji usługowej systemu Windows w Projektancie składników</span><span class="sxs-lookup"><span data-stu-id="308bc-146">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

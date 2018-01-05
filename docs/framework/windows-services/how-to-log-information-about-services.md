---
title: "Porady: rejestrowanie informacji o usługach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutoLog property
- services, logging information
- Windows Service applications, logging information about
- event logs, service applications
- application event logs, service applications
- logs, service applications
ms.assetid: c0d8140f-c055-4d8e-a2e0-37358a550116
caps.latest.revision: "17"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 2dabc20c3cd3a97ed86dc45436eaad5e7a07c91a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-log-information-about-services"></a><span data-ttu-id="a4f1b-102">Porady: rejestrowanie informacji o usługach</span><span class="sxs-lookup"><span data-stu-id="a4f1b-102">How to: Log Information About Services</span></span>
<span data-ttu-id="a4f1b-103">Domyślnie wszystkie projekty usługi systemu Windows mają możliwość interakcji z dziennika zdarzeń aplikacji i zapisywać do niego informacje i wyjątki.</span><span class="sxs-lookup"><span data-stu-id="a4f1b-103">By default, all Windows Service projects have the ability to interact with the Application event log and write information and exceptions to it.</span></span> <span data-ttu-id="a4f1b-104">Możesz użyć <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> Właściwość wskazująca, czy ma tę funkcję w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a4f1b-104">You use the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to indicate whether you want this functionality in your application.</span></span> <span data-ttu-id="a4f1b-105">Domyślnie rejestrowanie jest włączone dla żadnej usługi utworzone przy użyciu szablonu projektu usług systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a4f1b-105">By default, logging is turned on for any service you create with the Windows Service project template.</span></span> <span data-ttu-id="a4f1b-106">Można użyć statycznej formę <xref:System.Diagnostics.EventLog> klasa umożliwiająca zapisanie informacji o usłudze dziennika bez tworzenia wystąpienia <xref:System.Diagnostics.EventLog> składnika lub ręcznie zarejestrować źródło.</span><span class="sxs-lookup"><span data-stu-id="a4f1b-106">You can use a static form of the <xref:System.Diagnostics.EventLog> class to write service information to a log without having to create an instance of an <xref:System.Diagnostics.EventLog> component or manually register a source.</span></span>  
  
 <span data-ttu-id="a4f1b-107">Instalator usługi automatycznie rejestruje każdej usługi w projekcie jako prawidłowe źródło zdarzenia z dziennika aplikacji na komputerze, którym jest zainstalowana usługa, gdy jest włączone rejestrowanie.</span><span class="sxs-lookup"><span data-stu-id="a4f1b-107">The installer for your service automatically registers each service in your project as a valid source of events with the Application log on the computer where the service is installed, when logging is turned on.</span></span> <span data-ttu-id="a4f1b-108">Rejestruje informacje za każdym razem, usługa jest uruchomiona, zatrzymana, wstrzymana, wznowione, zainstalowany lub odinstalowany.</span><span class="sxs-lookup"><span data-stu-id="a4f1b-108">The service logs information each time the service is started, stopped, paused, resumed, installed, or uninstalled.</span></span> <span data-ttu-id="a4f1b-109">Rejestruje wszystkie błędy występujące.</span><span class="sxs-lookup"><span data-stu-id="a4f1b-109">It also logs any failures that occur.</span></span> <span data-ttu-id="a4f1b-110">Nie ma potrzeby pisania kodu na zapisywanie wpisów w dzienniku, używając domyślnego zachowania; Usługa obsługuje to dla Ciebie automatycznie.</span><span class="sxs-lookup"><span data-stu-id="a4f1b-110">You do not need to write any code to write entries to the log when using the default behavior; the service handles this for you automatically.</span></span>  
  
 <span data-ttu-id="a4f1b-111">Jeśli chcesz zapisać do dziennika zdarzeń niż dziennik aplikacji, musisz ustawić <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> właściwości `false`, tworzyć własne niestandardowe dziennika zdarzeń w kodzie usługi i zarejestrować usługi jako prawidłowe źródło pozycji dla tego dziennika.</span><span class="sxs-lookup"><span data-stu-id="a4f1b-111">If you want to write to an event log other than the Application log, you must set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to `false`, create your own custom event log within your services code, and register your service as a valid source of entries for that log.</span></span> <span data-ttu-id="a4f1b-112">Następnie należy napisać kodu do rejestrowania wpisów w dzienniku zawsze, gdy interesujący Cię w akcji.</span><span class="sxs-lookup"><span data-stu-id="a4f1b-112">You must then write code to record entries to the log whenever an action you're interested in occurs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4f1b-113">Jeśli używasz niestandardowego dziennika zdarzeń i konfigurowania aplikacji usługi do zapisu, nie musi podejmować dostępu do dziennika zdarzeń przed skonfigurowaniem usługi <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwości w kodzie.</span><span class="sxs-lookup"><span data-stu-id="a4f1b-113">If you use a custom event log and configure your service application to write to it, you must not attempt to access the event log before setting the service's <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property in your code.</span></span> <span data-ttu-id="a4f1b-114">Dziennik zdarzeń musi wartość tej właściwości można zarejestrować usługi jako prawidłowe źródło zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a4f1b-114">The event log needs this property's value to register your service as a valid source of events.</span></span>  
  
### <a name="to-enable-default-event-logging-for-your-service"></a><span data-ttu-id="a4f1b-115">Aby włączyć rejestrowanie zdarzeń domyślne usługi</span><span class="sxs-lookup"><span data-stu-id="a4f1b-115">To enable default event logging for your service</span></span>  
  
-   <span data-ttu-id="a4f1b-116">Ustaw <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> właściwość składnikowi `true`.</span><span class="sxs-lookup"><span data-stu-id="a4f1b-116">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property for your component to `true`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a4f1b-117">Domyślnie wartość tej właściwości to `true`.</span><span class="sxs-lookup"><span data-stu-id="a4f1b-117">By default, this property is set to `true`.</span></span> <span data-ttu-id="a4f1b-118">Nie trzeba ustawić to jawnie, chyba że tworzysz złożonych przetwarzania, takich jak oceniania warunku, a następnie ustawić <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> właściwości na podstawie wyniku tego warunku.</span><span class="sxs-lookup"><span data-stu-id="a4f1b-118">You do not need to set this explicitly unless you are building more complex processing, such as evaluating a condition and then setting the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property based on the result of that condition.</span></span>  
  
### <a name="to-disable-event-logging-for-your-service"></a><span data-ttu-id="a4f1b-119">Aby wyłączyć rejestrowanie zdarzeń dla usługi</span><span class="sxs-lookup"><span data-stu-id="a4f1b-119">To disable event logging for your service</span></span>  
  
-   <span data-ttu-id="a4f1b-120">Ustaw <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> właściwość składnikowi `false`.</span><span class="sxs-lookup"><span data-stu-id="a4f1b-120">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property for your component to `false`.</span></span>  
  
     [!code-csharp[VbRadconService#17](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#17)]
     [!code-vb[VbRadconService#17](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#17)]  
  
### <a name="to-set-up-logging-to-a-custom-log"></a><span data-ttu-id="a4f1b-121">Aby skonfigurować rejestrowanie do dziennika niestandardowego</span><span class="sxs-lookup"><span data-stu-id="a4f1b-121">To set up logging to a custom log</span></span>  
  
1.  <span data-ttu-id="a4f1b-122">Ustaw <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> właściwości `false`.</span><span class="sxs-lookup"><span data-stu-id="a4f1b-122">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to `false`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a4f1b-123">Należy ustawić <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> na wartość false, aby można było używać dziennik niestandardowy.</span><span class="sxs-lookup"><span data-stu-id="a4f1b-123">You must set <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> to false in order to use a custom log.</span></span>  
  
2.  <span data-ttu-id="a4f1b-124">Konfigurowanie wystąpienia <xref:System.Diagnostics.EventLog> składnika aplikacji usługi systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a4f1b-124">Set up an instance of an <xref:System.Diagnostics.EventLog> component in your Windows Service application.</span></span>  
  
3.  <span data-ttu-id="a4f1b-125">Utworzyć dziennika niestandardowego przez wywołanie metody <xref:System.Diagnostics.EventLog.CreateEventSource%2A> — metoda i określania ciągu źródła i nazwa dziennika plik chcesz utworzyć.</span><span class="sxs-lookup"><span data-stu-id="a4f1b-125">Create a custom log by calling the <xref:System.Diagnostics.EventLog.CreateEventSource%2A> method and specifying the source string and the name of the log file you want to create.</span></span>  
  
4.  <span data-ttu-id="a4f1b-126">Ustaw <xref:System.Diagnostics.EventLog.Source%2A> właściwość <xref:System.Diagnostics.EventLog> wystąpienie składnika ciąg źródłowy został utworzony w kroku 3.</span><span class="sxs-lookup"><span data-stu-id="a4f1b-126">Set the <xref:System.Diagnostics.EventLog.Source%2A> property on the <xref:System.Diagnostics.EventLog> component instance to the source string you created in step 3.</span></span>  
  
5.  <span data-ttu-id="a4f1b-127">Zapis wpisy uzyskując dostęp do <xref:System.Diagnostics.EventLog.WriteEntry%2A> metoda <xref:System.Diagnostics.EventLog> wystąpienia składnika.</span><span class="sxs-lookup"><span data-stu-id="a4f1b-127">Write your entries by accessing the <xref:System.Diagnostics.EventLog.WriteEntry%2A> method on the <xref:System.Diagnostics.EventLog> component instance.</span></span>  
  
     <span data-ttu-id="a4f1b-128">Poniższy kod przedstawia sposób rejestrowania w dzienniku niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="a4f1b-128">The following code shows how to set up logging to a custom log.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a4f1b-129">W tym przykładzie kodu wystąpienia <xref:System.Diagnostics.EventLog> nosi nazwę składnika `eventLog1` (`EventLog1` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="a4f1b-129">In this code example, an instance of an <xref:System.Diagnostics.EventLog> component is named `eventLog1` (`EventLog1` in Visual Basic).</span></span> <span data-ttu-id="a4f1b-130">Jeśli wystąpienie zostało utworzone z inną nazwą w kroku 2, należy odpowiednio zmienić kod.</span><span class="sxs-lookup"><span data-stu-id="a4f1b-130">If you created an instance with another name in step 2, change the code accordingly.</span></span>  
  
     [!code-csharp[VbRadconService#14](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#14)]
     [!code-vb[VbRadconService#14](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#14)]  
    [!code-csharp[VbRadconService#15](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#15)]
    [!code-vb[VbRadconService#15](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="a4f1b-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a4f1b-131">See Also</span></span>  
 [<span data-ttu-id="a4f1b-132">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a4f1b-132">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)

---
title: 'Instrukcje: Dziennik informacji o usługach'
ms.date: 03/30/2017
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
author: ghogen
ms.openlocfilehash: ff3eb0dd27f097899fc19f57142034ffd2bb382a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660148"
---
# <a name="how-to-log-information-about-services"></a><span data-ttu-id="d64d3-102">Instrukcje: Dziennik informacji o usługach</span><span class="sxs-lookup"><span data-stu-id="d64d3-102">How to: Log Information About Services</span></span>
<span data-ttu-id="d64d3-103">Domyślnie wszystkie projekty usługi Windows mają możliwość interakcji z dziennika zdarzeń aplikacji i w nim zapisywać informacje i wyjątki.</span><span class="sxs-lookup"><span data-stu-id="d64d3-103">By default, all Windows Service projects have the ability to interact with the Application event log and write information and exceptions to it.</span></span> <span data-ttu-id="d64d3-104">Możesz użyć <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> właściwość wskazuje, czy ta funkcja w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d64d3-104">You use the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to indicate whether you want this functionality in your application.</span></span> <span data-ttu-id="d64d3-105">Domyślnie rejestrowanie jest włączone dla dowolnej usługi utworzonej przy użyciu szablonu projektu usługi Windows.</span><span class="sxs-lookup"><span data-stu-id="d64d3-105">By default, logging is turned on for any service you create with the Windows Service project template.</span></span> <span data-ttu-id="d64d3-106">Można użyć statycznej formy <xref:System.Diagnostics.EventLog> klasę umożliwiającą zapisanie informacji o usłudze do dziennika bez tworzenia wystąpienia <xref:System.Diagnostics.EventLog> składnika lub ręcznie zarejestrować źródła.</span><span class="sxs-lookup"><span data-stu-id="d64d3-106">You can use a static form of the <xref:System.Diagnostics.EventLog> class to write service information to a log without having to create an instance of an <xref:System.Diagnostics.EventLog> component or manually register a source.</span></span>  
  
 <span data-ttu-id="d64d3-107">Instalator usługi powoduje automatyczne zarejestrowanie każdej usługi w projekcie jako poprawne źródło zdarzenia w dzienniku aplikacji na komputerze, gdzie usługa jest zainstalowana, gdy jest włączone rejestrowanie.</span><span class="sxs-lookup"><span data-stu-id="d64d3-107">The installer for your service automatically registers each service in your project as a valid source of events with the Application log on the computer where the service is installed, when logging is turned on.</span></span> <span data-ttu-id="d64d3-108">Rejestruje informacje o każdym usługi jest uruchomiona, zatrzymana, wstrzymana, wznowione, zainstalowane lub odinstalowane.</span><span class="sxs-lookup"><span data-stu-id="d64d3-108">The service logs information each time the service is started, stopped, paused, resumed, installed, or uninstalled.</span></span> <span data-ttu-id="d64d3-109">Rejestruje wszystkie błędy, które występują.</span><span class="sxs-lookup"><span data-stu-id="d64d3-109">It also logs any failures that occur.</span></span> <span data-ttu-id="d64d3-110">Nie trzeba pisać kodu na zapisywanie wpisów do dziennika, korzystając z domyślnym zachowaniem; Usługa obsługuje to dla Ciebie automatycznie.</span><span class="sxs-lookup"><span data-stu-id="d64d3-110">You do not need to write any code to write entries to the log when using the default behavior; the service handles this for you automatically.</span></span>  
  
 <span data-ttu-id="d64d3-111">Jeśli chcesz zapisać do dziennika zdarzeń niż dziennik aplikacji, musisz ustawić <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> właściwości `false`, Utwórz własny niestandardowy dziennik zdarzeń w kodzie usługi i zarejestrować usługę jako poprawne źródło pozycji dla tego dziennika.</span><span class="sxs-lookup"><span data-stu-id="d64d3-111">If you want to write to an event log other than the Application log, you must set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to `false`, create your own custom event log within your services code, and register your service as a valid source of entries for that log.</span></span> <span data-ttu-id="d64d3-112">Następnie należy napisać kodu do rejestrowania wpisów do dziennika zawsze wtedy, gdy akcję, którą chcesz.</span><span class="sxs-lookup"><span data-stu-id="d64d3-112">You must then write code to record entries to the log whenever an action you're interested in occurs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d64d3-113">Jeśli używasz niestandardowy dziennik zdarzeń i konfigurowanie aplikacji usługi do zapisu do nich, nie należy spróbować uzyskać dostęp w dzienniku zdarzeń przed ustawieniem usługi <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwości w kodzie.</span><span class="sxs-lookup"><span data-stu-id="d64d3-113">If you use a custom event log and configure your service application to write to it, you must not attempt to access the event log before setting the service's <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property in your code.</span></span> <span data-ttu-id="d64d3-114">W dzienniku zdarzeń musi wartość tej właściwości można zarejestrować usługi jako poprawne źródło zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d64d3-114">The event log needs this property's value to register your service as a valid source of events.</span></span>  
  
### <a name="to-enable-default-event-logging-for-your-service"></a><span data-ttu-id="d64d3-115">Aby włączyć rejestrowanie zdarzeń domyślnego dla usługi</span><span class="sxs-lookup"><span data-stu-id="d64d3-115">To enable default event logging for your service</span></span>  
  
-   <span data-ttu-id="d64d3-116">Ustaw <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> właściwości składnika do `true`.</span><span class="sxs-lookup"><span data-stu-id="d64d3-116">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property for your component to `true`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d64d3-117">Domyślnie wartość tej właściwości to `true`.</span><span class="sxs-lookup"><span data-stu-id="d64d3-117">By default, this property is set to `true`.</span></span> <span data-ttu-id="d64d3-118">Nie musisz ustawić to jawnie, chyba że tworzysz bardziej złożonych przetwarzania, takich jak ocena warunku, a następnie ustawiając <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> właściwości na podstawie wyniku tego warunku.</span><span class="sxs-lookup"><span data-stu-id="d64d3-118">You do not need to set this explicitly unless you are building more complex processing, such as evaluating a condition and then setting the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property based on the result of that condition.</span></span>  
  
### <a name="to-disable-event-logging-for-your-service"></a><span data-ttu-id="d64d3-119">Aby wyłączyć rejestrowanie zdarzeń dla usługi</span><span class="sxs-lookup"><span data-stu-id="d64d3-119">To disable event logging for your service</span></span>  
  
-   <span data-ttu-id="d64d3-120">Ustaw <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> właściwości składnika do `false`.</span><span class="sxs-lookup"><span data-stu-id="d64d3-120">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property for your component to `false`.</span></span>  
  
     [!code-csharp[VbRadconService#17](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#17)]
     [!code-vb[VbRadconService#17](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#17)]  
  
### <a name="to-set-up-logging-to-a-custom-log"></a><span data-ttu-id="d64d3-121">Aby skonfigurować rejestrowanie do dziennika niestandardowego</span><span class="sxs-lookup"><span data-stu-id="d64d3-121">To set up logging to a custom log</span></span>  
  
1.  <span data-ttu-id="d64d3-122">Ustaw <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="d64d3-122">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to `false`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d64d3-123">Należy ustawić <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> na wartość false, aby można było używać dzienników niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="d64d3-123">You must set <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> to false in order to use a custom log.</span></span>  
  
2.  <span data-ttu-id="d64d3-124">Konfigurowanie wystąpienia <xref:System.Diagnostics.EventLog> składnika w aplikacji usługi Windows.</span><span class="sxs-lookup"><span data-stu-id="d64d3-124">Set up an instance of an <xref:System.Diagnostics.EventLog> component in your Windows Service application.</span></span>  
  
3.  <span data-ttu-id="d64d3-125">Utworzyć dziennika niestandardowego przez wywołanie metody <xref:System.Diagnostics.EventLog.CreateEventSource%2A> metody i określając ciąg źródłowy i nazwę dziennika pliku, dla którego ma zostać utworzony.</span><span class="sxs-lookup"><span data-stu-id="d64d3-125">Create a custom log by calling the <xref:System.Diagnostics.EventLog.CreateEventSource%2A> method and specifying the source string and the name of the log file you want to create.</span></span>  
  
4.  <span data-ttu-id="d64d3-126">Ustaw <xref:System.Diagnostics.EventLog.Source%2A> właściwość <xref:System.Diagnostics.EventLog> wystąpienie składnika ciąg źródłowy został utworzony w kroku 3.</span><span class="sxs-lookup"><span data-stu-id="d64d3-126">Set the <xref:System.Diagnostics.EventLog.Source%2A> property on the <xref:System.Diagnostics.EventLog> component instance to the source string you created in step 3.</span></span>  
  
5.  <span data-ttu-id="d64d3-127">Zapis wpisy, uzyskując dostęp do <xref:System.Diagnostics.EventLog.WriteEntry%2A> metody <xref:System.Diagnostics.EventLog> wystąpienia składnika.</span><span class="sxs-lookup"><span data-stu-id="d64d3-127">Write your entries by accessing the <xref:System.Diagnostics.EventLog.WriteEntry%2A> method on the <xref:System.Diagnostics.EventLog> component instance.</span></span>  
  
     <span data-ttu-id="d64d3-128">Poniższy kod przedstawia sposób konfigurowania rejestrowania dzienników niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="d64d3-128">The following code shows how to set up logging to a custom log.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d64d3-129">W tym przykładzie kodu wystąpienie <xref:System.Diagnostics.EventLog> nosi nazwę składnika `eventLog1` (`EventLog1` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="d64d3-129">In this code example, an instance of an <xref:System.Diagnostics.EventLog> component is named `eventLog1` (`EventLog1` in Visual Basic).</span></span> <span data-ttu-id="d64d3-130">Jeśli utworzono wystąpienie z inną nazwą w kroku 2, należy odpowiednio zmienić kod.</span><span class="sxs-lookup"><span data-stu-id="d64d3-130">If you created an instance with another name in step 2, change the code accordingly.</span></span>  
  
     [!code-csharp[VbRadconService#14](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#14)]
     [!code-vb[VbRadconService#14](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#14)]  
    [!code-csharp[VbRadconService#15](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#15)]
    [!code-vb[VbRadconService#15](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="d64d3-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d64d3-131">See also</span></span>
- [<span data-ttu-id="d64d3-132">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d64d3-132">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)

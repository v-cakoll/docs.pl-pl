---
title: 'Instrukcje: Rejestrowanie informacji o usługach'
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
ms.openlocfilehash: 3c974d5a98f8056e45899b109878e5a28ab2938e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053606"
---
# <a name="how-to-log-information-about-services"></a><span data-ttu-id="2c830-102">Instrukcje: Rejestrowanie informacji o usługach</span><span class="sxs-lookup"><span data-stu-id="2c830-102">How to: Log Information About Services</span></span>
<span data-ttu-id="2c830-103">Domyślnie wszystkie projekty usług systemu Windows mają możliwość korzystania z dziennika zdarzeń aplikacji i zapisywania do niego informacji oraz wyjątków.</span><span class="sxs-lookup"><span data-stu-id="2c830-103">By default, all Windows Service projects have the ability to interact with the Application event log and write information and exceptions to it.</span></span> <span data-ttu-id="2c830-104">Użyj właściwości, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> aby określić, czy chcesz, aby ta funkcja w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2c830-104">You use the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to indicate whether you want this functionality in your application.</span></span> <span data-ttu-id="2c830-105">Domyślnie rejestrowanie jest włączone dla każdej usługi utworzonej przy użyciu szablonu projektu usługi systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2c830-105">By default, logging is turned on for any service you create with the Windows Service project template.</span></span> <span data-ttu-id="2c830-106">Możesz użyć statycznej formy <xref:System.Diagnostics.EventLog> klasy do zapisywania informacji o usłudze w dzienniku bez konieczności tworzenia wystąpienia <xref:System.Diagnostics.EventLog> składnika lub ręcznego rejestrowania źródła.</span><span class="sxs-lookup"><span data-stu-id="2c830-106">You can use a static form of the <xref:System.Diagnostics.EventLog> class to write service information to a log without having to create an instance of an <xref:System.Diagnostics.EventLog> component or manually register a source.</span></span>  
  
 <span data-ttu-id="2c830-107">Instalator usługi automatycznie rejestruje każdą usługę w projekcie jako prawidłowe źródło zdarzeń w dzienniku aplikacji na komputerze, na którym zainstalowano usługę, gdy rejestrowanie jest włączone.</span><span class="sxs-lookup"><span data-stu-id="2c830-107">The installer for your service automatically registers each service in your project as a valid source of events with the Application log on the computer where the service is installed, when logging is turned on.</span></span> <span data-ttu-id="2c830-108">Usługa rejestruje informacje za każdym razem, gdy usługa jest uruchomiona, zatrzymana, wstrzymana, wznowiona, zainstalowana lub odinstalowana.</span><span class="sxs-lookup"><span data-stu-id="2c830-108">The service logs information each time the service is started, stopped, paused, resumed, installed, or uninstalled.</span></span> <span data-ttu-id="2c830-109">Rejestruje także wszystkie błędy, które wystąpiły.</span><span class="sxs-lookup"><span data-stu-id="2c830-109">It also logs any failures that occur.</span></span> <span data-ttu-id="2c830-110">Nie trzeba pisać żadnego kodu w celu zapisania wpisów w dzienniku, gdy jest używane zachowanie domyślne; usługa obsługuje to automatycznie.</span><span class="sxs-lookup"><span data-stu-id="2c830-110">You do not need to write any code to write entries to the log when using the default behavior; the service handles this for you automatically.</span></span>  
  
 <span data-ttu-id="2c830-111">Jeśli chcesz zapisać w dzienniku zdarzeń innym niż dziennik aplikacji, musisz ustawić <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> właściwość na `false`, utworzyć własny dziennik zdarzeń w kodzie usług i zarejestrować usługę jako prawidłowe Źródło wpisów dla tego dziennika.</span><span class="sxs-lookup"><span data-stu-id="2c830-111">If you want to write to an event log other than the Application log, you must set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to `false`, create your own custom event log within your services code, and register your service as a valid source of entries for that log.</span></span> <span data-ttu-id="2c830-112">Następnie należy napisać kod, aby zarejestrować wpisy w dzienniku za każdym razem, gdy akcja jest zainteresowana.</span><span class="sxs-lookup"><span data-stu-id="2c830-112">You must then write code to record entries to the log whenever an action you're interested in occurs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2c830-113">Jeśli używasz niestandardowego dziennika zdarzeń i skonfigurujesz aplikację usługi do zapisu w niej, nie musisz próbować uzyskać dostępu do dziennika zdarzeń przed ustawieniem <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwości usługi w kodzie.</span><span class="sxs-lookup"><span data-stu-id="2c830-113">If you use a custom event log and configure your service application to write to it, you must not attempt to access the event log before setting the service's <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property in your code.</span></span> <span data-ttu-id="2c830-114">Dziennik zdarzeń wymaga wartości tej właściwości, aby zarejestrować usługę jako prawidłowe źródło zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2c830-114">The event log needs this property's value to register your service as a valid source of events.</span></span>  
  
### <a name="to-enable-default-event-logging-for-your-service"></a><span data-ttu-id="2c830-115">Aby włączyć domyślne rejestrowanie zdarzeń dla usługi</span><span class="sxs-lookup"><span data-stu-id="2c830-115">To enable default event logging for your service</span></span>  
  
- <span data-ttu-id="2c830-116">Ustaw właściwość dla składnika na `true`. <xref:System.ServiceProcess.ServiceBase.AutoLog%2A></span><span class="sxs-lookup"><span data-stu-id="2c830-116">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property for your component to `true`.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2c830-117">Domyślnie wartość tej właściwości to `true`.</span><span class="sxs-lookup"><span data-stu-id="2c830-117">By default, this property is set to `true`.</span></span> <span data-ttu-id="2c830-118">Nie musisz jawnie ustawiać tego ustawienia, chyba że tworzysz bardziej skomplikowane przetwarzanie, takie jak szacowanie warunku, a następnie Ustawianie <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> właściwości na podstawie wyniku tego warunku.</span><span class="sxs-lookup"><span data-stu-id="2c830-118">You do not need to set this explicitly unless you are building more complex processing, such as evaluating a condition and then setting the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property based on the result of that condition.</span></span>  
  
### <a name="to-disable-event-logging-for-your-service"></a><span data-ttu-id="2c830-119">Aby wyłączyć rejestrowanie zdarzeń dla usługi</span><span class="sxs-lookup"><span data-stu-id="2c830-119">To disable event logging for your service</span></span>  
  
- <span data-ttu-id="2c830-120">Ustaw właściwość dla składnika na `false`. <xref:System.ServiceProcess.ServiceBase.AutoLog%2A></span><span class="sxs-lookup"><span data-stu-id="2c830-120">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property for your component to `false`.</span></span>  
  
     [!code-csharp[VbRadconService#17](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#17)]
     [!code-vb[VbRadconService#17](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#17)]  
  
### <a name="to-set-up-logging-to-a-custom-log"></a><span data-ttu-id="2c830-121">Aby skonfigurować rejestrowanie do dziennika niestandardowego</span><span class="sxs-lookup"><span data-stu-id="2c830-121">To set up logging to a custom log</span></span>  
  
1. <span data-ttu-id="2c830-122">Ustaw <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="2c830-122">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to `false`.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2c830-123">Aby można było <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> użyć dziennika niestandardowego, należy ustawić wartość false.</span><span class="sxs-lookup"><span data-stu-id="2c830-123">You must set <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> to false in order to use a custom log.</span></span>  
  
2. <span data-ttu-id="2c830-124">Skonfiguruj wystąpienie <xref:System.Diagnostics.EventLog> składnika w aplikacji usługi systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2c830-124">Set up an instance of an <xref:System.Diagnostics.EventLog> component in your Windows Service application.</span></span>  
  
3. <span data-ttu-id="2c830-125">Utwórz dziennik niestandardowy, wywołując <xref:System.Diagnostics.EventLog.CreateEventSource%2A> metodę i określając ciąg źródłowy i nazwę pliku dziennika, który chcesz utworzyć.</span><span class="sxs-lookup"><span data-stu-id="2c830-125">Create a custom log by calling the <xref:System.Diagnostics.EventLog.CreateEventSource%2A> method and specifying the source string and the name of the log file you want to create.</span></span>  
  
4. <span data-ttu-id="2c830-126"><xref:System.Diagnostics.EventLog.Source%2A> Ustaw właściwość <xref:System.Diagnostics.EventLog> w wystąpieniu składnika na ciąg źródłowy, który został utworzony w kroku 3.</span><span class="sxs-lookup"><span data-stu-id="2c830-126">Set the <xref:System.Diagnostics.EventLog.Source%2A> property on the <xref:System.Diagnostics.EventLog> component instance to the source string you created in step 3.</span></span>  
  
5. <span data-ttu-id="2c830-127">Zapisz swoje wpisy, uzyskując <xref:System.Diagnostics.EventLog.WriteEntry%2A> dostęp do metody <xref:System.Diagnostics.EventLog> w wystąpieniu składnika.</span><span class="sxs-lookup"><span data-stu-id="2c830-127">Write your entries by accessing the <xref:System.Diagnostics.EventLog.WriteEntry%2A> method on the <xref:System.Diagnostics.EventLog> component instance.</span></span>  
  
     <span data-ttu-id="2c830-128">Poniższy kod pokazuje, jak skonfigurować rejestrowanie w dzienniku niestandardowym.</span><span class="sxs-lookup"><span data-stu-id="2c830-128">The following code shows how to set up logging to a custom log.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2c830-129">W tym przykładzie kodu wystąpienie <xref:System.Diagnostics.EventLog> składnika nosi nazwę `eventLog1` (`EventLog1` w Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="2c830-129">In this code example, an instance of an <xref:System.Diagnostics.EventLog> component is named `eventLog1` (`EventLog1` in Visual Basic).</span></span> <span data-ttu-id="2c830-130">Jeśli utworzono wystąpienie z inną nazwą w kroku 2, Zmień kod odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="2c830-130">If you created an instance with another name in step 2, change the code accordingly.</span></span>  
  
     [!code-csharp[VbRadconService#14](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#14)]
     [!code-vb[VbRadconService#14](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#14)]  
    [!code-csharp[VbRadconService#15](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#15)]
    [!code-vb[VbRadconService#15](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="2c830-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2c830-131">See also</span></span>

- [<span data-ttu-id="2c830-132">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2c830-132">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)

---
title: "Opóźnienie bezwzględne"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b483139a-39bb-4560-8003-8969a8fc2cd1
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 60e3b65851dba68b4d01d6e4195b5faf99b583de
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="absolute-delay"></a><span data-ttu-id="1ce7f-102">Opóźnienie bezwzględne</span><span class="sxs-lookup"><span data-stu-id="1ce7f-102">Absolute Delay</span></span>
<span data-ttu-id="1ce7f-103">Główne scenariusz dla tego przykładu jest opóźnienia do określonej <xref:System.DateTime> przy użyciu czasomierze trwałe w aplikacji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="1ce7f-103">The main scenario for this sample is to delay until a specified <xref:System.DateTime> using durable timers in a workflow application.</span></span> <span data-ttu-id="1ce7f-104">To jest inny niż przy użyciu wbudowanych <xref:System.Activities.Statements.Delay> działania, jak to tylko umożliwi to opóźnienie dla danego <xref:System.TimeSpan> (lub liczba minut i sekund).</span><span class="sxs-lookup"><span data-stu-id="1ce7f-104">This is different from using the built-in <xref:System.Activities.Statements.Delay> activity as this will only allow you to delay for a given <xref:System.TimeSpan> (or number of minutes/seconds).</span></span>  
  
 <span data-ttu-id="1ce7f-105">Niektóre scenariusze rzeczywistych, w których warto utworzyć tę różnicę, są następujące:</span><span class="sxs-lookup"><span data-stu-id="1ce7f-105">Some real-life scenarios in which you may want to make this distinction include the following:</span></span>  
  
1.  <span data-ttu-id="1ce7f-106">Chcesz Opóźnij wysyłanie wiadomości przez 30 sekund, upewnij się, że wszystkie błędy nie zostały wprowadzone.</span><span class="sxs-lookup"><span data-stu-id="1ce7f-106">You want to delay sending a mail for 30 seconds to make sure you didn’t make any errors.</span></span>  
  
2.  <span data-ttu-id="1ce7f-107">Czy działa zbyt długo i opóźnić wszystkie Twoje wysyła pocztę do normalnego godzinami pracy (na przykład 8 am).</span><span class="sxs-lookup"><span data-stu-id="1ce7f-107">You are working overtime and want to delay all of your mails until normal business hours (such as 8 am).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="1ce7f-108">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="1ce7f-108">Demonstrates</span></span>  
  
1.  <span data-ttu-id="1ce7f-109"><xref:System.Activities.Statements.DurableTimerExtension>Bezwzględny opóźnienie wykonywania</span><span class="sxs-lookup"><span data-stu-id="1ce7f-109"><xref:System.Activities.Statements.DurableTimerExtension> for implementing Absolute Delay</span></span>  
  
2.  <span data-ttu-id="1ce7f-110">Konfigurowanie przy użyciu trwałości <xref:System.Activities.WorkflowApplication> dla trwałego czasomierze</span><span class="sxs-lookup"><span data-stu-id="1ce7f-110">Setting up persistence using <xref:System.Activities.WorkflowApplication> for Durable Timers</span></span>  
  
3.  <span data-ttu-id="1ce7f-111">Użycie <xref:System.Activities.NativeActivity%601> z punktów rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="1ce7f-111">Use of <xref:System.Activities.NativeActivity%601> for using Extensibility points</span></span>  
  
4.  <span data-ttu-id="1ce7f-112">Użycie <xref:System.Activities.CodeActivity%601> w działaniu SendEmail</span><span class="sxs-lookup"><span data-stu-id="1ce7f-112">Use of <xref:System.Activities.CodeActivity%601> in the SendEmail activity</span></span>  
  
5.  <xref:System.Activities.Statements.Delay>  
  
6.  <span data-ttu-id="1ce7f-113">Tylko do XAML przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="1ce7f-113">XAML-only workflow</span></span>  
  
 <span data-ttu-id="1ce7f-114">Ten przykład przedstawia sposób tworzenia działań niestandardowych, który przyjmuje <xref:System.DateTime> i używa czasomierze trwałe, aby zarejestrować czas trwania opóźnienia.</span><span class="sxs-lookup"><span data-stu-id="1ce7f-114">This sample demonstrates how to create a custom activity which takes in a <xref:System.DateTime> and uses durable timers to register the delay duration.</span></span> <span data-ttu-id="1ce7f-115">Korzystając z czasomierze trwałe, należy użyć <xref:System.Activities.NativeActivity> utworzyć zakładki, ponieważ będzie on potrzebny do zarejestrowania tego zakładki z rozszerzeniem czasomierza.</span><span class="sxs-lookup"><span data-stu-id="1ce7f-115">When using durable timers, you must use a <xref:System.Activities.NativeActivity> to create a bookmark, as you will need to register this bookmark with the timer extension.</span></span> <span data-ttu-id="1ce7f-116">W tym przykładzie, po wygaśnięciu czasomierza trwałe `OnTimerExpired` metoda zostanie wywołana.</span><span class="sxs-lookup"><span data-stu-id="1ce7f-116">In this sample, when the durable timer expires, the `OnTimerExpired` method will be called.</span></span> <span data-ttu-id="1ce7f-117">Upewnij się, że dodawania rozszerzenia czasomierza <xref:System.Activities.NativeActivity%601.CacheMetadata%2A> zdarzenia w celu zapewnienia udostępniasz środowiska uruchomieniowego z tymi informacjami.</span><span class="sxs-lookup"><span data-stu-id="1ce7f-117">Make sure that you are adding the timer extension in the <xref:System.Activities.NativeActivity%601.CacheMetadata%2A> event to ensure you are providing the runtime with this information.</span></span> <span data-ttu-id="1ce7f-118">Tylko innych implementacji szczegółów jest należy wdrożyć logikę do przekonwertowania z <xref:System.DateTime> do <xref:System.TimeSpan>, ponieważ czasomierze trwałe tylko <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="1ce7f-118">The only other implementation detail is that you will need to implement logic to convert from <xref:System.DateTime> to <xref:System.TimeSpan>, as durable timers only take in a <xref:System.DateTime>.</span></span> <span data-ttu-id="1ce7f-119">Należy pamiętać, że małych wygasną dokładności za pomocą ćwiczeń</span><span class="sxs-lookup"><span data-stu-id="1ce7f-119">Do note that there is a small lapse in accuracy by doing</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1ce7f-120">Brak małych utratę dokładności poprzez konwersję z <xref:System.DateTime> do <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="1ce7f-120">There is a small loss of accuracy by converting from <xref:System.DateTime> to <xref:System.TimeSpan>.</span></span>  
  
 <span data-ttu-id="1ce7f-121">W tym przykładzie również pokazano, jak włączyć trwałości dla <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="1ce7f-121">This sample also demonstrates how to turn on persistence for a <xref:System.Activities.WorkflowApplication>.</span></span> <span data-ttu-id="1ce7f-122">Dla tego konkretnego przykładu użyjemy czasomierze trwałe, w których dane przepływu pracy zostanie usunięty w bazie danych trwałości w czasie bezczynności podczas oczekiwania na czasomierz wygaśnie.</span><span class="sxs-lookup"><span data-stu-id="1ce7f-122">For this particular sample, we will be using durable timers in which the workflow data will be unloaded into the persistence database during the idle time while waiting for timer to expire.</span></span> <span data-ttu-id="1ce7f-123">Ta implementacja można również dla innych akcji trwałości.</span><span class="sxs-lookup"><span data-stu-id="1ce7f-123">This implementation can also be used for other persistence actions.</span></span> <span data-ttu-id="1ce7f-124">W tym przykładzie pokazano, jak skonfigurować trwałości parametry połączenia z programem SQL Server oraz sposobu tworzenia w magazynie wystąpień w celu utrwalenia danych dla wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="1ce7f-124">This sample shows how to set up the persistence connection string with SQL Server, and how to create the instance store in order to persist the data for workflow instances.</span></span> <span data-ttu-id="1ce7f-125">Logika znajduje się na temat sposobu wznowienie działania przepływu pracy, gdy zdarzenie jest zgłaszane, co sprawia, że wystąpienie przepływu pracy do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="1ce7f-125">Logic is provided on how to resume the workflow once an event is raised which makes the workflow instance runnable.</span></span>  
  
 <span data-ttu-id="1ce7f-126">Podczas wykonywania kroków za pomocą tego przykładu, pojawi się, że czas, w którym wbudowane opóźnienie rozpoczyna się i zakończeniu, który z kolei spowoduje wysłanie wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="1ce7f-126">As you step through this sample, you will see the time in which the built-in delay begins and completes, which in turn will cause an email message to be sent.</span></span> <span data-ttu-id="1ce7f-127">Z tego miejsca, działanie AbsoluteDelay spowoduje zatrzymanie do określonej <xref:System.DateTime> (lub 0 sekund, jeśli <xref:System.DateTime> wygasł) który z kolei spowoduje wysłanie wiadomości e-mail po wygaśnięciu.</span><span class="sxs-lookup"><span data-stu-id="1ce7f-127">From there, the AbsoluteDelay activity will halt until a specified <xref:System.DateTime> (or 0 seconds if the <xref:System.DateTime> has expired) which in turn will send out an email upon expiration.</span></span> <span data-ttu-id="1ce7f-128">Wyświetli dwóch różnych zastosowań wbudowanych <xref:System.Activities.Statements.Delay> funkcjonalność w porównaniu z użyciem działania AbsoluteDelay.</span><span class="sxs-lookup"><span data-stu-id="1ce7f-128">This will show the two different use cases of the built-in <xref:System.Activities.Statements.Delay> functionality versus using an AbsoluteDelay activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1ce7f-129">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="1ce7f-129">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="1ce7f-130">Upewnij się, że program SQL Server Express (lub nowszej) zainstalowane na tym komputerze</span><span class="sxs-lookup"><span data-stu-id="1ce7f-130">Ensure you have SQL Server Express (or higher) installed on your machine</span></span>  
  
2.  <span data-ttu-id="1ce7f-131">Uruchom setup.cmd (z WF/Basic/Services/AbsoluteDelay/CS) [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia, aby utworzyć bazę danych AbsoluteDelaySampleDB, tworzony jest schemat trwałości i tworzenia logiki trwałości.</span><span class="sxs-lookup"><span data-stu-id="1ce7f-131">Run setup.cmd (from WF/Basic/Services/AbsoluteDelay/CS) in a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt to create the AbsoluteDelaySampleDB database, create the persistence schema and create the persistence logic.</span></span>  
  
3.  <span data-ttu-id="1ce7f-132">Otwórz rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1ce7f-132">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
4.  <span data-ttu-id="1ce7f-133">Określ czas trwania w działaniu Delay.</span><span class="sxs-lookup"><span data-stu-id="1ce7f-133">Specify the Duration in the Delay activity.</span></span>  
  
5.  <span data-ttu-id="1ce7f-134">Określ ExpirationTime w działaniu AbsoluteDelay.</span><span class="sxs-lookup"><span data-stu-id="1ce7f-134">Specify the ExpirationTime in the AbsoluteDelay activity.</span></span>  
  
6.  <span data-ttu-id="1ce7f-135">Zaktualizuj pola SendMailTo, SendMailFrom SendMailSubject, SendMailBody i SmtpHost w działaniu SendMail.</span><span class="sxs-lookup"><span data-stu-id="1ce7f-135">Update the SendMailTo, SendMailFrom, SendMailSubject, SendMailBody, and SmtpHost fields in the SendMail activity.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1ce7f-136">Jeśli nie podasz prawidłowego hosta SMTP aplikacji spowoduje zgłoszenie wyjątku SMTP.</span><span class="sxs-lookup"><span data-stu-id="1ce7f-136">If you do not enter a valid SMTP host, the application will throw a SMTP exception.</span></span>  
  
7.  <span data-ttu-id="1ce7f-137">Skompiluj rozwiązanie, wybierając **kompilacji**, **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="1ce7f-137">Build the solution by selecting **Build**, **Build Solution**.</span></span>  
  
8.  <span data-ttu-id="1ce7f-138">Uruchom rozwiązanie, naciskając klawisz **F5**.</span><span class="sxs-lookup"><span data-stu-id="1ce7f-138">Run the solution by pressing **F5**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1ce7f-139">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="1ce7f-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1ce7f-140">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="1ce7f-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1ce7f-141">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="1ce7f-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1ce7f-142">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="1ce7f-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\AbsoluteDelay`

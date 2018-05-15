---
title: Jak zdalnie przeglądać status drukarek
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- surveying printer status remotely [WPF]
- printer status [WPF], surveying remotely
- remotely surveying printer status [WPF]
- status [WPF], printers [WPF], surveying remotely
ms.assetid: d6324759-8292-4c23-9584-9c708887dc94
ms.openlocfilehash: eca1720aea1620683ebc9ed08b47a0f5625da9d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-remotely-survey-the-status-of-printers"></a><span data-ttu-id="7e2e5-102">Jak zdalnie przeglądać status drukarek</span><span class="sxs-lookup"><span data-stu-id="7e2e5-102">How to: Remotely Survey the Status of Printers</span></span>
<span data-ttu-id="7e2e5-103">W danym momencie w średnich i dużych firmach może być wiele drukarek, które nie są pracy z powodu papier lub jest poza papier lub inne problemy sytuacji.</span><span class="sxs-lookup"><span data-stu-id="7e2e5-103">At any given time at medium and large companies there may be multiple printers that are not working due to a paper jam or being out of paper or some other problematic situation.</span></span> <span data-ttu-id="7e2e5-104">Bogaty zestaw właściwości drukarki w [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] programu Microsoft .NET Framework stanowić sposób wykonywania szybką ankietę stanów drukarek.</span><span class="sxs-lookup"><span data-stu-id="7e2e5-104">The rich set of printer properties exposed in the [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] of Microsoft .NET Framework provide a means for performing a rapid survey of the states of printers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e2e5-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="7e2e5-105">Example</span></span>  
 <span data-ttu-id="7e2e5-106">Oto główne kroki tworzenia tego rodzaju narzędzia.</span><span class="sxs-lookup"><span data-stu-id="7e2e5-106">The major steps for creating this kind of utility are as follows.</span></span>  
  
1.  <span data-ttu-id="7e2e5-107">Uzyskaj listę wszystkich serwerów wydruku.</span><span class="sxs-lookup"><span data-stu-id="7e2e5-107">Obtain a list of all print servers.</span></span>  
  
2.  <span data-ttu-id="7e2e5-108">Pętla za pośrednictwem serwerów do badania ich kolejek wydruku.</span><span class="sxs-lookup"><span data-stu-id="7e2e5-108">Loop through the servers to query their print queues.</span></span>  
  
3.  <span data-ttu-id="7e2e5-109">W każdym przebiegu pętli serwera pętli wszystkich kolejek na serwerze i odczytu dla każdej właściwości, która może sygnalizować, że kolejka obecnie nie działa.</span><span class="sxs-lookup"><span data-stu-id="7e2e5-109">Within each pass of the server loop, loop through all the server's queues and read each property that might indicate that the queue is not currently working.</span></span>  
  
 <span data-ttu-id="7e2e5-110">Poniższy kod jest serią fragmentów.</span><span class="sxs-lookup"><span data-stu-id="7e2e5-110">The code below is a series of snippets.</span></span> <span data-ttu-id="7e2e5-111">Dla uproszczenia założono, że istnieje listę serwerów wydruku rozdzielonych CRLF.</span><span class="sxs-lookup"><span data-stu-id="7e2e5-111">For simplicity, this example assumes that there is a CRLF-delimited list of print servers.</span></span> <span data-ttu-id="7e2e5-112">Zmienna `fileOfPrintServers` jest <xref:System.IO.StreamReader> obiekt dla tego pliku.</span><span class="sxs-lookup"><span data-stu-id="7e2e5-112">The variable `fileOfPrintServers` is a <xref:System.IO.StreamReader> object for this file.</span></span> <span data-ttu-id="7e2e5-113">Ponieważ nazwa każdego serwera w osobnym wierszu, wszelkie wywołanie <xref:System.IO.StreamReader.ReadLine%2A> pobiera nazwę serwera dalej i przenosi <xref:System.IO.StreamReader>przez kursor na początek następnego wiersza.</span><span class="sxs-lookup"><span data-stu-id="7e2e5-113">Since each server name is on its own line, any call of <xref:System.IO.StreamReader.ReadLine%2A> gets the name of the next server and moves the <xref:System.IO.StreamReader>'s cursor to the beginning of the next line.</span></span>  
  
 <span data-ttu-id="7e2e5-114">W zewnętrznej pętli kod tworzy <xref:System.Printing.PrintServer> obiektu najnowsze serwera wydruku i określa, że aplikacja ma mieć uprawnienia administracyjne na serwerze.</span><span class="sxs-lookup"><span data-stu-id="7e2e5-114">Within the outer loop, the code creates a <xref:System.Printing.PrintServer> object for the latest print server and specifies that the application is to have administrative rights to the server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7e2e5-115">Jeśli istnieje wiele serwerów, może poprawić wydajność przy użyciu <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> konstruktorów tylko zainicjować właściwości mają być potrzebne.</span><span class="sxs-lookup"><span data-stu-id="7e2e5-115">If there are a lot of servers, you can improve performance by using the <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> constructors that only initialize the properties you are going to need.</span></span>  
  
 <span data-ttu-id="7e2e5-116">W przykładzie następnie użyto <xref:System.Printing.PrintServer.GetPrintQueues%2A> do utworzenia kolekcji wszystkich serwera obiektu kolejki i rozpoczyna się nimi pętli.</span><span class="sxs-lookup"><span data-stu-id="7e2e5-116">The example then uses <xref:System.Printing.PrintServer.GetPrintQueues%2A> to create a collection of all of the server's queues and begins to loop through them.</span></span> <span data-ttu-id="7e2e5-117">Wewnętrzny pętla zawiera rozgałęziania strukturę odpowiadający sprawdzanie stanu drukarki na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="7e2e5-117">This inner loop contains a branching structure corresponding to the two ways of checking a printer's status:</span></span>  
  
-   <span data-ttu-id="7e2e5-118">Możesz przeczytać flagi z <xref:System.Printing.PrintQueue.QueueStatus%2A> właściwość, która jest typu <xref:System.Printing.PrintQueueStatus>.</span><span class="sxs-lookup"><span data-stu-id="7e2e5-118">You can read the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property which is of type <xref:System.Printing.PrintQueueStatus>.</span></span>  
  
-   <span data-ttu-id="7e2e5-119">Każda właściwość może odczytywać takich jak <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, i <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.</span><span class="sxs-lookup"><span data-stu-id="7e2e5-119">You can read each relevant property such as <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, and <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.</span></span>  
  
 <span data-ttu-id="7e2e5-120">W przykładzie pokazano obu metod, dzięki czemu użytkownik został wcześniej zostanie wyświetlony monit, aby metody i zwrócił "y", jeśli użytkownik chce używać flag z <xref:System.Printing.PrintQueue.QueueStatus%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="7e2e5-120">This example demonstrates both methods, so the user was previously prompted as to which method to use and responded with "y" if he or she wanted to use the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property.</span></span> <span data-ttu-id="7e2e5-121">Aby uzyskać więcej informacji o te dwie metody są wymienione poniżej.</span><span class="sxs-lookup"><span data-stu-id="7e2e5-121">See below for the details of the two methods.</span></span>  
  
 <span data-ttu-id="7e2e5-122">Na koniec wyniki są prezentowane użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="7e2e5-122">Finally, the results are presented to the user.</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 <span data-ttu-id="7e2e5-123">Aby sprawdzić stan drukarki przy użyciu flagi z <xref:System.Printing.PrintQueue.QueueStatus%2A> właściwości, sprawdź flag odpowiednie, aby zobaczyć, jeśli jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="7e2e5-123">To check printer status using the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property, you check each relevant flag to see if it is set.</span></span> <span data-ttu-id="7e2e5-124">Standardowy sposób, aby zobaczyć, czy jeden bit jest ustawiona zestaw flagi bitów jest wykonanie operacji logicznych i przy użyciu flagi jako jeden operand i flagi co inne.</span><span class="sxs-lookup"><span data-stu-id="7e2e5-124">The standard way to see if one bit is set in a set of bit flags is to perform a logical AND operation with the set of flags as one operand and the flag itself as the other.</span></span> <span data-ttu-id="7e2e5-125">Ponieważ flagą sama ma tylko jeden bit, ustawić wyniku logicznym, a jest to, że, co najwyżej tego samego bit jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="7e2e5-125">Since the flag itself has only one bit set, the result of the logical AND is that, at most, that same bit is set.</span></span> <span data-ttu-id="7e2e5-126">Aby dowiedzieć się czy nie jest on, po prostu porównać wyniku logicznym i z ustawioną flagą sama.</span><span class="sxs-lookup"><span data-stu-id="7e2e5-126">To find out whether it is or not, just compare the result of the logical AND with the flag itself.</span></span> <span data-ttu-id="7e2e5-127">Aby uzyskać więcej informacji, zobacz <xref:System.Printing.PrintQueueStatus>, [& — Operator (odwołanie w C#)](~/docs/csharp/language-reference/operators/and-operator.md), i <xref:System.FlagsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7e2e5-127">For more information, see <xref:System.Printing.PrintQueueStatus>, the [& Operator (C# Reference)](~/docs/csharp/language-reference/operators/and-operator.md), and <xref:System.FlagsAttribute>.</span></span>  
  
 <span data-ttu-id="7e2e5-128">Dla każdego atrybutu ustawiono bit, którego kod dodaje powiadomienie do raportu końcowego, który będzie widoczne dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7e2e5-128">For each attribute whose bit is set, the code adds a notice to the final report that will be presented to the user.</span></span> <span data-ttu-id="7e2e5-129">( **ReportAvailabilityAtThisTime** metodę, która jest wywoływana po zakończeniu kodu została szczegółowo opisana poniżej.)</span><span class="sxs-lookup"><span data-stu-id="7e2e5-129">(The **ReportAvailabilityAtThisTime** method that is called at the end of the code is discussed below.)</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 <span data-ttu-id="7e2e5-130">Aby sprawdzić stan drukarek za pomocą każdej właściwości, należy po prostu odczytu dla każdej właściwości i dodania uwagi do raportu końcowego, który zostanie wyświetlone dla użytkownika, jeśli właściwość jest `true`.</span><span class="sxs-lookup"><span data-stu-id="7e2e5-130">To check printer status using each property, you simply read each property and add a note to the final report that will be presented to the user if the property is `true`.</span></span> <span data-ttu-id="7e2e5-131">( **ReportAvailabilityAtThisTime** metodę, która jest wywoływana po zakończeniu kodu została szczegółowo opisana poniżej.)</span><span class="sxs-lookup"><span data-stu-id="7e2e5-131">(The **ReportAvailabilityAtThisTime** method that is called at the end of the code is discussed below.)</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 <span data-ttu-id="7e2e5-132">**ReportAvailabilityAtThisTime** metody został utworzony, w razie potrzeby można określić, czy kolejka jest dostępna w aktualną porę dnia.</span><span class="sxs-lookup"><span data-stu-id="7e2e5-132">The **ReportAvailabilityAtThisTime** method was created in case you need to determine if the queue is available at the current time of day.</span></span>  
  
 <span data-ttu-id="7e2e5-133">Metoda nie przynosi Jeśli <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> i <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> właściwości są równe; ponieważ w takim przypadku drukarka jest dostępna przez cały czas.</span><span class="sxs-lookup"><span data-stu-id="7e2e5-133">The method will do nothing if the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties are equal; because in that case the printer is available at all times.</span></span> <span data-ttu-id="7e2e5-134">Jeśli są różne, metoda pobiera bieżącą godzinę, które mają zostać przekształcone łączną liczbę minut po północy, ponieważ <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> i <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> właściwości są <xref:System.Int32>s nie reprezentujący minut po północy, <xref:System.DateTime> obiekty.</span><span class="sxs-lookup"><span data-stu-id="7e2e5-134">If they are different, the method gets the current time which then has to be converted into total minutes past midnight because the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties are <xref:System.Int32>s representing minutes-after-midnight, not <xref:System.DateTime> objects.</span></span> <span data-ttu-id="7e2e5-135">Na koniec metody sprawdza, czy bieżąca godzina jest między rozpoczęciem a "do" razy.</span><span class="sxs-lookup"><span data-stu-id="7e2e5-135">Finally, the method checks to see if the current time is between the start and "until" times.</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## <a name="see-also"></a><span data-ttu-id="7e2e5-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7e2e5-136">See Also</span></span>  
 <xref:System.Printing.PrintQueue.StartTimeOfDay%2A>  
 <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>  
 <xref:System.DateTime>  
 <xref:System.Printing.PrintQueueStatus>  
 <xref:System.FlagsAttribute>  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 [<span data-ttu-id="7e2e5-137">& — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="7e2e5-137">& Operator (C# Reference)</span></span>](~/docs/csharp/language-reference/operators/and-operator.md)  
 [<span data-ttu-id="7e2e5-138">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="7e2e5-138">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="7e2e5-139">Przegląd drukowania</span><span class="sxs-lookup"><span data-stu-id="7e2e5-139">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)

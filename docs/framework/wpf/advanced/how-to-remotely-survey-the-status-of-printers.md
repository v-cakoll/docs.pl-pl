---
title: 'Instrukcje: Zdalne badanie stanu drukarek'
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
ms.openlocfilehash: da2576696b514dca882636125cfb3e31a82d7f6e
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65878202"
---
# <a name="how-to-remotely-survey-the-status-of-printers"></a><span data-ttu-id="456e5-102">Instrukcje: Zdalne badanie stanu drukarek</span><span class="sxs-lookup"><span data-stu-id="456e5-102">How to: Remotely Survey the Status of Printers</span></span>
<span data-ttu-id="456e5-103">W dowolnym momencie w średnich i dużych firmach może istnieć wiele drukarek, które nie działa z powodu zakleszczenie papieru lub Brak papieru lub problematycznych sytuacji.</span><span class="sxs-lookup"><span data-stu-id="456e5-103">At any given time at medium and large companies there may be multiple printers that are not working due to a paper jam or being out of paper or some other problematic situation.</span></span> <span data-ttu-id="456e5-104">Bogaty zestaw właściwości drukarki ujawnione w [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] programu Microsoft .NET Framework zapewniają środki do przeprowadzania szybkiej udział w ankiecie stanów drukarki.</span><span class="sxs-lookup"><span data-stu-id="456e5-104">The rich set of printer properties exposed in the [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] of Microsoft .NET Framework provide a means for performing a rapid survey of the states of printers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="456e5-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="456e5-105">Example</span></span>  
 <span data-ttu-id="456e5-106">Oto główne kroki tworzenia tego rodzaju narzędzia.</span><span class="sxs-lookup"><span data-stu-id="456e5-106">The major steps for creating this kind of utility are as follows.</span></span>  
  
1. <span data-ttu-id="456e5-107">Uzyskaj listę wszystkich serwerów wydruku.</span><span class="sxs-lookup"><span data-stu-id="456e5-107">Obtain a list of all print servers.</span></span>  
  
2. <span data-ttu-id="456e5-108">Pętla za pośrednictwem serwerów do wykonywania zapytań ich kolejek wydruku.</span><span class="sxs-lookup"><span data-stu-id="456e5-108">Loop through the servers to query their print queues.</span></span>  
  
3. <span data-ttu-id="456e5-109">W ramach każdego przebiegu serwera pętli w pętli poprzez wszystkich kolejek na serwerze, a następnie zapoznaj się każdej właściwości, które mogą wskazywać, że kolejka nie jest obecnie działa.</span><span class="sxs-lookup"><span data-stu-id="456e5-109">Within each pass of the server loop, loop through all the server's queues and read each property that might indicate that the queue is not currently working.</span></span>  
  
 <span data-ttu-id="456e5-110">Poniższy kod jest szereg fragmentów kodu.</span><span class="sxs-lookup"><span data-stu-id="456e5-110">The code below is a series of snippets.</span></span> <span data-ttu-id="456e5-111">Dla uproszczenia w tym przykładzie przyjęto założenie, że znajduje się lista rozdzielonych CRLF serwerów wydruku.</span><span class="sxs-lookup"><span data-stu-id="456e5-111">For simplicity, this example assumes that there is a CRLF-delimited list of print servers.</span></span> <span data-ttu-id="456e5-112">Zmienna `fileOfPrintServers` jest <xref:System.IO.StreamReader> obiektu dla tego pliku.</span><span class="sxs-lookup"><span data-stu-id="456e5-112">The variable `fileOfPrintServers` is a <xref:System.IO.StreamReader> object for this file.</span></span> <span data-ttu-id="456e5-113">Ponieważ nazwa każdego serwera w osobnym wierszu, żadnym wywołaniu, z <xref:System.IO.StreamReader.ReadLine%2A> pobiera nazwę kolejny serwer i przenosi <xref:System.IO.StreamReader>przez kursor na początku następnego wiersza.</span><span class="sxs-lookup"><span data-stu-id="456e5-113">Since each server name is on its own line, any call of <xref:System.IO.StreamReader.ReadLine%2A> gets the name of the next server and moves the <xref:System.IO.StreamReader>'s cursor to the beginning of the next line.</span></span>  
  
 <span data-ttu-id="456e5-114">W zewnętrznej pętli, kod tworzy <xref:System.Printing.PrintServer> obiektu dla najnowszych serwera wydruku i określa, czy aplikacja ma mieć uprawnienia administracyjne do serwera.</span><span class="sxs-lookup"><span data-stu-id="456e5-114">Within the outer loop, the code creates a <xref:System.Printing.PrintServer> object for the latest print server and specifies that the application is to have administrative rights to the server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="456e5-115">Jeśli jest dostępnych wiele serwerów, może poprawić wydajność przy użyciu <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> konstruktorów, które tylko inicjowania właściwości będą potrzebne.</span><span class="sxs-lookup"><span data-stu-id="456e5-115">If there are a lot of servers, you can improve performance by using the <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> constructors that only initialize the properties you are going to need.</span></span>  
  
 <span data-ttu-id="456e5-116">Następnie w przykładzie <xref:System.Printing.PrintServer.GetPrintQueues%2A> Aby utworzyć kolekcję zawierającą wszystkie serwera zachowania umieszcza w kolejce i rozpoczyna się w pętli poprzez ich.</span><span class="sxs-lookup"><span data-stu-id="456e5-116">The example then uses <xref:System.Printing.PrintServer.GetPrintQueues%2A> to create a collection of all of the server's queues and begins to loop through them.</span></span> <span data-ttu-id="456e5-117">Ta pętla wewnętrzny zawiera rozgałęziona struktura odpowiadający dwa sposoby sprawdzania stanu drukarki:</span><span class="sxs-lookup"><span data-stu-id="456e5-117">This inner loop contains a branching structure corresponding to the two ways of checking a printer's status:</span></span>  
  
- <span data-ttu-id="456e5-118">Może odczytywać flagi o <xref:System.Printing.PrintQueue.QueueStatus%2A> właściwość, która jest typu <xref:System.Printing.PrintQueueStatus>.</span><span class="sxs-lookup"><span data-stu-id="456e5-118">You can read the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property which is of type <xref:System.Printing.PrintQueueStatus>.</span></span>  
  
- <span data-ttu-id="456e5-119">Można znaleźć każdej odpowiednie właściwości, takie jak <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, i <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.</span><span class="sxs-lookup"><span data-stu-id="456e5-119">You can read each relevant property such as <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, and <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.</span></span>  
  
 <span data-ttu-id="456e5-120">W tym przykładzie przedstawiono obie metody, dzięki czemu użytkownik został wcześniej zostanie wyświetlony monit, aby metody i odpowiedziała, zgłaszając "y", jeśli użytkownik chce używać flagi o <xref:System.Printing.PrintQueue.QueueStatus%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="456e5-120">This example demonstrates both methods, so the user was previously prompted as to which method to use and responded with "y" if he or she wanted to use the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property.</span></span> <span data-ttu-id="456e5-121">Poniżej znajdują się szczegółowe informacje o dwóch metod.</span><span class="sxs-lookup"><span data-stu-id="456e5-121">See below for the details of the two methods.</span></span>  
  
 <span data-ttu-id="456e5-122">Na koniec wyniki są prezentowane użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="456e5-122">Finally, the results are presented to the user.</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 <span data-ttu-id="456e5-123">Aby sprawdzić stan drukarki przy użyciu flagi programu <xref:System.Printing.PrintQueue.QueueStatus%2A> właściwości, możesz sprawdzić każdy odpowiednie flagi, aby zobaczyć, jeśli jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="456e5-123">To check printer status using the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property, you check each relevant flag to see if it is set.</span></span> <span data-ttu-id="456e5-124">Standardowy sposób, aby zobaczyć, jeśli jest ustawiony bit jeden zestaw flag bitowych jest do wykonywania operacji logicznych i przy użyciu zestawu flag jako jeden z operandów i Flaga jako drugiego.</span><span class="sxs-lookup"><span data-stu-id="456e5-124">The standard way to see if one bit is set in a set of bit flags is to perform a logical AND operation with the set of flags as one operand and the flag itself as the other.</span></span> <span data-ttu-id="456e5-125">Ponieważ flagi, sama ma tylko jeden bit, ustaw wartości logicznej i jest to, że, co najwyżej ten sam bit jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="456e5-125">Since the flag itself has only one bit set, the result of the logical AND is that, at most, that same bit is set.</span></span> <span data-ttu-id="456e5-126">Aby dowiedzieć się, czy jest lub nie, po prostu Porównaj wynik logicznej i przy użyciu flagi sam.</span><span class="sxs-lookup"><span data-stu-id="456e5-126">To find out whether it is or not, just compare the result of the logical AND with the flag itself.</span></span> <span data-ttu-id="456e5-127">Aby uzyskać więcej informacji, zobacz <xref:System.Printing.PrintQueueStatus>, [& — Operator (C# odwołania)](~/docs/csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-), i <xref:System.FlagsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="456e5-127">For more information, see <xref:System.Printing.PrintQueueStatus>, the [& Operator (C# Reference)](~/docs/csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-), and <xref:System.FlagsAttribute>.</span></span>  
  
 <span data-ttu-id="456e5-128">Dla każdego atrybutu, którego bit jest ustawiony kod dodaje powiadomienie do raportu końcowego, który zostanie wyświetlony użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="456e5-128">For each attribute whose bit is set, the code adds a notice to the final report that will be presented to the user.</span></span> <span data-ttu-id="456e5-129">( **ReportAvailabilityAtThisTime** metodę, która jest wywoływany pod koniec kodu, omówiono poniżej.)</span><span class="sxs-lookup"><span data-stu-id="456e5-129">(The **ReportAvailabilityAtThisTime** method that is called at the end of the code is discussed below.)</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 <span data-ttu-id="456e5-130">Aby sprawdzić stan drukarki za pomocą każdej właściwości, możesz po prostu odczytywać każdej właściwości i dodać notatkę do raport końcowy, który zostanie wyświetlony dla użytkownika, jeśli właściwość jest `true`.</span><span class="sxs-lookup"><span data-stu-id="456e5-130">To check printer status using each property, you simply read each property and add a note to the final report that will be presented to the user if the property is `true`.</span></span> <span data-ttu-id="456e5-131">( **ReportAvailabilityAtThisTime** metodę, która jest wywoływany pod koniec kodu, omówiono poniżej.)</span><span class="sxs-lookup"><span data-stu-id="456e5-131">(The **ReportAvailabilityAtThisTime** method that is called at the end of the code is discussed below.)</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 <span data-ttu-id="456e5-132">**ReportAvailabilityAtThisTime** metoda została utworzona, w przypadku, gdy zachodzi potrzeba określenia, czy kolejka jest dostępna w aktualną porę dnia.</span><span class="sxs-lookup"><span data-stu-id="456e5-132">The **ReportAvailabilityAtThisTime** method was created in case you need to determine if the queue is available at the current time of day.</span></span>  
  
 <span data-ttu-id="456e5-133">Metoda będzie nic nie rób Jeśli <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> i <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> właściwości są równe; ponieważ w takim przypadku drukarka jest dostępna przez cały czas.</span><span class="sxs-lookup"><span data-stu-id="456e5-133">The method will do nothing if the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties are equal; because in that case the printer is available at all times.</span></span> <span data-ttu-id="456e5-134">Jeśli są różne, metoda pobiera bieżącą godzinę, które mają zostać przekształcone, kiedy łączna liczba minut po północy, ponieważ <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> i <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> właściwości są <xref:System.Int32>s reprezentujących minut po północy, nie <xref:System.DateTime> obiekty.</span><span class="sxs-lookup"><span data-stu-id="456e5-134">If they are different, the method gets the current time which then has to be converted into total minutes past midnight because the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties are <xref:System.Int32>s representing minutes-after-midnight, not <xref:System.DateTime> objects.</span></span> <span data-ttu-id="456e5-135">Na koniec metody sprawdza, czy bieżący czas między rozpoczęciem a "do" razy.</span><span class="sxs-lookup"><span data-stu-id="456e5-135">Finally, the method checks to see if the current time is between the start and "until" times.</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## <a name="see-also"></a><span data-ttu-id="456e5-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="456e5-136">See also</span></span>

- <xref:System.Printing.PrintQueue.StartTimeOfDay%2A>
- <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>
- <xref:System.DateTime>
- <xref:System.Printing.PrintQueueStatus>
- <xref:System.FlagsAttribute>
- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- [<span data-ttu-id="456e5-137">& — Operator (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="456e5-137">& Operator (C# Reference)</span></span>](~/docs/csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)
- [<span data-ttu-id="456e5-138">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="456e5-138">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="456e5-139">Przegląd drukowania</span><span class="sxs-lookup"><span data-stu-id="456e5-139">Printing Overview</span></span>](printing-overview.md)

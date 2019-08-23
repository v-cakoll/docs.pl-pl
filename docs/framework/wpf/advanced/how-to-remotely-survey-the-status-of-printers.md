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
ms.openlocfilehash: 0a7756684d5a133fa9cb014f109d14e413223ea9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945223"
---
# <a name="how-to-remotely-survey-the-status-of-printers"></a><span data-ttu-id="a0519-102">Instrukcje: Zdalne badanie stanu drukarek</span><span class="sxs-lookup"><span data-stu-id="a0519-102">How to: Remotely Survey the Status of Printers</span></span>
<span data-ttu-id="a0519-103">W dowolnym momencie w średnich i dużych firmach może istnieć wiele drukarek, które nie działają ze względu na zakleszczenie papieru lub brak papieru lub inne problemy.</span><span class="sxs-lookup"><span data-stu-id="a0519-103">At any given time at medium and large companies there may be multiple printers that are not working due to a paper jam or being out of paper or some other problematic situation.</span></span> <span data-ttu-id="a0519-104">Bogaty zestaw właściwości drukarki uwidocznionych w interfejsach API platformy Microsoft .NET Framework zapewnia metodę szybkiego przeglądu stanu drukarek.</span><span class="sxs-lookup"><span data-stu-id="a0519-104">The rich set of printer properties exposed in the APIs of Microsoft .NET Framework provide a means for performing a rapid survey of the states of printers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0519-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0519-105">Example</span></span>  
 <span data-ttu-id="a0519-106">Główne kroki tworzenia tego rodzaju narzędzi są następujące.</span><span class="sxs-lookup"><span data-stu-id="a0519-106">The major steps for creating this kind of utility are as follows.</span></span>  
  
1. <span data-ttu-id="a0519-107">Uzyskaj listę wszystkich serwerów wydruku.</span><span class="sxs-lookup"><span data-stu-id="a0519-107">Obtain a list of all print servers.</span></span>  
  
2. <span data-ttu-id="a0519-108">Przepętlenie między serwerami w celu wykonywania zapytań w ich kolejkach wydruku.</span><span class="sxs-lookup"><span data-stu-id="a0519-108">Loop through the servers to query their print queues.</span></span>  
  
3. <span data-ttu-id="a0519-109">W ramach każdego przebiegu pętli serwera pętla przez wszystkie kolejki serwera i odczytuje każdą właściwość, która może wskazywać, że kolejka nie działa.</span><span class="sxs-lookup"><span data-stu-id="a0519-109">Within each pass of the server loop, loop through all the server's queues and read each property that might indicate that the queue is not currently working.</span></span>  
  
 <span data-ttu-id="a0519-110">Poniższy kod to seria fragmentów kodu.</span><span class="sxs-lookup"><span data-stu-id="a0519-110">The code below is a series of snippets.</span></span> <span data-ttu-id="a0519-111">Dla uproszczenia w tym przykładzie przyjęto założenie, że lista serwerów wydruku ma rozdzielaną liczbę CRLF.</span><span class="sxs-lookup"><span data-stu-id="a0519-111">For simplicity, this example assumes that there is a CRLF-delimited list of print servers.</span></span> <span data-ttu-id="a0519-112">`fileOfPrintServers` Zmienna<xref:System.IO.StreamReader> jest obiektem dla tego pliku.</span><span class="sxs-lookup"><span data-stu-id="a0519-112">The variable `fileOfPrintServers` is a <xref:System.IO.StreamReader> object for this file.</span></span> <span data-ttu-id="a0519-113">Ponieważ każda nazwa serwera znajduje się w osobnym wierszu, każde wywołanie metody <xref:System.IO.StreamReader.ReadLine%2A> Pobiera nazwę następnego serwera i <xref:System.IO.StreamReader>przenosi kursor do początku następnego wiersza.</span><span class="sxs-lookup"><span data-stu-id="a0519-113">Since each server name is on its own line, any call of <xref:System.IO.StreamReader.ReadLine%2A> gets the name of the next server and moves the <xref:System.IO.StreamReader>'s cursor to the beginning of the next line.</span></span>  
  
 <span data-ttu-id="a0519-114">W ramach pętli zewnętrznej kod tworzy <xref:System.Printing.PrintServer> obiekt dla najnowszego serwera wydruku i określa, że aplikacja ma prawa administracyjne do serwera programu.</span><span class="sxs-lookup"><span data-stu-id="a0519-114">Within the outer loop, the code creates a <xref:System.Printing.PrintServer> object for the latest print server and specifies that the application is to have administrative rights to the server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a0519-115">Jeśli istnieje wiele serwerów, można zwiększyć wydajność przy użyciu <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> konstruktorów, które inicjują tylko te właściwości, które mają być potrzebne.</span><span class="sxs-lookup"><span data-stu-id="a0519-115">If there are a lot of servers, you can improve performance by using the <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> constructors that only initialize the properties you are going to need.</span></span>  
  
 <span data-ttu-id="a0519-116">Ten przykład używa <xref:System.Printing.PrintServer.GetPrintQueues%2A> do tworzenia kolekcji wszystkich kolejek serwera i rozpoczyna się w pętli.</span><span class="sxs-lookup"><span data-stu-id="a0519-116">The example then uses <xref:System.Printing.PrintServer.GetPrintQueues%2A> to create a collection of all of the server's queues and begins to loop through them.</span></span> <span data-ttu-id="a0519-117">Ta pętla wewnętrzna zawiera strukturę rozgałęzień odpowiadającą dwóm sposobom sprawdzania stanu drukarki:</span><span class="sxs-lookup"><span data-stu-id="a0519-117">This inner loop contains a branching structure corresponding to the two ways of checking a printer's status:</span></span>  
  
- <span data-ttu-id="a0519-118">Można odczytać flagi <xref:System.Printing.PrintQueue.QueueStatus%2A> właściwości, które są typu <xref:System.Printing.PrintQueueStatus>.</span><span class="sxs-lookup"><span data-stu-id="a0519-118">You can read the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property which is of type <xref:System.Printing.PrintQueueStatus>.</span></span>  
  
- <span data-ttu-id="a0519-119">Każdą odpowiednią właściwość, taką jak <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, i. <xref:System.Printing.PrintQueue.IsPaperJammed%2A></span><span class="sxs-lookup"><span data-stu-id="a0519-119">You can read each relevant property such as <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, and <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.</span></span>  
  
 <span data-ttu-id="a0519-120">W tym przykładzie pokazano obie metody, dlatego użytkownik był wcześniej monitowany o metodę użycia i odpowiedział na "y", jeśli chce użyć flag <xref:System.Printing.PrintQueue.QueueStatus%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="a0519-120">This example demonstrates both methods, so the user was previously prompted as to which method to use and responded with "y" if he or she wanted to use the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property.</span></span> <span data-ttu-id="a0519-121">Szczegóły dwóch metod znajdują się poniżej.</span><span class="sxs-lookup"><span data-stu-id="a0519-121">See below for the details of the two methods.</span></span>  
  
 <span data-ttu-id="a0519-122">Na koniec wyniki są prezentowane użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="a0519-122">Finally, the results are presented to the user.</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 <span data-ttu-id="a0519-123">Aby sprawdzić stan drukarki przy użyciu flag <xref:System.Printing.PrintQueue.QueueStatus%2A> właściwości, należy zaznaczyć każdą odpowiednią flagę, aby sprawdzić, czy została ustawiona.</span><span class="sxs-lookup"><span data-stu-id="a0519-123">To check printer status using the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property, you check each relevant flag to see if it is set.</span></span> <span data-ttu-id="a0519-124">Standardowym sposobem, aby zobaczyć, czy jeden bit jest ustawiony w zestawie flag bitowych, jest wykonywanie operacji logicznej i z zestawem flag jako jednego operandu i flagą.</span><span class="sxs-lookup"><span data-stu-id="a0519-124">The standard way to see if one bit is set in a set of bit flags is to perform a logical AND operation with the set of flags as one operand and the flag itself as the other.</span></span> <span data-ttu-id="a0519-125">Ponieważ sama flaga ma tylko jeden bit zestawu, wynik logiczny i to, co najwyżej, ten sam bit jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="a0519-125">Since the flag itself has only one bit set, the result of the logical AND is that, at most, that same bit is set.</span></span> <span data-ttu-id="a0519-126">Aby dowiedzieć się, czy jest lub nie, po prostu Porównaj wynik logiczny i z flagą.</span><span class="sxs-lookup"><span data-stu-id="a0519-126">To find out whether it is or not, just compare the result of the logical AND with the flag itself.</span></span> <span data-ttu-id="a0519-127">Aby uzyskać więcej informacji, <xref:System.Printing.PrintQueueStatus>Zobacz, [operator & (C# Reference)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)i. <xref:System.FlagsAttribute></span><span class="sxs-lookup"><span data-stu-id="a0519-127">For more information, see <xref:System.Printing.PrintQueueStatus>, the [& Operator (C# Reference)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-), and <xref:System.FlagsAttribute>.</span></span>  
  
 <span data-ttu-id="a0519-128">Dla każdego atrybutu, którego bit jest ustawiony, kod dodaje powiadomienie do raportu końcowego, który zostanie przedstawiony użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="a0519-128">For each attribute whose bit is set, the code adds a notice to the final report that will be presented to the user.</span></span> <span data-ttu-id="a0519-129">(Metoda **ReportAvailabilityAtThisTime** wywołana na końcu kodu została omówiona poniżej).</span><span class="sxs-lookup"><span data-stu-id="a0519-129">(The **ReportAvailabilityAtThisTime** method that is called at the end of the code is discussed below.)</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 <span data-ttu-id="a0519-130">Aby sprawdzić stan drukarki przy użyciu każdej właściwości, wystarczy odczytać każdą właściwość i dodać uwagę do raportu końcowego, który zostanie wyświetlony użytkownikowi, jeśli właściwość jest `true`.</span><span class="sxs-lookup"><span data-stu-id="a0519-130">To check printer status using each property, you simply read each property and add a note to the final report that will be presented to the user if the property is `true`.</span></span> <span data-ttu-id="a0519-131">(Metoda **ReportAvailabilityAtThisTime** wywołana na końcu kodu została omówiona poniżej).</span><span class="sxs-lookup"><span data-stu-id="a0519-131">(The **ReportAvailabilityAtThisTime** method that is called at the end of the code is discussed below.)</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 <span data-ttu-id="a0519-132">Metoda **ReportAvailabilityAtThisTime** została utworzona na wypadek, gdyby trzeba było określić, czy kolejka jest dostępna w bieżącym dniu.</span><span class="sxs-lookup"><span data-stu-id="a0519-132">The **ReportAvailabilityAtThisTime** method was created in case you need to determine if the queue is available at the current time of day.</span></span>  
  
 <span data-ttu-id="a0519-133">Metoda nie będzie niczego robić, jeśli <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> właściwości <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> i są równe. w takim przypadku drukarka jest dostępna przez cały czas.</span><span class="sxs-lookup"><span data-stu-id="a0519-133">The method will do nothing if the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties are equal; because in that case the printer is available at all times.</span></span> <span data-ttu-id="a0519-134">Jeśli różnią się one, Metoda pobiera bieżący czas, który następnie musi zostać przekonwertowany na łączną liczbę minut po północy <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> , <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> ponieważ właściwości <xref:System.Int32>i są s reprezentują minuty-po-północy <xref:System.DateTime> , nie elementy.</span><span class="sxs-lookup"><span data-stu-id="a0519-134">If they are different, the method gets the current time which then has to be converted into total minutes past midnight because the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties are <xref:System.Int32>s representing minutes-after-midnight, not <xref:System.DateTime> objects.</span></span> <span data-ttu-id="a0519-135">Na koniec Metoda sprawdza, czy bieżący czas jest między rozpoczęciem i "do" czasu.</span><span class="sxs-lookup"><span data-stu-id="a0519-135">Finally, the method checks to see if the current time is between the start and "until" times.</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## <a name="see-also"></a><span data-ttu-id="a0519-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0519-136">See also</span></span>

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
- [<span data-ttu-id="a0519-137">Operator & (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="a0519-137">& Operator (C# Reference)</span></span>](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)
- [<span data-ttu-id="a0519-138">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="a0519-138">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="a0519-139">Przegląd drukowania</span><span class="sxs-lookup"><span data-stu-id="a0519-139">Printing Overview</span></span>](printing-overview.md)

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
ms.openlocfilehash: 859ccb703c6c54c66d6ea7b433c67d156627e25b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187041"
---
# <a name="how-to-remotely-survey-the-status-of-printers"></a><span data-ttu-id="358d6-102">Jak zdalnie przeglądać status drukarek</span><span class="sxs-lookup"><span data-stu-id="358d6-102">How to: Remotely Survey the Status of Printers</span></span>
<span data-ttu-id="358d6-103">W dowolnym momencie w średnich i dużych firmach może istnieć wiele drukarek, które nie działają z powodu zacięcia papieru lub braku papieru lub innej problematycznej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="358d6-103">At any given time at medium and large companies there may be multiple printers that are not working due to a paper jam or being out of paper or some other problematic situation.</span></span> <span data-ttu-id="358d6-104">Bogaty zestaw właściwości drukarki udostępniane w interfejsach API programu Microsoft .NET Framework zapewniają sposób wykonywania szybkiego badania stanu drukarek.</span><span class="sxs-lookup"><span data-stu-id="358d6-104">The rich set of printer properties exposed in the APIs of Microsoft .NET Framework provide a means for performing a rapid survey of the states of printers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="358d6-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="358d6-105">Example</span></span>  
 <span data-ttu-id="358d6-106">Główne kroki tworzenia tego rodzaju narzędzia są następujące.</span><span class="sxs-lookup"><span data-stu-id="358d6-106">The major steps for creating this kind of utility are as follows.</span></span>  
  
1. <span data-ttu-id="358d6-107">Uzyskaj listę wszystkich serwerów wydruku.</span><span class="sxs-lookup"><span data-stu-id="358d6-107">Obtain a list of all print servers.</span></span>  
  
2. <span data-ttu-id="358d6-108">Pętla przez serwery do kwerendy ich kolejek wydruku.</span><span class="sxs-lookup"><span data-stu-id="358d6-108">Loop through the servers to query their print queues.</span></span>  
  
3. <span data-ttu-id="358d6-109">W ramach każdego przebiegu pętli serwera, pętli przez wszystkie kolejki serwera i odczytać każdą właściwość, która może wskazywać, że kolejka nie działa obecnie.</span><span class="sxs-lookup"><span data-stu-id="358d6-109">Within each pass of the server loop, loop through all the server's queues and read each property that might indicate that the queue is not currently working.</span></span>  
  
 <span data-ttu-id="358d6-110">Poniższy kod to seria urywków.</span><span class="sxs-lookup"><span data-stu-id="358d6-110">The code below is a series of snippets.</span></span> <span data-ttu-id="358d6-111">Dla uproszczenia w tym przykładzie przyjęto założenie, że istnieje lista serwerów wydruku rozdzielanych crlf.</span><span class="sxs-lookup"><span data-stu-id="358d6-111">For simplicity, this example assumes that there is a CRLF-delimited list of print servers.</span></span> <span data-ttu-id="358d6-112">Zmienna `fileOfPrintServers` jest <xref:System.IO.StreamReader> obiektem dla tego pliku.</span><span class="sxs-lookup"><span data-stu-id="358d6-112">The variable `fileOfPrintServers` is a <xref:System.IO.StreamReader> object for this file.</span></span> <span data-ttu-id="358d6-113">Ponieważ każda nazwa serwera jest w swoim <xref:System.IO.StreamReader.ReadLine%2A> własnym wierszu, każde wywołanie pobiera nazwę następnego serwera i przenosi kursor <xref:System.IO.StreamReader>'s na początek następnego wiersza.</span><span class="sxs-lookup"><span data-stu-id="358d6-113">Since each server name is on its own line, any call of <xref:System.IO.StreamReader.ReadLine%2A> gets the name of the next server and moves the <xref:System.IO.StreamReader>'s cursor to the beginning of the next line.</span></span>  
  
 <span data-ttu-id="358d6-114">W pętli zewnętrznej kod tworzy <xref:System.Printing.PrintServer> obiekt dla najnowszego serwera wydruku i określa, że aplikacja ma mieć prawa administracyjne do serwera.</span><span class="sxs-lookup"><span data-stu-id="358d6-114">Within the outer loop, the code creates a <xref:System.Printing.PrintServer> object for the latest print server and specifies that the application is to have administrative rights to the server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="358d6-115">Jeśli istnieje wiele serwerów, można zwiększyć wydajność <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> przy użyciu konstruktorów, które tylko inicjować właściwości, które będą potrzebne.</span><span class="sxs-lookup"><span data-stu-id="358d6-115">If there are a lot of servers, you can improve performance by using the <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> constructors that only initialize the properties you are going to need.</span></span>  
  
 <span data-ttu-id="358d6-116">Następnie w przykładzie użyto <xref:System.Printing.PrintServer.GetPrintQueues%2A> do utworzenia kolekcji wszystkich kolejek serwera i zaczyna się przez nie zapętlać.</span><span class="sxs-lookup"><span data-stu-id="358d6-116">The example then uses <xref:System.Printing.PrintServer.GetPrintQueues%2A> to create a collection of all of the server's queues and begins to loop through them.</span></span> <span data-ttu-id="358d6-117">Ta wewnętrzna pętla zawiera strukturę rozgałęziania odpowiadającą dwóm sposobom sprawdzania stanu drukarki:</span><span class="sxs-lookup"><span data-stu-id="358d6-117">This inner loop contains a branching structure corresponding to the two ways of checking a printer's status:</span></span>  
  
- <span data-ttu-id="358d6-118">Można odczytać flagi właściwości, <xref:System.Printing.PrintQueue.QueueStatus%2A> która jest <xref:System.Printing.PrintQueueStatus>typu .</span><span class="sxs-lookup"><span data-stu-id="358d6-118">You can read the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property which is of type <xref:System.Printing.PrintQueueStatus>.</span></span>  
  
- <span data-ttu-id="358d6-119">Można przeczytać każdą odpowiednią <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>właściwość, taką jak , i <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.</span><span class="sxs-lookup"><span data-stu-id="358d6-119">You can read each relevant property such as <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, and <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.</span></span>  
  
 <span data-ttu-id="358d6-120">W tym przykładzie pokazano obie metody, więc użytkownik został wcześniej poproszony o to, która metoda użyć i odpowiedział <xref:System.Printing.PrintQueue.QueueStatus%2A> z "y", jeśli chcą użyć flagi właściwości.</span><span class="sxs-lookup"><span data-stu-id="358d6-120">This example demonstrates both methods, so the user was previously prompted as to which method to use and responded with "y" if they wanted to use the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property.</span></span> <span data-ttu-id="358d6-121">Poniżej znajdują się szczegółowe informacje na temat tych dwóch metod.</span><span class="sxs-lookup"><span data-stu-id="358d6-121">See below for the details of the two methods.</span></span>  
  
 <span data-ttu-id="358d6-122">Na koniec wyniki są prezentowane użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="358d6-122">Finally, the results are presented to the user.</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 <span data-ttu-id="358d6-123">Aby sprawdzić stan drukarki przy <xref:System.Printing.PrintQueue.QueueStatus%2A> użyciu flag właściwości, należy sprawdzić każdą odpowiednią flagę, aby sprawdzić, czy jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="358d6-123">To check printer status using the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property, you check each relevant flag to see if it is set.</span></span> <span data-ttu-id="358d6-124">Standardowy sposób, aby sprawdzić, czy jeden bit jest ustawiony w zestawie flag bitowych jest wykonanie logicznej operacji AND z zestawem flag jako jeden operand i samą flagę jako drugą.</span><span class="sxs-lookup"><span data-stu-id="358d6-124">The standard way to see if one bit is set in a set of bit flags is to perform a logical AND operation with the set of flags as one operand and the flag itself as the other.</span></span> <span data-ttu-id="358d6-125">Ponieważ sama flaga ma tylko jeden bit ustawiony, wynik logicznego i jest to, że co najwyżej ten sam bit jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="358d6-125">Since the flag itself has only one bit set, the result of the logical AND is that, at most, that same bit is set.</span></span> <span data-ttu-id="358d6-126">Aby dowiedzieć się, czy jest, czy nie, wystarczy porównać wynik logicznego i z samą flagą.</span><span class="sxs-lookup"><span data-stu-id="358d6-126">To find out whether it is or not, just compare the result of the logical AND with the flag itself.</span></span> <span data-ttu-id="358d6-127">Aby uzyskać więcej <xref:System.Printing.PrintQueueStatus>informacji, zobacz , [operator& (odwołanie C# i](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-). <xref:System.FlagsAttribute></span><span class="sxs-lookup"><span data-stu-id="358d6-127">For more information, see <xref:System.Printing.PrintQueueStatus>, the [& Operator (C# Reference)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-), and <xref:System.FlagsAttribute>.</span></span>  
  
 <span data-ttu-id="358d6-128">Dla każdego atrybutu, którego bit jest ustawiony, kod dodaje powiadomienie do raportu końcowego, który zostanie przedstawiony użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="358d6-128">For each attribute whose bit is set, the code adds a notice to the final report that will be presented to the user.</span></span> <span data-ttu-id="358d6-129">**(ReportAvailabilityAtThisTime** metoda, która jest wywoływana na końcu kodu jest omówiona poniżej.)</span><span class="sxs-lookup"><span data-stu-id="358d6-129">(The **ReportAvailabilityAtThisTime** method that is called at the end of the code is discussed below.)</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 <span data-ttu-id="358d6-130">Aby sprawdzić stan drukarki przy użyciu każdej właściwości, wystarczy przeczytać każdą właściwość i dodać notatkę `true`do raportu końcowego, który zostanie przedstawiony użytkownikowi, jeśli właściwość jest .</span><span class="sxs-lookup"><span data-stu-id="358d6-130">To check printer status using each property, you simply read each property and add a note to the final report that will be presented to the user if the property is `true`.</span></span> <span data-ttu-id="358d6-131">**(ReportAvailabilityAtThisTime** metoda, która jest wywoływana na końcu kodu jest omówiona poniżej.)</span><span class="sxs-lookup"><span data-stu-id="358d6-131">(The **ReportAvailabilityAtThisTime** method that is called at the end of the code is discussed below.)</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 <span data-ttu-id="358d6-132">**ReportAvailabilityAtThisTime** metoda została utworzona w przypadku, gdy trzeba ustalić, czy kolejka jest dostępna o bieżącej porze dnia.</span><span class="sxs-lookup"><span data-stu-id="358d6-132">The **ReportAvailabilityAtThisTime** method was created in case you need to determine if the queue is available at the current time of day.</span></span>  
  
 <span data-ttu-id="358d6-133">Metoda nic nie <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> zrobi, <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> jeśli i właściwości są równe; ponieważ w takim przypadku drukarka jest dostępna przez cały czas.</span><span class="sxs-lookup"><span data-stu-id="358d6-133">The method will do nothing if the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties are equal; because in that case the printer is available at all times.</span></span> <span data-ttu-id="358d6-134">Jeśli są one różne, metoda pobiera bieżący czas, który następnie musi <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> zostać <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> przekonwertowany na całkowitą liczbę minut po północy, ponieważ i właściwości są <xref:System.Int32>s reprezentujących minut po północy, a nie <xref:System.DateTime> obiektów.</span><span class="sxs-lookup"><span data-stu-id="358d6-134">If they are different, the method gets the current time which then has to be converted into total minutes past midnight because the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties are <xref:System.Int32>s representing minutes-after-midnight, not <xref:System.DateTime> objects.</span></span> <span data-ttu-id="358d6-135">Na koniec metoda sprawdza, czy bieżący czas jest między czasem rozpoczęcia i "do" razy.</span><span class="sxs-lookup"><span data-stu-id="358d6-135">Finally, the method checks to see if the current time is between the start and "until" times.</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## <a name="see-also"></a><span data-ttu-id="358d6-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="358d6-136">See also</span></span>

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
- [<span data-ttu-id="358d6-137">& Operator (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="358d6-137">& Operator (C# Reference)</span></span>](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)
- [<span data-ttu-id="358d6-138">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="358d6-138">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="358d6-139">Przegląd drukowania</span><span class="sxs-lookup"><span data-stu-id="358d6-139">Printing Overview</span></span>](printing-overview.md)

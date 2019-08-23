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
# <a name="how-to-remotely-survey-the-status-of-printers"></a>Instrukcje: Zdalne badanie stanu drukarek
W dowolnym momencie w średnich i dużych firmach może istnieć wiele drukarek, które nie działają ze względu na zakleszczenie papieru lub brak papieru lub inne problemy. Bogaty zestaw właściwości drukarki uwidocznionych w interfejsach API platformy Microsoft .NET Framework zapewnia metodę szybkiego przeglądu stanu drukarek.  
  
## <a name="example"></a>Przykład  
 Główne kroki tworzenia tego rodzaju narzędzi są następujące.  
  
1. Uzyskaj listę wszystkich serwerów wydruku.  
  
2. Przepętlenie między serwerami w celu wykonywania zapytań w ich kolejkach wydruku.  
  
3. W ramach każdego przebiegu pętli serwera pętla przez wszystkie kolejki serwera i odczytuje każdą właściwość, która może wskazywać, że kolejka nie działa.  
  
 Poniższy kod to seria fragmentów kodu. Dla uproszczenia w tym przykładzie przyjęto założenie, że lista serwerów wydruku ma rozdzielaną liczbę CRLF. `fileOfPrintServers` Zmienna<xref:System.IO.StreamReader> jest obiektem dla tego pliku. Ponieważ każda nazwa serwera znajduje się w osobnym wierszu, każde wywołanie metody <xref:System.IO.StreamReader.ReadLine%2A> Pobiera nazwę następnego serwera i <xref:System.IO.StreamReader>przenosi kursor do początku następnego wiersza.  
  
 W ramach pętli zewnętrznej kod tworzy <xref:System.Printing.PrintServer> obiekt dla najnowszego serwera wydruku i określa, że aplikacja ma prawa administracyjne do serwera programu.  
  
> [!NOTE]
> Jeśli istnieje wiele serwerów, można zwiększyć wydajność przy użyciu <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> konstruktorów, które inicjują tylko te właściwości, które mają być potrzebne.  
  
 Ten przykład używa <xref:System.Printing.PrintServer.GetPrintQueues%2A> do tworzenia kolekcji wszystkich kolejek serwera i rozpoczyna się w pętli. Ta pętla wewnętrzna zawiera strukturę rozgałęzień odpowiadającą dwóm sposobom sprawdzania stanu drukarki:  
  
- Można odczytać flagi <xref:System.Printing.PrintQueue.QueueStatus%2A> właściwości, które są typu <xref:System.Printing.PrintQueueStatus>.  
  
- Każdą odpowiednią właściwość, taką jak <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, i. <xref:System.Printing.PrintQueue.IsPaperJammed%2A>  
  
 W tym przykładzie pokazano obie metody, dlatego użytkownik był wcześniej monitowany o metodę użycia i odpowiedział na "y", jeśli chce użyć flag <xref:System.Printing.PrintQueue.QueueStatus%2A> właściwości. Szczegóły dwóch metod znajdują się poniżej.  
  
 Na koniec wyniki są prezentowane użytkownikowi.  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 Aby sprawdzić stan drukarki przy użyciu flag <xref:System.Printing.PrintQueue.QueueStatus%2A> właściwości, należy zaznaczyć każdą odpowiednią flagę, aby sprawdzić, czy została ustawiona. Standardowym sposobem, aby zobaczyć, czy jeden bit jest ustawiony w zestawie flag bitowych, jest wykonywanie operacji logicznej i z zestawem flag jako jednego operandu i flagą. Ponieważ sama flaga ma tylko jeden bit zestawu, wynik logiczny i to, co najwyżej, ten sam bit jest ustawiony. Aby dowiedzieć się, czy jest lub nie, po prostu Porównaj wynik logiczny i z flagą. Aby uzyskać więcej informacji, <xref:System.Printing.PrintQueueStatus>Zobacz, [operator & (C# Reference)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)i. <xref:System.FlagsAttribute>  
  
 Dla każdego atrybutu, którego bit jest ustawiony, kod dodaje powiadomienie do raportu końcowego, który zostanie przedstawiony użytkownikowi. (Metoda **ReportAvailabilityAtThisTime** wywołana na końcu kodu została omówiona poniżej).  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 Aby sprawdzić stan drukarki przy użyciu każdej właściwości, wystarczy odczytać każdą właściwość i dodać uwagę do raportu końcowego, który zostanie wyświetlony użytkownikowi, jeśli właściwość jest `true`. (Metoda **ReportAvailabilityAtThisTime** wywołana na końcu kodu została omówiona poniżej).  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 Metoda **ReportAvailabilityAtThisTime** została utworzona na wypadek, gdyby trzeba było określić, czy kolejka jest dostępna w bieżącym dniu.  
  
 Metoda nie będzie niczego robić, jeśli <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> właściwości <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> i są równe. w takim przypadku drukarka jest dostępna przez cały czas. Jeśli różnią się one, Metoda pobiera bieżący czas, który następnie musi zostać przekonwertowany na łączną liczbę minut po północy <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> , <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> ponieważ właściwości <xref:System.Int32>i są s reprezentują minuty-po-północy <xref:System.DateTime> , nie elementy. Na koniec Metoda sprawdza, czy bieżący czas jest między rozpoczęciem i "do" czasu.  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## <a name="see-also"></a>Zobacz także

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
- [Operator & (C# odwołanie)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)
- [Dokumenty w WPF](documents-in-wpf.md)
- [Przegląd drukowania](printing-overview.md)

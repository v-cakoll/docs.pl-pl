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
# <a name="how-to-remotely-survey-the-status-of-printers"></a>Jak zdalnie przeglądać status drukarek
W dowolnym momencie w średnich i dużych firmach może istnieć wiele drukarek, które nie działają z powodu zacięcia papieru lub braku papieru lub innej problematycznej sytuacji. Bogaty zestaw właściwości drukarki udostępniane w interfejsach API programu Microsoft .NET Framework zapewniają sposób wykonywania szybkiego badania stanu drukarek.  
  
## <a name="example"></a>Przykład  
 Główne kroki tworzenia tego rodzaju narzędzia są następujące.  
  
1. Uzyskaj listę wszystkich serwerów wydruku.  
  
2. Pętla przez serwery do kwerendy ich kolejek wydruku.  
  
3. W ramach każdego przebiegu pętli serwera, pętli przez wszystkie kolejki serwera i odczytać każdą właściwość, która może wskazywać, że kolejka nie działa obecnie.  
  
 Poniższy kod to seria urywków. Dla uproszczenia w tym przykładzie przyjęto założenie, że istnieje lista serwerów wydruku rozdzielanych crlf. Zmienna `fileOfPrintServers` jest <xref:System.IO.StreamReader> obiektem dla tego pliku. Ponieważ każda nazwa serwera jest w swoim <xref:System.IO.StreamReader.ReadLine%2A> własnym wierszu, każde wywołanie pobiera nazwę następnego serwera i przenosi kursor <xref:System.IO.StreamReader>'s na początek następnego wiersza.  
  
 W pętli zewnętrznej kod tworzy <xref:System.Printing.PrintServer> obiekt dla najnowszego serwera wydruku i określa, że aplikacja ma mieć prawa administracyjne do serwera.  
  
> [!NOTE]
> Jeśli istnieje wiele serwerów, można zwiększyć wydajność <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> przy użyciu konstruktorów, które tylko inicjować właściwości, które będą potrzebne.  
  
 Następnie w przykładzie użyto <xref:System.Printing.PrintServer.GetPrintQueues%2A> do utworzenia kolekcji wszystkich kolejek serwera i zaczyna się przez nie zapętlać. Ta wewnętrzna pętla zawiera strukturę rozgałęziania odpowiadającą dwóm sposobom sprawdzania stanu drukarki:  
  
- Można odczytać flagi właściwości, <xref:System.Printing.PrintQueue.QueueStatus%2A> która jest <xref:System.Printing.PrintQueueStatus>typu .  
  
- Można przeczytać każdą odpowiednią <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>właściwość, taką jak , i <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.  
  
 W tym przykładzie pokazano obie metody, więc użytkownik został wcześniej poproszony o to, która metoda użyć i odpowiedział <xref:System.Printing.PrintQueue.QueueStatus%2A> z "y", jeśli chcą użyć flagi właściwości. Poniżej znajdują się szczegółowe informacje na temat tych dwóch metod.  
  
 Na koniec wyniki są prezentowane użytkownikowi.  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 Aby sprawdzić stan drukarki przy <xref:System.Printing.PrintQueue.QueueStatus%2A> użyciu flag właściwości, należy sprawdzić każdą odpowiednią flagę, aby sprawdzić, czy jest ustawiona. Standardowy sposób, aby sprawdzić, czy jeden bit jest ustawiony w zestawie flag bitowych jest wykonanie logicznej operacji AND z zestawem flag jako jeden operand i samą flagę jako drugą. Ponieważ sama flaga ma tylko jeden bit ustawiony, wynik logicznego i jest to, że co najwyżej ten sam bit jest ustawiony. Aby dowiedzieć się, czy jest, czy nie, wystarczy porównać wynik logicznego i z samą flagą. Aby uzyskać więcej <xref:System.Printing.PrintQueueStatus>informacji, zobacz , [operator& (odwołanie C# i](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-). <xref:System.FlagsAttribute>  
  
 Dla każdego atrybutu, którego bit jest ustawiony, kod dodaje powiadomienie do raportu końcowego, który zostanie przedstawiony użytkownikowi. **(ReportAvailabilityAtThisTime** metoda, która jest wywoływana na końcu kodu jest omówiona poniżej.)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 Aby sprawdzić stan drukarki przy użyciu każdej właściwości, wystarczy przeczytać każdą właściwość i dodać notatkę `true`do raportu końcowego, który zostanie przedstawiony użytkownikowi, jeśli właściwość jest . **(ReportAvailabilityAtThisTime** metoda, która jest wywoływana na końcu kodu jest omówiona poniżej.)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 **ReportAvailabilityAtThisTime** metoda została utworzona w przypadku, gdy trzeba ustalić, czy kolejka jest dostępna o bieżącej porze dnia.  
  
 Metoda nic nie <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> zrobi, <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> jeśli i właściwości są równe; ponieważ w takim przypadku drukarka jest dostępna przez cały czas. Jeśli są one różne, metoda pobiera bieżący czas, który następnie musi <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> zostać <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> przekonwertowany na całkowitą liczbę minut po północy, ponieważ i właściwości są <xref:System.Int32>s reprezentujących minut po północy, a nie <xref:System.DateTime> obiektów. Na koniec metoda sprawdza, czy bieżący czas jest między czasem rozpoczęcia i "do" razy.  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## <a name="see-also"></a>Zobacz też

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
- [& Operator (odwołanie do języka C#)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)
- [Dokumenty w WPF](documents-in-wpf.md)
- [Przegląd drukowania](printing-overview.md)

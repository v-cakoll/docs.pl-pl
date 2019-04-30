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
ms.openlocfilehash: dc187a4ea120661e8118ce79a966d3d4a3b40711
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768504"
---
# <a name="how-to-remotely-survey-the-status-of-printers"></a>Instrukcje: Zdalne badanie stanu drukarek
W dowolnym momencie w średnich i dużych firmach może istnieć wiele drukarek, które nie działa z powodu zakleszczenie papieru lub Brak papieru lub problematycznych sytuacji. Bogaty zestaw właściwości drukarki ujawnione w [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] programu Microsoft .NET Framework zapewniają środki do przeprowadzania szybkiej udział w ankiecie stanów drukarki.  
  
## <a name="example"></a>Przykład  
 Oto główne kroki tworzenia tego rodzaju narzędzia.  
  
1. Uzyskaj listę wszystkich serwerów wydruku.  
  
2. Pętla za pośrednictwem serwerów do wykonywania zapytań ich kolejek wydruku.  
  
3. W ramach każdego przebiegu serwera pętli w pętli poprzez wszystkich kolejek na serwerze, a następnie zapoznaj się każdej właściwości, które mogą wskazywać, że kolejka nie jest obecnie działa.  
  
 Poniższy kod jest szereg fragmentów kodu. Dla uproszczenia w tym przykładzie przyjęto założenie, że znajduje się lista rozdzielonych CRLF serwerów wydruku. Zmienna `fileOfPrintServers` jest <xref:System.IO.StreamReader> obiektu dla tego pliku. Ponieważ nazwa każdego serwera w osobnym wierszu, żadnym wywołaniu, z <xref:System.IO.StreamReader.ReadLine%2A> pobiera nazwę kolejny serwer i przenosi <xref:System.IO.StreamReader>przez kursor na początku następnego wiersza.  
  
 W zewnętrznej pętli, kod tworzy <xref:System.Printing.PrintServer> obiektu dla najnowszych serwera wydruku i określa, czy aplikacja ma mieć uprawnienia administracyjne do serwera.  
  
> [!NOTE]
>  Jeśli jest dostępnych wiele serwerów, może poprawić wydajność przy użyciu <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> konstruktorów, które tylko inicjowania właściwości będą potrzebne.  
  
 Następnie w przykładzie <xref:System.Printing.PrintServer.GetPrintQueues%2A> Aby utworzyć kolekcję zawierającą wszystkie serwera zachowania umieszcza w kolejce i rozpoczyna się w pętli poprzez ich. Ta pętla wewnętrzny zawiera rozgałęziona struktura odpowiadający dwa sposoby sprawdzania stanu drukarki:  
  
- Może odczytywać flagi o <xref:System.Printing.PrintQueue.QueueStatus%2A> właściwość, która jest typu <xref:System.Printing.PrintQueueStatus>.  
  
- Można znaleźć każdej odpowiednie właściwości, takie jak <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, i <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.  
  
 W tym przykładzie przedstawiono obie metody, dzięki czemu użytkownik został wcześniej zostanie wyświetlony monit, aby metody i odpowiedziała, zgłaszając "y", jeśli użytkownik chce używać flagi o <xref:System.Printing.PrintQueue.QueueStatus%2A> właściwości. Poniżej znajdują się szczegółowe informacje o dwóch metod.  
  
 Na koniec wyniki są prezentowane użytkownikowi.  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 Aby sprawdzić stan drukarki przy użyciu flagi programu <xref:System.Printing.PrintQueue.QueueStatus%2A> właściwości, możesz sprawdzić każdy odpowiednie flagi, aby zobaczyć, jeśli jest ustawiony. Standardowy sposób, aby zobaczyć, jeśli jest ustawiony bit jeden zestaw flag bitowych jest do wykonywania operacji logicznych i przy użyciu zestawu flag jako jeden z operandów i Flaga jako drugiego. Ponieważ flagi, sama ma tylko jeden bit, ustaw wartości logicznej i jest to, że, co najwyżej ten sam bit jest ustawiony. Aby dowiedzieć się, czy jest lub nie, po prostu Porównaj wynik logicznej i przy użyciu flagi sam. Aby uzyskać więcej informacji, zobacz <xref:System.Printing.PrintQueueStatus>, [& — Operator (C# odwołania)](~/docs/csharp/language-reference/operators/and-operator.md), i <xref:System.FlagsAttribute>.  
  
 Dla każdego atrybutu, którego bit jest ustawiony kod dodaje powiadomienie do raportu końcowego, który zostanie wyświetlony użytkownikowi. ( **ReportAvailabilityAtThisTime** metodę, która jest wywoływany pod koniec kodu, omówiono poniżej.)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 Aby sprawdzić stan drukarki za pomocą każdej właściwości, możesz po prostu odczytywać każdej właściwości i dodać notatkę do raport końcowy, który zostanie wyświetlony dla użytkownika, jeśli właściwość jest `true`. ( **ReportAvailabilityAtThisTime** metodę, która jest wywoływany pod koniec kodu, omówiono poniżej.)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 **ReportAvailabilityAtThisTime** metoda została utworzona, w przypadku, gdy zachodzi potrzeba określenia, czy kolejka jest dostępna w aktualną porę dnia.  
  
 Metoda będzie nic nie rób Jeśli <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> i <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> właściwości są równe; ponieważ w takim przypadku drukarka jest dostępna przez cały czas. Jeśli są różne, metoda pobiera bieżącą godzinę, które mają zostać przekształcone, kiedy łączna liczba minut po północy, ponieważ <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> i <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> właściwości są <xref:System.Int32>s reprezentujących minut po północy, nie <xref:System.DateTime> obiekty. Na koniec metody sprawdza, czy bieżący czas między rozpoczęciem a "do" razy.  
  
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
- [& — Operator (C# odwołania)](~/docs/csharp/language-reference/operators/and-operator.md)
- [Dokumenty w WPF](documents-in-wpf.md)
- [Przegląd drukowania](printing-overview.md)

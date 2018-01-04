---
title: "Jak zdalnie przeglądać status drukarek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eef67d6ade8fb2a17edadff35fc3155608f831cd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-remotely-survey-the-status-of-printers"></a>Jak zdalnie przeglądać status drukarek
W danym momencie w średnich i dużych firmach może być wiele drukarek, które nie są pracy z powodu papier lub jest poza papier lub inne problemy sytuacji. Bogaty zestaw właściwości drukarki w [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] z [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] stanowić sposób wykonywania szybką ankietę stanów drukarek.  
  
## <a name="example"></a>Przykład  
 Oto główne kroki tworzenia tego rodzaju narzędzia.  
  
1.  Uzyskaj listę wszystkich serwerów wydruku.  
  
2.  Pętla za pośrednictwem serwerów do badania ich kolejek wydruku.  
  
3.  W każdym przebiegu pętli serwera pętli wszystkich kolejek na serwerze i odczytu dla każdej właściwości, która może sygnalizować, że kolejka obecnie nie działa.  
  
 Poniższy kod jest serią fragmentów. Dla uproszczenia założono, że istnieje listę serwerów wydruku rozdzielonych CRLF. Zmienna `fileOfPrintServers` jest <xref:System.IO.StreamReader> obiekt dla tego pliku. Ponieważ nazwa każdego serwera w osobnym wierszu, wszelkie wywołanie <xref:System.IO.StreamReader.ReadLine%2A> pobiera nazwę serwera dalej i przenosi <xref:System.IO.StreamReader>przez kursor na początek następnego wiersza.  
  
 W zewnętrznej pętli kod tworzy <xref:System.Printing.PrintServer> obiektu najnowsze serwera wydruku i określa, że aplikacja ma mieć uprawnienia administracyjne na serwerze.  
  
> [!NOTE]
>  Jeśli istnieje wiele serwerów, może poprawić wydajność przy użyciu <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> konstruktorów tylko zainicjować właściwości mają być potrzebne.  
  
 W przykładzie następnie użyto <xref:System.Printing.PrintServer.GetPrintQueues%2A> do utworzenia kolekcji wszystkich serwera obiektu kolejki i rozpoczyna się nimi pętli. Wewnętrzny pętla zawiera rozgałęziania strukturę odpowiadający sprawdzanie stanu drukarki na dwa sposoby:  
  
-   Możesz przeczytać flagi z <xref:System.Printing.PrintQueue.QueueStatus%2A> właściwość, która jest typu <xref:System.Printing.PrintQueueStatus>.  
  
-   Każda właściwość może odczytywać takich jak <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, i <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.  
  
 W przykładzie pokazano obu metod, dzięki czemu użytkownik został wcześniej zostanie wyświetlony monit, aby metody i zwrócił "y", jeśli użytkownik chce używać flag z <xref:System.Printing.PrintQueue.QueueStatus%2A> właściwości. Aby uzyskać więcej informacji o te dwie metody są wymienione poniżej.  
  
 Na koniec wyniki są prezentowane użytkownikowi.  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 Aby sprawdzić stan drukarki przy użyciu flagi z <xref:System.Printing.PrintQueue.QueueStatus%2A> właściwości, sprawdź flag odpowiednie, aby zobaczyć, jeśli jest ustawiona. Standardowy sposób, aby zobaczyć, czy jeden bit jest ustawiona zestaw flagi bitów jest wykonanie operacji logicznych i przy użyciu flagi jako jeden operand i flagi co inne. Ponieważ flagą sama ma tylko jeden bit, ustawić wyniku logicznym, a jest to, że, co najwyżej tego samego bit jest ustawiony. Aby dowiedzieć się czy nie jest on, po prostu porównać wyniku logicznym i z ustawioną flagą sama. Aby uzyskać więcej informacji, zobacz <xref:System.Printing.PrintQueueStatus>, [& — Operator (odwołanie w C#)](~/docs/csharp/language-reference/operators/and-operator.md), i <xref:System.FlagsAttribute>.  
  
 Dla każdego atrybutu ustawiono bit, którego kod dodaje powiadomienie do raportu końcowego, który będzie widoczne dla użytkownika. ( **ReportAvailabilityAtThisTime** metodę, która jest wywoływana po zakończeniu kodu została szczegółowo opisana poniżej.)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 Aby sprawdzić stan drukarek za pomocą każdej właściwości, należy po prostu odczytu dla każdej właściwości i dodania uwagi do raportu końcowego, który zostanie wyświetlone dla użytkownika, jeśli właściwość jest `true`. ( **ReportAvailabilityAtThisTime** metodę, która jest wywoływana po zakończeniu kodu została szczegółowo opisana poniżej.)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 **ReportAvailabilityAtThisTime** metody został utworzony, w razie potrzeby można określić, czy kolejka jest dostępna w aktualną porę dnia.  
  
 Metoda nie przynosi Jeśli <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> i <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> właściwości są równe; ponieważ w takim przypadku drukarka jest dostępna przez cały czas. Jeśli są różne, metoda pobiera bieżącą godzinę, które mają zostać przekształcone łączną liczbę minut po północy, ponieważ <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> i <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> właściwości są <xref:System.Int32>s nie reprezentujący minut po północy, <xref:System.DateTime> obiekty. Na koniec metody sprawdza, czy bieżąca godzina jest między rozpoczęciem a "do" razy.  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## <a name="see-also"></a>Zobacz też  
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
 [& — Operator (odwołanie w C#)](~/docs/csharp/language-reference/operators/and-operator.md)  
 [Dokumenty w WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Przegląd drukowania](../../../../docs/framework/wpf/advanced/printing-overview.md)

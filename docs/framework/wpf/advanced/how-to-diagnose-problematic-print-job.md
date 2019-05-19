---
title: 'Instrukcje: Diagnozowanie problematycznych zadań drukowania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- troubleshooting print job problems [WPF]
- print jobs [WPF], troubleshooting
- print jobs [WPF], diagnosing problems
ms.assetid: b081a170-84c6-48f9-a487-5766a8d58a82
ms.openlocfilehash: c9da2e1daff23ef9ba39d8b5d53cb3be67f35a27
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65878209"
---
# <a name="how-to-diagnose-problematic-print-job"></a>Instrukcje: Diagnozowanie problematycznych zadań drukowania
Administratorzy sieci często pola skarg od użytkowników dotyczące zadania drukowania, które nie drukowania lub wydrukować powoli. Bogaty zestaw właściwości zadania drukowania, udostępniane w [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] programu Microsoft .NET Framework zapewniają środki do przeprowadzania szybkiej diagnostyki zdalnej zadań drukowania.  
  
## <a name="example"></a>Przykład  
 Oto główne kroki tworzenia tego rodzaju narzędzia.  
  
1. Zidentyfikuj zadania drukowania, które użytkownik jest skarżących o. Użytkownicy często nie można tego zrobić dokładnie. Może nie wiedzieć nazwy serwerów wydruku i drukarek. Może zawierać opis lokalizacji drukarki w terminologii innego, niż zostało użyte w ustawieniach jego <xref:System.Printing.PrintQueue.Location%2A> właściwości. W związku z tym jest to dobry pomysł, aby wygenerować listę użytkownika aktualnie przesłanych zadań. Jeśli istnieje więcej niż jeden, następnie komunikacji między określonym użytkownikiem a administrator systemu drukowania może służyć do punktu przyczepienia zadanie, które występują problemy. Poniżej znajdują się podkroki.  
  
    1. Uzyskaj listę wszystkich serwerów wydruku.  
  
    2. Pętla za pośrednictwem serwerów do wykonywania zapytań ich kolejek wydruku.  
  
    3. W ramach każdego przebiegu pętli serwera pętli wszystkich kolejek na serwerze do wykonywania zapytań swoich zadań  
  
    4. W ramach każdego przebiegu pętli kolejki w pętli poprzez zadania, a następnie Zbierz informacje identyfikujące te, które zostały przesłane przez użytkownika wnioskujących.  
  
2. W przypadku wykryto problematyczne zadanie drukowania, należy sprawdzić odpowiednie właściwości, aby zobaczyć, co może być problem. Na przykład jest zadanie w stanie błędu, lub czy drukarki obsługi kolejki przejdź do trybu offline przed zadania można wydrukować?  
  
 Poniższy kod jest szereg przykładów kodu. Pierwszy przykład kodu zawiera pętlę za pośrednictwem kolejek wydruku. (Krok 1c powyżej). Zmienna `myPrintQueues` jest <xref:System.Printing.PrintQueueCollection> obiektu dla bieżącego serwera wydruku.  
  
 Przykładowy kod, który rozpoczyna się od bieżącego obiektu kolejki wydruku z odświeżania <xref:System.Printing.PrintQueue.Refresh%2A?displayProperty=nameWithType>. Daje to gwarancję, że właściwości obiektu przedstawiać stanu drukarki fizycznej, który reprezentuje. Następnie aplikacja pobiera kolekcję zadań drukowania aktualnie w kolejce wydruku przy użyciu <xref:System.Printing.PrintQueue.GetPrintJobInfoCollection%2A>.  
  
 Następnie aplikacja pętli <xref:System.Printing.PrintSystemJobInfo> kolekcji, jak i porównuje <xref:System.Printing.PrintSystemJobInfo.Submitter%2A> właściwości z aliasem użytkownika wnioskujących. Jeśli są zgodne, aplikacja dodaje informacje identyfikacyjne o zadaniu parametry, które zostanie wyświetlone. ( `userName` i `jobList` zmienne są inicjowane we wcześniejszej części aplikacji.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#enumeratejobsinqueues)]
 [!code-csharp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#enumeratejobsinqueues)]
 [!code-vb[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#enumeratejobsinqueues)]  
  
 Następny przykład kodu przejmuje aplikację w kroku 2. (Zobacz powyżej). Wykryto problematyczne zadanie, a aplikacja wyświetla monit dotyczący informacje identyfikujące go. Z tej informacji tworzy <xref:System.Printing.PrintServer>, <xref:System.Printing.PrintQueue>, i <xref:System.Printing.PrintSystemJobInfo> obiektów.  
  
 Na tym etapie aplikacja zawiera rozgałęziona struktura odpowiadający sprawdzanie stanu zadania drukowania na dwa sposoby:  
  
- Może odczytywać flagi o <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> właściwość, która jest typu <xref:System.Printing.PrintJobStatus>.  
  
- Można znaleźć każdej odpowiednie właściwości, takie jak <xref:System.Printing.PrintSystemJobInfo.IsBlocked%2A> i <xref:System.Printing.PrintSystemJobInfo.IsInError%2A>.  
  
 W tym przykładzie przedstawiono obie metody, dzięki czemu użytkownik został wcześniej zostanie wyświetlony monit, aby metody i odpowiedziała, zgłaszając "Y", jeśli użytkownik chce używać flagi o <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> właściwości. Poniżej znajdują się szczegółowe informacje o dwóch metod. Na koniec aplikacja używa metodę o nazwie **ReportQueueAndJobAvailability** Aby sporządzić raport na temat tego, czy zadanie może zostać zrealizowane o tej porze dnia. Metoda ta jest omówiona w [odnajdywanie czy drukowania zadania może być drukowane na ten pory dnia](how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day.md).  
  
 [!code-cpp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#identifyanddiagnoseproblematicjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#identifyanddiagnoseproblematicjob)]
 [!code-vb[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#identifyanddiagnoseproblematicjob)]  
  
 Aby sprawdzić stan zadania drukowania, przy użyciu flagi o <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> właściwości, możesz sprawdzić każdy odpowiednie flagi, aby zobaczyć, jeśli jest ustawiony. Standardowy sposób, aby zobaczyć, jeśli jest ustawiony bit jeden zestaw flag bitowych jest do wykonywania operacji logicznych i przy użyciu zestawu flag jako jeden z operandów i Flaga jako drugiego. Ponieważ flagi, sama ma tylko jeden bit, ustaw wartości logicznej i jest to, że, co najwyżej ten sam bit jest ustawiony. Aby dowiedzieć się, czy jest lub nie, po prostu Porównaj wynik logicznej i przy użyciu flagi sam. Aby uzyskać więcej informacji, zobacz <xref:System.Printing.PrintJobStatus>, [& — Operator (C# odwołania)](~/docs/csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-), i <xref:System.FlagsAttribute>.  
  
 Dla każdego atrybutu, którego bit jest ustawiony kod zgłasza to do ekranu konsoli i czasami sugeruje sposób na odpowiedź. ( **HandlePausedJob** metodę, która jest wywoływana, jeśli zadania lub kolejki jest wstrzymana, omówiono poniżej.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobattributes)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobattributes)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobattributes)]  
  
 Aby sprawdzić stan zadania drukowania, przy użyciu oddzielnych właściwości, po prostu odczytywać każdej właściwości i, jeśli właściwość jest `true`raportu do ekranu konsoli i prawdopodobnie sugeruje sposób na odpowiedź. ( **HandlePausedJob** metodę, która jest wywoływana, jeśli zadania lub kolejki jest wstrzymana, omówiono poniżej.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobproperties)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobproperties)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobproperties)]  
  
 **HandlePausedJob** metoda umożliwia użytkownikowi aplikacji zdalnie wznawianie wstrzymanej prac. Ponieważ może to być powód, dlaczego został wstrzymany kolejki wydruku, metoda rozpoczyna się od monitowania do podjęcia decyzji użytkownika o tym, czy można je wznowić. Jeśli odpowiedź to "Y", a następnie <xref:System.Printing.PrintQueue.Resume%2A?displayProperty=nameWithType> metoda jest wywoływana.  
  
 Następnie użytkownik jest monitowany zdecydować, jeśli samo zadanie powinno wznowione, na wypadek, jest on wstrzymany niezależnie od kolejki wydruku. (Porównanie <xref:System.Printing.PrintQueue.IsPaused%2A?displayProperty=nameWithType> i <xref:System.Printing.PrintSystemJobInfo.IsPaused%2A?displayProperty=nameWithType>.) Jeśli padnie "Y", następnie <xref:System.Printing.PrintSystemJobInfo.Resume%2A?displayProperty=nameWithType> jest wywołany; w przeciwnym razie <xref:System.Printing.PrintSystemJobInfo.Cancel%2A> jest wywoływana.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#handlepausedjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#handlepausedjob)]
 [!code-vb[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#handlepausedjob)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Printing.PrintJobStatus>
- <xref:System.Printing.PrintSystemJobInfo>
- <xref:System.FlagsAttribute>
- <xref:System.Printing.PrintQueue>
- [& — Operator (C# odwołania)](~/docs/csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)
- [Dokumenty w WPF](documents-in-wpf.md)
- [Przegląd drukowania](printing-overview.md)

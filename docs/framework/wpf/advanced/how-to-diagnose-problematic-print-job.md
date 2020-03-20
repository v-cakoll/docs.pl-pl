---
title: Jak zdiagnozować problematyczne zadanie drukowania
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
ms.openlocfilehash: 15de5d9ec8dc4016753b9d4cbed6fb0c64571774
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186043"
---
# <a name="how-to-diagnose-problematic-print-job"></a>Jak zdiagnozować problematyczne zadanie drukowania
Administratorzy sieci często wysyłają skargi od użytkowników dotyczące zadań drukowania, które nie drukują ani nie drukują powoli. Bogaty zestaw właściwości zadania drukowania udostępniane w interfejsach API programu Microsoft .NET Framework zapewnia sposób wykonywania szybkiej zdalnej diagnostyki zadań drukowania.  
  
## <a name="example"></a>Przykład  
 Główne kroki tworzenia tego rodzaju narzędzia są następujące.  
  
1. Zidentyfikuj zadanie drukowania, na które użytkownik narzeka. Użytkownicy często nie mogą tego zrobić dokładnie. Mogą nie znać nazw serwerów wydruku lub drukarek. Mogą one opisywać lokalizację drukarki w innej terminologii <xref:System.Printing.PrintQueue.Location%2A> niż została użyta w ustawieniu jej właściwości. W związku z tym dobrym pomysłem jest wygenerowanie listy aktualnie przesłanych zadań użytkownika. Jeśli istnieje więcej niż jeden, komunikacja między użytkownikiem a administratorem systemu drukowania może służyć do określenia zadania, które ma problemy. Podkroki są następujące.  
  
    1. Uzyskaj listę wszystkich serwerów wydruku.  
  
    2. Pętla przez serwery do kwerendy ich kolejek wydruku.  
  
    3. W każdym przebiegu pętli serwera należy przechodzić przez wszystkie kolejki serwera, aby zbadać ich zadania  
  
    4. W każdym przebiegu pętli kolejki, pętli przez jego zadania i zbierać informacje identyfikujące o tych, które zostały przesłane przez użytkownika skarżącego.  
  
2. Po zidentyfikowaniu problematycznego zadania drukowania sprawdź odpowiednie właściwości, aby zobaczyć, co może być problemem. Na przykład czy zadanie jest w stanie błędu, czy drukarka obsługująca kolejkę przechodzi w tryb offline, zanim zadanie będzie mogło drukować?  
  
 Poniższy kod jest seria przykładów kodu. Pierwszy przykład kodu zawiera pętlę za pośrednictwem kolejek wydruku. (Krok 1c powyżej.) Zmienna `myPrintQueues` jest <xref:System.Printing.PrintQueueCollection> obiektem bieżącego serwera wydruku.  
  
 Przykładowy kod rozpoczyna się od odświeżenia <xref:System.Printing.PrintQueue.Refresh%2A?displayProperty=nameWithType>bieżącego obiektu kolejki wydruku za pomocą pliku . Gwarantuje to, że właściwości obiektu dokładnie reprezentują stan drukarki fizycznej, która reprezentuje. Następnie aplikacja pobiera kolekcję zadań drukowania aktualnie <xref:System.Printing.PrintQueue.GetPrintJobInfoCollection%2A>w kolejce wydruku przy użyciu programu .  
  
 Następnie aplikacja pętli za <xref:System.Printing.PrintSystemJobInfo> pośrednictwem kolekcji <xref:System.Printing.PrintSystemJobInfo.Submitter%2A> i porównuje każdą właściwość z aliasem użytkownika skarżącego. Jeśli są one zgodne, aplikacja dodaje informacje identyfikujące zadanie do ciągu, który zostanie przedstawiony. `userName` (Zmienne `jobList` i są inicjowane wcześniej w aplikacji.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#enumeratejobsinqueues)]
 [!code-csharp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#enumeratejobsinqueues)]
 [!code-vb[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#enumeratejobsinqueues)]  
  
 Następny przykład kodu odbiera aplikację w kroku 2. (Patrz wyżej). Problematyczne zadanie zostało zidentyfikowane, a aplikacja monituje o informacje, które go identyfikują. Z tych informacji <xref:System.Printing.PrintServer> <xref:System.Printing.PrintQueue>tworzy <xref:System.Printing.PrintSystemJobInfo> , i obiektów.  
  
 W tym momencie aplikacja zawiera strukturę rozgałęziania odpowiadającą dwóm sposobom sprawdzania stanu zadania drukowania:  
  
- Można odczytać flagi właściwości, <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> która jest <xref:System.Printing.PrintJobStatus>typu .  
  
- Możesz przeczytać każdą odpowiednią <xref:System.Printing.PrintSystemJobInfo.IsBlocked%2A> właściwość, taką jak i <xref:System.Printing.PrintSystemJobInfo.IsInError%2A>.  
  
 W tym przykładzie pokazano obie metody, więc użytkownik został wcześniej poproszony o to, która metoda użyć i odpowiedział <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> z "Y", jeśli chcą użyć flagi właściwości. Poniżej znajdują się szczegółowe informacje na temat tych dwóch metod. Na koniec aplikacja używa metody o nazwie **ReportQueueAndJobAvailability** do raportowania, czy zadanie można wydrukować o tej porze dnia. Ta metoda jest omówiona w [Discover, czy zadanie drukowania może być drukowane o tej porze dnia](how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day.md).  
  
 [!code-cpp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#identifyanddiagnoseproblematicjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#identifyanddiagnoseproblematicjob)]
 [!code-vb[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#identifyanddiagnoseproblematicjob)]  
  
 Aby sprawdzić stan zadania drukowania <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> przy użyciu flag właściwości, należy sprawdzić każdą odpowiednią flagę, aby sprawdzić, czy jest ustawiona. Standardowy sposób, aby sprawdzić, czy jeden bit jest ustawiony w zestawie flag bitowych jest wykonanie logicznej operacji AND z zestawem flag jako jeden operand i samą flagę jako drugą. Ponieważ sama flaga ma tylko jeden bit ustawiony, wynik logicznego i jest to, że co najwyżej ten sam bit jest ustawiony. Aby dowiedzieć się, czy jest, czy nie, wystarczy porównać wynik logicznego i z samą flagą. Aby uzyskać więcej <xref:System.Printing.PrintJobStatus>informacji, zobacz , [operator& (odwołanie C# i](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-). <xref:System.FlagsAttribute>  
  
 Dla każdego atrybutu, którego bit jest ustawiony, kod zgłasza to na ekranie konsoli i czasami sugeruje sposób reagowania. **(HandlePausedJob** metoda, która jest wywoływana, jeśli zadanie lub kolejka jest wstrzymana jest omówiona poniżej.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobattributes)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobattributes)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobattributes)]  
  
 Aby sprawdzić stan zadania drukowania przy użyciu oddzielnych właściwości, `true`wystarczy przeczytać każdą właściwość, a jeśli właściwość jest , raport na ekranie konsoli i ewentualnie zaproponować sposób odpowiedzi. **(HandlePausedJob** metoda, która jest wywoływana, jeśli zadanie lub kolejka jest wstrzymana jest omówiona poniżej.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobproperties)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobproperties)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobproperties)]  
  
 **HandlePausedJob** Metoda umożliwia użytkownikowi aplikacji zdalnie wznowić wstrzymane zadania. Ponieważ może istnieć dobry powód, dla którego kolejka wydruku została wstrzymana, metoda rozpoczyna się od monitowania o decyzję użytkownika o tym, czy ją wznowić. Jeśli odpowiedź brzmi "Y", <xref:System.Printing.PrintQueue.Resume%2A?displayProperty=nameWithType> metoda jest wywoływana.  
  
 Następnie użytkownik jest monitowany, aby zdecydować, czy samo zadanie powinno zostać wznowione, na wypadek gdyby zostało wstrzymane niezależnie od kolejki wydruku. <xref:System.Printing.PrintQueue.IsPaused%2A?displayProperty=nameWithType> (Porównaj <xref:System.Printing.PrintSystemJobInfo.IsPaused%2A?displayProperty=nameWithType>i .) Jeśli odpowiedź brzmi "Y", to <xref:System.Printing.PrintSystemJobInfo.Resume%2A?displayProperty=nameWithType> jest wywoływana; w <xref:System.Printing.PrintSystemJobInfo.Cancel%2A> przeciwnym razie jest wywoływana.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#handlepausedjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#handlepausedjob)]
 [!code-vb[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#handlepausedjob)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Printing.PrintJobStatus>
- <xref:System.Printing.PrintSystemJobInfo>
- <xref:System.FlagsAttribute>
- <xref:System.Printing.PrintQueue>
- [& Operator (odwołanie do języka C#)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)
- [Dokumenty w WPF](documents-in-wpf.md)
- [Przegląd drukowania](printing-overview.md)

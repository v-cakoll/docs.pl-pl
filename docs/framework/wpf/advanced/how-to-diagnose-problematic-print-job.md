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
ms.openlocfilehash: 181248f69684860fd43648952ef4eb3cced1c0ba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944634"
---
# <a name="how-to-diagnose-problematic-print-job"></a>Instrukcje: Diagnozowanie problematycznych zadań drukowania
Administratorzy sieci często zgłaszają reklamacje użytkowników o zadaniach drukowania, które nie drukują się ani nie drukują powoli. Bogaty zestaw właściwości zadania drukowania uwidocznionych w interfejsach API platformy Microsoft .NET Framework zapewnia metodę wykonywania szybkiej zdalnej diagnostyki zadań drukowania.  
  
## <a name="example"></a>Przykład  
 Główne kroki tworzenia tego rodzaju narzędzi są następujące.  
  
1. Zidentyfikuj zadanie drukowania, którego dotyczy użytkownik. Użytkownicy często nie mogą dokładnie wykonać tej czynności. Mogą nie znać nazw serwerów wydruku lub drukarek. Mogą oni opisać lokalizację drukarki w innej terminologii niż została użyta w celu ustawienia jej <xref:System.Printing.PrintQueue.Location%2A> właściwości. W związku z tym dobrym pomysłem jest wygenerowanie listy aktualnie przesłanych zadań użytkownika. Jeśli istnieje więcej niż jeden, wówczas komunikacja między użytkownikiem a administratorem systemu drukowania może być używana do lokalizowania zadania, które ma problemy. Poniżej przedstawiono podkroky.  
  
    1. Uzyskaj listę wszystkich serwerów wydruku.  
  
    2. Przepętlenie między serwerami w celu wykonywania zapytań w ich kolejkach wydruku.  
  
    3. W ramach każdego przebiegu pętli serwera pętla przez wszystkie kolejki serwera, aby wykonać zapytanie o swoje zadania  
  
    4. W ramach każdego przebiegu pętli kolejki, pętla przez zadania i gromadzenie informacji identyfikacyjnych o tych, które zostały przesłane przez użytkownika wnoszącego skargę.  
  
2. Po zidentyfikowaniu problematycznego zadania drukowania Przejrzyj odpowiednie właściwości, aby zobaczyć, co może być problemem. Na przykład, czy zadanie jest w stanie błędu, czy drukarka obsługuje kolejkę przejdź do trybu offline przed wydrukowaniem zadania?  
  
 Poniższy kod zawiera serie przykładów kodu. Pierwszy przykład kodu zawiera pętlę w kolejkach wydruku. (Krok 1c powyżej) `myPrintQueues` Zmienna<xref:System.Printing.PrintQueueCollection> jest obiektem bieżącego serwera wydruku.  
  
 Przykładowy kod rozpoczyna się od odświeżenia bieżącego obiektu kolejki wydruku <xref:System.Printing.PrintQueue.Refresh%2A?displayProperty=nameWithType>za pomocą. Gwarantuje to, że właściwości obiektu dokładnie przedstawiają stan reprezentowanej drukarki fizycznej. Następnie aplikacja pobiera kolekcję zadań drukowania w kolejce wydruku przy użyciu <xref:System.Printing.PrintQueue.GetPrintJobInfoCollection%2A>.  
  
 Kolejna pętla aplikacji przez <xref:System.Printing.PrintSystemJobInfo> kolekcję i porównuje każdą <xref:System.Printing.PrintSystemJobInfo.Submitter%2A> właściwość z aliasem użytkownika wnoszącego skargę. Jeśli są one zgodne, aplikacja dodaje informacje identyfikacyjne dotyczące zadania do ciągu, który zostanie przedstawiony. `userName` (I `jobList` zmienne są inicjowane we wcześniejszej części aplikacji).  
  
 [!code-cpp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#enumeratejobsinqueues)]
 [!code-csharp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#enumeratejobsinqueues)]
 [!code-vb[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#enumeratejobsinqueues)]  
  
 Następny przykład kodu wybiera aplikację w kroku 2. (Zobacz powyżej). Wykryto problematyczne zadanie, a aplikacja wyświetli komunikat z informacjami identyfikującymi ją. Z tych informacji są tworzone <xref:System.Printing.PrintServer>obiekty <xref:System.Printing.PrintQueue>, i <xref:System.Printing.PrintSystemJobInfo> .  
  
 W tym momencie aplikacja zawiera strukturę rozgałęzień odpowiadającą dwóm sposobom sprawdzania stanu zadania drukowania:  
  
- Można odczytać flagi <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> właściwości, które są typu <xref:System.Printing.PrintJobStatus>.  
  
- Każdą odpowiednią właściwość, taką jak <xref:System.Printing.PrintSystemJobInfo.IsBlocked%2A> i. <xref:System.Printing.PrintSystemJobInfo.IsInError%2A>  
  
 W tym przykładzie pokazano obie metody, dlatego użytkownik był wcześniej monitowany o metodę użycia i odpowiedział na "Y", jeśli chce użyć flag <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> właściwości. Szczegóły dwóch metod znajdują się poniżej. Na koniec aplikacja używa metody o nazwie **ReportQueueAndJobAvailability** , aby zgłosić, czy zadanie można wydrukować o tej porze dnia. Ta metoda została omówiona w sekcji [wykrywanie, czy zadanie drukowania można wydrukować o tej porze dnia](how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day.md).  
  
 [!code-cpp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#identifyanddiagnoseproblematicjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#identifyanddiagnoseproblematicjob)]
 [!code-vb[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#identifyanddiagnoseproblematicjob)]  
  
 Aby sprawdzić stan zadania drukowania przy użyciu flag <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> właściwości, należy zaznaczyć każdą odpowiednią flagę, aby sprawdzić, czy została ustawiona. Standardowym sposobem, aby zobaczyć, czy jeden bit jest ustawiony w zestawie flag bitowych, jest wykonywanie operacji logicznej i z zestawem flag jako jednego operandu i flagą. Ponieważ sama flaga ma tylko jeden bit zestawu, wynik logiczny i to, co najwyżej, ten sam bit jest ustawiony. Aby dowiedzieć się, czy jest lub nie, po prostu Porównaj wynik logiczny i z flagą. Aby uzyskać więcej informacji, <xref:System.Printing.PrintJobStatus>Zobacz, [operator & (C# Reference)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)i. <xref:System.FlagsAttribute>  
  
 Dla każdego atrybutu, którego bit jest ustawiony, kod raportuje ten element na ekranie konsoli i czasami sugeruje sposób odpowiedzi. (Metoda **HandlePausedJob** wywoływana w przypadku wstrzymania zadania lub kolejki jest omówiona poniżej).  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobattributes)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobattributes)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobattributes)]  
  
 Aby sprawdzić stan zadania drukowania przy użyciu osobnych właściwości, wystarczy odczytać każdą właściwość i, jeśli właściwość jest `true`, raport na ekranie konsoli i może sugerować sposób odpowiedzi. (Metoda **HandlePausedJob** wywoływana w przypadku wstrzymania zadania lub kolejki jest omówiona poniżej).  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobproperties)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobproperties)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobproperties)]  
  
 Metoda **HandlePausedJob** umożliwia użytkownikowi aplikacji zdalne wznawianie wstrzymanych zadań. Ze względu na to, że może istnieć dobry powód, dla którego kolejka wydruku została wstrzymana, Metoda rozpoczyna się, monitując o decyzję użytkownika o tym, czy wznowić ją. Jeśli odpowiedź ma wartość "Y", <xref:System.Printing.PrintQueue.Resume%2A?displayProperty=nameWithType> Metoda jest wywoływana.  
  
 Następnie użytkownik jest monitowany o podjęcie decyzji o tym, czy zadanie powinno zostać wznowione, podobnie jak zostało wstrzymane niezależnie od kolejki wydruku. (Porównaj <xref:System.Printing.PrintQueue.IsPaused%2A?displayProperty=nameWithType> i <xref:System.Printing.PrintSystemJobInfo.IsPaused%2A?displayProperty=nameWithType>.) Jeśli odpowiedź jest "Y", <xref:System.Printing.PrintSystemJobInfo.Resume%2A?displayProperty=nameWithType> to jest wywoływana; w przeciwnym razie <xref:System.Printing.PrintSystemJobInfo.Cancel%2A> jest wywoływana.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#handlepausedjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#handlepausedjob)]
 [!code-vb[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#handlepausedjob)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Printing.PrintJobStatus>
- <xref:System.Printing.PrintSystemJobInfo>
- <xref:System.FlagsAttribute>
- <xref:System.Printing.PrintQueue>
- [Operator & (C# odwołanie)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)
- [Dokumenty w WPF](documents-in-wpf.md)
- [Przegląd drukowania](printing-overview.md)

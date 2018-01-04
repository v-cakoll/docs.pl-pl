---
title: "Jak zdiagnozować problematyczne zadanie drukowania"
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
- troubleshooting print job problems [WPF]
- print jobs [WPF], troubleshooting
- print jobs [WPF], diagnosing problems
ms.assetid: b081a170-84c6-48f9-a487-5766a8d58a82
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cd9bfb187f77f1cff344aaeabebd36aec1312e30
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-diagnose-problematic-print-job"></a>Jak zdiagnozować problematyczne zadanie drukowania
Administratorzy sieci często pola utrudnień od użytkowników o zadań drukowania, które nie wydruku lub wydrukować powoli. Bogaty zestaw właściwości zadania drukowania w [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] z [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] stanowić sposób przeprowadzania szybkiej diagnostyki zdalnego zadań drukowania.  
  
## <a name="example"></a>Przykład  
 Oto główne kroki tworzenia tego rodzaju narzędzia.  
  
1.  Zidentyfikuj zadania drukowania, które użytkownik jest strona skarżąca o. Użytkownicy często nie można tego zrobić dokładnie. Może nie wiedzieć nazwy serwerów wydruku i drukarek. Może zawierać opis lokalizacji drukarki w inną terminologię, niż zostało użyte w ustawieniu jego <xref:System.Printing.PrintQueue.Location%2A> właściwości. W związku z tym jest dobrym pomysłem jest obecnie Generowanie listy użytkownika przesłać zadania. Jeśli istnieje więcej niż jeden, komunikacji między użytkownikiem a administrator systemu wydruku można używane do punktu przyczepienia zadanie, które występują problemy. Dostępne są następujące podetapów.  
  
    1.  Uzyskaj listę wszystkich serwerów wydruku.  
  
    2.  Pętla za pośrednictwem serwerów do badania ich kolejek wydruku.  
  
    3.  W każdym przebiegu pętli serwera pętli wszystkich kolejek na serwerze do badania swoich zadań  
  
    4.  W każdym przebiegu pętli kolejki pętli jego zadania i Zbierz informacje identyfikujące te, które zostały przesłane przez wnioskujących użytkownika.  
  
2.  Jeśli zidentyfikowano problemy zadania drukowania, sprawdź odpowiednie właściwości, aby zobaczyć, co może być problem. Na przykład jest zadanie w stanie błędu lub czy drukarki obsługi kolejki przejścia do trybu offline można drukowanie zadania?  
  
 Poniższy kod jest szereg przykładowych. W pierwszym przykładzie kodu zawiera pętlę za pośrednictwem kolejek wydruku. (Krok 1c powyżej). Zmienna `myPrintQueues` jest <xref:System.Printing.PrintQueueCollection> obiektu dla bieżącego serwera wydruku.  
  
 Przykład kodu rozpoczyna się od odświeżanie bieżący obiekt kolejki wydruku z <xref:System.Printing.PrintQueue.Refresh%2A?displayProperty=nameWithType>. Dzięki temu, że właściwości obiektu przedstawiać stan drukarki fizycznej, która reprezentuje. Następnie aplikacja pobiera kolekcję zadań drukowania obecnie w kolejce wydruku przy użyciu <xref:System.Printing.PrintQueue.GetPrintJobInfoCollection%2A>.  
  
 Następnie aplikacja w pętli <xref:System.Printing.PrintSystemJobInfo> kolekcji, jak i porównuje <xref:System.Printing.PrintSystemJobInfo.Submitter%2A> właściwości z aliasem wnioskujących użytkownika. Jeśli są zgodne, aplikacja dodaje informacje identyfikacyjne o zadaniu na ciąg, który zostanie wyświetlone. ( `userName` i `jobList` zmienne są inicjowane we wcześniejszej części aplikacji.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#enumeratejobsinqueues)]
 [!code-csharp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#enumeratejobsinqueues)]
 [!code-vb[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#enumeratejobsinqueues)]  
  
 W następnym przykładzie kodu przejmuje aplikację w kroku 2. (Zobacz powyżej). Zidentyfikowano problemy zadania i aplikacja wyświetli monit o informacje, które identyfikuje go. Z tej informacji tworzy <xref:System.Printing.PrintServer>, <xref:System.Printing.PrintQueue>, i <xref:System.Printing.PrintSystemJobInfo> obiektów.  
  
 W tym momencie aplikacja zawiera rozgałęziania strukturę odpowiadający sposobów sprawdzania stanu zadania drukowania:  
  
-   Możesz przeczytać flagi z <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> właściwość, która jest typu <xref:System.Printing.PrintJobStatus>.  
  
-   Każda właściwość może odczytywać takich jak <xref:System.Printing.PrintSystemJobInfo.IsBlocked%2A> i <xref:System.Printing.PrintSystemJobInfo.IsInError%2A>.  
  
 W przykładzie pokazano obu metod, dzięki czemu użytkownik został wcześniej zostanie wyświetlony monit, aby metody i zwrócił "Y", jeśli użytkownik chce używać flag z <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> właściwości. Aby uzyskać więcej informacji o te dwie metody są wymienione poniżej. Ponadto aplikacja używa metody o nazwie **ReportQueueAndJobAvailability** raport ma dotyczyć Określa, czy w tej chwili dzień, w którym można go wydrukować zadania. Ta metoda została szczegółowo opisana w [odnajdywanie czy drukowania zadania można być drukowane na ten czas dnia](../../../../docs/framework/wpf/advanced/how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day.md).  
  
 [!code-cpp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#identifyanddiagnoseproblematicjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#identifyanddiagnoseproblematicjob)]
 [!code-vb[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#identifyanddiagnoseproblematicjob)]  
  
 Aby sprawdzić stan zadania drukowania przy użyciu flagi z <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> właściwości, sprawdź flag odpowiednie, aby zobaczyć, jeśli jest ustawiona. Standardowy sposób, aby zobaczyć, czy jeden bit jest ustawiona zestaw flagi bitów jest wykonanie operacji logicznych i przy użyciu flagi jako jeden operand i flagi co inne. Ponieważ flagą sama ma tylko jeden bit, ustawić wyniku logicznym, a jest to, że, co najwyżej tego samego bit jest ustawiony. Aby dowiedzieć się czy nie jest on, po prostu porównać wyniku logicznym i z ustawioną flagą sama. Aby uzyskać więcej informacji, zobacz <xref:System.Printing.PrintJobStatus>, [& — Operator (odwołanie w C#)](~/docs/csharp/language-reference/operators/and-operator.md), i <xref:System.FlagsAttribute>.  
  
 Dla każdego atrybutu ustawiono bit, którego kod to raporty do ekranu konsoli i czasami sugeruje sposób odpowiedzi. ( **HandlePausedJob** metodę, która jest wywoływana, gdy zadanie lub kolejki jest wstrzymana, została szczegółowo opisana poniżej.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobattributes)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobattributes)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobattributes)]  
  
 Aby sprawdzić stan zadania drukowania przy użyciu oddzielnych właściwości, po prostu przeczytaj każdej właściwości i, jeśli właściwość jest `true`, raport do ekranu konsoli i prawdopodobnie zaproponuje sposób odpowiedzi. ( **HandlePausedJob** metodę, która jest wywoływana, gdy zadanie lub kolejki jest wstrzymana, została szczegółowo opisana poniżej.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobproperties)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobproperties)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobproperties)]  
  
 **HandlePausedJob** metody umożliwia użytkownikowi aplikacji zdalnie wznawianie prac wstrzymana. Ponieważ może to być powód, dlaczego Wstrzymano kolejkę wydruku, metody rozpoczyna się od monitowanie o decyzji użytkownika o tym, czy jego wznowienie. Jeśli odpowiedź brzmi "Y", a następnie <xref:System.Printing.PrintQueue.Resume%2A?displayProperty=nameWithType> metoda jest wywoływana.  
  
 Następnie użytkownik jest monitowany decyzji o tym, jeśli zadanie sam powinien wznowione, na wypadek jest wstrzymana niezależnie od kolejki wydruku. (Porównanie <xref:System.Printing.PrintQueue.IsPaused%2A?displayProperty=nameWithType> i <xref:System.Printing.PrintSystemJobInfo.IsPaused%2A?displayProperty=nameWithType>.) Jeśli odpowiedź brzmi "Y", następnie <xref:System.Printing.PrintSystemJobInfo.Resume%2A?displayProperty=nameWithType> jest wywołana; w przeciwnym <xref:System.Printing.PrintSystemJobInfo.Cancel%2A> jest wywoływana.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#HandlePausedJob](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#handlepausedjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#HandlePausedJob](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#handlepausedjob)]
 [!code-vb[DiagnoseProblematicPrintJob#HandlePausedJob](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#handlepausedjob)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Printing.PrintJobStatus>  
 <xref:System.Printing.PrintSystemJobInfo>  
 <xref:System.FlagsAttribute>  
 <xref:System.Printing.PrintQueue>  
 [& — Operator (odwołanie w C#)](~/docs/csharp/language-reference/operators/and-operator.md)  
 [Dokumenty w WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Przegląd drukowania](../../../../docs/framework/wpf/advanced/printing-overview.md)

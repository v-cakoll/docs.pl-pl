---
title: "Jak wykryć czy zadanie drukowania może zostać zrealizowane o tej porze dnia"
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
- print queues [WPF], timing
- printers [WPF], availability
- print jobs [WPF], timing
ms.assetid: 7e9c8ec1-abf6-4b3d-b1c6-33b35d3c4063
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9ac89b8dce67c95c78a5dd46e591d84730a68346
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day"></a>Jak wykryć czy zadanie drukowania może zostać zrealizowane o tej porze dnia
Kolejki wydruku nie zawsze są dostępne przez 24 godziny na dobę. Mają one właściwości czasu rozpoczęcia i zakończenia, które można ustawić, aby były niedostępne w pewnych porach dnia. Ta funkcja może być używana na przykład zarezerwować drukarek do wyłącznego użytku niektórych działu po 17: 00. Działu musi innej kolejki drukarki niż aplikacje innych działów obsługi użycia. Czy można ustawić kolejki dla innych działów będzie dostępny od 17: 00, gdy kolejka działu favored można ustawić jako dostępne przez cały czas.  
  
 Ponadto można ustawić zadania drukowania, same do druku tylko w ramach określonego zakresu czasu.  
  
 <xref:System.Printing.PrintQueue> i <xref:System.Printing.PrintSystemJobInfo> klasy widoczne w [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] z [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] umożliwiają zdalne sprawdzania, czy danego zadania drukowania można drukować na danej kolejki w danym momencie.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie jest to przykład przedstawiający diagnozować problemy z zadaniem drukowania.  
  
 Istnieją dwa główne kroki tego rodzaju funkcji w następujący sposób.  
  
1.  Odczyt <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> i <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> właściwości <xref:System.Printing.PrintQueue> do ustalenia, czy bieżący czas jest między nimi.  
  
2.  Odczyt <xref:System.Printing.PrintSystemJobInfo.StartTimeOfDay%2A> i <xref:System.Printing.PrintSystemJobInfo.UntilTimeOfDay%2A> właściwości <xref:System.Printing.PrintSystemJobInfo> do ustalenia, czy bieżący czas jest między nimi.  
  
 Ale komplikacji wynikać z faktu, że te właściwości nie są <xref:System.DateTime> obiektów. Zamiast tego są one <xref:System.Int32> obiektów, które express godzinę jako liczbę minut od północy. Ponadto to nie jest północy w bieżącej strefy czasowej, ale o północy czasu UTC (Coordinated Universal Time).  
  
 W pierwszym przykładzie kodu przedstawiono metody statycznej **ReportQueueAndJobAvailability**, która jest przekazywana <xref:System.Printing.PrintSystemJobInfo> i wywołuje metody pomocnicze, aby określić, czy w danej chwili można drukować zadania i, jeśli nie, jeśli można drukować. Zwróć uwagę, że <xref:System.Printing.PrintQueue> nie zostanie przekazany do metody. Jest to spowodowane <xref:System.Printing.PrintSystemJobInfo> zawiera odwołanie do kolejki w jego <xref:System.Printing.PrintSystemJobInfo.HostingPrintQueue%2A> właściwości.  
  
 Podrzędny metody obejmują przeciążone **ReportAvailabilityAtThisTime** metodę, która może zająć jedną <xref:System.Printing.PrintQueue> lub <xref:System.Printing.PrintSystemJobInfo> jako parametr. Istnieje również **TimeConverter.ConvertToLocalHumanReadableTime**. Wszystkie te metody opisano poniżej.  
  
 **ReportQueueAndJobAvailability** metody rozpoczyna się przez sprawdzenie, czy kolejka lub zadanie drukowania jest niedostępny w tej chwili. Jeśli jeden z nich jest niedostępny, następnie sprawdza, czy kolejka niedostępny. Jeśli nie jest dostępna, metoda zgłasza ten fakt i czasu, gdy kolejka ponownie staną się dostępne. Następnie sprawdza zadania i jeśli jest niedostępny, raporty przy następnym span podczas gdy można go wydrukować. Na koniec metoda zgłasza najwcześniejszą czas, kiedy zadanie można drukować. Jest to po następujące dwa razy.  
  
-   Czas, kiedy kolejki wydruku obok jest dostępny.  
  
-   Czas, kiedy zadanie drukowania obok jest dostępny.  
  
 Podczas raportowania porach dnia, <xref:System.DateTime.ToShortTimeString%2A> metody jest również nazywany, ponieważ ta metoda powoduje pominięcie lat, miesiące i liczba dni korzystania z danych wyjściowych. Nie można ograniczyć dostępności kolejki wydruku lub zadania drukowania do konkretnego lat, miesięcy lub dni.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#reportqueueandjobavailability)]
 [!code-csharp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#reportqueueandjobavailability)]
 [!code-vb[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#reportqueueandjobavailability)]  
  
 Overloads dwa z **ReportAvailabilityAtThisTime** metody są identyczne z wyjątkiem przekazany do nich tylko typ <xref:System.Printing.PrintQueue> wersji znajduje się poniżej.  
  
> [!NOTE]
>  Fakt, że te metody są identyczne z wyjątkiem typu zgłasza kwestia, dlaczego próbki nie tworzy metody rodzajowej **ReportAvailabilityAtThisTime\<T >**. Przyczyną jest to, że taka metoda musi być ograniczone do klasy, która ma **StartTimeOfDay** i **UntilTimeOfDay** właściwości, które wywołuje metodę, ale metoda ogólna tylko może być ograniczone do Pojedyncza klasa i klasy tylko wspólne <xref:System.Printing.PrintQueue> i <xref:System.Printing.PrintSystemJobInfo> jest drzewa dziedziczenia <xref:System.Printing.PrintSystemObject> której nie ma takich właściwości.  
  
 **ReportAvailabilityAtThisTime** — metoda (przedstawione w poniższym przykładzie kodu) rozpoczyna się od zainicjowania <xref:System.Boolean> zmiennej wartownik `true`. Zostanie zresetowana do wartości `false`, jeśli kolejka jest niedostępna.  
  
 Następnie metoda sprawdza, czy początek, a "do momentu" czasy są identyczne. Jeśli są one kolejki zawsze jest dostępna, więc metoda zwraca `true`.  
  
 Jeśli kolejka nie jest dostępna przez cały czas, metoda używa statycznych <xref:System.DateTime.UtcNow%2A> właściwości, aby uzyskać bieżącą godzinę jako <xref:System.DateTime> obiektu. (Firma Microsoft nie muszą czasu lokalnego, ponieważ <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> i <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> właściwości są w formacie UTC.)  
  
 Te dwie właściwości nie są jednak <xref:System.DateTime> obiektów. Są one <xref:System.Int32>s wyrażanie czas jako liczba minut po UTC północy. A więc musimy przekonwertować naszych <xref:System.DateTime> obiektu minut po północy. Po zakończeniu tej operacji metoda sprawdza po prostu do sprawdzenia, czy "teraz" jest między kolejki rozpoczęcia i "godziny, ustawia wartownik na wartość false, jeśli"teraz"nie jest między dwiema wartościami godziny i zwraca wartownik do".  
  
 [!code-cpp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#printqueuestartuntil)]
 [!code-csharp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#printqueuestartuntil)]
 [!code-vb[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#printqueuestartuntil)]  
  
 **TimeConverter.ConvertToLocalHumanReadableTime** — metoda (przedstawione w poniższym przykładzie kodu) nie używa żadnych metod wprowadzone w systemie [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)], więc dyskusji jest krótki. Metoda ma zadań podwójna konwersja: musi podjąć całkowitą wyrażanie minut po północy i przekonwertować go na czas zrozumiałą dla użytkownika i należy przekonwertować to na czas lokalny. Jest to osiągane przez utworzenie <xref:System.DateTime> obiekt, który ma ustawioną wartość północy czasu UTC, a następnie go używa <xref:System.DateTime.AddMinutes%2A> metody w celu dodania minut, które zostały przekazane do metody. To polecenie zwróci nowy <xref:System.DateTime> wyrażanie oryginalnego czas, który został przekazany do metody. <xref:System.DateTime.ToLocalTime%2A> Metoda następnie konwertuje to na czas lokalny.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#timeconverter)]
 [!code-csharp[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#timeconverter)]
 [!code-vb[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#timeconverter)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.DateTime>  
 <xref:System.Printing.PrintSystemJobInfo>  
 <xref:System.Printing.PrintQueue>  
 [Dokumentów na platformie WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Omówienie drukowania](../../../../docs/framework/wpf/advanced/printing-overview.md)

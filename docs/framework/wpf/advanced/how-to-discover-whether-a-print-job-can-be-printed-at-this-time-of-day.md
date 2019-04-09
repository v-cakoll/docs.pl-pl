---
title: 'Instrukcje: Wykrywanie, czy zadanie drukowania może zostać zrealizowane o tej porze dnia'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print queues [WPF], timing
- printers [WPF], availability
- print jobs [WPF], timing
ms.assetid: 7e9c8ec1-abf6-4b3d-b1c6-33b35d3c4063
ms.openlocfilehash: dab836af8ba3d177719d910142cd93f8f6de0002
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099862"
---
# <a name="how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day"></a>Instrukcje: Wykrywanie, czy zadanie drukowania może zostać zrealizowane o tej porze dnia
Kolejki wydruku nie zawsze są dostępne 24 godziny na dobę. Mają one właściwości czasu rozpoczęcia i zakończenia, które można ustawić, aby były niedostępne w pewnych porach dnia. Ta funkcja może być używana na przykład, aby zarezerwować drukarki do wyłącznego użytku określony dział po 17: 00. Takim wydziale musi innej kolejki drukarki niż innych działów obsługi użycia. Kolejka dla innych działów będzie miał ustawienie będzie niedostępna po 17: 00, podczas gdy kolejka dla działu favored mógł zostać ustawiony jako dostępny przez cały czas.  
  
 Ponadto można ustawić zadania drukowania, samodzielnie do druku tylko w obrębie określonego zakresu czasu.  
  
 <xref:System.Printing.PrintQueue> i <xref:System.Printing.PrintSystemJobInfo> klasy widoczne w [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] programu Microsoft .NET Framework zapewniają środki do zdalnego sprawdzanie, czy dane zadanie drukowania może drukować na danej kolejki w danej chwili.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono przykład diagnozować problemy z zadaniem drukowania.  
  
 Istnieją dwa główne kroki dla tego rodzaju funkcji w następujący sposób.  
  
1.  Odczyt <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> i <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> właściwości <xref:System.Printing.PrintQueue> do ustalenia, czy bieżący czas jest między nimi.  
  
2.  Odczyt <xref:System.Printing.PrintSystemJobInfo.StartTimeOfDay%2A> i <xref:System.Printing.PrintSystemJobInfo.UntilTimeOfDay%2A> właściwości <xref:System.Printing.PrintSystemJobInfo> do ustalenia, czy bieżący czas jest między nimi.  
  
 Ale komplikacji wynikać z faktu, że te właściwości są <xref:System.DateTime> obiektów. Zamiast tego są one <xref:System.Int32> obiektów, które express godzinę jako liczbę minut, które upłynęły od północy. Ponadto to nie jest o północy w bieżącej strefie czasowej, ale o północy czasu UTC (Coordinated Universal Time).  
  
 Pierwszy przykład kodu przedstawia metody statycznej **ReportQueueAndJobAvailability**, która jest przekazywana <xref:System.Printing.PrintSystemJobInfo> i wywołuje metody pomocnika, aby ustalić, czy zadania można wydrukować w danym momencie i, jeśli nie, kiedy można wydrukować. Należy zauważyć, że <xref:System.Printing.PrintQueue> nie zostanie przekazany do metody. Jest to spowodowane <xref:System.Printing.PrintSystemJobInfo> zawiera odwołanie do kolejki w jego <xref:System.Printing.PrintSystemJobInfo.HostingPrintQueue%2A> właściwości.  
  
 Podrzędny metody obejmują przeciążone **ReportAvailabilityAtThisTime** metodę, która może zająć jedną <xref:System.Printing.PrintQueue> lub <xref:System.Printing.PrintSystemJobInfo> jako parametr. Istnieje również **TimeConverter.ConvertToLocalHumanReadableTime**. Wszystkie te metody zostały podane poniżej.  
  
 **ReportQueueAndJobAvailability** metoda rozpoczyna się od sprawdzenia, aby sprawdzić, czy kolejka lub zadanie drukowania jest niedostępny w tej chwili. Jeśli którąś z tych funkcji jest niedostępny, następnie sprawdza, czy sprawdzić, czy kolejka niedostępny. Jeśli nie jest dostępna, metoda zgłasza, ten fakt i czasu, gdy kolejka stanie się ponownie dostępne. Następnie sprawdza zadania i jeśli jest niedostępna, raportuje następnym razem gdy span ją podczas drukowania. Na koniec metody raporty Najwcześniejsza godzina, kiedy zadanie można wydrukować. Jest to po następujące dwa razy.  
  
-   Czas, kiedy kolejki wydruku obok jest dostępny.  
  
-   Czas, kiedy zadanie drukowania obok jest dostępny.  
  
 Podczas zgłaszania porach dnia, <xref:System.DateTime.ToShortTimeString%2A> metoda również jest wywoływana, ponieważ ta metoda powoduje pominięcie lat, miesięcy i dni z danych wyjściowych. Nie można ograniczyć dostępności kolejki wydruku lub zadania drukowania do konkretnego lat, miesięcy i dni.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#reportqueueandjobavailability)]
 [!code-csharp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#reportqueueandjobavailability)]
 [!code-vb[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#reportqueueandjobavailability)]  
  
 Dwa przeciążenia **ReportAvailabilityAtThisTime** metody są identyczne, z wyjątkiem typu przekazany do nich tylko <xref:System.Printing.PrintQueue> wersji znajduje się poniżej.  
  
> [!NOTE]
>  Fakt, że te metody są identyczne, z wyjątkiem typu wywołuje pytanie, dlaczego przykład nie powoduje utworzenia metody ogólnej **ReportAvailabilityAtThisTime\<T >**. Przyczyną jest to, że taka metoda musi zostać ograniczone do klasy, która ma **StartTimeOfDay** i **UntilTimeOfDay** właściwości, które wywołuje metodę, ale metody ogólnej tylko można ograniczyć do klasy i jedyna klasa wspólna dla obu <xref:System.Printing.PrintQueue> i <xref:System.Printing.PrintSystemJobInfo> jest drzewo dziedziczenia <xref:System.Printing.PrintSystemObject> którego nie ma takiego właściwości.  
  
 **ReportAvailabilityAtThisTime** — metoda (przedstawiony w poniższym przykładzie kodu), który rozpoczyna się od inicjowania <xref:System.Boolean> zmienną wartownik `true`. Urządzenie zostanie zresetowane do `false`, jeśli kolejka jest niedostępna.  
  
 Następnie metoda sprawdza, czy początek "dopiero wtedy, gdy" razy są identyczne. Jeśli są one kolejki są zawsze dostępne, dlatego metoda ta zwraca `true`.  
  
 Jeśli kolejka nie jest dostępny przez cały czas, metoda jest używana statyczna <xref:System.DateTime.UtcNow%2A> właściwości, aby uzyskać bieżącą godzinę jako <xref:System.DateTime> obiektu. (Nie potrzebujemy czasu lokalnego ponieważ <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> i <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> właściwości znajdują się w czasie UTC.)  
  
 Te dwie właściwości nie są jednak <xref:System.DateTime> obiektów. Są one <xref:System.Int32>s może przedstawiać czas jako liczba minut po UTC północy. Dlatego musimy przekonwertować naszych <xref:System.DateTime> obiektu minut po północy. Gdy zostanie to zrobione, metoda po prostu sprawdza, aby zobaczyć, czy "teraz" jest od początku kolejki i "godziny, zestawy wartownik na wartość false, jeśli"teraz"nie jest między dwiema wartościami godziny i zwraca wartownik do".  
  
 [!code-cpp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#printqueuestartuntil)]
 [!code-csharp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#printqueuestartuntil)]
 [!code-vb[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#printqueuestartuntil)]  
  
 **TimeConverter.ConvertToLocalHumanReadableTime** — metoda (przedstawiony w poniższym przykładzie kodu) nie używa żadnych metod wprowadzone w programie Microsoft .NET Framework, więc dyskusję jest krótki. Metoda ma zadanie podwójna konwersja: musi podjąć całkowitą wyrażanie minut po północy i przekonwertować go na czas czytelny dla człowieka i musi przekonwertować to konto na czas lokalny. Jest to osiągane przez utworzenie <xref:System.DateTime> obiektu, który jest ustawiony na północy czasu UTC, a następnie go używa <xref:System.DateTime.AddMinutes%2A> metody w celu dodania minut, które zostały przekazane do metody. Spowoduje to zwrócenie nowego <xref:System.DateTime> wyrażanie pierwotny czas, który został przekazany do metody. <xref:System.DateTime.ToLocalTime%2A> Metoda następnie konwertuje to na czas lokalny.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#timeconverter)]
 [!code-csharp[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#timeconverter)]
 [!code-vb[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#timeconverter)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.DateTime>
- <xref:System.Printing.PrintSystemJobInfo>
- <xref:System.Printing.PrintQueue>
- [Dokumenty w WPF](documents-in-wpf.md)
- [Przegląd Drukowanie](printing-overview.md)

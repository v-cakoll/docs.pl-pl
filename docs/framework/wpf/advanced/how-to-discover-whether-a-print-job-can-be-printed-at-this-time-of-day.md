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
ms.openlocfilehash: 859dc75169e443d07361951692a428507886fa2e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947810"
---
# <a name="how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day"></a>Instrukcje: Wykrywanie, czy zadanie drukowania może zostać zrealizowane o tej porze dnia
Kolejki wydruku nie są zawsze dostępne przez 24 godziny dziennie. Mają właściwości czasu rozpoczęcia i zakończenia, które można ustawić w taki sposób, aby były niedostępne o określonych porach dnia. Ta funkcja może być używana na przykład w celu zarezerwowania drukarki do wyłącznego użycia pewnego działu po 5 P.M.. Ten dział będzie miał inną kolejkę obsługującą drukarki niż inne firmy. Kolejka dla innych działów zostanie ustawiona jako niedostępna po 5 godzinach, podczas gdy kolejka dla danego działu ma być dostępna przez cały czas.  
  
 Ponadto zadania drukowania można ustawić tak, aby można było drukować tylko w określonym zakresie czasu.  
  
 Klasy <xref:System.Printing.PrintQueue> i<xref:System.Printing.PrintSystemJobInfo> udostępniane w interfejsach API Microsoft .NET Framework umożliwiają zdalne sprawdzanie, czy dane zadanie drukowania można wydrukować w danej kolejce w bieżącej chwili.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład to przykład, który może zdiagnozować problemy z zadaniem drukowania.  
  
 Istnieją dwa główne kroki dla tego rodzaju funkcji w następujący sposób.  
  
1. Zapoznaj się <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> z właściwościami <xref:System.Printing.PrintQueue>i, aby określić, czy bieżący czas jest między nimi. <xref:System.Printing.PrintQueue.StartTimeOfDay%2A>  
  
2. Zapoznaj się <xref:System.Printing.PrintSystemJobInfo.UntilTimeOfDay%2A> z właściwościami <xref:System.Printing.PrintSystemJobInfo>i, aby określić, czy bieżący czas jest między nimi. <xref:System.Printing.PrintSystemJobInfo.StartTimeOfDay%2A>  
  
 Jednak komplikacje wynikają z faktu, że te <xref:System.DateTime> właściwości nie są obiektami. Zamiast tego są <xref:System.Int32> to obiekty, które wyrażają czas dnia jako liczbę minut od północy. Ponadto nie jest to północ w bieżącej strefie czasowej, ale północy czasu UTC (uniwersalny czas koordynowany).  
  
 Pierwszy przykład kodu przedstawia metodę statyczną **ReportQueueAndJobAvailability**, która jest przenoszona <xref:System.Printing.PrintSystemJobInfo> i wywołuje metody pomocnika, aby określić, czy zadanie może drukować w bieżącym czasie, a jeśli nie, kiedy może drukować. Zwróć uwagę, <xref:System.Printing.PrintQueue> że nie jest przekazywany do metody. Wynika to z faktu, że <xref:System.Printing.PrintSystemJobInfo> zawiera odwołanie do kolejki <xref:System.Printing.PrintSystemJobInfo.HostingPrintQueue%2A> we właściwości.  
  
 Metody podrzędne zawierają przeciążoną metodę **ReportAvailabilityAtThisTime** , która może przyjmować <xref:System.Printing.PrintQueue> albo albo <xref:System.Printing.PrintSystemJobInfo> jako parametr. Istnieje również element **TimeConverter. ConvertToLocalHumanReadableTime**. Wszystkie te metody zostały omówione poniżej.  
  
 Metoda **ReportQueueAndJobAvailability** rozpoczyna się od sprawdzenia, czy kolejka lub zadanie drukowania jest w tej chwili niedostępne. Jeśli jedna z nich jest niedostępna, sprawdza, czy kolejka jest niedostępna. Jeśli nie jest dostępny, metoda zgłasza ten fakt i czas, kiedy kolejka znów stanie się dostępna. Następnie sprawdza to zadanie i jeśli jest niedostępne, będzie zgłaszać następny przedział czasu, gdy będzie mógł drukować. Na koniec Metoda raportuje najwcześniejszą godzinę, kiedy zadanie może drukować. Jest to późniejsze dwa razy.  
  
- Czas, w którym kolejka wydruku jest dalej dostępna.  
  
- Godzina, o której zadanie drukowania jest dalej dostępne.  
  
 Przy raportowaniu czasów dziennie <xref:System.DateTime.ToShortTimeString%2A> Metoda jest również wywoływana, ponieważ ta metoda pomija lata, miesiące i dni z danych wyjściowych. Nie można ograniczyć dostępności kolejki wydruku lub zadania drukowania do określonych lat, miesięcy i dni.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#reportqueueandjobavailability)]
 [!code-csharp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#reportqueueandjobavailability)]
 [!code-vb[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#reportqueueandjobavailability)]  
  
 Dwa przeciążenia metody **ReportAvailabilityAtThisTime** są identyczne, z wyjątkiem typu przekazywanego do nich, dlatego tylko <xref:System.Printing.PrintQueue> wersja jest przedstawiona poniżej.  
  
> [!NOTE]
> Fakt, że metody są identyczne z wyjątkiem typu, podnosi pytanie dlaczego przykład nie tworzy metody generycznej **\<ReportAvailabilityAtThisTime T >** . Powodem jest to, że taka metoda musi być ograniczona do klasy, która ma właściwości **StartTimeOfDay** i **UntilTimeOfDay** , które wywołuje metoda, ale metoda generyczna może być ograniczona tylko do jednej klasy, a jedyna klasa wspólna dla obu tych elementów <xref:System.Printing.PrintQueue> i<xref:System.Printing.PrintSystemJobInfo>wdrzewie dziedziczenianie<xref:System.Printing.PrintSystemObject> ma takich właściwości.  
  
 Metoda **ReportAvailabilityAtThisTime** (przedstawiona w poniższym przykładzie kodu) rozpoczyna się od inicjowania <xref:System.Boolean> zmiennej wskaźnikowej `true`do. Zostanie ona zresetowana do `false`, jeśli kolejka nie jest dostępna.  
  
 Następnie metoda sprawdza, czy godziny rozpoczęcia i "until" są identyczne. Jeśli są, kolejka jest zawsze dostępna, więc metoda zwraca `true`.  
  
 Jeśli kolejka nie jest dostępna przez cały czas, metoda używa właściwości statycznej <xref:System.DateTime.UtcNow%2A> do pobrania bieżącego czasu <xref:System.DateTime> jako obiektu. (Czas lokalny nie jest wymagany, <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> ponieważ właściwości i <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> są same w czasie UTC).  
  
 Jednak te dwie właściwości nie <xref:System.DateTime> są obiektami. Są <xref:System.Int32>one wyrażane jako liczba minut po godzinie-czasu UTC. Dlatego musimy przekonwertować <xref:System.DateTime> obiekt na kilka minut — po północy. Gdy to zrobisz, metoda po prostu sprawdza, czy "teraz" jest między początkiem kolejki i "do" czasu, ustawia wskaźnik na wartość false, jeśli "teraz" nie jest między dwa razy i zwraca wskaźnik kontrolny.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#printqueuestartuntil)]
 [!code-csharp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#printqueuestartuntil)]
 [!code-vb[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#printqueuestartuntil)]  
  
 Metoda **TimeConverter. ConvertToLocalHumanReadableTime** (przedstawiona w poniższym przykładzie kodu) nie używa żadnych metod wprowadzonych w Microsoft .NET Framework, więc dyskusja jest krótka. Metoda ma podwójne zadanie konwersji: musi przyjmować liczbę całkowitą wyrażaną w minutach — po północy i przekonwertuj ją na czas do odczytu przez człowieka i musi ją przekonwertować na czas lokalny. Osiąga to, tworząc <xref:System.DateTime> najpierw obiekt, który jest ustawiony na północ czasu UTC, a następnie <xref:System.DateTime.AddMinutes%2A> używa metody, aby dodać minuty, które zostały przesłane do metody. Spowoduje to zwrócenie nowego <xref:System.DateTime> , wyjściowego czasu, który został przekazano do metody. Metoda <xref:System.DateTime.ToLocalTime%2A> następnie konwertuje tę wartość na czas lokalny.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#timeconverter)]
 [!code-csharp[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#timeconverter)]
 [!code-vb[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#timeconverter)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.DateTime>
- <xref:System.Printing.PrintSystemJobInfo>
- <xref:System.Printing.PrintQueue>
- [Dokumenty w WPF](documents-in-wpf.md)
- [Przegląd drukowania](printing-overview.md)

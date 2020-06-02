---
title: 'Porady: implementowanie dostawcy'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- observer design pattern [.NET Framework], implementing providers
- providers [.NET Framework], in observer design pattern
- observables [.NET Framework], in observer design pattern
ms.assetid: 790b5d8b-d546-40a6-beeb-151b574e5ee5
ms.openlocfilehash: 4f8a213c0df3ef3c633106b7249a4947fe77c0d2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280026"
---
# <a name="how-to-implement-a-provider"></a>Porady: implementowanie dostawcy
Wzorzec projektowy obserwatora wymaga podziału między dostawcą, który monitoruje dane i wysyła powiadomienia oraz co najmniej jednego obserwatora, który odbiera powiadomienia (wywołania zwrotne) od dostawcy. W tym temacie omówiono sposób tworzenia dostawcy. Pokrewny temat, [jak: implementowanie obserwatora](how-to-implement-an-observer.md), omawia sposób tworzenia obserwatora.  
  
### <a name="to-create-a-provider"></a>Aby utworzyć dostawcę  
  
1. Zdefiniuj dane, które dostawca jest odpowiedzialny za wysyłanie do obserwatorów. Mimo że dostawca i dane wysyłane do obserwatorów mogą być pojedynczym typem, są one ogólnie reprezentowane przez różne typy. Na przykład w aplikacji do monitorowania temperatury `Temperature` Struktura definiuje dane, które dostawca (reprezentowany przez `TemperatureMonitor` klasę zdefiniowaną w następnym kroku) monitoruje i do których obserwatorzy subskrybują.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/data.cs#1)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/data.vb#1)]  
  
2. Zdefiniuj dostawcę danych, który jest typem, który implementuje <xref:System.IObservable%601?displayProperty=nameWithType> interfejs. Argument typu ogólnego dostawcy jest typem wysyłanym przez dostawcę do obserwatorów. W poniższym przykładzie zdefiniowano `TemperatureMonitor` klasę, która jest zbudowaną <xref:System.IObservable%601?displayProperty=nameWithType> implementacją z argumentem typu ogólnego `Temperature` .  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#2)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#2)]  
  
3. Określ, w jaki sposób dostawca będzie przechowywać odwołania do obserwatorów, tak aby każdy obserwator mógł zostać powiadomiony, gdy będzie to konieczne. Najczęściej w <xref:System.Collections.Generic.List%601> tym celu jest używany obiekt kolekcji, taki jak obiekt generyczny. W poniższym przykładzie zdefiniowano <xref:System.Collections.Generic.List%601> obiekt prywatny, który jest skonkretyzowany w `TemperatureMonitor` konstruktorze klasy.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#3)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#3)]  
  
4. Zdefiniuj <xref:System.IDisposable> implementację, którą dostawca może zwrócić do subskrybentów, tak aby mogli oni zrezygnować z otrzymywania powiadomień w dowolnym momencie. W poniższym przykładzie zdefiniowano klasę zagnieżdżoną `Unsubscriber` , która przekazuje odwołanie do kolekcji Subskrybenci i subskrybentowi podczas tworzenia wystąpienia klasy. Ten kod umożliwia subskrybentowi wywołanie implementacji obiektu, <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> Aby usunąć siebie z kolekcji Subskrybenci.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#4)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#4)]  
  
5. Zaimplementuj <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> metodę. Metoda jest przenoszona odwołanie do <xref:System.IObserver%601?displayProperty=nameWithType> interfejsu i powinna być przechowywana w obiekcie przeznaczonym do tego celu w kroku 3. Metoda powinna następnie zwrócić <xref:System.IDisposable> implementację opracowaną w kroku 4. Poniższy przykład pokazuje implementację <xref:System.IObservable%601.Subscribe%2A> metody w `TemperatureMonitor` klasie.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#5)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#5)]  
  
6. Powiadamiaj obserwatorów odpowiednio przez wywołanie ich <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType> <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType> implementacji,, i <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> . W niektórych przypadkach dostawca może nie wywołać <xref:System.IObserver%601.OnError%2A> metody w przypadku wystąpienia błędu. Na przykład Poniższa `GetTemperature` Metoda symuluje monitor, który odczytuje dane temperatury co pięć sekund i powiadamia obserwatorów o zmianie temperatury przez co najmniej dziesiąty stopień od momentu ostatniego odczytu. Jeśli urządzenie nie zgłosi temperatury (czyli jeśli jej wartość jest równa null), dostawca powiadamia obserwatorów o ukończeniu transmisji. Należy zauważyć, że oprócz wywoływania metody każdego obserwatora <xref:System.IObserver%601.OnCompleted%2A> `GetTemperature` Metoda czyści <xref:System.Collections.Generic.List%601> kolekcję. W takim przypadku dostawca nie wykonuje wywołań do <xref:System.IObserver%601.OnError%2A> metody jej obserwatorów.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#6)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#6)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera pełen kod źródłowy służący do definiowania <xref:System.IObservable%601> implementacji dla aplikacji monitorującej temperaturę. Obejmuje ona `Temperature` strukturę, czyli dane wysyłane do obserwatorów oraz `TemperatureMonitor` klasę, która jest <xref:System.IObservable%601> implementacją.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#7)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#7)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IObservable%601>
- [Wzorzec projektowy obserwatora](observer-design-pattern.md)
- [Instrukcje: implementowanie obserwatora](how-to-implement-an-observer.md)
- [Wzorzec projektowy obserwatora — Najlepsze praktyki](observer-design-pattern-best-practices.md)

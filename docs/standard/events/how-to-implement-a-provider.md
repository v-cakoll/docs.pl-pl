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
ms.openlocfilehash: f5bb3cda0caa39ba3fd094b80e0b769a4bfc1f85
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141555"
---
# <a name="how-to-implement-a-provider"></a>Porady: implementowanie dostawcy
Wzorzec projektowy obserwatora wymaga podziału między dostawcą, który monitoruje dane i wysyła powiadomienia oraz co najmniej jednego obserwatora, który odbiera powiadomienia (wywołania zwrotne) od dostawcy. W tym temacie omówiono sposób tworzenia dostawcy. Pokrewny temat, [jak: implementowanie obserwatora](../../../docs/standard/events/how-to-implement-an-observer.md), omawia sposób tworzenia obserwatora.  
  
### <a name="to-create-a-provider"></a>Aby utworzyć dostawcę  
  
1. Zdefiniuj dane, które dostawca jest odpowiedzialny za wysyłanie do obserwatorów. Mimo że dostawca i dane wysyłane do obserwatorów mogą być pojedynczym typem, są one ogólnie reprezentowane przez różne typy. Na przykład w aplikacji do monitorowania temperatury struktura `Temperature` definiuje dane, które dostawca (który jest reprezentowany przez klasę `TemperatureMonitor`ą zdefiniowaną w następnym kroku) Monitorzy i do których zasubskrybuje obserwatorów.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/data.cs#1)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/data.vb#1)]  
  
2. Zdefiniuj dostawcę danych, który jest typem, który implementuje interfejs <xref:System.IObservable%601?displayProperty=nameWithType>. Argument typu ogólnego dostawcy jest typem wysyłanym przez dostawcę do obserwatorów. W poniższym przykładzie zdefiniowano klasę `TemperatureMonitor`, która jest skonstruowaną <xref:System.IObservable%601?displayProperty=nameWithType> implementacją z argumentem typu ogólnego `Temperature`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#2)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#2)]  
  
3. Określ, w jaki sposób dostawca będzie przechowywać odwołania do obserwatorów, tak aby każdy obserwator mógł zostać powiadomiony, gdy będzie to konieczne. Najczęściej w tym celu jest używany obiekt kolekcji, taki jak ogólny obiekt <xref:System.Collections.Generic.List%601>. Poniższy przykład definiuje prywatny obiekt <xref:System.Collections.Generic.List%601>, którego wystąpienie jest tworzone w konstruktorze klasy `TemperatureMonitor`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#3)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#3)]  
  
4. Zdefiniuj implementację <xref:System.IDisposable>, którą dostawca może zwrócić do subskrybentów, aby mogli przestać otrzymywać powiadomienia w dowolnym momencie. W poniższym przykładzie zdefiniowano zagnieżdżoną klasę `Unsubscriber`, która przekazuje odwołanie do kolekcji Subskrybenci i subskrybentowi podczas tworzenia wystąpienia klasy. Ten kod umożliwia subskrybentowi wywołanie implementacji <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> obiektu, aby usunąć siebie z kolekcji Subskrybenci.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#4)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#4)]  
  
5. Zaimplementuj metodę <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType>. Metoda jest przenoszona do interfejsu <xref:System.IObserver%601?displayProperty=nameWithType> i powinna być przechowywana w obiekcie przeznaczonym do tego celu w kroku 3. Metoda powinna następnie zwracać implementację <xref:System.IDisposable> opracowaną w kroku 4. W poniższym przykładzie przedstawiono implementację metody <xref:System.IObservable%601.Subscribe%2A> w klasie `TemperatureMonitor`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#5)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#5)]  
  
6. Powiadamiaj obserwatorów odpowiednio przez wywołanie ich <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>i implementacji <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>. W niektórych przypadkach dostawca może nie wywołać metody <xref:System.IObserver%601.OnError%2A> w przypadku wystąpienia błędu. Na przykład Poniższa metoda `GetTemperature` symuluje monitor, który odczytuje dane temperatury co pięć sekund i powiadamia obserwatorów o zmianie temperatury o co najmniej dziesiąty stopień od czasu ostatniego odczytu. Jeśli urządzenie nie zgłosi temperatury (czyli jeśli jej wartość jest równa null), dostawca powiadamia obserwatorów o ukończeniu transmisji. Należy zauważyć, że oprócz wywoływania metody <xref:System.IObserver%601.OnCompleted%2A> każdego obserwatora Metoda `GetTemperature` czyści kolekcję <xref:System.Collections.Generic.List%601>. W takim przypadku dostawca nie wykonuje wywołań do metody <xref:System.IObserver%601.OnError%2A> jej obserwatorów.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#6)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#6)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera pełen kod źródłowy służący do definiowania implementacji <xref:System.IObservable%601> dla aplikacji monitorującej temperaturę. Zawiera ona strukturę `Temperature`, czyli dane wysyłane do obserwatorów oraz klasę `TemperatureMonitor`, która jest implementacją <xref:System.IObservable%601>.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#7)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#7)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IObservable%601>
- [Wzorzec projektowy obserwatora](../../../docs/standard/events/observer-design-pattern.md)
- [Instrukcje: Implementowanie obserwatora](../../../docs/standard/events/how-to-implement-an-observer.md)
- [Wzorzec projektowy obserwatora — najlepsze rozwiązania](../../../docs/standard/events/observer-design-pattern-best-practices.md)

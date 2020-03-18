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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141555"
---
# <a name="how-to-implement-a-provider"></a>Porady: implementowanie dostawcy
Wzorzec projektowania obserwatora wymaga podziału między dostawcą, który monitoruje dane i wysyła powiadomienia, a jednym lub większą liczbą obserwatorów, którzy otrzymują powiadomienia (wywołania wywołania wstecznego) od dostawcy. W tym temacie omówiono sposób tworzenia dostawcy. Temat pokrewny, [Jak: Implementować obserwatora](../../../docs/standard/events/how-to-implement-an-observer.md), omawia sposób tworzenia obserwatora.  
  
### <a name="to-create-a-provider"></a>Aby utworzyć dostawcę  
  
1. Zdefiniuj dane, które dostawca jest odpowiedzialny za wysyłanie do obserwatorów. Mimo że dostawca i dane, które wysyła do obserwatorów może być jeden typ, są one zazwyczaj reprezentowane przez różne typy. Na przykład w aplikacji do `Temperature` monitorowania temperatury struktura definiuje dane, które dostawca `TemperatureMonitor` (który jest reprezentowany przez klasę zdefiniowaną w następnym kroku) monitoruje i do których obserwatorzy subskrybują.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/data.cs#1)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/data.vb#1)]  
  
2. Zdefiniuj dostawcę danych, który <xref:System.IObservable%601?displayProperty=nameWithType> jest typem, który implementuje interfejs. Argument typu ogólnego dostawcy jest typem, który dostawca wysyła do obserwatorów. Poniższy przykład definiuje `TemperatureMonitor` klasę, która jest <xref:System.IObservable%601?displayProperty=nameWithType> skonstruowaną implementacją z argumentem typu ogólnego . `Temperature`  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#2)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#2)]  
  
3. Określ, w jaki sposób dostawca będzie przechowywać odwołania do obserwatorów, aby każdy obserwator mógł o trzymywać powiadomienia w razie potrzeby. Najczęściej obiekt kolekcji, takich jak <xref:System.Collections.Generic.List%601> obiekt ogólny jest używany do tego celu. W poniższym przykładzie <xref:System.Collections.Generic.List%601> definiuje obiekt prywatny, który `TemperatureMonitor` jest tworzony w konstruktorze klasy.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#3)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#3)]  
  
4. Zdefiniuj <xref:System.IDisposable> implementację, którą dostawca może powrócić do subskrybentów, aby mogli przestać otrzymywać powiadomienia w dowolnym momencie. W poniższym przykładzie definiuje `Unsubscriber` zagnieżdżonych klasy, która jest przekazywana odwołanie do kolekcji subskrybentów i subskrybenta, gdy klasa jest tworzone. Ten kod umożliwia subskrybentowi wywołanie <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementacji obiektu, aby usunąć się z kolekcji subskrybentów.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#4)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#4)]  
  
5. Zaimplementuj <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> metodę. Metoda jest przekazywana odwołanie <xref:System.IObserver%601?displayProperty=nameWithType> do interfejsu i powinny być przechowywane w obiekcie przeznaczonym do tego celu w kroku 3. Metoda powinna następnie <xref:System.IDisposable> zwrócić implementację opracowaną w kroku 4. W poniższym przykładzie przedstawiono <xref:System.IObservable%601.Subscribe%2A> implementację metody w `TemperatureMonitor` klasie.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#5)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#5)]  
  
6. Powiadamiaj obserwatorów, stosownie do potrzeb, dzwoniąc do ich <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>i <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementacji. W niektórych przypadkach dostawca może <xref:System.IObserver%601.OnError%2A> nie wywołać metody, gdy wystąpi błąd. Na przykład następująca `GetTemperature` metoda symuluje monitor, który odczytuje dane temperatury co pięć sekund i powiadamia obserwatorów, jeśli temperatura zmieniła się o co najmniej 0,1 stopnia od poprzedniego odczytu. Jeśli urządzenie nie zgłasza temperatury (oznacza to, że jego wartość jest null), dostawca powiadamia obserwatorów, że transmisja została zakończona. Należy zauważyć, że oprócz wywoływania <xref:System.IObserver%601.OnCompleted%2A> metody `GetTemperature` każdego obserwatora <xref:System.Collections.Generic.List%601> metoda czyści kolekcję. W takim przypadku dostawca nie wywołuje <xref:System.IObserver%601.OnError%2A> metody swoich obserwatorów.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#6)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#6)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera kompletny kod źródłowy do definiowania <xref:System.IObservable%601> implementacji dla aplikacji do monitorowania temperatury. Zawiera strukturę, `Temperature` która jest dane wysyłane do `TemperatureMonitor` obserwatorów i <xref:System.IObservable%601> klasy, która jest implementacją.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#7)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#7)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IObservable%601>
- [Wzorzec projektowy obserwatora](../../../docs/standard/events/observer-design-pattern.md)
- [Instrukcje: Implementowanie obserwatora](../../../docs/standard/events/how-to-implement-an-observer.md)
- [Wzorzec projektowy obserwatora — Najlepsze praktyki](../../../docs/standard/events/observer-design-pattern-best-practices.md)

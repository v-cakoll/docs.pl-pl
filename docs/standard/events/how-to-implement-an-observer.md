---
title: 'Porady: implementowanie obserwatora'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- observers [.NET Framework], observer design pattern
- observer design pattern [.NET Framework], implementing observers
ms.assetid: 8ecfa9f5-b500-473d-bcf0-5652ffb1e53d
ms.openlocfilehash: e6aba4d85e502563291478640927bd0f234736a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139308"
---
# <a name="how-to-implement-an-observer"></a>Porady: implementowanie obserwatora
Wzorzec projektowania obserwatora wymaga podziału między obserwatora, który rejestruje powiadomienia, a dostawcą, który monitoruje dane i wysyła powiadomienia do jednego lub więcej obserwatorów. W tym temacie omówiono sposób tworzenia obserwatora. Temat pokrewny, [Jak: Implementowanie dostawcy](../../../docs/standard/events/how-to-implement-a-provider.md), omówiono sposób tworzenia dostawcy.  
  
### <a name="to-create-an-observer"></a>Aby utworzyć obserwatora  
  
1. Zdefiniuj obserwatora, który <xref:System.IObserver%601?displayProperty=nameWithType> jest typem, który implementuje interfejs. Na przykład poniższy kod definiuje typ `TemperatureReporter` o nazwie, który jest skonstruowaną <xref:System.IObserver%601?displayProperty=nameWithType> implementacją z argumentem typu ogólnego . `Temperature`  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2. Jeśli obserwator może przestać odbierać powiadomienia, <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> zanim dostawca wywołuje jego implementacji, należy zdefiniować zmienną prywatną, która będzie przechowywać <xref:System.IDisposable> implementacji zwrócone przez <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> metodę dostawcy. Należy również zdefiniować metodę subskrypcji, która <xref:System.IObservable%601.Subscribe%2A> wywołuje metodę dostawcy <xref:System.IDisposable> i przechowuje zwrócony obiekt. Na przykład poniższy kod definiuje zmienną `unsubscriber` prywatną `Subscribe` o nazwie i definiuje <xref:System.IObservable%601.Subscribe%2A> metodę, która wywołuje metodę `unsubscriber` dostawcy i przypisuje zwrócony obiekt do zmiennej.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3. Zdefiniuj metodę, która umożliwia obserwatorowi zaprzestanie <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> odbierania powiadomień, zanim dostawca wywołuje jego implementację, jeśli ta funkcja jest wymagana. Poniższy przykład definiuje `Unsubscribe` metodę.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4. Podaj implementacje trzech metod <xref:System.IObserver%601> zdefiniowanych <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>przez <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>interfejs: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, , i . W zależności od dostawcy i potrzeb aplikacji <xref:System.IObserver%601.OnError%2A> <xref:System.IObserver%601.OnCompleted%2A> i metody mogą być implementacje skrótowe. Należy zauważyć, <xref:System.IObserver%601.OnError%2A> że metoda <xref:System.Exception> nie powinna obsługiwać przekazany <xref:System.IObserver%601.OnCompleted%2A> obiekt jako wyjątek, a <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> metoda jest swobodnie wywołać implementacji dostawcy. W poniższym <xref:System.IObserver%601> przykładzie przedstawiono `TemperatureReporter` implementację klasy.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera kompletny kod `TemperatureReporter` źródłowy dla <xref:System.IObserver%601> klasy, który zapewnia implementację dla aplikacji monitorowania temperatury.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IObserver%601>
- [Wzorzec projektowy obserwatora](../../../docs/standard/events/observer-design-pattern.md)
- [Instrukcje: Implementowanie dostawcy](../../../docs/standard/events/how-to-implement-a-provider.md)
- [Wzorzec projektowy obserwatora — Najlepsze praktyki](../../../docs/standard/events/observer-design-pattern-best-practices.md)

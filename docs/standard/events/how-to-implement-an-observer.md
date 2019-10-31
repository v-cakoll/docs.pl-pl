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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139308"
---
# <a name="how-to-implement-an-observer"></a>Porady: implementowanie obserwatora
Wzorzec projektowy obserwatora wymaga podziału między obserwatorem, który rejestruje powiadomienia i dostawca, który monitoruje dane i wysyła powiadomienia do jednego lub kilku obserwatorów. W tym temacie omówiono sposób tworzenia obserwatora. Pokrewny temat, [jak: implementowanie dostawcy](../../../docs/standard/events/how-to-implement-a-provider.md), omawia sposób tworzenia dostawcy.  
  
### <a name="to-create-an-observer"></a>Aby utworzyć obserwatora  
  
1. Zdefiniuj obserwatora, który jest typem, który implementuje interfejs <xref:System.IObserver%601?displayProperty=nameWithType>. Na przykład poniższy kod definiuje typ o nazwie `TemperatureReporter`, który jest skonstruowaną <xref:System.IObserver%601?displayProperty=nameWithType> implementacją z argumentem typu ogólnego `Temperature`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2. Jeśli obserwator może przestać odbierać powiadomienia, zanim dostawca wywoła jego implementację <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, zdefiniuj zmienną prywatną, która będzie przechowywać implementację <xref:System.IDisposable> zwróconą przez metodę <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> dostawcy. Należy również zdefiniować metodę subskrypcji, która wywołuje metodę <xref:System.IObservable%601.Subscribe%2A> dostawcy i zapisuje zwrócony obiekt <xref:System.IDisposable>. Na przykład poniższy kod definiuje zmienną prywatną o nazwie `unsubscriber` i definiuje metodę `Subscribe`, która wywołuje metodę <xref:System.IObservable%601.Subscribe%2A> dostawcy i przypisuje zwracany obiekt do zmiennej `unsubscriber`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3. Zdefiniuj metodę, która umożliwia obserwatorowi zatrzymanie otrzymywania powiadomień, zanim dostawca wywoła jego implementację <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, jeśli ta funkcja jest wymagana. W poniższym przykładzie zdefiniowano metodę `Unsubscribe`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4. Podaj implementacje trzech metod zdefiniowanych przez interfejs <xref:System.IObserver%601>: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>i <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>. W zależności od dostawcy i potrzeb aplikacji metody <xref:System.IObserver%601.OnError%2A> i <xref:System.IObserver%601.OnCompleted%2A> mogą być implementacjami klasy zastępczej. Należy zauważyć, że metoda <xref:System.IObserver%601.OnError%2A> nie powinna obsłużyć pożądanego obiektu <xref:System.Exception> jako wyjątek, a metoda <xref:System.IObserver%601.OnCompleted%2A> jest bezpłatna do wywołania implementacji <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> dostawcy. W poniższym przykładzie przedstawiono implementację <xref:System.IObserver%601> klasy `TemperatureReporter`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera kompletny kod źródłowy dla klasy `TemperatureReporter`, która zapewnia <xref:System.IObserver%601> implementację dla aplikacji monitorującej temperatury.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IObserver%601>
- [Wzorzec projektowy obserwatora](../../../docs/standard/events/observer-design-pattern.md)
- [Instrukcje: Implementowanie dostawcy](../../../docs/standard/events/how-to-implement-a-provider.md)
- [Wzorzec projektowy obserwatora — najlepsze rozwiązania](../../../docs/standard/events/observer-design-pattern-best-practices.md)

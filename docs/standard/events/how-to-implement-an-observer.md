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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6426e8bd138d06d3655562de6384e46a12c09279
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44038656"
---
# <a name="how-to-implement-an-observer"></a>Porady: implementowanie obserwatora
Wzorzec projektowy obserwatora wymaga dzielenia między obserwatora, co spowoduje rejestrację dla powiadomień, a dostawca, który monitoruje danych i wysyłanie powiadomień do co najmniej jeden obserwatorów. W tym temacie omówiono sposób tworzenia obserwatora. Temat pokrewny [porady: Implementowanie dostawcy](../../../docs/standard/events/how-to-implement-a-provider.md), w tym artykule omówiono sposób tworzenia dostawcy usługi.  
  
### <a name="to-create-an-observer"></a>Aby utworzyć obserwatora  
  
1.  Zdefiniuj obserwatora, który jest typem, który implementuje <xref:System.IObserver%601?displayProperty=nameWithType> interfejsu. Na przykład, poniższy kod definiuje typ o nazwie `TemperatureReporter` czyli skonstruowany <xref:System.IObserver%601?displayProperty=nameWithType> implementację argument typu ogólnego `Temperature`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2.  Jeśli obserwatora może zrezygnować z otrzymywania powiadomień przed wywołania dostawcy jego <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementacji, Zdefiniuj zmienną prywatną, w którym będą przechowywane <xref:System.IDisposable> implementacji zwrócona przez dostawcę <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> metody. Należy także zdefiniować metodę subskrypcji, która wywołuje dostawcy <xref:System.IObservable%601.Subscribe%2A> metody i magazyny zwracanego <xref:System.IDisposable> obiektu. Na przykład, poniższy kod definiuje prywatnej zmiennej o nazwie `unsubscriber` i definiuje `Subscribe` metodę, która wywołuje dostawcy <xref:System.IObservable%601.Subscribe%2A> metody i przypisuje zwracany obiekt `unsubscriber` zmiennej.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3.  Zdefiniuj metodę, która umożliwia obserwatora zrezygnować z otrzymywania powiadomień przed wywołania dostawcy jego <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> wdrożenia, jeśli ta funkcja jest wymagana. W poniższym przykładzie zdefiniowano `Unsubscribe` metody.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4.  Zapewniają implementacje trzy metody zdefiniowane przez <xref:System.IObserver%601> interfejsu: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, i <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>. W zależności od dostawcy i potrzeby aplikacji <xref:System.IObserver%601.OnError%2A> i <xref:System.IObserver%601.OnCompleted%2A> metody mogą być implementacji klasy zastępczej. Należy pamiętać, że <xref:System.IObserver%601.OnError%2A> metoda nie powinna obsługiwać przekazany <xref:System.Exception> obiektu jako wyjątek i <xref:System.IObserver%601.OnCompleted%2A> metody jest bezpłatny do wywoływania dostawcy <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementacji. W poniższym przykładzie przedstawiono <xref:System.IObserver%601> implementacji `TemperatureReporter` klasy.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera pełnego kodu źródłowego dla `TemperatureReporter` klasy, która dostarcza <xref:System.IObserver%601> implementację temperatury monitorowania aplikacji.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IObserver%601>  
- [Wzorzec projektowy obserwatora](../../../docs/standard/events/observer-design-pattern.md)  
- [Instrukcje: Implementowanie dostawcy](../../../docs/standard/events/how-to-implement-a-provider.md)  
- [Wzorzec projektowy obserwatora — najlepsze rozwiązania](../../../docs/standard/events/observer-design-pattern-best-practices.md)

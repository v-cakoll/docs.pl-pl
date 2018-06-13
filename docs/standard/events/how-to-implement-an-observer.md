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
ms.openlocfilehash: f291bc91575ccde346f16552636d44951a0e6eac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574858"
---
# <a name="how-to-implement-an-observer"></a>Porady: implementowanie obserwatora
Wzorzec projektowy obserwatora wymaga podziału między obserwatora, który służy do rejestrowania dla powiadomień, a dostawcę, który monitoruje danych i wysyła powiadomienia do co najmniej jeden obserwatorów. W tym temacie omówiono sposób tworzenia obserwatora. Pokrewnego tematu, [porady: implementowania dostawcy](../../../docs/standard/events/how-to-implement-a-provider.md), w tym artykule omówiono sposób tworzenia dostawcy.  
  
### <a name="to-create-an-observer"></a>Aby utworzyć obserwatora  
  
1.  Zdefiniuj obserwatora, który jest typem, który implementuje <xref:System.IObserver%601?displayProperty=nameWithType> interfejsu. Na przykład poniższy kod definiuje typu o nazwie `TemperatureReporter` czyli skonstruowane <xref:System.IObserver%601?displayProperty=nameWithType> implementacji z argumentem typu ogólnego `Temperature`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2.  Jeśli obserwatora zrezygnować z otrzymywania powiadomień przed wywołania dostawcy jego <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementacji, zdefiniuj zmiennej prywatnej, w którym będą przechowywane <xref:System.IDisposable> implementacji zwrócona przez dostawcę <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> — metoda. Należy również definiować metody subskrypcji, która wywołuje metody dostawcy <xref:System.IObservable%601.Subscribe%2A> — metoda i magazyny zwróconego <xref:System.IDisposable> obiektu. Na przykład poniższy kod definiuje prywatnej zmiennej o nazwie `unsubscriber` i definiuje `Subscribe` metodę, która wywołuje metody dostawcy <xref:System.IObservable%601.Subscribe%2A> — metoda i przypisuje zwrócony obiekt do `unsubscriber` zmiennej.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3.  Zdefiniuj metodę, która umożliwia obserwatora przestać otrzymywać powiadomienia przed wywołania dostawcy jego <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> wykonania, jeśli ta funkcja jest wymagana. W poniższym przykładzie zdefiniowano `Unsubscribe` metody.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4.  Podaj implementacje trzy metody zdefiniowane przez <xref:System.IObserver%601> interfejsu: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, i <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>. W zależności od potrzeb aplikacji i dostawcy <xref:System.IObserver%601.OnError%2A> i <xref:System.IObserver%601.OnCompleted%2A> metody mogą być stub implementacji. Należy pamiętać, że <xref:System.IObserver%601.OnError%2A> — metoda nie powinna obsługiwać przekazany <xref:System.Exception> obiektu jako wyjątek i <xref:System.IObserver%601.OnCompleted%2A> metoda jest bezpłatna do wywoływania dostawcy <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementacji. W poniższym przykładzie przedstawiono <xref:System.IObserver%601> implementacja `TemperatureReporter` klasy.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono przykład zawierający kod źródłowy pełną `TemperatureReporter` klasy, która dostarcza <xref:System.IObserver%601> implementacji dla temperatury monitorowania aplikacji.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IObserver%601>  
 [Wzorzec projektowy obserwatora](../../../docs/standard/events/observer-design-pattern.md)  
 [Instrukcje: Implementowanie dostawcy](../../../docs/standard/events/how-to-implement-a-provider.md)  
 [Wzorzec projektowy obserwatora — najlepsze rozwiązania](../../../docs/standard/events/observer-design-pattern-best-practices.md)

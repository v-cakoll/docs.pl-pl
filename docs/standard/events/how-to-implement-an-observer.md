---
title: 'Porady: implementowanie obserwatora'
description: Zaimplementuj obserwatora w programie .NET. Wzorzec projektowy obserwatora wymaga podziału między obserwatorem, który rejestruje powiadomienia i dostawcę.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- observers [.NET Framework], observer design pattern
- observer design pattern [.NET Framework], implementing observers
ms.assetid: 8ecfa9f5-b500-473d-bcf0-5652ffb1e53d
ms.openlocfilehash: 43236ead15be0777f4284ba553a2f2f5e09d0a73
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768998"
---
# <a name="how-to-implement-an-observer"></a>Porady: implementowanie obserwatora
Wzorzec projektowy obserwatora wymaga podziału między obserwatorem, który rejestruje powiadomienia i dostawca, który monitoruje dane i wysyła powiadomienia do jednego lub kilku obserwatorów. W tym temacie omówiono sposób tworzenia obserwatora. Pokrewny temat, [jak: implementowanie dostawcy](how-to-implement-a-provider.md), omawia sposób tworzenia dostawcy.  
  
### <a name="to-create-an-observer"></a>Aby utworzyć obserwatora  
  
1. Zdefiniuj obserwatora, który jest typem, który implementuje <xref:System.IObserver%601?displayProperty=nameWithType> interfejs. Na przykład poniższy kod definiuje typ o nazwie `TemperatureReporter` , który jest konstruowaną <xref:System.IObserver%601?displayProperty=nameWithType> implementacją z argumentem typu ogólnego `Temperature` .  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2. Jeśli obserwator może zrezygnować z otrzymywania powiadomień, zanim dostawca wywoła jego <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementację, zdefiniuj zmienną prywatną, która będzie przechowywać <xref:System.IDisposable> implementację zwróconą przez <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> metodę dostawcy. Należy również zdefiniować metodę subskrypcji, która wywołuje <xref:System.IObservable%601.Subscribe%2A> metodę dostawcy i zapisuje zwracany <xref:System.IDisposable> obiekt. Na przykład poniższy kod definiuje zmienną prywatną o nazwie `unsubscriber` i definiuje `Subscribe` metodę, która wywołuje <xref:System.IObservable%601.Subscribe%2A> metodę dostawcy i przypisuje zwracany obiekt do `unsubscriber` zmiennej.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3. Zdefiniuj metodę, która umożliwia obserwatorowi zatrzymanie otrzymywania powiadomień, zanim dostawca wywoła jego <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementację, jeśli ta funkcja jest wymagana. W poniższym przykładzie zdefiniowano `Unsubscribe` metodę.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4. Podaj implementacje trzech metod zdefiniowanych przez <xref:System.IObserver%601> Interfejs: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType> , <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType> , i <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> . W zależności od dostawcy i potrzeb aplikacji <xref:System.IObserver%601.OnError%2A> <xref:System.IObserver%601.OnCompleted%2A> metody i mogą być implementacjami zastępczymi. Należy zauważyć, że <xref:System.IObserver%601.OnError%2A> Metoda nie powinna obsłużyć pożądanego <xref:System.Exception> obiektu jako wyjątek, a <xref:System.IObserver%601.OnCompleted%2A> Metoda jest bezpłatna do wywołania <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementacji dostawcy. W poniższym przykładzie przedstawiono <xref:System.IObserver%601> implementację `TemperatureReporter` klasy.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera kompletny kod źródłowy dla `TemperatureReporter` klasy, który zapewnia <xref:System.IObserver%601> implementację aplikacji monitorującej temperatury.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IObserver%601>
- [Wzorzec projektowy obserwatora](observer-design-pattern.md)
- [Instrukcje: implementowanie dostawcy](how-to-implement-a-provider.md)
- [Wzorzec projektowy obserwatora — Najlepsze praktyki](observer-design-pattern-best-practices.md)

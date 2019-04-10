---
title: 'Instrukcje: Implementowanie dostawcy'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12c229b3a1436f9794258fec13905cce0fb767aa
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59324776"
---
# <a name="how-to-implement-a-provider"></a>Instrukcje: Implementowanie dostawcy
Wzorzec projektowy obserwatora wymaga dzielenia od dostawcy, który monitoruje danych i wysyła powiadomienia, i co najmniej jeden obserwatorów, które otrzymują powiadomienia (wywołania zwrotne) od dostawcy. W tym temacie omówiono sposób utworzenia dostawcy. Temat pokrewny [jak: Implementowanie obserwatora](../../../docs/standard/events/how-to-implement-an-observer.md), w tym artykule omówiono sposób tworzenia obserwatora.  
  
### <a name="to-create-a-provider"></a>Aby utworzyć dostawcę  
  
1. Zdefiniować dane, że dostawca jest odpowiedzialny za wysyłanie do obserwatorów. Mimo że dostawcy i dane, które wysyła do obserwatora może być jeden typ, zwykle są one reprezentowane przez różne typy. Na przykład w przypadku monitorowania aplikacji, temperatury `Temperature` struktury definiuje dane, dostawca (reprezentowany przez `TemperatureMonitor` klasy zdefiniowanej w następnym kroku) monitoruje i do których obserwatorów subskrypcję.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/data.cs#1)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/data.vb#1)]  
  
2. Zdefiniuj dostawcy danych, który jest typem, który implementuje <xref:System.IObservable%601?displayProperty=nameWithType> interfejsu. Argument typu ogólnego dostawcy to typ, który dostawca wysyła do obserwatorów. W poniższym przykładzie zdefiniowano `TemperatureMonitor` klasy, która jest zbudowany <xref:System.IObservable%601?displayProperty=nameWithType> implementację argument typu ogólnego `Temperature`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#2)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#2)]  
  
3. Określ, jak dostawca zapisze odwołania do obserwatorów tak, aby może zostać poinformowany każdego obserwatora, gdy jest to konieczne. Najczęściej obiekt kolekcji takich jak ogólnego <xref:System.Collections.Generic.List%601> obiekt jest używany w tym celu. W poniższym przykładzie zdefiniowano prywatnej <xref:System.Collections.Generic.List%601> obiektu, który zostanie uruchomiony w `TemperatureMonitor` konstruktora klasy.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#3)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#3)]  
  
4. Zdefiniuj <xref:System.IDisposable> implementacji dostawcy mogą zwracać do subskrybentów, dzięki czemu mogą oni zrezygnować z otrzymywania powiadomień w dowolnym momencie. W poniższym przykładzie zdefiniowano zagnieżdżoną `Unsubscriber` klasę, która jest przekazywana odwołania do kolekcji subskrybentów i subskrybenta, podczas tworzenia wystąpienia klasy. Ten kod umożliwia subskrybentom wywołać obiekt <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementacji do usunięcia samego z kolekcji subskrybentów.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#4)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#4)]  
  
5. Implementowanie <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> metody. Metoda jest przekazywana odwołanie do <xref:System.IObserver%601?displayProperty=nameWithType> interfejs i powinny być przechowywane w obiekcie, który został zaprojektowany w tym celu w kroku 3. Metoda następnie powinna zwrócić <xref:System.IDisposable> implementacji opracowanych w kroku 4. W poniższym przykładzie pokazano implementację <xref:System.IObservable%601.Subscribe%2A> method in Class metoda `TemperatureMonitor` klasy.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#5)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#5)]  
  
6. Powiadom obserwatorów zgodnie z potrzebami, wywołując ich <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, i <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementacji. W niektórych przypadkach nie może wywołać dostawcę <xref:System.IObserver%601.OnError%2A> metody, gdy wystąpi błąd. Na przykład następująca `GetTemperature` metoda symuluje monitor, który odczytuje dane dotyczące temperatury co pięć sekund, a następnie powiadamia użytkownika obserwatorów, gdy temperatura został zmieniony przez co najmniej.1 stopień od czasu poprzedniego odczytu. Jeśli urządzenie nie raportuje temperatury (to znaczy, jeśli jego wartość jest równa null), dostawca powiadamia obserwatorów, że przekazywanie zostało zakończone. Należy zauważyć, że oprócz wywoływania każdego obserwatora <xref:System.IObserver%601.OnCompleted%2A> metody `GetTemperature` czyści metoda <xref:System.Collections.Generic.List%601> kolekcji. W takim przypadku dostawca sprawia, że nie wywołania <xref:System.IObserver%601.OnError%2A> metody jej obserwatorów.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#6)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#6)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera pełnego kodu źródłowego do definiowania <xref:System.IObservable%601> implementację temperatury monitorowania aplikacji. Zawiera on `Temperature` struktury, czyli dane wysyłane do obserwatorów i `TemperatureMonitor` klasy, która jest <xref:System.IObservable%601> implementacji.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#7)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#7)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IObservable%601>
- [Wzorzec projektowy obserwatora](../../../docs/standard/events/observer-design-pattern.md)
- [Instrukcje: Implementowanie obserwatora](../../../docs/standard/events/how-to-implement-an-observer.md)
- [Wzorzec projektowy obserwatora — Najlepsze praktyki](../../../docs/standard/events/observer-design-pattern-best-practices.md)

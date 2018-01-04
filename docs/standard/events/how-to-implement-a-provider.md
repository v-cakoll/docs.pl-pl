---
title: 'Porady: implementowanie dostawcy'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- observer design pattern [.NET Framework], implementing providers
- providers [.NET Framework], in observer design pattern
- observables [.NET Framework], in observer design pattern
ms.assetid: 790b5d8b-d546-40a6-beeb-151b574e5ee5
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0f99a611de4bc344a0fd35130a59d496126e3af5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-implement-a-provider"></a>Porady: implementowanie dostawcy
Wzorzec projektowy obserwatora wymaga podziału między dostawcę, który monitoruje danych i wysyła powiadomienia, i co najmniej jeden obserwatorów, które otrzymywać powiadomienia (wywołań zwrotnych) od dostawcy. W tym temacie omówiono tworzenie dostawcy. Pokrewnego tematu [porady: Implementowanie obserwatora](../../../docs/standard/events/how-to-implement-an-observer.md), w tym artykule omówiono sposób tworzenia obserwatora.  
  
### <a name="to-create-a-provider"></a>Aby utworzyć dostawcę  
  
1.  Definiowanie danych, który dostawca jest odpowiedzialny za wysyłanie do obserwatorów. Chociaż danych wysyłanych do obserwatorów i dostawcy może być jeden typ, zwykle są one reprezentowane przez różnych typów. Na przykład w przypadku monitorowania aplikacji, temperatury `Temperature` struktury definiuje dane który dostawcy (reprezentowany przez `TemperatureMonitor` klas zdefiniowanych w następnym kroku) monitoruje i do których obserwatorów subskrypcji.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/data.cs#1)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/data.vb#1)]  
  
2.  Zdefiniuj dostawcy danych, który jest typem, który implementuje <xref:System.IObservable%601?displayProperty=nameWithType> interfejsu. Argumentu typu ogólnego dostawcy jest typ, który dostawca wysyła do obserwatora. W poniższym przykładzie zdefiniowano `TemperatureMonitor` klasy, która jest zbudowany <xref:System.IObservable%601?displayProperty=nameWithType> implementacji z argumentem typu ogólnego `Temperature`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#2)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#2)]  
  
3.  Określ, jak dostawca będzie przechowywać odwołania do obserwatorów, dzięki czemu każdego obserwatora może otrzymać powiadomienie, gdy jest to odpowiednie. Najczęściej obiekt kolekcji takich jak ogólnego <xref:System.Collections.Generic.List%601> obiekt jest używany w tym celu. W poniższym przykładzie zdefiniowano prywatnej <xref:System.Collections.Generic.List%601> obiekt, który zostanie uruchomiony w `TemperatureMonitor` konstruktora klasy.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#3)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#3)]  
  
4.  Zdefiniuj <xref:System.IDisposable> implementacji dostawcy mogą zwracać do subskrybentów, dzięki czemu można zatrzymać odbieranie powiadomień w dowolnym momencie. W poniższym przykładzie zdefiniowano zagnieżdżoną `Unsubscriber` klasy, która została przekazana odwołanie do kolekcji subskrybentów i z subskrybentem, podczas tworzenia wystąpienia klasy. Ten kod umożliwia subskrybenta do wywołania obiektu <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementacji, aby usunąć się z kolekcji subskrybentów.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#4)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#4)]  
  
5.  Implementowanie <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> metody. Metoda jest przekazywana odwołanie do <xref:System.IObserver%601?displayProperty=nameWithType> interfejsu i powinny być przechowywane w obiekcie przeznaczone do tego celu, w kroku 3. Następnie metoda nie powinna zwracać <xref:System.IDisposable> implementacji opracowane w kroku 4. Poniższy przykład przedstawia implementację <xref:System.IObservable%601.Subscribe%2A> metoda `TemperatureMonitor` klasy.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#5)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#5)]  
  
6.  Powiadom obserwatorów zgodnie z potrzebami, wywołując ich <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, i <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementacji. W niektórych przypadkach dostawcy nie może wywołać <xref:System.IObserver%601.OnError%2A> metody po wystąpieniu błędu. Na przykład następująca `GetTemperature` metody symuluje monitor, który odczytuje dane temperaturę co pięć sekund i powiadamia obserwatorów, jeśli temperatura został zmieniony przez co najmniej.1 stopnia od czasu poprzedniego odczytu. Jeśli urządzenie nie raportuje temperatury (jeśli jego wartość jest równa null), dostawca powiadamia obserwatorów zakończeniu przekazywania. Należy zauważyć, że oprócz wywoływania każdego obserwatora <xref:System.IObserver%601.OnCompleted%2A> metody `GetTemperature` czyści metody <xref:System.Collections.Generic.List%601> kolekcji. W takim przypadku dostawca wywołań nie do <xref:System.IObserver%601.OnError%2A> metoda jego obserwatorów.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#6)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#6)]  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono przykład zawierający kod źródłowy pełną definiowanie <xref:System.IObservable%601> implementacji dla temperatury monitorowania aplikacji. Obejmuje on `Temperature` struktury, która jest dane wysłane do obserwatorów, i `TemperatureMonitor` klasy, która jest <xref:System.IObservable%601> implementacji.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#7)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#7)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IObservable%601>  
 [Wzorzec projektowy obserwatora](../../../docs/standard/events/observer-design-pattern.md)  
 [Instrukcje: Implementowanie obserwatora](../../../docs/standard/events/how-to-implement-an-observer.md)  
 [Wzorzec projektowy obserwatora — najlepsze rozwiązania](../../../docs/standard/events/observer-design-pattern-best-practices.md)

---
title: Operacje blokowane
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Interlocked class, about Interlocked class
- threading [.NET Framework], Interlocked class
ms.assetid: cbda7114-c752-4f3e-ada1-b1e8dd262f2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38532228f7a5d07bb1b9fcf7e90d2be53a28b04c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="interlocked-operations"></a>Operacje blokowane
<xref:System.Threading.Interlocked> Klasa dostarcza metody, które synchronizują dostęp do zmiennej, który jest współużytkowany przez wiele wątków. Wątki różnych procesów służy ten mechanizm, jeśli zmienna znajduje się w pamięci współużytkowanej. Operacje blokowane są atomic — całej operacji jest jednostki, która nie może być przerwana przez inną operację blokowanego na tę samą zmienną. Jest to ważne w systemach operacyjnych z cenią sobie wcześniejsze wielowątkowości, gdy wątek może zostać zawieszone po załadowaniu wartości z adres pamięci, ale przed uzyskaniem możliwość zmienienia go i zapisać go.  
  
 <xref:System.Threading.Interlocked> Klasa udostępnia następujące operacje:  
  
-   W programie .NET Framework w wersji 2.0 <xref:System.Threading.Interlocked.Add%2A> metoda dodaje wartość do zmiennej i zwraca nową wartość zmiennej.  
  
-   W programie .NET Framework w wersji 2.0 <xref:System.Threading.Interlocked.Read%2A> metoda odczytuje wartość 64-bitową liczbę całkowitą jako niepodzielną operację. Jest to przydatne w 32-bitowych systemach operacyjnych, gdzie odczytywania 64-bitową liczbę całkowitą nie zwykle niepodzielną operację.  
  
-   <xref:System.Threading.Interlocked.Increment%2A> i <xref:System.Threading.Interlocked.Decrement%2A> metody zwiększyć lub zmniejszyć zmiennej i zwróć wartość wynikową.  
  
-   <xref:System.Threading.Interlocked.Exchange%2A> Metoda wykonuje atomic exchange wartości w określonej zmiennej zwraca tę wartość i zastępuje go z nową wartością. W programie .NET Framework w wersji 2.0 ogólnego przeciążenie tej metody może posłużyć do wykonania tego programu exchange zmiennej dowolnego typu odwołania. Zobacz <xref:System.Threading.Interlocked.Exchange%60%601%28%60%600%40%2C%60%600%29>.  
  
-   <xref:System.Threading.Interlocked.CompareExchange%2A> Metody również dwa wymiany wartości, ale uzależnione od wyniku porównania. W programie .NET Framework w wersji 2.0 ogólnego przeciążenie tej metody może posłużyć do wykonania tego programu exchange zmiennej dowolnego typu odwołania. Zobacz <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29>.  
  
 W nowoczesnych procesorów, metody <xref:System.Threading.Interlocked> klasy często może być zaimplementowany przez jednej instrukcji. W związku z tym Podaj synchronizacji bardzo wysokiej wydajności i może służyć do tworzenia mechanizmów synchronizacji wyższego poziomu, takich jak blokad pokrętła.  
  
 Na przykład, który używa <xref:System.Threading.Monitor> i <xref:System.Threading.Interlocked> klas w połączeniu, zobacz [monitorów](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).  
  
## <a name="compareexchange-example"></a>Przykład CompareExchange  
 <xref:System.Threading.Interlocked.CompareExchange%2A> Metody można użyć do obliczenia, które są bardziej skomplikowane niż proste inkrementacja i dekrementacja ochrony. W poniższym przykładzie pokazano metodę wątkowo, która dodaje do całkowitej działającego przechowywane jako zmiennoprzecinkową numer punktu. (Liczb całkowitych, <xref:System.Threading.Interlocked.Add%2A> metoda jest prostsza rozwiązania.) Kompletny kod przykłady można znaleźć w temacie przeciążeń <xref:System.Threading.Interlocked.CompareExchange%2A> , które wymagają argumenty zmiennoprzecinkowych pojedynczej precyzji i podwójnej precyzji (<xref:System.Threading.Interlocked.CompareExchange%28System.Single%40%2CSystem.Single%2CSystem.Single%29> i <xref:System.Threading.Interlocked.CompareExchange%28System.Double%40%2CSystem.Double%2CSystem.Double%29>).  
  
 [!code-cpp[Conceptual.Interlocked#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Interlocked#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source1.cs#1)]
 [!code-vb[Conceptual.Interlocked#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source1.vb#1)]  
  
## <a name="untyped-overloads-of-exchange-and-compareexchange"></a>Nieuwzględniające typów przeciążenia programu Exchange i CompareExchange  
 <xref:System.Threading.Interlocked.Exchange%2A> i <xref:System.Threading.Interlocked.CompareExchange%2A> metody mają przeciążenia, które przyjmują argumentów typu <xref:System.Object>. Pierwszy argument każdego z tych przeciążenia jest `ref Object` (`ByRef … As Object` w języku Visual Basic), i bezpieczeństwo typów wymaga zmiennej przekazany do tego argumentu wpisywania wyłącznie jako <xref:System.Object>; po prostu nie można rzutować na typ pierwszego argumentu <xref:System.Object> podczas wywoływania metody.  
  
> [!NOTE]
>  W programie .NET Framework w wersji 2.0, użyj ogólnych przeciążeń <xref:System.Threading.Interlocked.Exchange%2A> i <xref:System.Threading.Interlocked.CompareExchange%2A> metody do wymiany silnie typizowanych zmiennych.  
  
 Poniższy przykład kodu pokazuje właściwość typu `ClassA` które można ustawić tylko raz, ponieważ może być zaimplementowany w programie .NET Framework w wersji 1.0 lub 1.1.  
  
 [!code-cpp[Conceptual.Interlocked#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Interlocked#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source2.cs#2)]
 [!code-vb[Conceptual.Interlocked#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.Interlocked>  
 <xref:System.Threading.Monitor>  
 [Wątkowość](../../../docs/standard/threading/index.md)  
 [Wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md)

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
ms.openlocfilehash: 3bc790628d4331c9bc3d958997db5151c886109a
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46480646"
---
# <a name="interlocked-operations"></a>Operacje blokowane
<xref:System.Threading.Interlocked> Klasa dostarcza metody, które synchronizują dostęp do zmiennej, która jest współużytkowana przez wiele wątków. Wątki różnych procesów można użyć tego mechanizmu, jeśli zmienna znajduje się w pamięci współużytkowanej. Operacje blokowane są niepodzielne, cała operacja jest jednostki, która nie może zostać przerwane przez inną operację w tej samej zmiennej. Jest to ważne w systemach operacyjnych z preemptive wielowątkowości, gdzie wątek może zostać zawieszone po załadowaniu wartość z adresu pamięci, ale przed masz szansę, aby go zmienić i zapisz go.  
  
 <xref:System.Threading.Interlocked> Klasa udostępnia następujące operacje:  
  
-   W .NET Framework w wersji 2.0 <xref:System.Threading.Interlocked.Add%2A> metoda dodaje wartość do zmiennej i zwraca nową wartość zmiennej.  
  
-   W .NET Framework w wersji 2.0 <xref:System.Threading.Interlocked.Read%2A> metoda odczytuje wartość 64-bitową liczbę całkowitą jako operację niepodzielną. Jest to przydatne na 32-bitowe systemy operacyjne, których odczytywanie 64-bitową liczbę całkowitą nie jest zazwyczaj operacją niepodzielną.  
  
-   <xref:System.Threading.Interlocked.Increment%2A> i <xref:System.Threading.Interlocked.Decrement%2A> metod zwiększyć lub zmniejszyć zmienną i zwracania wartości wynikowej.  
  
-   <xref:System.Threading.Interlocked.Exchange%2A> Metoda wykonuje niepodzielne exchange wartość w określonej zmiennej, która zwraca tę wartość i zastępuje go z nową wartością. W programie .NET Framework 2.0 ogólny przeciążenia tej metody może służyć do wykonywania tej wymiany na zmiennej typu odwołania. Zobacz <xref:System.Threading.Interlocked.Exchange%60%601%28%60%600%40%2C%60%600%29>.  
  
-   <xref:System.Threading.Interlocked.CompareExchange%2A> Metoda również wymienia dwie wartości, ale warunkowe na wyniku porównania. W programie .NET Framework 2.0 ogólny przeciążenia tej metody może służyć do wykonywania tej wymiany na zmiennej typu odwołania. Zobacz <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29>.  
  
 W nowoczesnych procesorów, metody <xref:System.Threading.Interlocked> klasy, często może być implementowany przez pojedynczej instrukcji. W związku z tym, zapewniają bardzo wydajny synchronizacji i może służyć do tworzenia wyższego poziomu mechanizmy synchronizacji, takich jak blokad pokrętła.  
  
 Aby uzyskać przykład, który używa <xref:System.Threading.Monitor> i <xref:System.Threading.Interlocked> klas w połączeniu, zobacz [monitorów](https://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).  
  
## <a name="compareexchange-example"></a>Przykład CompareExchange  
 <xref:System.Threading.Interlocked.CompareExchange%2A> Metoda może służyć do ochrony obliczenia, które są bardziej skomplikowane niż proste inkrementacja i dekrementacja. W poniższym przykładzie pokazano metodę metodą o bezpiecznych wątkach, która dodaje do sumy przechowywane jako zmiennoprzecinkowy numer punktu. (Dla liczb całkowitych, <xref:System.Threading.Interlocked.Add%2A> metoda jest prostsza rozwiązania.) Kompletny kod przykłady można znaleźć w temacie przeciążenia <xref:System.Threading.Interlocked.CompareExchange%2A> , które wymagają argumentów zmiennoprzecinkowych pojedynczej precyzji i podwójnej precyzji (<xref:System.Threading.Interlocked.CompareExchange%28System.Single%40%2CSystem.Single%2CSystem.Single%29> i <xref:System.Threading.Interlocked.CompareExchange%28System.Double%40%2CSystem.Double%2CSystem.Double%29>).  
  
 [!code-cpp[Conceptual.Interlocked#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Interlocked#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source1.cs#1)]
 [!code-vb[Conceptual.Interlocked#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source1.vb#1)]  
  
## <a name="untyped-overloads-of-exchange-and-compareexchange"></a>Nietypizowane przeciążenia programu Exchange i CompareExchange  
 <xref:System.Threading.Interlocked.Exchange%2A> i <xref:System.Threading.Interlocked.CompareExchange%2A> metody mają przeciążenia, które przyjmują argumenty typu <xref:System.Object>. Pierwszy argument każdego z tych przeciążeń jest `ref Object` (`ByRef … As Object` w języku Visual Basic), i bezpieczeństwo typów wymaga zmiennej przekazany do tego argumentu do można wpisać wyłącznie jako <xref:System.Object>; po prostu nie można rzutować na typ pierwszego argumentu <xref:System.Object> podczas wywołania tych metod.  
  
> [!NOTE]
>  W .NET Framework w wersji 2.0, użyj przeciążenia ogólne <xref:System.Threading.Interlocked.Exchange%2A> i <xref:System.Threading.Interlocked.CompareExchange%2A> metody do wymiany silnie typizowanych zmiennych.  
  
 Poniższy przykład kodu pokazuje właściwości typu `ClassA` , można ustawić tylko raz, ponieważ mogą zostać zaimplementowane w .NET Framework w wersji 1.0 i 1.1.  
  
 [!code-cpp[Conceptual.Interlocked#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Interlocked#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source2.cs#2)]
 [!code-vb[Conceptual.Interlocked#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Interlocked>  
- <xref:System.Threading.Monitor>  
- [Wątkowość](../../../docs/standard/threading/index.md)  
- [Wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md)

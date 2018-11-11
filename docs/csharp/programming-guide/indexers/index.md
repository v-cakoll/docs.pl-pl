---
title: Indeksatory (Przewodnik programowania w języku C#)
ms.date: 03/10/2017
f1_keywords:
- cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
ms.openlocfilehash: 405de22ea7e48a5964de48eb20becdaf5fc5ae01
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2018
ms.locfileid: "43503636"
---
# <a name="indexers-c-programming-guide"></a>Indeksatory (Przewodnik programowania w języku C#)

Indeksatory umożliwiają wystąpienia klasy lub struktury, które mają być indeksowane, podobnie jak tablice. Indeksowanej wartości można ustawić lub pobrać bez jawne określenie typu lub wystąpienia elementu członkowskiego. Indeksatory przypominają [właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md) z tą różnicą, że ich metod dostępu przyjmują parametry.  
 
 W poniższym przykładzie zdefiniowano klasę ogólną za pomocą prostego [uzyskać](../../../csharp/language-reference/keywords/get.md) i [ustaw](../../../csharp/language-reference/keywords/set.md) metody dostępu do przypisywania i pobierać wartości. `Program` Klasy tworzy wystąpienie tej klasy do przechowywania ciągów.  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
>  Aby uzyskać więcej przykładów, zobacz [sekcje pokrewne](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections).  
  
## <a name="expression-body-definitions"></a>Definicje treści wyrażenia  
 
Bardzo często indeksator get lub metody dostępu set składają się z pojedynczej instrukcji, która zwraca lub ustawia wartość. Elementy członkowskie z wyrażeniem zapewniają uproszczoną składnię do obsługi tego scenariusza. Począwszy od C# 6, indeksator tylko do odczytu można zaimplementować jako wyrażeniem w treści elementu członkowskiego, co ilustruje poniższy przykład.

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

Należy pamiętać, że `=>` wprowadza treści wyrażenia, a `get` — słowo kluczowe nie jest używany. 

Począwszy od C# 7.0, zarówno get, jak i metody dostępu set mogą być implementowane jako elementy członkowskie z wyrażeniem. W takim przypadku zarówno `get` i `set` należy używać słów kluczowych. Na przykład:

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a>Omówienie indeksatorów  
  
-   Indeksatory Włącz obiekty, które mają być indeksowane w sposób podobny do tablic.  
  
-   A `get` akcesor zwraca wartość. A `set` akcesor przypisuje wartość.  
  
-   [To](../../../csharp/language-reference/keywords/this.md) — słowo kluczowe jest używane do definiowania indeksatora.  
  
-   [Wartość](../../../csharp/language-reference/keywords/value.md) — słowo kluczowe jest używane do definiowania wartości przypisywane przez `set` indeksatora.  
  
-   Indeksatory nie muszą być indeksowane przez wartość całkowitą; jest do Ciebie sposób definiowania mechanizm określonych wyszukiwania.  
  
-   Indeksatory mogą być przeciążone.  
  
-   Indeksatory może mieć więcej niż jeden parametr formalny, na przykład podczas uzyskiwania dostępu do tablicy dwuwymiarowej.  
  
##  <a name="BKMK_RelatedSections"></a> Sekcje pokrewne  
  
-   [Używanie indeksatorów](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [Indeksatory w interfejsach](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
-   [Porównanie właściwości i indeksatorów](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [Ograniczanie dostępności metody dostępu](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [indeksatory](~/_csharplang/spec/classes.md#indexers) w [ C# specyfikacji języka](../../language-reference/language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)

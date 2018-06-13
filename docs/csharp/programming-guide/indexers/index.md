---
title: Indeksatory (Przewodnik programowania w języku C#)
ms.date: 03/10/2017
f1_keywords:
- cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
ms.openlocfilehash: acc82ca370a71a0469fc543d042da9c279d69fb2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334223"
---
# <a name="indexers-c-programming-guide"></a>Indeksatory (Przewodnik programowania w języku C#)

Indeksatory Zezwalaj wystąpienia klasy lub struktury zostać pomyślnie zindeksowane, podobnie jak tablic. Indeksowane wartość można ustawić ani pobrać bez jawnego określenia członka typu lub wystąpienia. Indeksatory przypominać [właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md) z tą różnicą, że ich metod dostępu przyjmować parametrów.  
 
 W poniższym przykładzie zdefiniowano klasy ogólnej przy prostego [uzyskać](../../../csharp/language-reference/keywords/get.md) i [ustawić](../../../csharp/language-reference/keywords/set.md) metod dostępu, aby przypisać lub pobrać wartości. `Program` Klasy tworzy wystąpienie tej klasy do przechowywania ciągów.  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
>  Aby uzyskać więcej przykładów, zobacz [sekcje pokrewne](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections).  
  
## <a name="expression-body-definitions"></a>Definicje treść wyrażenia  
 
Bardzo często indeksator get lub składać się z jednej instrukcji, która zwraca lub ustawia wartość metody dostępu set. Członkowie zabudowanych wyrażenie zapewniają uproszczoną składnię tego scenariusza. Począwszy od języka C# 6, indeksatora tylko do odczytu można zaimplementować jako zabudowanych wyrażenie elementu członkowskiego, jak przedstawiono na poniższym przykładzie.

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

Należy pamiętać, że `=>` wprowadza treść wyrażenia, a `get` — słowo kluczowe nie jest używany. 

Począwszy od C# 7.0, zarówno get, jak i metody dostępu set może być wdrożony jako członków zabudowanych wyrażenia. W takim przypadku zarówno `get` i `set` słowa kluczowe muszą być używane. Na przykład:

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a>Omówienie indeksatorów  
  
-   Indeksatory Włącz obiektów do zindeksowania w sposób podobny do tablic.  
  
-   A `get` akcesor zwraca wartość. A `set` akcesor przypisuje wartość.  
  
-   [To](../../../csharp/language-reference/keywords/this.md) — słowo kluczowe jest używane do definiowania indeksatora.  
  
-   [Wartość](../../../csharp/language-reference/keywords/value.md) — słowo kluczowe jest używane do definiowania przypisywane przez wartość `set` indeksatora.  
  
-   Indeksatory nie muszą być indeksowane według całkowitą; jest możesz sposób definiowania mechanizm określonego wyszukiwania.  
  
-   Indeksatory mogą być przeciążone.  
  
-   Indeksatory może mieć więcej niż jeden parametr formalny, na przykład podczas uzyskiwania dostępu do tablicą dwuwymiarową.  
  
##  <a name="BKMK_RelatedSections"></a> Sekcje pokrewne  
  
-   [Używanie indeksatorów](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [Indeksatory w interfejsach](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
-   [Porównanie właściwości i indeksatorów](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [Ograniczanie dostępności metody dostępu](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)

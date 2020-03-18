---
title: Indeksatory - Przewodnik programowania C#
ms.date: 03/10/2017
f1_keywords:
- cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
ms.openlocfilehash: 539b2861e975c0c758c43c8a5d4cca86e3d2bb2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79167546"
---
# <a name="indexers-c-programming-guide"></a>Indeksatory (Przewodnik programowania w języku C#)

Indeksatory zezwalają na indeksowanie wystąpień klasy lub struktury, podobnie jak tablice. Wartość indeksowana można ustawić lub pobrać bez jawnego określenia typu lub elementu członkowskiego wystąpienia. Indeksatory przypominają [właściwości,](../classes-and-structs/properties.md) z tą różnicą, że ich akcesory przyjmują parametry.  

 W poniższym przykładzie definiuje klasę rodzajową z [prosteget](../../language-reference/keywords/get.md) i [set](../../language-reference/keywords/set.md) metody akcesora do przypisywania i pobierania wartości. Klasa `Program` tworzy wystąpienie tej klasy do przechowywania ciągów.  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
> Aby uzyskać więcej przykładów, zobacz [powiązane sekcje](./index.md#BKMK_RelatedSections).  
  
## <a name="expression-body-definitions"></a>Definicje treści wyrażeń  

Jest wspólne dla indeksatora get lub set akcesor składa się z pojedynczej instrukcji, która zwraca lub ustawia wartość. Elementy członkowskie zabudowane wyrażeniem zapewniają uproszczoną składnię do obsługi tego scenariusza. Począwszy od C# 6 indeksator tylko do odczytu można zaimplementować jako element członkowski zabudowany wyrażeniem, jak pokazano w poniższym przykładzie.

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

Należy `=>` zauważyć, że wprowadza treść `get` wyrażenia i że słowo kluczowe nie jest używany.

Począwszy od języka C# 7.0, get i set akcesor może być implementowane jako elementy członkowskie zabudowane wyrażeniem. W takim przypadku `get` `set` należy użyć zarówno słów kluczowych, jak i słów kluczowych. Przykład:

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a>Omówienie indeksatorów  
  
- Indeksatory umożliwiają indeksowanie obiektów w sposób podobny do tablic.  
  
- Akcesor `get` zwraca wartość. Akcesor `set` przypisuje wartość.  
  
- [To](../../language-reference/keywords/this.md) słowo kluczowe służy do definiowania indeksatora.  
  
- Value [value](../../language-reference/keywords/value.md) — słowo kluczowe służy do definiowania wartości przypisanej `set` przez indeksatora.  
  
- Indeksatory nie muszą być indeksowane przez wartość całkowitą; to od Ciebie zależy, jak zdefiniować konkretny mechanizm wyszukiwania.  
  
- Indeksatory mogą być przeciążone.  
  
- Indeksatory mogą mieć więcej niż jeden parametr formalny, na przykład podczas uzyskiwania dostępu do tablicy dwuwymiarowej.  
  
## <a name="BKMK_RelatedSections"></a>Sekcje pokrewne  
  
- [Używanie indeksatorów](./using-indexers.md)  
  
- [Indeksatory w interfejsach](./indexers-in-interfaces.md)  
  
- [Porównanie właściwości i indeksatorów](./comparison-between-properties-and-indexers.md)  
  
- [Ograniczanie dostępności metody dostępu](../classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [Indeksatory](~/_csharplang/spec/classes.md#indexers) w [specyfikacji języka Języka C #](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Właściwości](../classes-and-structs/properties.md)

---
title: Właściwości — C# przewodnik programowania
ms.custom: seodec18
ms.date: 03/10/2017
f1_keywords:
- cs.properties
helpviewer_keywords:
- properties [C#]
- C# language, properties
ms.assetid: e295a8a2-b357-4ee7-a12e-385a44146fa8
ms.openlocfilehash: 260c9e362281ba7996dc834ab47d7beb2755b636
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59977096"
---
# <a name="properties-c-programming-guide"></a>Właściwości (Przewodnik programowania w języku C#)

Właściwość jest elementem członkowskim, który oferuje elastyczny mechanizm do odczytu, zapisu lub obliczenia wartości pola prywatnego. Właściwości mogą być używane, tak, jakby znajdowały publiczne elementy członkowskie danych, ale są one faktycznie specjalne metody o nazwie *Akcesory*. Umożliwia danych można łatwo uzyskać dostęp i nadal pomaga wspierać bezpieczeństwo i elastyczność metody.  

## <a name="properties-overview"></a>Przegląd właściwości  
  
- Właściwości pozwala klasie do udostępnienia publicznego sposób pobierania i ustawiania wartości, wykonania lub weryfikacji kodu są ukryte.  
  
- A [uzyskać](../../../csharp/language-reference/keywords/get.md) metody dostępu właściwości służy do zwracania wartości właściwości i [ustaw](../../../csharp/language-reference/keywords/set.md) metody dostępu właściwości jest używany do przypisywania nową wartość. Te metody dostępu może mieć różne poziomy dostępu. Aby uzyskać więcej informacji, zobacz [Ograniczanie dostępności metody dostępu](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).  
  
- [Wartość](../../../csharp/language-reference/keywords/value.md) — słowo kluczowe jest używane do definiowania wartości przypisywane przez `set` metody dostępu.  
- Właściwości mogą być *odczytu i zapisu* (zarówno mają `get` i `set` dostępu), *tylko do odczytu* (mają `get` dostępu, ale nie `set` dostępu), lub *tylko do zapisu* (mają `set` dostępu, ale nie `get` dostępu). Właściwości tylko do zapisu występują rzadko i są najczęściej używane do ograniczania dostępu do poufnych danych.

- Proste właściwości, które wymagają bez kodu niestandardowej metody dostępu można zaimplementować jako definicje treści wyrażenia lub [właściwości zaimplementowane automatycznie](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).
 
## <a name="properties-with-backing-fields"></a>Właściwości pola zapasowe

Jeden podstawowy wzorzec implementacji właściwości polega na tym, za pomocą pola prywatne zapasowy, ustawiania i pobierania wartości właściwości. `get` Akcesor zwraca wartość pola prywatnego i `set` dostępu może wykonywać niektóre sprawdzanie poprawności danych przed przypisaniem wartości do pola prywatnego. Obu metod dostępu może również wykonywać niektóre konwersji lub obliczeń na danych, przed jego przechowywane lub zwracane.

Poniższy przykład ilustruje ten wzorzec. W tym przykładzie `TimePeriod` klasa reprezentuje przedział czasu. Wewnętrznie klasa przechowuje przedział czasu w ciągu kilku sekund w prywatnej pole o nazwie `_seconds`. Właściwości odczytu / zapisu o nazwie `Hours` umożliwia klientowi określenie interwału czasu w godzinach. Zarówno `get` i `set` metod dostępu do wykonania niezbędnych konwersji między godzin i sekund. Ponadto `set` akcesor weryfikuje ona dane i zgłasza <xref:System.ArgumentOutOfRangeException> Jeśli liczba godzin jest nieprawidłowa. 
   
 [!code-csharp[Properties#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-1.cs)]  
  
## <a name="expression-body-definitions"></a>Definicje treści wyrażenia  

 Akcesory właściwości często składają się z instrukcji jednowierszowego, które po prostu przypisać lub zwrócić wynik wyrażenia. Te właściwości można zaimplementować jako elementy członkowskie z wyrażeniem. Wyrażenie treści definicji składają się z `=>` symbolu wraz z wyrażeniem przypisać do lub pobrać z właściwości.

 Począwszy od C# 6, można zaimplementować właściwości tylko do odczytu `get` dostępu jako element członkowski wyrażeniem. W tym przypadku, ani `get` — słowo kluczowe dostępu ani `return` słowo kluczowe jest używane. Poniższy przykład wykonuje tylko do odczytu `Name` właściwość jako element członkowski z wyrażeniem w treści.

 [!code-csharp[Properties#2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-2.cs)]  

 Począwszy od C# 7.0, zarówno `get` i `set` dostępu można zaimplementować jako elementy członkowskie z wyrażeniem. W tym przypadku `get` i `set` słowa kluczowe musi być obecny. Poniższy przykład ilustruje użycie definicji treści wyrażenia dla obu metod dostępu. Należy pamiętać, że `return` — słowo kluczowe nie jest używany z `get` metody dostępu.
 
  [!code-csharp[Properties#3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-3.cs)]  

## <a name="auto-implemented-properties"></a>Właściwości zaimplementowane automatycznie

W niektórych przypadkach właściwość `get` i `set` tylko przypisanie wartości do metod dostępu lub pobrania wartości z polem zapasowym, bez uwzględniania dodatkowej logiki. Przy użyciu automatycznie implementowanych właściwości, można uprościć kod, mając kompilator języka C# przezroczyste Podaj pola pomocniczego. 

Jeśli właściwość ma jednocześnie `get` i `set` dostępu, obie wartości muszą być zaimplementowane automatycznie. Właściwości zaimplementowane automatycznie definiowane za pomocą `get` i `set` słów kluczowych bez podawania implementacji. Poniższy przykład jest powtarzany w poprzedniej wersji, chyba że `Name` i `Price` są automatycznie implementowane właściwości. Należy pamiętać, że w przykładzie usunięto także Konstruktor sparametryzowany, tak aby `SaleItem` obiekty są teraz inicjowane w wyniku wywołania konstruktora bez parametrów i [inicjatora obiektu](object-and-collection-initializers.md).

  [!code-csharp[Properties#4](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-4.cs)]  

## <a name="related-sections"></a>Sekcje pokrewne  
  
-   [Używanie właściwości](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [Właściwości interfejsu](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)  
  
-   [Porównanie właściwości i indeksatorów](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [Ograniczanie dostępności metody dostępu](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
-   [Właściwości zaimplementowane automatycznie](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [właściwości](~/_csharplang/spec/classes.md#properties) w [ C# specyfikacji języka](../../language-reference/language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Używanie właściwości](../../../csharp/programming-guide/classes-and-structs/using-properties.md)
- [Indeksatory](../../../csharp/programming-guide/indexers/index.md)
- [Get — słowo kluczowe](../../../csharp/language-reference/keywords/get.md)
- [set — słowo kluczowe](../../../csharp/language-reference/keywords/set.md)

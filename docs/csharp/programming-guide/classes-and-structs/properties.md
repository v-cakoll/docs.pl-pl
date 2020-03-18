---
title: Właściwości — przewodnik programowania C#
ms.date: 03/10/2017
f1_keywords:
- cs.properties
helpviewer_keywords:
- properties [C#]
- C# language, properties
ms.assetid: e295a8a2-b357-4ee7-a12e-385a44146fa8
ms.openlocfilehash: ee530e981e0c85302b2b11cc739d6c51d6650ddd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170107"
---
# <a name="properties-c-programming-guide"></a>Właściwości (Przewodnik programowania w języku C#)

Właściwość jest elementem członkowskim, który zapewnia elastyczny mechanizm odczytu, zapisu lub obliczania wartości pola prywatnego. Właściwości mogą służyć tak, jakby były członkami danych publicznych, ale w rzeczywistości są to specjalne metody nazywane *akcesorami.* Umożliwia to łatwy dostęp do danych i nadal pomaga promować bezpieczeństwo i elastyczność metod.  

## <a name="properties-overview"></a>Przegląd właściwości  
  
- Właściwości umożliwiają klasy, aby uwidaczniać publiczny sposób uzyskiwania i ustawiania wartości podczas ukrywania kodu implementacji lub weryfikacji.  
  
- A [get](../../language-reference/keywords/get.md) property akcesor jest używany do zwracania wartości właściwości, a akcesor właściwości [set](../../language-reference/keywords/set.md) jest używany do przypisywania nowej wartości. Te akcesory mogą mieć różne poziomy dostępu. Aby uzyskać więcej informacji, zobacz [Ograniczanie ułatwień dostępu .](./restricting-accessor-accessibility.md)  
  
- Value [value](../../language-reference/keywords/value.md) — słowo kluczowe służy do definiowania wartości przypisanej przez akcesora. `set`  
- Właściwości mogą być *odczytu i zapisu* (mają zarówno `get` a i `set` akcesor), tylko do *odczytu* `get` (mają akcesor, ale nie `set` ma akcesora) lub tylko do *zapisu* `set` (mają akcesor, ale nie `get` ma akcesora). Właściwości tylko do zapisu są rzadkie i są najczęściej używane do ograniczania dostępu do poufnych danych.

- Proste właściwości, które nie wymagają niestandardowego kodu akcesora, mogą być implementowane jako definicje treści wyrażeń lub jako [właściwości implementowane automatycznie.](./auto-implemented-properties.md)

## <a name="properties-with-backing-fields"></a>Właściwości z polami zapasowymi

Jeden podstawowy wzorzec do implementowania właściwości polega na użyciu prywatnego pola zapasowego do ustawiania i pobierania wartości właściwości. Akcesor `get` zwraca wartość pola prywatnego, a `set` akcesor może wykonać niektóre sprawdzanie poprawności danych przed przypisaniem wartości do pola prywatnego. Oba akcesory mogą również wykonać konwersję lub obliczenia na danych, zanim zostaną zapisane lub zwrócone.

Poniższy przykład ilustruje ten wzorzec. W tym przykładzie `TimePeriod` klasa reprezentuje interwał czasu. Wewnętrznie klasa przechowuje przedział czasu w sekundach `_seconds`w polu prywatnym o nazwie . Właściwość odczytu i `Hours` zapisu o nazwie umożliwia klientowi określenie przedziału czasu w godzinach. Zarówno `get` akcesorów `set` i wykonać niezbędne konwersji między godzinami i sekundami. Ponadto `set` akcesor sprawdza poprawność danych <xref:System.ArgumentOutOfRangeException> i zgłasza, jeśli liczba godzin jest nieprawidłowa.

 [!code-csharp[Properties#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-1.cs)]  
  
## <a name="expression-body-definitions"></a>Definicje treści wyrażeń  

 Akcesory właściwości często składają się z jednowierszowych instrukcji, które po prostu przypisują lub zwracają wynik wyrażenia. Można zaimplementować te właściwości jako elementy członkowskie zabudowane wyrażeniem. Definicje treści wyrażenia `=>` składają się z symbolu, po którym następuje wyrażenie przypisywane do właściwości lub pobieranie z niej.

 Począwszy od Języka C# 6 właściwości `get` tylko do odczytu można zaimplementować akcesor jako element członkowski zabudowany wyrażeń. W takim przypadku nie `get` jest używany `return` ani słowo kluczowe akcesor, ani słowo kluczowe. W poniższym przykładzie implementuje `Name` właściwości tylko do odczytu jako element członkowski zabudowany wyrażeń.

 [!code-csharp[Properties#2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-2.cs)]  

 Począwszy od języka C# `get` 7.0, zarówno i `set` akcesor akcesor akcesor akcesor akcesora można zaimplementować jako elementy członkowskie zabudowane wyrażeniem. W takim przypadku `get` `set` słowa kluczowe i muszą być obecne. W poniższym przykładzie przedstawiono użycie definicji treści wyrażenia dla obu akcesorów. Należy pamiętać, że `return` słowo `get` kluczowe nie jest używany z akcesor.

  [!code-csharp[Properties#3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-3.cs)]  

## <a name="auto-implemented-properties"></a>Właściwości implementowane automatycznie

W niektórych przypadkach `get` `set` właściwości i akcesorów po prostu przypisać wartość do lub pobrać wartość z pola zapasowego bez uwzględnienia żadnych dodatkowych logiki. Za pomocą właściwości auto-implementowane, można uprościć kodu, a kompilator Języka C# w sposób niewidoczny dla ciebie.

Jeśli właściwość ma `get` zarówno `set` a, jak i akcesor, oba muszą być automatycznie implementowane. Można zdefiniować właściwości zaimplementowane automatycznie `get` `set` przy użyciu i słów kluczowych bez podawania implementacji. Poniższy przykład powtarza poprzedni, z `Name` tą `Price` różnicą, że i są właściwościami implementowane automatycznie. Należy zauważyć, że w przykładzie również usuwa `SaleItem` konstruktora sparametryzowany, tak, że obiekty są teraz inicjowane z wywołaniem konstruktora bezparametrów i [inicjatora obiektu](object-and-collection-initializers.md).

  [!code-csharp[Properties#4](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-4.cs)]  

## <a name="related-sections"></a>Sekcje pokrewne  
  
- [Używanie właściwości](./using-properties.md)  
  
- [Właściwości interfejsu](./interface-properties.md)  
  
- [Porównanie właściwości i indeksatorów](../indexers/comparison-between-properties-and-indexers.md)  
  
- [Ograniczanie dostępności metody dostępu](./restricting-accessor-accessibility.md)  
  
- [Właściwości zaimplementowane automatycznie](./auto-implemented-properties.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [Właściwości](~/_csharplang/spec/classes.md#properties) w [specyfikacji języka Języka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Używanie właściwości](./using-properties.md)
- [Indexers](../indexers/index.md) (Indeksatory)
- [pobierz słowo kluczowe](../../language-reference/keywords/get.md)
- [set — słowo kluczowe](../../language-reference/keywords/set.md)

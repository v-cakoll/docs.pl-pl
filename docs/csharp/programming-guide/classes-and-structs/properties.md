---
title: Właściwości — Przewodnik programowania w języku C#
description: Właściwość w języku C# jest członkiem, który używa metod dostępu do odczytywania, zapisywania lub obliczania wartości pola prywatnego, tak jakby była publiczną składową danych.
ms.date: 03/10/2017
f1_keywords:
- cs.properties
helpviewer_keywords:
- properties [C#]
- C# language, properties
ms.assetid: e295a8a2-b357-4ee7-a12e-385a44146fa8
ms.openlocfilehash: 231e8e6a11f2655ccdea5489f054910a1ecf2586
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86863945"
---
# <a name="properties-c-programming-guide"></a>Właściwości (Przewodnik programowania w języku C#)

Właściwość jest członkiem, który zapewnia elastyczny mechanizm odczytu, zapisu lub obliczania wartości pola prywatnego. Właściwości mogą być używane tak, jakby były publicznymi elementami członkowskimi danych, ale w rzeczywistości są to specjalne metody nazywane metodami *dostępu*. Dzięki temu można łatwo uzyskać dostęp do danych, a następnie zapewnić bezpieczeństwo i elastyczność metod.  

## <a name="properties-overview"></a>Przegląd właściwości  
  
- Właściwości umożliwiają klasy udostępnianie publicznego sposobu pobierania i ustawiania wartości podczas ukrywania implementacji lub kodu weryfikacyjnego.  
  
- Metoda dostępu [Get](../../language-reference/keywords/get.md) właściwości służy do zwracania wartości właściwości, a metoda dostępu do właściwości [zestawu](../../language-reference/keywords/set.md) jest używana do przypisywania nowej wartości. Te metody dostępu mogą mieć różne poziomy dostępu. Aby uzyskać więcej informacji, zobacz [ograniczanie dostępności metody](./restricting-accessor-accessibility.md)dostępu.  
  
- Słowo kluczowe [Value](../../language-reference/keywords/value.md) służy do definiowania wartości przypisywanej przez `set` metodę dostępu.  
- Właściwościami mogą być *Odczyt i zapis* (mają zarówno `get` metodę dostępu, jak i `set` akcesor), *tylko do odczytu* (mają `get` Akcesory, ale nie `set` metodę dostępu) lub *tylko do zapisu* (mają `set` Akcesory, ale nie `get` metodę dostępu). Właściwości tylko do zapisu są rzadkie i najczęściej są używane do ograniczania dostępu do poufnych danych.

- Proste właściwości, które nie wymagają niestandardowego kodu dostępu, można zaimplementować jako definicje treści wyrażenia lub jako właściwości, które są [implementowane](./auto-implemented-properties.md).

## <a name="properties-with-backing-fields"></a>Właściwości z polami zapasowymi

Jeden wzorzec podstawowy do implementowania właściwości obejmuje użycie prywatnego pola zapasowego w celu ustawienia i pobrania wartości właściwości. `get`Metoda dostępu zwraca wartość pola prywatnego, a `set` metoda dostępu może wykonać pewne sprawdzanie poprawności danych przed przypisaniem wartości do pola prywatnego. Oba metody dostępu mogą także wykonać konwersję lub obliczenia danych przed ich zapisaniem lub zwróceniem.

Poniższy przykład ilustruje ten wzorzec. W tym przykładzie `TimePeriod` Klasa reprezentuje interwał czasu. Wewnętrznie Klasa przechowuje przedział czasu (w sekundach) w polu prywatnym o nazwie `_seconds` . Właściwość do odczytu i zapisu o nazwie `Hours` umożliwia klientowi określenie przedziału czasu w godzinach. Zarówno, `get` jak i metody `set` dostępu, wykonują wymagane konwersji między godzinami i sekundami. Ponadto `set` metoda dostępu sprawdza poprawność danych i zgłasza, że <xref:System.ArgumentOutOfRangeException> Liczba godzin jest nieprawidłowa.

 [!code-csharp[Properties#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-1.cs)]  
  
## <a name="expression-body-definitions"></a>Definicje treści wyrażenia  

 Metody dostępu do właściwości często składają się z jednowierszowych instrukcji, które po prostu przypisują lub zwracają wynik wyrażenia. Te właściwości można zaimplementować jako elementy członkowskie z wyrażeniami. Definicje treści wyrażenia składają się z `=>` symbolu, a po nim wyrażenie do przypisania lub pobrania z właściwości.

 Począwszy od języka C# 6, właściwości tylko do odczytu mogą implementować `get` metodę dostępu jako składowaną wyrażeniem. W takim przypadku nie `get` jest używane słowo kluczowe metody dostępu ani `return` słowo kluczowe. W poniższym przykładzie jest implementowana właściwość tylko do odczytu `Name` jako składowa wyrażeń.

 [!code-csharp[Properties#2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-2.cs)]  

 Począwszy od języka C# 7,0, zarówno, jak `get` i `set` metodę dostępu można zaimplementować jako elementy członkowskie z wyrażeniami. W takim przypadku `get` `set` słowa kluczowe i muszą być obecne. Poniższy przykład ilustruje użycie definicji treści wyrażenia dla obu metod dostępu. Należy zauważyć, że `return` słowo kluczowe nie jest używane z `get` akcesorem.

  [!code-csharp[Properties#3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-3.cs)]  

## <a name="auto-implemented-properties"></a>Właściwości zaimplementowane wstępnie

W niektórych przypadkach właściwości `get` i metody `set` dostępu po prostu przypisują wartość lub pobierze wartość z pola zapasowego bez uwzględniania dodatkowej logiki. Za pomocą zaimplementowanych właściwości, można uprościć kod, gdy kompilator języka C# w niewidoczny sposób udostępnia pole zapasowe.

Jeśli właściwość ma zarówno `get` , jak i `set` metodę dostępu, oba muszą być implementowane. Należy zdefiniować właściwość, która jest implementowana przy użyciu `get` `set` słów kluczowych i bez podawania żadnej implementacji. Poniższy przykład powtarza poprzedni, z tą różnicą, że `Name` i `Price` są właściwościami, które są implementowane. Należy zauważyć, że w przykładzie jest również usuwany Konstruktor sparametryzowany, dzięki czemu `SaleItem` obiekty są teraz inicjowane z wywołaniem konstruktora bez parametrów i [inicjatora obiektów](object-and-collection-initializers.md).

  [!code-csharp[Properties#4](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-4.cs)]  

## <a name="related-sections"></a>Sekcje pokrewne  
  
- [Używanie właściwości](./using-properties.md)  
  
- [Właściwości interfejsu](./interface-properties.md)  
  
- [Porównanie właściwości i indeksatorów](../indexers/comparison-between-properties-and-indexers.md)  
  
- [Ograniczanie dostępności metody dostępu](./restricting-accessor-accessibility.md)  
  
- [Właściwości zaimplementowane automatycznie](./auto-implemented-properties.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [Właściwości](~/_csharplang/spec/classes.md#properties) w [specyfikacji języka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Używanie właściwości](./using-properties.md)
- [Indexers (Indeksatory)](../indexers/index.md)
- [Get — słowo kluczowe](../../language-reference/keywords/get.md)
- [Set — słowo kluczowe](../../language-reference/keywords/set.md)

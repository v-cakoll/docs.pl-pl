---
title: Właściwości — C# Przewodnik programowania
ms.date: 03/10/2017
f1_keywords:
- cs.properties
helpviewer_keywords:
- properties [C#]
- C# language, properties
ms.assetid: e295a8a2-b357-4ee7-a12e-385a44146fa8
ms.openlocfilehash: 4f83d574357aa725b955870e3d93aa1f8222723a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714707"
---
# <a name="properties-c-programming-guide"></a>Właściwości (Przewodnik programowania w języku C#)

Właściwość jest członkiem, który zapewnia elastyczny mechanizm odczytu, zapisu lub obliczania wartości pola prywatnego. Właściwości mogą być używane tak, jakby były publicznymi elementami członkowskimi danych, ale w rzeczywistości są to specjalne metody nazywane metodami *dostępu*. Dzięki temu można łatwo uzyskać dostęp do danych, a następnie zapewnić bezpieczeństwo i elastyczność metod.  

## <a name="properties-overview"></a>Przegląd właściwości  
  
- Właściwości umożliwiają klasy udostępnianie publicznego sposobu pobierania i ustawiania wartości podczas ukrywania implementacji lub kodu weryfikacyjnego.  
  
- Metoda dostępu [Get](../../language-reference/keywords/get.md) właściwości służy do zwracania wartości właściwości, a metoda dostępu do właściwości [zestawu](../../language-reference/keywords/set.md) jest używana do przypisywania nowej wartości. Te metody dostępu mogą mieć różne poziomy dostępu. Aby uzyskać więcej informacji, zobacz [ograniczanie dostępności metody](./restricting-accessor-accessibility.md)dostępu.  
  
- Słowo kluczowe [Value](../../language-reference/keywords/value.md) służy do definiowania wartości przypisywanej przez metodę dostępu `set`.  
- Właściwościami mogą być *Odczyt-zapis* (mają zarówno `get`, jak i metodę dostępu `set`), *tylko do odczytu* (mają `get` metodę dostępu, ale nie ma metody dostępu do `set`) ani tylko do *zapisu* (mają `set` metodę dostępu, ale bez metody dostępu `get`). Właściwości tylko do zapisu są rzadkie i najczęściej są używane do ograniczania dostępu do poufnych danych.

- Proste właściwości, które nie wymagają niestandardowego kodu dostępu, można zaimplementować jako definicje treści wyrażenia lub jako właściwości, które są [implementowane](./auto-implemented-properties.md).
 
## <a name="properties-with-backing-fields"></a>Właściwości z polami zapasowymi

Jeden wzorzec podstawowy do implementowania właściwości obejmuje użycie prywatnego pola zapasowego w celu ustawienia i pobrania wartości właściwości. Metoda dostępu `get` zwraca wartość pola prywatnego, a metoda dostępu `set` może wykonać pewne sprawdzanie poprawności danych przed przypisaniem wartości do pola prywatnego. Oba metody dostępu mogą także wykonać konwersję lub obliczenia danych przed ich zapisaniem lub zwróceniem.

Poniższy przykład ilustruje ten wzorzec. W tym przykładzie Klasa `TimePeriod` reprezentuje interwał czasu. Wewnętrznie Klasa przechowuje przedział czasu (w sekundach) w polu prywatnym o nazwie `_seconds`. Właściwość do odczytu i zapisu o nazwie `Hours` umożliwia klientowi określenie przedziału czasu w godzinach. Zarówno `get`, jak i metody dostępu `set` wykonują wymaganą konwersję między godzinami i sekundami. Ponadto metoda dostępu `set` sprawdza poprawność danych i zgłasza <xref:System.ArgumentOutOfRangeException>, jeśli liczba godzin jest nieprawidłowa. 
   
 [!code-csharp[Properties#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-1.cs)]  
  
## <a name="expression-body-definitions"></a>Definicje treści wyrażenia  

 Metody dostępu do właściwości często składają się z jednowierszowych instrukcji, które po prostu przypisują lub zwracają wynik wyrażenia. Te właściwości można zaimplementować jako elementy członkowskie z wyrażeniami. Definicje treści wyrażenia składają się z symbolu `=>`, po którym następuje wyrażenie, które ma zostać przypisane do właściwości lub z niego pobrane.

 Począwszy od C# 6, właściwości tylko do odczytu mogą zaimplementować metodę dostępu `get`ną jako składowa wyrażeń. W takim przypadku nie jest używane słowo kluczowe metody dostępu `get` ani słowa kluczowego `return`. Poniższy przykład implementuje Właściwość `Name` tylko do odczytu jako element członkowski posiadający wyrażenie.

 [!code-csharp[Properties#2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-2.cs)]  

 Począwszy od C# 7,0, zarówno `get`, jak i metodę dostępu `set` można zaimplementować jako elementy członkowskie z wyrażeniami. W takim przypadku `get` i `set` słowa kluczowe muszą być obecne. Poniższy przykład ilustruje użycie definicji treści wyrażenia dla obu metod dostępu. Należy zauważyć, że słowo kluczowe `return` nie jest używane z akcesorem `get`.
 
  [!code-csharp[Properties#3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-3.cs)]  

## <a name="auto-implemented-properties"></a>Właściwości zaimplementowane wstępnie

W niektórych przypadkach właściwości `get` i metody dostępu `set` po prostu przypisują wartość lub pobierze wartość z pola zapasowego bez uwzględniania dodatkowej logiki. Za pomocą zaimplementowanych właściwości, można uprościć kod, gdy C# kompilator nieprzezroczystie udostępnia pole zapasowe. 

Jeśli właściwość ma zarówno `get`, jak i metodę dostępu `set`, oba muszą być implementowane. Należy zdefiniować właściwość, która jest implementowana przy użyciu słów kluczowych `get` i `set` bez podawania żadnej implementacji. Poniższy przykład powtarza poprzedni, z tą różnicą, że `Name` i `Price` są właściwościami, które są implementowane. Należy zauważyć, że w przykładzie jest również usuwany Konstruktor sparametryzowany, dzięki czemu obiekty `SaleItem` są teraz inicjowane z wywołaniem konstruktora bez parametrów i [inicjatora obiektów](object-and-collection-initializers.md).

  [!code-csharp[Properties#4](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-4.cs)]  

## <a name="related-sections"></a>Sekcje pokrewne  
  
- [Używanie właściwości](./using-properties.md)  
  
- [Właściwości interfejsu](./interface-properties.md)  
  
- [Porównanie właściwości i indeksatorów](../indexers/comparison-between-properties-and-indexers.md)  
  
- [Ograniczanie dostępności metody dostępu](./restricting-accessor-accessibility.md)  
  
- [Właściwości zaimplementowane automatycznie](./auto-implemented-properties.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [Właściwości](~/_csharplang/spec/classes.md#properties) w [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Używanie właściwości](./using-properties.md)
- [Indeksatory](../indexers/index.md)
- [Get — słowo kluczowe](../../language-reference/keywords/get.md)
- [Set — słowo kluczowe](../../language-reference/keywords/set.md)

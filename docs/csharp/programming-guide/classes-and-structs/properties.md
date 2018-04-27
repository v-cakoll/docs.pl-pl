---
title: Właściwości (Przewodnik programowania w języku C#)
ms.date: 03/10/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.properties
helpviewer_keywords:
- properties [C#]
- C# language, properties
ms.assetid: e295a8a2-b357-4ee7-a12e-385a44146fa8
caps.latest.revision: 38
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 186384c0a251d72b8726b3ae2f8f3faf0e6e008f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="properties-c-programming-guide"></a>Właściwości (Przewodnik programowania w języku C#)

Właściwość jest element członkowski, który zapewnia elastyczne mechanizm do odczytu, zapisu lub obliczenia wartości pole prywatne. Właściwości mogą być używane jako, jeśli są one publiczne elementy członkowskie danych, ale są faktycznie specjalne metody wywołane *metody dostępu*. To umożliwia danych można łatwo uzyskać dostęp oraz i nadal podwyższyć poziom bezpieczeństwa i elastyczność metody.  

## <a name="properties-overview"></a>Przegląd właściwości  
  
- Właściwości włączenia klasy ujawniać publicznego sposób pobierania i ustawiania wartości, podczas ukrywanie implementacji lub weryfikacji kodu.  
  
- A [uzyskać](../../../csharp/language-reference/keywords/get.md) metody dostępu właściwości służy do zwracania wartości właściwości i [ustawić](../../../csharp/language-reference/keywords/set.md) metody dostępu właściwości jest używana do przypisywania nową wartość. Te metody dostępu może mieć różne poziomy dostępu. Aby uzyskać więcej informacji, zobacz [Ograniczanie dostępności metody dostępu](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).  
  
- [Wartość](../../../csharp/language-reference/keywords/value.md) — słowo kluczowe jest używane do definiowania wartość przypisywane przez `set` dostępu.  
- Właściwości mogą być *odczytu i zapisu* (zarówno mają `get` i `set` akcesor), *tylko do odczytu* (mają `get` dostępu, ale nie `set` dostępu), lub *tylko do zapisu* (mają `set` dostępu, ale nie `get` dostępu). Właściwości tylko do zapisu są rzadko i są najczęściej używane do ograniczania dostępu do poufnych danych.

- Proste właściwości, które wymagają żaden kod dostępu niestandardowych można zaimplementować jako wyrażenie treści definicji lub [właściwości zaimplementowane automatycznie](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).
 
## <a name="properties-with-backing-fields"></a>Właściwości z kopii pól

Jeden podstawowy wzorzec wykonywania właściwość polega na użyciu polem zapasowym prywatnej ustawiania i pobierania wartości właściwości. `get` Akcesor zwraca wartość pola prywatne i `set` dostępu może wykonywać niektórych sprawdzania poprawności danych przed przypisywanie wartości do pola prywatne. Obu metod dostępu może również wykonać niektóre konwersji lub obliczeń na danych przed jest przechowywany lub zwrócona.

Poniższy przykład przedstawia tego wzorca. W tym przykładzie `TimePeriod` klasa reprezentuje interwał czasu. Wewnętrznie klasa przechowuje przedział czasu w sekundach w prywatnej pole o nazwie `seconds`. Właściwości odczytu / zapisu o nazwie `Hours` umożliwia klientowi określenie interwału czasu w godzinach. Zarówno `get` i `set` metody dostępu wykonania konwersji konieczne godziny i sekundy. Ponadto `set` akcesor sprawdza poprawność danych i zgłasza <xref:System.ArgumentOutOfRangeException> Jeśli liczba godzin jest nieprawidłowy. 
   
 [!code-csharp[Properties#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-1.cs)]  
  
## <a name="expression-body-definitions"></a>Definicje treść wyrażenia  

 Metod dostępu do właściwości często składają się z pojedynczej linii instrukcji, które właśnie przypisać lub zwrócenia wyniku wyrażenia. Te właściwości można zaimplementować jako członków zabudowanych wyrażenia. Definicje treści wyrażeń składają się z `=>` symbol następuje wyrażenie, tak aby przypisać lub pobrać z właściwości.

 Począwszy od języka C# 6 właściwości tylko do odczytu można zaimplementować `get` akcesor jako element członkowski zabudowanych wyrażenia. W takim przypadku, ani `get` — słowo kluczowe dostępu ani `return` słowo kluczowe jest używane. Poniższy przykład implementuje tylko do odczytu `Name` właściwość jako element członkowski zabudowanych wyrażenia.

 [!code-csharp[Properties#2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-2.cs)]  

 Począwszy od C# 7.0, zarówno `get` i `set` akcesor można zaimplementować jako członków zabudowanych wyrażenia. W takim przypadku `get` i `set` słowa kluczowe muszą być obecne. Poniższy przykład przedstawia użycie wyrażenia treści definicji dla obu metod dostępu. Należy pamiętać, że `return` — słowo kluczowe nie jest używany z `get` metody dostępu.
 
  [!code-csharp[Properties#3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-3.cs)]  

## <a name="auto-implemented-properties"></a>Właściwości zaimplementowane automatycznie

W niektórych przypadkach właściwość `get` i `set` tylko przypisanie wartości do metody dostępu lub pobrać wartości z polem zapasowym bez uwzględniania wszelka logika dodatkowe. Przy użyciu automatycznie implementowanych właściwości, można uprościć kod przy jednoczesnym zachowaniu kompilatora C# niewidocznie Podaj pola zapasowego. 

Jeśli właściwość ma zarówno atrybut `get` i `set` metody dostępu muszą mieć jednocześnie zaimplementowane automatycznie. Definiowanie właściwości zaimplementowane automatycznie za pomocą `get` i `set` słowa kluczowe bez podawania implementacji. Poniższy przykład powtarza poprzedniej wersji, z wyjątkiem `Name` i `Price` są automatycznie implementowane właściwości. Należy pamiętać, że przykładzie spowoduje również usunięcie parametryzowanym konstruktorem, dzięki czemu `SaleItem` obiekty są teraz inicjowane w wyniku wywołania konstruktora domyślnego i [inicjatora obiektu](object-and-collection-initializers.md).

  [!code-csharp[Properties#4](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-4.cs)]  

## <a name="related-sections"></a>Sekcje pokrewne  
  
-   [Używanie właściwości](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [Właściwości interfejsu](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)  
  
-   [Porównanie właściwości i indeksatorów](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [Ograniczanie dostępności metody dostępu](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
-   [Właściwości zaimplementowane automatycznie](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Używanie właściwości](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
 [Indeksatory](../../../csharp/programming-guide/indexers/index.md)  
 [Get — słowo kluczowe](../../../csharp/language-reference/keywords/get.md)    
 [set — słowo kluczowe](../../../csharp/language-reference/keywords/set.md)    

---
title: Odwołanie w C#
ms.date: 02/14/2017
helpviewer_keywords:
- Visual C#, language reference
- language reference [C#]
- Programmer's Reference for C#
- C# language, reference
- reference, C# language
ms.assetid: 06de3167-c16c-4e1a-b3c5-c27841d4569a
ms.openlocfilehash: 45352d97372e556627ead75d969f088de9c85bd0
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833244"
---
# <a name="c-reference"></a>Odwołanie w C#
Ta sekcja zawiera materiały źródłowe dotyczące C# słów kluczowych, operatorów, znaki specjalne, dyrektyw preprocesora, opcji kompilatora i kompilatora błędy i ostrzeżenia.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Słowa kluczowe języka C#](../../csharp/language-reference/keywords/index.md)  
 Zawiera łącza do informacji na temat C# słów kluczowych i składni.  
  
 [Operatory języka C#](../../csharp/language-reference/operators/index.md)  
 Zawiera łącza do informacji na temat C# operatorów i składni.  

 [Znaki specjalne języka C#](../../csharp/language-reference/tokens/index.md)  
 Zawiera łącza do informacji na temat kontekstowe znaki specjalne w C# i ich użycia.  

 [Dyrektywy preprocesora C#](../../csharp/language-reference/preprocessor-directives/index.md)  
 Zawiera łącza do informacji dotyczących kompilatora poleceń do osadzania w C# kodu źródłowego.  
  
 [Opcje kompilatora C#](../../csharp/language-reference/compiler-options/index.md)  
 Zawiera informacje na temat opcji kompilatora i sposobu ich używania.  
  
 [Błędy kompilatora C#](../../csharp/language-reference/compiler-messages/index.md)  
 Obejmuje wstawki kodu demonstrujące przyczynę i dodaje się korekcji C# kompilatora, błędy i ostrzeżenia.  
  
 [Specyfikacja języka C#](../../../_csharplang/spec/introduction.md)  
 C# Specyfikacji języka w wersji 6.0. Jest to szkice C# języka w wersji 6.0. W wersji 5.0 wydano w grudniu 2017 r jako [Standard ECMA-334 5th Edition](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf) dokumentu.

Funkcje, które zostały wdrożone w C# wersji po 6.0 są reprezentowane w propozycji specyfikacji języka. W tych dokumentach opisano różnice do specyfikacji języka, aby można było dodać te nowe funkcje.

 [C#7.0 propozycje języka](../../../_csharplang/proposals/csharp-7.0/pattern-matching.md)  
 Istnieje wiele nowych funkcji w C# 7.0. One obejmują wzorzec dopasowania, lokalnych funkcji, deklaracji zmiennych, throw wyrażeń, literały binarne oraz separatory cyfr. Ten folder zawiera specyfikacje dla każdej z tych funkcji.
  
 [C#7.1 propozycje języka](../../../_csharplang/proposals/csharp-7.1/async-main.md)  
 Są dostępne nowe funkcje dodane w C# 7.1. Po pierwsze, można napisać `Main` metodę, która zwraca `Task` lub `Task<int>`. Dzięki temu można dodać `async` modyfikatora `Main`. `default` Wyrażenie może być używana bez typu w lokalizacjach, w której można wywnioskować typu. Ponadto można wywnioskować nazwy elementów członkowskich spójnej kolekcji. Na koniec dopasowywania do wzorca można za pomocą typów ogólnych.

 [C#7.2 propozycje języka](../../../_csharplang/proposals/csharp-7.2/readonly-ref.md)  
 C#7.2 dodano wiele małych funkcji. Argumenty można przekazać za pomocą odwołań tylko do odczytu `in` — słowo kluczowe. Istnieje kilka zmian niskiego poziomu do obsługi kompilacji bezpieczeństwa dla `Span` i typów pokrewnych. Można użyć argumenty nazwane, gdzie argumenty nowszych są pozycyjne, w niektórych sytuacjach. `private protected` Modyfikator dostępu pozwala na określenie, że obiekty wywołujące są ograniczone do typów pochodnych zaimplementowane w tym samym zestawie. `?:` Operator może rozpoznać odwołania do zmiennej. Możesz również sformatować cyfry szesnastkowe i binarny przy użyciu wiodący separator cyfr.

 [C#7.3 propozycje języka](../../../_csharplang/proposals/csharp-7.3/blittable.md)  
 C#7.3 jest innej wersji punkt, który zawiera kilka małych aktualizacji. Można użyć nowego ograniczenia dotyczące parametrów typu ogólnego. Inne zmiany w ułatwienia pracy z `fixed` pól, w tym za pomocą [ `stackalloc` ](./operators/stackalloc.md) alokacji. Zmienne lokalne są zadeklarowane za pomocą `ref` — słowo kluczowe może być reasssigned do odwoływania się do nowego magazynu. Atrybuty można umieścić na automatycznie implementowane właściwości przeznaczonych do pola pomocniczego generowanych przez kompilator. Zmienne wyrażeń może służyć w inicjatorach. Kolekcje można porównywać pod względem równości (lub nierówności). Wprowadzono również kilka ulepszeń do przeciążenia.
  
 [C#8.0 propozycje language](../../../_csharplang/proposals/csharp-8.0/nullable-reference-types.md) C# 8.0 jest dostępna w wersji zapoznawczej. Następujące propozycje są aktualne wersje specyfikacji dla tych funkcji. Niektóre są bardziej szczegółowy; Niektóre są nadal w toku. Funkcje, które zostały wprowadzone do użytku w wersjach zapoznawczych obejmują typy dopuszczające wartości null odwołań, dopasowanie wzorca cykliczne, strumieni asynchronicznych, zakresy i indeksów, na podstawie przy użyciu wzorca i za pomocą deklaracje i przypisania łączącego o wartości null.
  
## <a name="related-sections"></a>Sekcje pokrewne  

 [Przewodnik dla języka C#](../../csharp/index.md)  
 Udostępnia portal wizualizacji C# dokumentacji.  
  
 [Używanie środowiska programistycznego Visual Studio dla C#](/visualstudio/csharp-ide/using-the-visual-studio-development-environment-for-csharp)  
 Zawiera łącza do pojęć i tematów zadań, które opisują IDE i edytorem.  
  
 [Przewodnik programowania w języku C#](../../csharp/programming-guide/index.md)  
 Zawiera informacje o sposobie używania C# języka programowania.

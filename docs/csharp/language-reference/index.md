---
title: Dokumentacja języka C#
ms.date: 02/14/2017
helpviewer_keywords:
- Visual C#, language reference
- language reference [C#]
- Programmer's Reference for C#
- C# language, reference
- reference, C# language
ms.assetid: 06de3167-c16c-4e1a-b3c5-c27841d4569a
ms.openlocfilehash: 4875e53327e24c4b5983a4a3b79b5beced368725
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74428604"
---
# <a name="c-reference"></a>Dokumentacja języka C#

Ta sekcja zawiera materiały referencyjne dotyczące słów kluczowych c#, operatorów, znaków specjalnych, dyrektyw preprocesora, opcji kompilatora oraz błędów i ostrzeżeń kompilatora.  
  
## <a name="in-this-section"></a>W tej sekcji

 [Słowa kluczowe języka C#](./keywords/index.md)  
 Zawiera łącza do informacji o słowach kluczowych języka C# i składni.  
  
 [Operatory języka C#](./operators/index.md)  
 Zawiera łącza do informacji o operatorach języka C# i składni.  

 [Znaki specjalne języka C#](./tokens/index.md)  
 Zawiera łącza do informacji o specjalnych znaków kontekstowych w języku C# i ich użycia.  

 [Dyrektywy przedprocesorowe C#](./preprocessor-directives/index.md)  
 Zawiera łącza do informacji o poleceniach kompilatora do osadzania w kodzie źródłowym języka C#.  
  
 [Opcje kompilatora Języka C#](./compiler-options/index.md)  
 Zawiera informacje o opcjach kompilatora i jak z nich korzystać.  
  
 [Błędy kompilatora Języka C#](./compiler-messages/index.md)  
 Zawiera fragmenty kodu, które pokazują przyczynę i korekcję błędów kompilatora C#i ostrzeżenia.  
  
 [Specyfikacja języka C#](../../../_csharplang/spec/introduction.md)  
 Specyfikacja języka Języka C# 6.0. Jest to projekt wniosku dla języka C# 6.0. Niniejszy dokument zostanie udoskonalony dzięki współpracy z komitetem normalizacyjnym ECMA C#. Wersja 5.0 została wydana w grudniu 2017 r. jako standardowy dokument [ECMA-334 5th Edition.](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf)

Funkcje, które zostały zaimplementowane w wersji Języka C# po 6.0 są reprezentowane w propozycjach specyfikacji języka. Dokumenty te opisują różnice do specyfikacji języka w celu dodania tych nowych funkcji. Są one w formie projektu wniosku. Specyfikacje te zostaną udoskonalone i przedłożone komitetowi normalizacyjnemu ECMA w celu formalnego przeglądu i włączenia do przyszłej wersji normy C#.

 [Propozycje specyfikacji języka C# 7.0](../../../_csharplang/proposals/csharp-7.0/pattern-matching.md)  
 Istnieje wiele nowych funkcji zaimplementowanych w języku C# 7.0. Obejmują one dopasowywanie wzorców, funkcje lokalne, deklaracje zmiennych, wyrażenia rzutów, literały binarne i separatory cyfr. Ten folder zawiera specyfikacje dla każdej z tych funkcji.
  
 [Propozycje specyfikacji C# 7.1](../../../_csharplang/proposals/csharp-7.1/async-main.md)  
 W języku C# 7.1 dodano nowe funkcje. Najpierw można napisać `Main` metodę, `Task` która `Task<int>`zwraca lub . Dzięki temu można `async` dodać modyfikator do `Main`. Wyrażenie `default` może być używane bez typu w lokalizacjach, w których można wywnioskować typ. Ponadto nazwy elementów członkowskich krotki można wywnioskować. Na koniec dopasowywania wzorców można używać z generycznych.

 [Propozycje specyfikacji C# 7.2](../../../_csharplang/proposals/csharp-7.2/readonly-ref.md)  
 C# 7.2 dodał szereg małych funkcji. Argumenty można przekazywać przez `in` odwołanie tylko do odczytu za pomocą słowa kluczowego. Istnieje wiele zmian niskiego poziomu do obsługi bezpieczeństwa kompilacji czasu dla `Span` i powiązanych typów. Można użyć nazwanych argumentów, gdzie później argumenty są pozycyjne, w niektórych sytuacjach. Modyfikator `private protected` dostępu umożliwia określenie, że obiekty wywołujące są ograniczone do typów pochodnych zaimplementowanych w tym samym zestawie. Operator `?:` może rozpoznać odwołanie do zmiennej. Można również formatować liczby szesnastkowe i binarne za pomocą separatora cyfr wiodących.

 [Propozycje specyfikacji C# 7.3](../../../_csharplang/proposals/csharp-7.3/blittable.md)  
 C# 7.3 to kolejna wersja punktowa, która zawiera kilka małych aktualizacji. Można użyć nowych ograniczeń parametrów typu ogólnego. Inne zmiany ułatwiają pracę `fixed` z polami, w tym przy użyciu [`stackalloc`](./operators/stackalloc.md) alokacji. Zmienne lokalne zadeklarowane `ref` za pomocą słowa kluczowego mogą zostać ponownie przypisane w celu odwoływania się do nowego magazynu. Atrybuty można umieścić na właściwościach implementowanych automatycznie, które są przeznaczone dla pola zapasowego wygenerowanego przez kompilator. Zmienne wyrażenia mogą być używane w inicjatorach. Krotek można porównać do równości (lub nierówności). Wprowadzono również pewne ulepszenia w rozdzielczości przeciążenia.
  
 [Propozycje specyfikacji języka C# 8.0](../../../_csharplang/proposals/csharp-8.0/nullable-reference-types.md)  
 C# 8.0 jest dostępny z .NET Core 3.0. Funkcje obejmują typy odwołań nullable, cykliczne dopasowywanie wzorców, domyślne metody interfejsu, strumienie asynchroniczne, zakresy i indeksy, wzorzec oparty przy użyciu i przy użyciu deklaracji, null łączenia przypisania i readonly elementów członkowskich wystąpienia.
  
## <a name="related-sections"></a>Sekcje pokrewne  

 [Używanie środowiska programistycznego Visual Studio dla języka C#](/visualstudio/get-started/csharp)  
 Zawiera łącza do tematów koncepcyjnych i zadań, które opisują IDE i Edytor.  
  
 [Przewodnik programowania języka C#](../programming-guide/index.md)  
 Zawiera informacje dotyczące używania języka programowania Języka C#.

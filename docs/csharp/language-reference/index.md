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
ms.openlocfilehash: 96fd360342a3bc0f82df37761abb372bdcaa8d7a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606124"
---
# <a name="c-reference"></a>Odwołanie w C#
Ta sekcja zawiera materiały referencyjne C# dotyczące słów kluczowych, operatorów, znaków specjalnych, dyrektyw preprocesora, opcji kompilatora i błędów i ostrzeżeń kompilatora.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Słowa kluczowe języka C#](./keywords/index.md)  
 Zawiera łącza do informacji o C# słowach kluczowych i składni.  
  
 [Operatory języka C#](./operators/index.md)  
 Zawiera łącza do informacji na C# temat operatorów i składni.  

 [Znaki specjalne języka C#](./tokens/index.md)  
 Zawiera łącza do informacji na temat specjalnych znaków kontekstowych w programie C# i ich użycia.  

 [Dyrektywy preprocesora C#](./preprocessor-directives/index.md)  
 Zawiera łącza do informacji o poleceniach kompilatora osadzania w C# kodzie źródłowym.  
  
 [Opcje kompilatora C#](./compiler-options/index.md)  
 Zawiera informacje o opcjach kompilatora i sposobach ich użycia.  
  
 [Błędy kompilatora C#](./compiler-messages/index.md)  
 Zawiera fragmenty kodu, które pokazują przyczynę i korekcję C# błędów i ostrzeżeń kompilatora.  
  
 [C#Specyfikacja języka](../../../_csharplang/spec/introduction.md)  
 Specyfikacja C# języka 6,0. Jest to wersja robocza propozycja C# języka 6,0. Wersja 5,0 została wydana w grudniu 2017 jako standardowy dokument [ECMA-334 5](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf) .

Funkcje, które zostały zaimplementowane w C# wersjach po 6,0 są reprezentowane w propozycjach specyfikacji języka. Te dokumenty opisują różnice w specyfikacji języka w celu dodania tych nowych funkcji.

 [C#Propozycje dotyczące języka 7,0](../../../_csharplang/proposals/csharp-7.0/pattern-matching.md)  
 Istnieje kilka nowych funkcji wdrożonych w C# 7,0. Obejmują one Dopasowywanie wzorców, funkcje lokalne, deklaracje zmiennych wyjściowych, wyrażenia throw, literały binarne i separatory cyfr. Ten folder zawiera specyfikacje dla każdej z tych funkcji.
  
 [C#Propozycje dotyczące języka 7,1](../../../_csharplang/proposals/csharp-7.1/async-main.md)  
 Dodano nowe funkcje w C# 7,1. Najpierw można napisać `Main` metodę zwracającą `Task` lub `Task<int>`. Pozwala to na dodanie `async` modyfikatora do. `Main` `default` Wyrażenia można użyć bez typu w lokalizacjach, w których można wywnioskować typ. Ponadto można wywnioskować nazwy elementów członkowskich krotki. Na koniec dopasowanie do wzorca może być używane z typami ogólnymi.

 [C#Propozycje dotyczące języka 7,2](../../../_csharplang/proposals/csharp-7.2/readonly-ref.md)  
 C#7,2 dodano wiele małych funkcji. Argumenty można przekazać przez odwołanie tylko do odczytu za `in` pomocą słowa kluczowego. Istnieją pewne zmiany niskiego poziomu, które umożliwiają obsługę bezpieczeństwa w czasie kompilacji dla `Span` i powiązanych typów. Można użyć nazwanych argumentów, jeśli późniejsze argumenty są pozycjonowane w niektórych sytuacjach. Modyfikator `private protected` dostępu pozwala określić, że wywołania są ograniczone do typów pochodnych wdrożonych w tym samym zestawie. `?:` Operator może rozpoznać odwołanie do zmiennej. Możesz również sformatować liczby szesnastkowe i binarne przy użyciu wiodącego separatora cyfr.

 [C#Propozycje dotyczące języka 7,3](../../../_csharplang/proposals/csharp-7.3/blittable.md)  
 C#7,3 to kolejna wersja punktu, która obejmuje kilka małych aktualizacji. Możesz użyć nowych ograniczeń dla parametrów typu ogólnego. Inne zmiany ułatwiają pracę z `fixed` polami, w tym za pomocą [`stackalloc`](./operators/stackalloc.md) przydziałów. Zmienne lokalne zadeklarowane za `ref` pomocą słowa kluczowego mogą być reasssigned w celu odwoływania się do nowego magazynu. Można umieścić atrybuty dla automatycznie implementowanych właściwości, które są przeznaczone dla pola zapasowego wygenerowanego przez kompilator. Zmiennych wyrażeń można używać w inicjatorach. Krotki można porównać pod kątem równości (lub nierówności). Wprowadzono również pewne ulepszenia dotyczące rozpoznawania przeciążenia.
  
 Propozycje dotyczące języka 8,0 [ C# ](../../../_csharplang/proposals/csharp-8.0/nullable-reference-types.md) C# 8,0 jest dostępny w wersji zapoznawczej. Poniższe propozycje są bieżącymi wersjami specyfikacji dla tych funkcji. Niektóre są bardziej kompletne. Niektóre nadal pracują w toku. Funkcje, które zostały wysłane w ramach wersji zapoznawczych, obejmują typy referencyjne dopuszczające wartość null, cykliczne Dopasowywanie wzorców, strumienie asynchroniczne, zakresy i indeksy, wzorzec oparty przy użyciu i używanie deklaracji oraz przypisanie łączenia wartości null.
  
## <a name="related-sections"></a>Sekcje pokrewne  

 [Przewodnik dla języka C#](../index.md)  
 Udostępnia Portal dokumentacji wizualnej C# .  
  
 [Używanie środowiska programistycznego Visual Studio dla C#](/visualstudio/csharp-ide/using-the-visual-studio-development-environment-for-csharp)  
 Zawiera łącza do tematów dotyczących pojęć i zadań, które opisują środowisko IDE i edytor.  
  
 [Przewodnik programowania w języku C#](../programming-guide/index.md)  
 Zawiera informacje o sposobach korzystania z C# języka programowania.

---
title: C#odwoła
ms.date: 02/14/2017
helpviewer_keywords:
- Visual C#, language reference
- language reference [C#]
- Programmer's Reference for C#
- C# language, reference
- reference, C# language
ms.assetid: 06de3167-c16c-4e1a-b3c5-c27841d4569a
ms.openlocfilehash: 4fed33272dbed50100a37aa9fcd30befc46435f9
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771843"
---
# <a name="c-reference"></a>C#odwoła

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
 Specyfikacja C# języka 6,0. Jest to wersja robocza propozycja C# języka 6,0. Ten dokument zostanie rafinowany przez współpracę z Komitetem standardowym C# ECMA. Wersja 5,0 została wydana w grudniu 2017 jako standardowy dokument [ECMA-334 5](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf) .

Funkcje, które zostały zaimplementowane w C# wersjach po 6,0 są reprezentowane w propozycjach specyfikacji języka. Te dokumenty opisują różnice w specyfikacji języka w celu dodania tych nowych funkcji. Są one w wersji roboczej formularza propozycji. Te specyfikacje zostaną ulepszone i przesłane do Komitetu standardów ECMA dla formalnego przeglądu i w przyszłych wersjach C# Standard.

 [C#7,0 propozycja specyfikacji](../../../_csharplang/proposals/csharp-7.0/pattern-matching.md)  
 Istnieje kilka nowych funkcji wdrożonych w C# 7,0. Obejmują one Dopasowywanie wzorców, funkcje lokalne, deklaracje zmiennych wyjściowych, wyrażenia throw, literały binarne i separatory cyfr. Ten folder zawiera specyfikacje dla każdej z tych funkcji.
  
 [C#7,1 propozycja specyfikacji](../../../_csharplang/proposals/csharp-7.1/async-main.md)  
 Dodano nowe funkcje w C# 7,1. Najpierw można napisać metodę `Main`, która zwraca `Task` lub `Task<int>`. Pozwala to na dodanie modyfikatora `async` do `Main`. Wyrażenia `default` można używać bez typu w lokalizacjach, w których można wywnioskować typ. Ponadto można wywnioskować nazwy elementów członkowskich krotki. Na koniec dopasowanie do wzorca może być używane z typami ogólnymi.

 [C#7,2 Propozycja specyfikacji](../../../_csharplang/proposals/csharp-7.2/readonly-ref.md)  
 C#7,2 dodano wiele małych funkcji. Argumenty można przekazać przez odwołanie tylko do odczytu za pomocą słowa kluczowego `in`. Istnieją pewne zmiany niskiego poziomu, które umożliwiają obsługę bezpieczeństwa w czasie kompilacji dla `Span` i typów pokrewnych. Można użyć nazwanych argumentów, jeśli późniejsze argumenty są pozycjonowane w niektórych sytuacjach. Modyfikator dostępu `private protected` umożliwia określenie, że wywołania są ograniczone do typów pochodnych wdrożonych w tym samym zestawie. Operator `?:` może rozpoznać odwołanie do zmiennej. Możesz również sformatować liczby szesnastkowe i binarne przy użyciu wiodącego separatora cyfr.

 [C#7,3 propozycja specyfikacji](../../../_csharplang/proposals/csharp-7.3/blittable.md)  
 C#7,3 to kolejna wersja punktu, która obejmuje kilka małych aktualizacji. Możesz użyć nowych ograniczeń dla parametrów typu ogólnego. Inne zmiany ułatwiają współpracę z polami `fixed`, w tym przy użyciu przydziałów [`stackalloc`](./operators/stackalloc.md) . Zmienne lokalne zadeklarowane za pomocą słowa kluczowego `ref` mogą być reasssigned w celu odwoływania się do nowego magazynu. Można umieścić atrybuty dla automatycznie implementowanych właściwości, które są przeznaczone dla pola zapasowego wygenerowanego przez kompilator. Zmiennych wyrażeń można używać w inicjatorach. Krotki można porównać pod kątem równości (lub nierówności). Wprowadzono również pewne ulepszenia dotyczące rozpoznawania przeciążenia.
  
 [C#8,0 propozycja specyfikacji](../../../_csharplang/proposals/csharp-8.0/nullable-reference-types.md)  
 C#8,0 jest dostępny z platformą .NET Core 3,0. Funkcje obejmują typy referencyjne dopuszczające wartość null, cykliczne dopasowywanie do wzorca, domyślne metody interfejsu, strumienie asynchroniczne, zakresy i indeksy, wzorzec oparty na używaniu i używaniu deklaracji, przypisywaniu łączenia zerowego i elementów członkowskich wystąpień tylko do odczytu.
  
## <a name="related-sections"></a>Sekcje pokrewne  

 [Przewodnik dla języka C#](../index.md)  
 Udostępnia Portal dokumentacji wizualnej C# .  
  
 [Używanie środowiska programistycznego Visual Studio dla C#](/visualstudio/get-started/csharp)  
 Zawiera łącza do tematów dotyczących pojęć i zadań, które opisują środowisko IDE i edytor.  
  
 [Przewodnik programowania w języku C#](../programming-guide/index.md)  
 Zawiera informacje o sposobach korzystania z C# języka programowania.

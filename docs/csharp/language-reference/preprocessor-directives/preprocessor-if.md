---
title: "#Jeśli dyrektywy preprocesora (odwołanie w C#)"
ms.date: 02/13/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 710452d6fddea239cb2e65901fd5ce56d6be699f
ms.sourcegitcommit: 08684dd61444c2f072b89b926370f750e456fca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="if-c-reference"></a>#if (odwołanie w C#)

Gdy wystąpi kompilatora C# `#if` dyrektywy, a następnie po pewnym czasie przez [#endif](preprocessor-endif.md) dyrektywy, kompiluje kod między dyrektywami tylko wtedy, gdy zdefiniowano określony symbol. W przeciwieństwie do C i C++ nie można przypisać wartości numerycznej symbolu. Wykonywanie instrukcji #if w języku C# jest wartość logiczna i tylko sprawdzenie, czy symbol został zdefiniowany lub nie. Na przykład:

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

Można używać operatorów [ == ](../operators/equality-comparison-operator.md) (równości) i [! =](../operators/not-equal-operator.md) (nierówność) tylko do testowania [true](../keywords/true.md) lub [false](../keywords/false.md). PRAWDA oznacza, że jest zdefiniowany symbol. Instrukcja `#if DEBUG` ma takie samo znaczenie jak `#if (DEBUG == true)`. Można używać operatorów [ && ](../operators/conditional-and-operator.md) (a), [&#124; &#124;](../operators/conditional-or-operator.md) (lub) i [!](../operators/logical-negation-operator.md) (nie) do oceny, czy zdefiniowano wiele symboli. Można także grupować symbole i operatory w nawiasach.

## <a name="remarks"></a>Uwagi

`#if`, wraz z [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md), i [#undef](preprocessor-undef.md) dyrektywy, umożliwia Dołącz lub Wyklucz kodu opartego na istnienie jednego lub więcej symboli. Może to być przydatne podczas kompilowania kodu dla kompilacji debugowania lub w przypadku kompilowania kodu dla określonej konfiguracji.

Warunkowe początku dyrektywy z `#if` dyrektywa musi być jawnie zakończona z `#endif` dyrektywy.

`#define` Umożliwia zdefiniowanie symbolu. Za pomocą symbolu wyrażenie przekazane do `#if` dyrektywy, wyrażenie daje w wyniku `true`.

Możesz również definiować symbol [/ define](../compiler-options/define-compiler-option.md) — opcja kompilatora. Można nie zdefiniowany symbol [#undef](preprocessor-undef.md).

Symbol, który definiuje z `/define` lub `#define` nie koliduje to z zmienna o takiej samej nazwie. To, że nazwa zmiennej nie powinien zostać przekazany do dyrektywy preprocesora i symbol będzie możliwe tylko w dyrektywie preprocesora.

Zakres symbol utworzone za pomocą `#define` jest plikiem, w którym została zdefiniowana.

System kompilacji jest również pamiętać o wstępnie zdefiniowanych symboli preprocesora reprezentująca różne [platform docelowych](../../../standard/frameworks.md). Są one przydatne podczas tworzenia aplikacji przeznaczonych dla więcej niż jedna implementacja .NET lub wersji.

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

Inne wstępnie zdefiniowane symbole obejmują stałe debugowania i śledzenia. Można zastąpić wartości projekt za pomocą `#define`. Symbol debugowania, na przykład jest automatycznie ustawiana w zależności od właściwości konfiguracji kompilacji (tryb "Debug" i "Release").

## <a name="examples"></a>Przykłady

Poniższy przykład pokazuje, jak definiować symbol test na pliku, a następnie sprawdź wartości symboli test i debugowania. Dane wyjściowe w tym przykładzie zależy od tego, czy projekt jest oparty na debugowanie czy wydanie trybu konfiguracji.

```csharp
#define MYTEST
using System;
public class MyClass
{
    static void Main()
    {
#if (DEBUG && !MYTEST)
        Console.WriteLine("DEBUG is defined");
#elif (!DEBUG && MYTEST)
        Console.WriteLine("MYTEST is defined");
#elif (DEBUG && MYTEST)
        Console.WriteLine("DEBUG and MYTEST are defined");  
#else
        Console.WriteLine("DEBUG and MYTEST are not defined");
#endif
    }
}
```

Poniższy przykład pokazuje, jak przetestować dla struktur inny element docelowy, dzięki czemu można używać nowszej interfejsów API, jeśli to możliwe:

```csharp
public class MyClass
{
    static void Main()
    {
#if NET40
        WebClient _client = new WebClient();
#else
        HttpClient _client = new HttpClient();
#endif
    }
    //...
}
```

## <a name="see-also"></a>Zobacz także

[Odwołanie w C#](../../../csharp/language-reference/index.md)  
[Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
[Dyrektywy preprocesora C#](index.md)  
[Porady: kompilowanie warunkowe ze śledzeniem i debugowaniem](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md).

---
title: '#Jeśli dyrektywa preprocesora (odwołanie w C#)'
ms.date: 06/30/2018
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: c54a1fe0dba5f6d57b03b2ffeb4f1737fadfe039
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406281"
---
# <a name="if-c-reference"></a>#if (odwołanie w C#)

Gdy kompilator języka C# napotka `#if` dyrektywy, a następnie po pewnym czasie przez [#endif](preprocessor-endif.md) dyrektywy, kompiluje kod między dyrektyw tylko wtedy, gdy zdefiniowano określonego symbolu. W przeciwieństwie do C i C++ nie można przypisać wartości numerycznej symbolu. Instrukcji #if w języku C# jest wartością logiczną, a tylko sprawdzenie, czy symbol został zdefiniowany lub nie. Na przykład:

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

Można używać operatorów [ == ](../operators/equality-comparison-operator.md) (równości) i [! =](../operators/not-equal-operator.md) (nierówność) tylko do testowania [true](../keywords/true.md) lub [false](../keywords/false.md). PRAWDA oznacza, że symbol jest zdefiniowany. Wykonywanie instrukcji `#if DEBUG` ma takie samo znaczenie jak `#if (DEBUG == true)`. Można używać operatorów [ && ](../operators/conditional-and-operator.md) (a) [ &#124; &#124; ](../operators/conditional-or-operator.md) (lub) i [!](../operators/logical-negation-operator.md) (nie) do oceny, czy zostały zdefiniowane wiele symboli. Można także grupować symboli i operatorów, za pomocą nawiasów.

## <a name="remarks"></a>Uwagi

`#if`, wraz z [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md), i [#undef](preprocessor-undef.md) dyrektyw, umożliwia Dołącz lub Wyklucz kod oparty na istnienie jednego lub wielu symboli. Może to być przydatne podczas kompilowania kodu do kompilacji debugowania lub podczas kompilowania dla konkretnej konfiguracji.

Warunkowe dyrektywy zaczyna się od `#if` dyrektywy jawnie muszą być zakończone znakiem `#endif` dyrektywy.

`#define` pozwala zdefiniować symbol. Za pomocą symbolu wyrażenia są przekazywane do `#if` dyrektywy, wyrażenie ma wartość `true`.

Można również zdefiniować symbol za pomocą [— Zdefiniuj](../compiler-options/define-compiler-option.md) — opcja kompilatora. Aby anulować definicję symbolu, użyj dyrektywy [#undef](preprocessor-undef.md).

Symbol, który zdefiniujesz z `-define` lub `#define` nie koliduje ze zmienną o takiej samej nazwie. Oznacza to, że nazwa zmiennej nie powinna być przekazywana do dyrektywy preprocesora i symbol może być oceniany tylko przez dyrektywy preprocesora.

Zakres symbolu utworzonych za pomocą `#define` jest plikiem, w którym został zdefiniowany.

System kompilacji jest również pamiętać o wstępnie zdefiniowanych symboli preprocesora reprezentująca różne [ustalać platformy docelowe](../../../standard/frameworks.md). Są one przydatne podczas tworzenia aplikacji przeznaczonych więcej niż jednej implementacji .NET lub wersji.

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

Inne wstępnie zdefiniowane symbole obejmują stałe debugowania i śledzenia. Można zastąpić wartości ustawione dla projektu za pomocą `#define`. Symbol debugowania, na przykład, jest automatycznie ustawiana w zależności od właściwości konfiguracji kompilacji (w trybie "Debug" lub "Release").

## <a name="examples"></a>Przykłady

Poniższy przykład pokazuje jak zdefiniować symbol test dla pliku, a następnie przetestować wartości symboli test i debugowania. Dane wyjściowe w tym przykładzie zależy od tego, czy projekt jest oparty na tryb konfiguracji Debug i Release.

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

Poniższy przykład pokazuje, jak przetestować dla platform docelowych innej, aby można było używać nowszych interfejsów API, jeśli jest to możliwe:

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

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Dyrektywy preprocesora C#](index.md)  
- [Porady: kompilowanie warunkowe ze śledzeniem i debugowaniem](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md).

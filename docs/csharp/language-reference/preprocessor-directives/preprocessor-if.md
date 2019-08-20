---
title: '#Jeśli dyrektywa preprocesora — C# odwołanie'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: d0297094fbb8098b706cb8c6338fa123afc0753b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605689"
---
# <a name="if-c-reference"></a>#if (odwołanie w C#)

Gdy C# kompilator napotyka `#if` dyrektywę, a następnie [#endif](preprocessor-endif.md) dyrektywie, kompiluje kod między dyrektywami tylko wtedy, gdy określony symbol jest zdefiniowany. W przeciwieństwie do C++języka C i nie można przypisać wartości liczbowej do symbolu. Instrukcja #if w C# jest wartością logiczną i tylko testuje, czy symbol został zdefiniowany. Przykład:

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

[==](../operators/equality-operators.md#equality-operator-) Można użyć operatorów (równość) i [! =](../operators/equality-operators.md#inequality-operator-) (nierówność) tylko do testowania [wartości true](../keywords/true-literal.md) lub [false](../keywords/false-literal.md). Prawda oznacza, że symbol jest zdefiniowany. Instrukcja `#if DEBUG` ma takie samo znaczenie jak `#if (DEBUG == true)`. Można użyć operatorów [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) (i), [ &#124; ](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) (lub), i [!](../operators/boolean-logical-operators.md#logical-negation-operator-) (nie), aby sprawdzić, czy zdefiniowano wiele symboli. Można również grupować symbole i operatory za pomocą nawiasów.

## <a name="remarks"></a>Uwagi

`#if`wraz z [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md)i [#undef](preprocessor-undef.md) umożliwiają uwzględnienie lub wykluczenie kodu na podstawie istnienia jednego lub kilku symboli. Może to być przydatne podczas kompilowania kodu dla kompilacji debugowania lub kompilowania dla określonej konfiguracji.

Dyrektywa warunkowa rozpoczynająca się `#if` od dyrektywy musi być jawnie zakończona `#endif` dyrektywą.

`#define`umożliwia zdefiniowanie symbolu. Używając symbolu jako wyrażenia przesłanego do `#if` dyrektywy, wyrażenie daje w `true`wyniku.

Można również zdefiniować symbol z opcją [-define](../compiler-options/define-compiler-option.md) kompilatora. Aby anulować definicję symbolu, użyj dyrektywy [#undef](preprocessor-undef.md).

Symbol zdefiniowany za pomocą `-define` lub with `#define` nie powoduje konfliktu ze zmienną o tej samej nazwie. Oznacza to, że nazwa zmiennej nie powinna być przenoszona do dyrektywy preprocesora, a symbol może być oceniany tylko przez dyrektywę preprocesora.

Zakres symbolu utworzonego za pomocą `#define` to plik, w którym został zdefiniowany.

System kompilacji jest również świadomy wstępnie zdefiniowanych symboli preprocesora, które reprezentują różne [Platformy docelowe](../../../standard/frameworks.md). Są one przydatne podczas tworzenia aplikacji, które mogą być ukierunkowane na więcej niż jedną implementację lub wersję platformy .NET.

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

Inne wstępnie zdefiniowane symbole obejmują stałe debugowania i śledzenia. Można zastąpić wartości ustawione dla projektu przy użyciu `#define`. Symbol debugowania, na przykład, jest automatycznie ustawiany w zależności od właściwości konfiguracji kompilacji ("Debugowanie" lub "wersja").

## <a name="examples"></a>Przykłady

W poniższym przykładzie pokazano, jak zdefiniować symbol elementu WebTest dla pliku, a następnie przetestować wartości symboli TEST i DEBUG. Dane wyjściowe tego przykładu zależą od tego, czy projekt został skompilowany w trybie konfiguracji debugowania czy wydania.

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

Poniższy przykład pokazuje, jak przeprowadzić test dla różnych platform docelowych, aby można było używać nowszych interfejsów API, gdy jest to możliwe:

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

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Dyrektywy preprocesora C#](index.md)
- [Instrukcje: Kompiluj warunkowo z użyciem śledzenia i debugowania](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

---
title: '#Jeśli dyrektywa preprocesora — C# odwołanie'
ms.custom: seodec18
ms.date: 10/27/2019
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: 561a628c60888a8d4f3c50c8413784e1ed210599
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73035992"
---
# <a name="if-c-reference"></a>#if (odwołanie w C#)

Gdy C# kompilator napotyka dyrektywę`#if`, po której nastąpi w końcu dyrektywą [#endif](preprocessor-endif.md) , kompiluje kod między dyrektywami tylko wtedy, gdy określony symbol jest zdefiniowany. W przeciwieństwie do C++języka C i nie można przypisać wartości liczbowej do symbolu. Instrukcja #if w C# jest wartością logiczną i tylko testuje, czy symbol został zdefiniowany. Na przykład:

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

Operatorów [==](../operators/equality-operators.md#equality-operator-) (równość) i [! =](../operators/equality-operators.md#inequality-operator-) (nierówność) można użyć tylko do testowania [wartości true](../keywords/true-literal.md) lub [false](../keywords/false-literal.md). Prawda oznacza, że symbol jest zdefiniowany. Instrukcja `#if DEBUG` ma takie samo znaczenie jak `#if (DEBUG == true)`. Można użyć operatorów [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) (i), [ &#124; ](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) (lub), i [!](../operators/boolean-logical-operators.md#logical-negation-operator-) (nie), aby sprawdzić, czy zdefiniowano wiele symboli. Można również grupować symbole i operatory za pomocą nawiasów.

## <a name="remarks"></a>Uwagi

`#if`, wraz z [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md)i [#undef](preprocessor-undef.md) dyrektywy, umożliwiają uwzględnienie lub wykluczenie kodu na podstawie istnienia jednego lub kilku symboli. Może to być przydatne podczas kompilowania kodu dla kompilacji debugowania lub kompilowania dla określonej konfiguracji.

Dyrektywa warunkowa rozpoczynająca się od dyrektywy `#if` musi być jawnie zakończona dyrektywą `#endif`.

`#define` umożliwia zdefiniowanie symbolu. Używając symbolu jako wyrażenia przesłanego do dyrektywy `#if`, wyrażenie daje w wyniku `true`.

Można również zdefiniować symbol z opcją [-define](../compiler-options/define-compiler-option.md) kompilatora. Możesz oddefiniować symbol z [#undef](preprocessor-undef.md).

Symbol zdefiniowany za pomocą `-define` lub z `#define` nie powoduje konfliktu ze zmienną o tej samej nazwie. Oznacza to, że nazwa zmiennej nie powinna być przenoszona do dyrektywy preprocesora, a symbol może być oceniany tylko przez dyrektywę preprocesora.

Zakres symbolu utworzonego za pomocą `#define` jest plikiem, w którym został zdefiniowany.

System kompilacji jest również świadomy wstępnie zdefiniowanych symboli preprocesora reprezentujących różne [Platformy docelowe](../../../standard/frameworks.md) w projektach w stylu zestawu SDK. Są one przydatne podczas tworzenia aplikacji, które mogą być ukierunkowane na więcej niż jedną implementację lub wersję platformy .NET.

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

> [!NOTE]
> W przypadku tradycyjnych projektów .NET Framework należy ręcznie skonfigurować symbole kompilacji warunkowej dla różnych platform docelowych w programie Visual Studio za pośrednictwem stron właściwości projektu.

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

- [C#Odwoła](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Dyrektywy preprocesora C#](index.md)
- [Instrukcje: Kompilowanie warunkowe ze śledzeniem i debugowaniem](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

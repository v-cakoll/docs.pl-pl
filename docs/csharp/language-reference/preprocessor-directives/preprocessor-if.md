---
title: '#jeśli preprocesor dyrektywy - C# Reference'
ms.date: 10/27/2019
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: d047b88f202341a795834809d0b601706c30fcb4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75899854"
---
# <a name="if-c-reference"></a>#if (odwołanie do języka C#)

Gdy kompilator C# `#if` napotka dyrektywy, a następnie ostatecznie [#endif](preprocessor-endif.md) dyrektywy, kompiluje kod między dyrektywami tylko wtedy, gdy określony symbol jest zdefiniowany. W przeciwieństwie do C i C++ nie można przypisać wartości liczbowej do symbolu. Instrukcja `#if` w języku C# jest logiczna i sprawdza tylko, czy symbol został zdefiniowany, czy nie. Przykład:

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

[==](../operators/equality-operators.md#equality-operator-) Operatory (równość) i [!=](../operators/equality-operators.md#inequality-operator-) (nierówności) można używać tylko `false`do testowania wartości `true` [bool](../builtin-types/bool.md) lub . `true`oznacza, że symbol jest zdefiniowany. Instrukcja `#if DEBUG` ma takie `#if (DEBUG == true)`samo znaczenie jak . Możesz użyć [&&  (i)](../operators/boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124;  (lub)](../operators/boolean-logical-operators.md#conditional-logical-or-operator-)i [! (nie)](../operators/boolean-logical-operators.md#logical-negation-operator-) operatory, aby ocenić, czy zdefiniowano wiele symboli. Można również grupować symbole i operatory z nawiasami.

## <a name="remarks"></a>Uwagi

`#if`, wraz z [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md)i [#undef](preprocessor-undef.md) dyrektywy, pozwala dołączyć lub wykluczyć kod na podstawie istnienia jednego lub więcej symboli. Może to być przydatne podczas kompilowania kodu dla kompilacji debugowania lub podczas kompilowania dla określonej konfiguracji.

Dyrektywa warunkowa `#if` rozpoczynająca się od dyrektywy `#endif` musi zostać wyraźnie zakończona dyrektywą.

`#define`umożliwia zdefiniowanie symbolu. Następnie przy użyciu symbolu jako `#if` wyrażenie przekazane do dyrektywy, wyrażenie oblicza . `true`

Można również zdefiniować symbol z opcją [-define](../compiler-options/define-compiler-option.md) kompilatora. Można cofnąć definicję symbolu za pomocą [#undef](preprocessor-undef.md).

Symbol, który można `-define` zdefiniować `#define` z lub z nie powoduje konfliktu ze zmienną o tej samej nazwie. Oznacza to, że nazwa zmiennej nie powinny być przekazywane do dyrektywy preprocesora, a symbol może być oceniane tylko przez dyrektywy preprocesora.

Zakres symbolu utworzonego `#define` za pomocą jest plik, w którym został zdefiniowany.

System kompilacji jest również świadomy wstępnie zdefiniowanych symboli preprocesora reprezentujących różne struktury docelowe w [projektach](../../../standard/frameworks.md) w stylu SDK. Są one przydatne podczas tworzenia aplikacji, które mogą być przeznaczone dla więcej niż jednej implementacji lub wersji .NET.

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

> [!NOTE]
> W przypadku tradycyjnych projektów .NET Framework należy ręcznie skonfigurować symbole kompilacji warunkowej dla różnych struktur docelowych w programie Visual Studio za pośrednictwem stron właściwości projektu.

Inne wstępnie zdefiniowane symbole obejmują stałe DEBUG i TRACE. Można zastąpić wartości ustawione dla projektu `#define`za pomocą . Na przykład symbol DEBUG jest ustawiany automatycznie w zależności od właściwości konfiguracji kompilacji ("Debug" lub "Release").

## <a name="examples"></a>Przykłady

W poniższym przykładzie pokazano, jak zdefiniować symbol MYTEST w pliku, a następnie przetestować wartości symboli MYTEST i DEBUG. Dane wyjściowe w tym przykładzie zależy od tego, czy został utworzony projekt w trybie konfiguracji debugowania lub wydania.

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

W poniższym przykładzie pokazano, jak przetestować dla różnych platform docelowych, dzięki czemu można używać nowszych interfejsów API, jeśli to możliwe:

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

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Dyrektywy przedprocesorowe C#](index.md)
- [Instrukcje: Kompilowanie warunkowe ze śledzeniem i debugowaniem](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

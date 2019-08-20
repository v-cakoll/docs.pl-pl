---
title: '#odwołanie do C# wiersza'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
ms.openlocfilehash: b4ac4fd3277fb53251e87321500d1b8007458037
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608534"
---
# <a name="line-c-reference"></a>#line (odwołanie w C#)

`#line`umożliwia zmodyfikowanie numeracji linii kompilatora oraz (opcjonalnie) dane wyjściowe nazwy pliku dla błędów i ostrzeżeń.

Poniższy przykład pokazuje, jak zgłosić dwa ostrzeżenia skojarzone z numerami wierszy. Dyrektywa wymusza numer następnego wiersza do 200 (mimo że wartość domyślna to #6), a do następnej `#line` dyrektywy nazwa pliku będzie raportowana jako "Specjalna". `#line 200` `#line default` Dyrektywa zwraca numery wierszy do domyślnej numeracji, która zlicza wiersze, które zostały zmienione przez poprzednią dyrektywę.

```csharp
class MainClass
{
    static void Main()
    {
#line 200 "Special"
        int i;
        int j;
#line default
        char c;
        float f;
#line hidden // numbering not affected
        string s;
        double d;
    }
}
```

Kompilacja generuje następujące dane wyjściowe:

```console
Special(200,13): warning CS0168: The variable 'i' is declared but never used
Special(201,13): warning CS0168: The variable 'j' is declared but never used
MainClass.cs(9,14): warning CS0168: The variable 'c' is declared but never used
MainClass.cs(10,15): warning CS0168: The variable 'f' is declared but never used
MainClass.cs(12,16): warning CS0168: The variable 's' is declared but never used
MainClass.cs(13,16): warning CS0168: The variable 'd' is declared but never used
```

## <a name="remarks"></a>Uwagi

Dyrektywa `#line` może być używana w automatycznym, pośrednim etapie procesu kompilacji. Na przykład jeśli z oryginalnego pliku kodu źródłowego zostały usunięte wiersze, ale kompilator nadal ma generować dane wyjściowe na podstawie oryginalnego numerowania wierszy w pliku, możesz usunąć wiersze i zasymulować oryginalne numerowanie za pomocą dyrektywy `#line`.

Dyrektywa `#line hidden` ukrywa kolejne wiersze przed debugerem, w taki sposób, że podczas wykonywania kodu przez dewelopera wszystkie wiersze między dyrektywą `#line hidden` a następną dyrektywą `#line` (przy założeniu, że nie będzie to kolejna dyrektywa `#line hidden`) zostaną pominięte. Ta opcja pozwala także platformie ASP.NET odróżnić kod zdefiniowany przez użytkownika od kodu wygenerowanego maszynowo. Mimo że funkcja ta jest używana głównie w ASP.NET, to prawdopodobne jest, że będzie z niej korzystać więcej generatorów kodu źródłowego.

Dyrektywa `#line hidden` nie wpływa na nazwy plików ani numery wierszy w raportowaniu błędów. Oznacza to, że w przypadku napotkania błędu w ukrytym bloku kompilator zgłosi obecną nazwę pliku oraz numer wiersza, w którym wystąpił błąd.

Dyrektywa `#line filename` określa nazwę pliku, która ma być wyświetlana w danych wyjściowych kompilatora. Domyślnie używana jest rzeczywista nazwa pliku kodu źródłowego. Nazwa pliku musi być ujęta w podwójny cudzysłów ("") oraz musi być poprzedzona numerem wiersza.

Plik kodu źródłowego może mieć dowolną liczbę wystąpeń dyrektywy `#line`.

## <a name="example-1"></a>Przykład 1

W poniższym przykładzie pokazano, jak debuger ignoruje ukryte wiersze w kodzie. Po uruchomieniu przykładu zostaną wyświetlone trzy wiersze tekstu. Jednak gdy ustawisz punkt przerwania (jak pokazano w przykładzie) i naciśniesz klawisz F10, aby wykonywać kod krokowo, zobaczysz, że debuger zignoruje ukryty wiersz. Nawet jeśli ustawisz punkt przerwania w ukrytym wierszu, debuger go zignoruje.

```csharp
// preprocessor_linehidden.cs
using System;
class MainClass
{
    static void Main()
    {
        Console.WriteLine("Normal line #1."); // Set break point here.
#line hidden
        Console.WriteLine("Hidden line.");
#line default
        Console.WriteLine("Normal line #2.");
    }
}
```

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Dyrektywy preprocesora C#](./index.md)

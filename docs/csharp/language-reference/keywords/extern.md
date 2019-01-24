---
title: extern — modyfikator - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: d860f1a3c6917238a529093672dc5f2abc5ae066
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620200"
---
# <a name="extern-c-reference"></a>extern (odwołanie w C#)

`extern` Modyfikator jest używany do deklarowania metody implementowanej zewnętrznie. Typowym zastosowaniem `extern` jest modyfikator `DllImport` atrybutu podczas korzystania z usług międzyoperacyjnych w celu wywołania kodu niezarządzanego. W tym przypadku metoda musi być także zadeklarowana jako `static`, jak pokazano w poniższym przykładzie:

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

`extern` — Słowo kluczowe może także definiować alias zestawu zewnętrznego, który sprawia, że można odwoływać się do różnych wersji jednego składnika z poziomu jednego zestawu. Aby uzyskać więcej informacji, zobacz [alias zewnętrzny](extern-alias.md).

Jest to błąd, aby użyć [abstrakcyjne](abstract.md) i `extern` Modyfikatory ze sobą, aby zmodyfikować tego samego członka. Za pomocą `extern` modyfikator oznacza, że metoda jest zaimplementowana poza kodu C#, natomiast przy użyciu `abstract` modyfikator oznacza, że implementacja metody nie znajduje się w klasie.

Użycie słowa kluczowego extern podlega większym ograniczeniom w języku C# niż w języku C++. Aby porównać to słowo kluczowe w języku C# z wersją w języku C++, zobacz temat „Używanie słowa kluczowego extern w celu określenia powiązania” w dokumentacji języka C++.

## <a name="example-1"></a>Przykład 1

W tym przykładzie program odbiera ciąg od użytkownika i wyświetla go w oknie komunikatu. Program używa `MessageBox` metoda zaimportowany z biblioteki User32.dll.

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a>Przykład 2

Ten przykład ilustruje program C#, który wywołuje bibliotekę języka C (natywna Biblioteka DLL).

1. Utwórz następujący plik języka C i nadaj mu `cmdll.c`:

```c
// cmdll.c
// Compile with: -LD
int __declspec(dllexport) SampleMethod(int i)
{
  return i*10;
}
```

2. Otwórz okno Wiersz polecenia narzędzi Native Tools x64 (lub x32) programu Visual Studio w katalogu instalacyjnym programu Visual Studio i skompiluj `cmdll.c` pliku, wpisując **cl -LD cmdll.c** w wierszu polecenia.

3. W tym samym katalogu Utwórz następujący plik języka C# i nadaj jej nazwę `cm.cs`:

```csharp
// cm.cs
using System;
using System.Runtime.InteropServices;
public class MainClass
{
    [DllImport("Cmdll.dll")]
      public static extern int SampleMethod(int x);

    static void Main()
    {
        Console.WriteLine("SampleMethod() returns {0}.", SampleMethod(5));
    }
}
```

4. Otwórz okno Wiersz polecenia narzędzi Native Tools x64 (lub x32) programu Visual Studio w katalogu instalacyjnym programu Visual Studio i skompiluj `cm.cs` pliku, wpisując:

> **CSC cm.cs** (x64 wiersza polecenia) — lub — **csc-platform: x 86 cm.cs** (dla x32 wiersza polecenia)

Spowoduje to utworzenie pliku wykonywalnego `cm.exe`.

5. Uruchom `cm.exe`. `SampleMethod` Metoda przekazuje wartość 5 do pliku DLL, który zwraca tę wartość pomnożoną przez 10.  Program generuje następujące wyniki:

```
SampleMethod() returns 50.
```

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>
- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Modyfikatory](modifiers.md)

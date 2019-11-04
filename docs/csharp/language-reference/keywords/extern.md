---
title: modyfikator extern — C# odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: 5f4a4b143578603a3285b1a3bc0b1efa11840e77
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422812"
---
# <a name="extern-c-reference"></a>extern (odwołanie w C#)

Modyfikator `extern` jest używany do deklarowania metody, która jest implementowana zewnętrznie. Typowym zastosowaniem modyfikatora `extern` jest z atrybutem `DllImport`, gdy używasz usług międzyoperacyjnych do wywoływania kodu niezarządzanego. W takim przypadku metoda musi być również zadeklarowana jako `static`, jak pokazano w następującym przykładzie:

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

Za pomocą słowa kluczowego `extern` można także zdefiniować zewnętrzny alias zestawu, który umożliwia odwoływanie się do różnych wersji tego samego składnika z poziomu jednego zestawu. Aby uzyskać więcej informacji, zobacz [alias zewnętrzny](extern-alias.md).

Nie można użyć modyfikatorów [abstrakcyjnych](abstract.md) i `extern`, aby zmodyfikować ten sam element członkowski. Użycie modyfikatora `extern` oznacza, że metoda jest implementowana poza C# kodem, podczas gdy użycie modyfikatora `abstract` oznacza, że implementacja metody nie jest podana w klasie.

Użycie słowa kluczowego extern podlega większym ograniczeniom w języku C# niż w języku C++. Aby porównać to słowo kluczowe w języku C# z wersją w języku C++, zobacz temat „Używanie słowa kluczowego extern w celu określenia powiązania” w dokumentacji języka C++.

## <a name="example-1"></a>Przykład 1

W tym przykładzie program odbiera ciąg od użytkownika i wyświetla go w oknie komunikatu. Program używa metody `MessageBox` zaimportowanej z biblioteki User32. dll.

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a>Przykład 2

Ten przykład ilustruje C# program wywoływany do biblioteki języka C (NATYWNEJ biblioteki dll).

1. Utwórz następujący plik C i nadaj mu nazwę `cmdll.c`:

    ```c
    // cmdll.c
    // Compile with: -LD
    int __declspec(dllexport) SampleMethod(int i)
    {
      return i*10;
    }
    ```

2. Otwórz okno wiersza polecenia narzędzi Visual Studio x64 (lub x32) Native Tools z katalogu instalacyjnego programu Visual Studio i skompiluj plik `cmdll.c`, wpisując **CL-LD cmdll. c** w wierszu polecenia.

3. W tym samym katalogu Utwórz następujący C# plik i nadaj mu nazwę `cm.cs`:

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

4. Otwórz okno wiersza polecenia narzędzi Visual Studio x64 (lub x32) Native Tools z katalogu instalacyjnego programu Visual Studio i skompiluj plik `cm.cs`, wpisując:

    > **csc cm.cs** (wiersz polecenia x64) — lub — **CSC-platform: x86 cm.cs** (dla wiersza polecenia x32)

    Spowoduje to utworzenie pliku wykonywalnego `cm.exe`.

5. Uruchom `cm.exe`. Metoda `SampleMethod` przekazuje wartość 5 do pliku DLL, który zwraca wartość pomnożoną przez 10.  Program tworzy następujące dane wyjściowe:

    ```output
    SampleMethod() returns 50.
    ```

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>
- [C#Odwoła](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Modyfikatory](index.md)

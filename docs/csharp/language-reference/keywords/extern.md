---
title: egzterzolog - Odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: c121d810e64b5fa27f105f814253c0752e028a95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713540"
---
# <a name="extern-c-reference"></a>extern (odwołanie w C#)

Modyfikator `extern` jest używany do deklarowania metody, która jest implementowana zewnętrznie. Typowe użycie modyfikatora `extern` `DllImport` jest z atrybutem, gdy używasz usług Interop wywołać do kodu niezarządzanego. W takim przypadku metoda musi być `static`również zadeklarowana jako , jak pokazano w poniższym przykładzie:

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

Słowo `extern` kluczowe można również zdefiniować alias złożenia zewnętrznego, co umożliwia odwoływanie się do różnych wersji tego samego komponentu z poziomu jednego zestawu. Aby uzyskać więcej informacji, zobacz [alias extern](extern-alias.md).

Jest to błąd, aby `extern` użyć [abstrakcyjne](abstract.md) i modyfikatory razem do modyfikowania tego samego elementu członkowskiego. Za `extern` pomocą modyfikatora oznacza, że metoda jest implementowana `abstract` poza kodem C#, podczas gdy przy użyciu modyfikatora oznacza, że implementacja metody nie jest dostępna w klasie.

Użycie słowa kluczowego extern podlega większym ograniczeniom w języku C# niż w języku C++. Aby porównać to słowo kluczowe w języku C# z wersją w języku C++, zobacz temat „Używanie słowa kluczowego extern w celu określenia powiązania” w dokumentacji języka C++.

## <a name="example-1"></a>Przykład 1

W tym przykładzie program odbiera ciąg od użytkownika i wyświetla go wewnątrz okna komunikatu. Program używa `MessageBox` metody zaimportowanej z biblioteki User32.dll.

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a>Przykład 2

W tym przykładzie przedstawiono program C#, który wywołuje do biblioteki C (natywnej biblioteki DLL).

1. Utwórz następujący plik C `cmdll.c`i nawadom go nas:

    ```c
    // cmdll.c
    // Compile with: -LD
    int __declspec(dllexport) SampleMethod(int i)
    {
      return i*10;
    }
    ```

2. Otwórz okno wiersza polecenia programu Visual Studio x64 (lub x32) Z `cmdll.c` katalogu instalacyjnego programu Visual Studio i skompiluj plik, wpisując cl **-LD cmdll.c** w wierszu polecenia.

3. W tym samym katalogu utwórz następujący plik `cm.cs`Języka C# i najmiej nazwę:

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

4. Otwórz okno wiersza polecenia programu Visual Studio x64 (lub x32) Z `cm.cs` katalogu instalacyjnego programu Visual Studio i skompiluj plik, wpisując:

    > **csc cm.cs** (dla wiersza polecenia x64) —lub — **csc -platform:x86 cm.cs** (dla wiersza polecenia x32)

    Spowoduje to utworzenie pliku `cm.exe`wykonywalnego .

5. Uruchom polecenie `cm.exe`. Metoda `SampleMethod` przekazuje wartość 5 do pliku DLL, który zwraca wartość pomnożoną przez 10.  Program generuje następujące dane wyjściowe:

    ```output
    SampleMethod() returns 50.
    ```

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>
- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Modyfikatory](index.md)

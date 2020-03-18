---
title: '#wiersz - Odwołanie do języka C#'
ms.date: 07/20/2015
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
ms.openlocfilehash: 79033fa652af62c76d54737fbf0a0b47cf3aae99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712497"
---
# <a name="line-c-reference"></a>#line (odwołanie w C#)

`#line`umożliwia modyfikowanie numeracji wiersza kompilatora i (opcjonalnie) danych wyjściowych nazwy pliku dla błędów i ostrzeżeń.

W poniższym przykładzie pokazano, jak zgłosić dwa ostrzeżenia skojarzone z numerami linii. Dyrektywa `#line 200` wymusza numer następnego wiersza na 200 (chociaż wartość domyślna `#line` jest #6), a do następnej dyrektywy nazwa pliku będzie zgłaszana jako "Specjalna". Dyrektywa `#line default` zwraca numeracji wiersza do jego domyślnej numeracji, która zlicza wiersze, które zostały ponownie numerowane przez poprzednią dyrektywę.

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

Kompilacja daje następujące dane wyjściowe:

```console
Special(200,13): warning CS0168: The variable 'i' is declared but never used
Special(201,13): warning CS0168: The variable 'j' is declared but never used
MainClass.cs(9,14): warning CS0168: The variable 'c' is declared but never used
MainClass.cs(10,15): warning CS0168: The variable 'f' is declared but never used
MainClass.cs(12,16): warning CS0168: The variable 's' is declared but never used
MainClass.cs(13,16): warning CS0168: The variable 'd' is declared but never used
```

## <a name="remarks"></a>Uwagi

Dyrektywa `#line` może być używana w zautomatyzowanym, pośrednim kroku w procesie kompilacji. Na przykład jeśli wiersze zostały usunięte z oryginalnego pliku kodu źródłowego, ale nadal chcesz, aby kompilator generował dane wyjściowe na `#line`podstawie oryginalnej numeracji wierszy w pliku, można usunąć wiersze, a następnie symulować oryginalną numeracz wiersza z .

Dyrektywa `#line hidden` ukrywa kolejne wiersze z debugera, tak aby podczas kroków dewelopera `#line hidden` za `#line` pośrednictwem kodu, wszelkie `#line hidden` wiersze między a i następnej dyrektywy (przy założeniu, że nie jest to inna dyrektywa) zostanie nadepnięcie. Ta opcja może również służyć do umożliwienia ASP.NET rozróżniania kodu zdefiniowanego przez użytkownika i wygenerowanego maszynowo. Mimo że ASP.NET jest głównym konsumentem tej funkcji, jest prawdopodobne, że więcej generatorów źródłowych będzie z niej korzystać.

Dyrektywa `#line hidden` nie ma wpływu na nazwy plików ani numery wierszy w raportowaniu błędów. Oznacza to, że jeśli wystąpi błąd w ukrytym bloku, kompilator zgłosi bieżącą nazwę pliku i numer wiersza błędu.

Dyrektywa `#line filename` określa nazwę pliku, który ma być wyświetlany w danych wyjściowych kompilatora. Domyślnie używana jest rzeczywista nazwa pliku kodu źródłowego. Nazwa pliku musi być w podwójnych cudzysłowie ("") i musi być poprzedzona numerem wiersza.

Plik kodu źródłowego może `#line` mieć dowolną liczbę dyrektyw.

## <a name="example-1"></a>Przykład 1

W poniższym przykładzie pokazano, jak debuger ignoruje ukryte wiersze w kodzie. Po uruchomieniu przykładu wyświetli się trzy wiersze tekstu. Jednak po ustawieniu punktu przerwania, jak pokazano w przykładzie i naciśnij F10 krok po kroku kodu, można zauważyć, że debuger ignoruje ukryty wiersz. Należy również zauważyć, że nawet jeśli ustawisz punkt przerwania w ukrytym wierszu, debuger nadal będzie go ignorować.

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

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Dyrektywy przedprocesorowe C#](./index.md)

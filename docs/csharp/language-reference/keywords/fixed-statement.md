---
title: fixed — Instrukcja (odwołanie w C#)
ms.date: 04/20/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5dd117461f792ec7a10b740fbad277de52d05623
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="fixed-statement-c-reference"></a>fixed — Instrukcja (odwołanie w C#)

`fixed` Instrukcji uniemożliwia przemieszczanie zmienną ruchomy moduł garbage collector. `fixed` Instrukcji jest dozwolona tylko w [niebezpieczne](unsafe.md) kontekstu. `Fixed` można również utworzyć [stały rozmiar buforów](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).

`fixed` Instrukcja ustawia wskaźnik zarządzanych zmienną i "numerów PIN" zmiennej podczas wykonywania instrukcji. Wskaźniki do ruchomy zarządzanych zmienne są przydatne tylko w `fixed` kontekstu. Bez `fixed` kontekstu, wyrzucanie elementów bezużytecznych można przenosić zmienne nieprzewidywalny. Kompilator języka C# tylko można przypisać wskaźnik do zmiennej zarządzanych w `fixed` instrukcji.

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

Wskaźnik można zainicjować za pomocą tablicy, ciąg, buforu o stałym rozmiarze lub adresu zmiennej. Poniższy przykład przedstawia użycie zmiennej adresów, tablic i ciągów. Aby uzyskać więcej informacji na temat bufory o ustalonym rozmiarze, zobacz [buforów o rozmiarze stałym](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

Jeśli są one ten sam typ można zainicjować wielu wskaźniki w jednej instrukcji:

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

Aby zainicjować wskaźników różnych typów, po prostu zagnieździć `fixed` instrukcje, jak pokazano w poniższym przykładzie.

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

Po wykonaniu kodu w instrukcji zmiennych przypiętych są odpiąć i wyrzucanie elementów bezużytecznych. W związku z tym nie wskazują na tych zmiennych poza `fixed` instrukcji. Zmienne zadeklarowane w `fixed` zestawienie ograniczone do tej instrukcji, ułatwiając to:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

Wskaźniki zainicjowany w `fixed` instrukcje są zmienne tylko do odczytu. Jeśli chcesz zmodyfikować wartość wskaźnika należy zadeklarować Druga zmienna wskaźnika i zmodyfikować to. Zmienna zadeklarowana w `fixed` instrukcji nie można zmodyfikować:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```


W trybie bezpiecznym można przydzielić pamięci na stosie, w którym nie podlega wyrzucanie elementów bezużytecznych i dlatego nie trzeba przypięty. Aby uzyskać więcej informacji, zobacz [stackalloc](stackalloc.md).

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#4)]

## <a name="c-language-specification"></a>Specyfikacja języka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

 [Odwołanie w C#](../index.md)  
 [Przewodnik programowania w języku C#](../../programming-guide/index.md)  
 [Słowa kluczowe języka C#](index.md)  
 [unsafe](unsafe.md)  
 [Bufory o ustalonym rozmiarze](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)

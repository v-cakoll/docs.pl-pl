---
title: Integer, typ danych
ms.date: 01/31/2018
f1_keywords:
- vb.Integer
- Integer
helpviewer_keywords:
- numbers [Visual Basic], whole
- enumerated values [Visual Basic]
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- literal type characters [Visual Basic], I
- integers [Visual Basic], types
- data types [Visual Basic], integral
- '% identifier type character'
- data types [Visual Basic], assigning
- identifier type characters [Visual Basic], %
- I literal type character [Visual Basic]
- Integer data type
ms.assetid: a8f233b4-4be3-455c-861b-05af2fbb6c60
ms.openlocfilehash: c5b1041b8ef0ca9898a846fea03888537bb4abbf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343982"
---
# <a name="integer-data-type-visual-basic"></a>Integer — typ danych (Visual Basic)

Przechowuje 32-bitowe (4-bajtowe) liczby całkowite ze znakiem z zakresu wartości od -2 147 483,648 do 2 147 483 647.  
  
## <a name="remarks"></a>Uwagi

 Typ danych `Integer` zapewnia optymalną wydajność procesora 32-bitowego. Inne typy całkowitoliczbowe wolniej wczytują się z pamięci i są w niej zapisywane.  
  
 Wartość domyślna `Integer` wynosi 0.  

## <a name="literal-assignments"></a>Przypisania literałów

Można zadeklarować i zainicjować zmienną `Integer`, przypisując jej literał dziesiętny, literał szesnastkowy, literał ósemkowy lub (Zaczynając od Visual Basic 2017) literał binarny. Jeśli literał liczby całkowitej znajduje się poza zakresem `Integer` (czyli jeśli jest mniejszy niż <xref:System.Int32.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.Int32.MaxValue?displayProperty=nameWithType>, wystąpi błąd kompilacji.

W poniższym przykładzie liczby całkowite równe 90 946 są reprezentowane jako literały dziesiętne, szesnastkowe i binarne są przypisywane do wartości `Integer`.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> Możesz użyć prefiksu `&h` lub `&H` do określenia literału szesnastkowego, prefiksu `&b` lub `&B`, aby zauważyć literał binarny, a prefiks `&o` lub `&O`, aby zauważyć literał ósemkowy. Literały dziesiętne nie mają prefiksu.

Począwszy od Visual Basic 2017, można również użyć znaku podkreślenia, `_`, jako separatora cyfr, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

Począwszy od Visual Basic 15,5, można również użyć znaku podkreślenia (`_`) jako wiodącego separatora między cyframi prefiksu i szesnastkową, binarną lub ósemkową. Na przykład:

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literały numeryczne mogą również zawierać `I` [znak typu](../../programming-guide/language-features/data-types/type-characters.md) , aby zauważyć `Integer` typ danych, jak pokazano w poniższym przykładzie.

```vb
Dim number = &H_035826I
```

## <a name="programming-tips"></a>Porady dotyczące programowania

- **Zagadnienia dotyczące międzyoperacyjnych.** Jeśli korzystasz z składników niepisanych dla .NET Framework, takich jak Automatyzacja lub obiekty COM, pamiętaj, że `Integer` ma inną szerokość danych (16 bitów) w innych środowiskach. Jeśli przekazujesz argument 16-bitowy do takiego składnika, zadeklaruj go jako `Short` zamiast `Integer` w nowym kodzie Visual Basic.  
  
- **Rozszerzającą.** Typ danych `Integer` poszerza do `Long`, `Decimal`, `Single`lub `Double`. Oznacza to, że można skonwertować `Integer` do dowolnego jednego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.  
  
- **Znaki typu.** Dołączanie znaku typu literału `I` do literału wymusza go do `Integer` typu danych. Dołączanie znaku typu identyfikatora `%` do dowolnego identyfikatora wymusza `Integer`.  
  
- **Typ struktury.** Odpowiedni typ w .NET Framework jest strukturą <xref:System.Int32?displayProperty=nameWithType>.  
  
## <a name="range"></a>Zakres

Jeśli spróbujesz ustawić zmienną typu całkowitoliczbowego na liczbę spoza zakresu dla tego typu, wystąpi błąd. Jeśli spróbujesz ustawić ją na ułamek, liczba jest zaokrąglana w górę lub w dół do najbliższej wartości liczby całkowitej. Jeśli liczba jest jednakowo blisko dwóch wartości całkowitych, wartość jest zaokrąglana do najbliższej parzystej liczby całkowitej. To zachowanie minimalizuje błędy zaokrągleń, które powstają w wyniku konsekwentnego zaokrąglania wartości punktu środkowego w jednym kierunku. W poniższym kodzie pokazano przykłady zaokrąglania.  

```vb  
' The valid range of an Integer variable is -2147483648 through +2147483647.  
Dim k As Integer  
' The following statement causes an error because the value is too large.  
k = 2147483648  
' The following statement sets k to 6.  
k = 5.9  
' The following statement sets k to 4  
k = 4.5  
' The following statement sets k to 6  
' Note, Visual Basic uses banker’s rounding (toward nearest even number)  
k = 5.5  
```

## <a name="see-also"></a>Zobacz także

- <xref:System.Int32?displayProperty=nameWithType>
- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
- [Long, typ danych](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [Short, typ danych](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

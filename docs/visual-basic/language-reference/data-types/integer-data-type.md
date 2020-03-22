---
title: Integer — Typ danych
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400737"
---
# <a name="integer-data-type-visual-basic"></a>Typ danych liczby całkowitej (Visual Basic)

Przechowuje 32-bitowe (4-bajtowe) liczby całkowite ze znakiem z zakresu wartości od -2 147 483,648 do 2 147 483 647.  
  
## <a name="remarks"></a>Uwagi

 Typ `Integer` danych zapewnia optymalną wydajność procesora 32-bitowego. Inne typy całkowitoliczbowe wolniej wczytują się z pamięci i są w niej zapisywane.  
  
 Wartość domyślna `Integer` to 0.  

## <a name="literal-assignments"></a>Przydziały dosłowne

Można zadeklarować i `Integer` zainicjować zmienną, przypisując jej literał dziesiętny, szesnastkowy literał, literał ósemkowy lub (zaczynając od języka Visual Basic 2017) literał binarny. Jeśli litera liczba całkowita znajduje się `Integer` poza zakresem (oznacza <xref:System.Int32.MinValue?displayProperty=nameWithType> to, <xref:System.Int32.MaxValue?displayProperty=nameWithType>że jest mniejsza lub większa niż , występuje błąd kompilacji.

W poniższym przykładzie liczby całkowite równe 90 946, które są reprezentowane jako dziesiętne, szesnastkowe i binarne literały są przypisywane do `Integer` wartości.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> Prefiksu `&h` lub `&H` oznaczasz szesnastkowy literał, `&b` `&B` prefiks lub oznacza literał binarny i prefiks `&o` lub `&O` oznacza literał ósemkowy. Literały dziesiętne nie mają prefiksu.

Począwszy od języka Visual Basic 2017, `_`można również użyć znaku podkreślenia, jako separatora cyfry, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

Począwszy od języka Visual Basic 15.5,`_`można również użyć znaku podkreślenia ( ) jako interełownika wiodącego między prefiksem a cyframi szesnastkowymi, binarnymi lub ósemkowymi. Przykład:

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literały liczbowe mogą również `I` zawierać [znak](../../programming-guide/language-features/data-types/type-characters.md) typu `Integer` oznaczającego typ danych, jak pokazano w poniższym przykładzie.

```vb
Dim number = &H_035826I
```

## <a name="programming-tips"></a>Porady dotyczące programowania

- **Zagadnienia międzyoperacyjne.** W przypadku łączenia ze składnikami nieuznawane dla programu .NET Framework, `Integer` takich jak automatyzacja lub COM, należy pamiętać, że ma inną szerokość danych (16 bitów) w innych środowiskach. Jeśli przekazujesz 16-bitowy argument do takiego składnika, zadeklaruj go jako `Short` zamiast `Integer` w nowym kodzie języka Visual Basic.  
  
- **Poszerzenie.** Typ `Integer` danych rozszerza `Long`się `Decimal` `Single`do `Double`, , , lub . Oznacza to, `Integer` że można przekonwertować do <xref:System.OverflowException?displayProperty=nameWithType> jednego z tych typów bez napotkania błędu.  
  
- **Wpisz znaki.** Dołączenie znaku literału `I` do literału wymusza go do `Integer` typu danych. Dołączenie znaku `%` typu identyfikatora do dowolnego identyfikatora wymusza jego `Integer`  
  
- **Typ struktury.** Odpowiedni typ w .NET Framework <xref:System.Int32?displayProperty=nameWithType> jest strukturą.  
  
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

## <a name="see-also"></a>Zobacz też

- <xref:System.Int32?displayProperty=nameWithType>
- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
- [Long, typ danych](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [Short, typ danych](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

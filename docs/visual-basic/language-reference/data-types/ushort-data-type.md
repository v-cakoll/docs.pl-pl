---
title: UShort — Typ danych
ms.date: 01/31/2018
f1_keywords:
- vb.ushort
helpviewer_keywords:
- numbers [Visual Basic], whole
- literal type characters [Visual Basic], US
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- UShort data type
- US literal type characters [Visual Basic]
ms.assetid: 138db892-665d-4ba8-9cae-d8d91c4a8f39
ms.openlocfilehash: 7cdbd5fb192fd5cc1be6260dcdcdb1f30cf3f865
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343853"
---
# <a name="ushort-data-type-visual-basic"></a>UShort — Typ danych (Visual Basic)

Przechowuje liczby całkowite (2-bajtowe) bez znaku w zakresie od 0 do 65 535.  
  
## <a name="remarks"></a>Uwagi

 Użyj `UShort` typ danych, aby zawierać dane binarne zbyt duże dla `Byte`.  
  
 Wartość domyślna `UShort` wynosi 0.  

## <a name="literal-assignments"></a>Przypisania literałów

Można zadeklarować i zainicjować zmienną `UShort`, przypisując jej literał dziesiętny, literał szesnastkowy, literał ósemkowy lub (Zaczynając od Visual Basic 2017) literał binarny. Jeśli literał liczby całkowitej znajduje się poza zakresem `UShort` (czyli jeśli jest mniejszy niż <xref:System.UInt16.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, wystąpi błąd kompilacji.

W poniższym przykładzie liczby całkowite równe 65 034 są reprezentowane jako literały dziesiętne, szesnastkowe i binarne są przypisywane do wartości `UShort`.
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> Możesz użyć prefiksu `&h` lub `&H` do określenia literału szesnastkowego, prefiksu `&b` lub `&B`, aby zauważyć literał binarny, a prefiks `&o` lub `&O`, aby zauważyć literał ósemkowy. Literały dziesiętne nie mają prefiksu.

Począwszy od Visual Basic 2017, można również użyć znaku podkreślenia, `_`, jako separatora cyfr, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

Począwszy od Visual Basic 15,5, można również użyć znaku podkreślenia (`_`) jako wiodącego separatora między cyframi prefiksu i szesnastkową, binarną lub ósemkową. Na przykład:

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literały numeryczne mogą również zawierać [znak](../../programming-guide/language-features/data-types/type-characters.md) `US` lub `us`, aby zauważyć `UShort` typ danych, jak pokazano w poniższym przykładzie.

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a>Porady dotyczące programowania
  
- **Liczby ujemne.** Ponieważ `UShort` jest typem bez znaku, nie może reprezentować liczby ujemnej. Jeśli używasz operatora jednoargumentowego minus (`-`) w wyrażeniu, które oblicza `UShort`, Visual Basic konwertuje wyrażenie na `Integer` jako pierwsze.  
  
- **Zgodność ze specyfikacją CLS.** `UShort` typ danych nie jest częścią [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), więc kod zgodny ze specyfikacją CLS nie może używać składnika, który go używa.
  
- **Rozszerzającą.** Typ danych `UShort` poszerza do `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`i `Double`. Oznacza to, że można skonwertować `UShort` do dowolnego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.  
  
- **Znaki typu.** Dołączanie znaków literału `US` do literału wymusza `UShort` do typu danych. `UShort` nie ma znaku typu identyfikatora.  
  
- **Typ struktury.** Odpowiedni typ w .NET Framework jest strukturą <xref:System.UInt16?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.UInt16>
- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Instrukcje: wywoływanie funkcji Windows wykorzystującej typy bez znaku](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

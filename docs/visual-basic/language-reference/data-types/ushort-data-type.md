---
title: UShort, typ danych
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400695"
---
# <a name="ushort-data-type-visual-basic"></a>Typ danych UShort (Visual Basic)

Przechowuje niepodpisane 16-bitowe (2-bajtowe) liczby całkowite o wartości od 0 do 65 535.  
  
## <a name="remarks"></a>Uwagi

 Użyj `UShort` typu danych, aby zawierać `Byte`dane binarne zbyt duże dla .  
  
 Wartość domyślna `UShort` to 0.  

## <a name="literal-assignments"></a>Przydziały dosłowne

Można zadeklarować i `UShort` zainicjować zmienną, przypisując jej literał dziesiętny, szesnastkowy literał, literał ósemkowy lub (zaczynając od języka Visual Basic 2017) literał binarny. Jeśli litera liczba całkowita znajduje się `UShort` poza zakresem (oznacza <xref:System.UInt16.MinValue?displayProperty=nameWithType> to, <xref:System.UInt16.MaxValue?displayProperty=nameWithType>że jest mniejsza lub większa niż , występuje błąd kompilacji.

W poniższym przykładzie liczby całkowite równe 65 034, które są reprezentowane jako dziesiętne, szesnastkowe i binarne literały są przypisywane do `UShort` wartości.
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> Prefiksu `&h` lub `&H` oznaczasz szesnastkowy literał, `&b` `&B` prefiks lub oznacza literał binarny i prefiks `&o` lub `&O` oznacza literał ósemkowy. Literały dziesiętne nie mają prefiksu.

Począwszy od języka Visual Basic 2017, `_`można również użyć znaku podkreślenia, jako separatora cyfry, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

Począwszy od języka Visual Basic 15.5,`_`można również użyć znaku podkreślenia ( ) jako interełownika wiodącego między prefiksem a cyframi szesnastkowymi, binarnymi lub ósemkowymi. Przykład:

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literały liczbowe mogą również `US` `us` zawierać [znak](../../programming-guide/language-features/data-types/type-characters.md) lub `UShort` typ oznaczania typu danych, jak pokazano w poniższym przykładzie.

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a>Porady dotyczące programowania
  
- **Liczby ujemne.** Ponieważ `UShort` jest typem niepodpisanym, nie może reprezentować liczby ujemnej. Jeśli w wyrażeniu, które ma być wpisane, użyjesz operatora unary minus (`-`) w wyrażeniu, które ma być wpisane, `UShort`visual basic konwertuje wyrażenie na `Integer` pierwsze.  
  
- **Zgodność z CLS.** Typ `UShort` danych nie jest częścią [specyfikacji języka wspólnego](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), więc kod zgodny ze specyfikacją CLS nie może korzystać ze składnika, który go używa.
  
- **Poszerzenie.** Typ `UShort` danych rozszerza `Integer`się `UInteger` `Long`do `ULong` `Decimal`, `Single`, `Double`, , , i . Oznacza to, `UShort` że można przekonwertować <xref:System.OverflowException?displayProperty=nameWithType> do dowolnego z tych typów bez napotkania błędu.  
  
- **Wpisz znaki.** Dołączenie znaków `US` typu literału do literału `UShort` wymusza go do typu danych. `UShort`nie ma znaku typu identyfikatora.  
  
- **Typ struktury.** Odpowiedni typ w .NET Framework <xref:System.UInt16?displayProperty=nameWithType> jest strukturą.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.UInt16>
- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Porady: wywoływanie funkcji Windows wykorzystującej typy bez znaku](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

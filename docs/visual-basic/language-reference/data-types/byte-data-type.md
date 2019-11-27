---
title: Byte, typ danych
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 347d7e7d0f09e089886bc81bd0be659deaca9b46
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344075"
---
# <a name="byte-data-type-visual-basic"></a>Byte — typ danych (Visual Basic)

Zawiera 8-bitowe (1-bajtowe) liczby całkowite bez znaku, który ma wartość z zakresu od 0 do 255.

## <a name="remarks"></a>Uwagi

Użyj typu danych `Byte`, aby zawierać dane binarne.  
  
Wartość domyślna `Byte` wynosi 0.

## <a name="literal-assignments"></a>Przypisania literałów

Można zadeklarować i zainicjować zmienną `Byte`, przypisując jej literał dziesiętny, literał szesnastkowy, literał ósemkowy lub (Zaczynając od Visual Basic 2017) literał binarny. Jeśli literał całkowity znajduje się poza zakresem `Byte` (czyli jeśli jest mniejszy niż <xref:System.Byte.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.Byte.MaxValue?displayProperty=nameWithType>), wystąpi błąd kompilacji.

W poniższym przykładzie liczby całkowite równe 201, które są reprezentowane jako dziesiętne, szesnastkowe i literały binarne, są niejawnie konwertowane z [liczby całkowitej](integer-data-type.md) na wartości `byte`.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> Możesz użyć prefiksu `&h` lub `&H` do określenia literału szesnastkowego, prefiksu `&b` lub `&B`, aby zauważyć literał binarny, a prefiks `&o` lub `&O`, aby zauważyć literał ósemkowy. Literały dziesiętne nie mają prefiksu.

Począwszy od Visual Basic 2017, można również użyć znaku podkreślenia, `_`, jako separatora cyfr, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

Począwszy od Visual Basic 15,5, można również użyć znaku podkreślenia (`_`) jako wiodącego separatora między cyframi prefiksu i szesnastkową, binarną lub ósemkową. Na przykład:

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a>Porady dotyczące programowania

- **Liczby ujemne.** Ponieważ `Byte` jest typem bez znaku, nie może reprezentować liczby ujemnej. Jeśli używasz operatora jednoargumentowego minus (`-`) w wyrażeniu, które oblicza `Byte`, Visual Basic konwertuje wyrażenie na `Short` jako pierwsze.
  
- **Konwersje formatu.** Gdy Visual Basic odczytuje lub zapisuje pliki, lub gdy wywołuje biblioteki DLL, metody i właściwości, można automatycznie konwertować między formatami danych. Dane binarne przechowywane w zmiennych `Byte` i tablicach są zachowywane podczas konwersji tego formatu. Nie należy używać zmiennej `String` dla danych binarnych, ponieważ jej zawartość może być uszkodzona podczas konwersji między formatami ANSI i Unicode.

- **Rozszerzającą.** Typ danych `Byte` poszerza do `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`lub `Double`. Oznacza to, że można skonwertować `Byte` do dowolnego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.
  
- **Znaki typu.** `Byte` nie ma znaku typu literału lub typu identyfikatora.

- **Typ struktury.** Odpowiedni typ w .NET Framework jest strukturą <xref:System.Byte?displayProperty=nameWithType>.

## <a name="example"></a>Przykład

 W poniższym przykładzie `b` jest zmienną `Byte`. Instrukcje przedstawiają zakres zmiennej i zastosowano do niej operatory przesunięcia bitowego.

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a>Zobacz także

- <xref:System.Byte?displayProperty=nameWithType>
- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

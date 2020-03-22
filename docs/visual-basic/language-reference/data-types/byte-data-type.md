---
title: Byte — Typ danych
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 347d7e7d0f09e089886bc81bd0be659deaca9b46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400744"
---
# <a name="byte-data-type-visual-basic"></a>Typ danych bajtów (Visual Basic)

Przechowuje niepodpisane 8-bitowe (1-bajtowe) liczby całkowite o wartości od 0 do 255.

## <a name="remarks"></a>Uwagi

Użyj `Byte` typu danych, aby zawierać dane binarne.  
  
Wartość domyślna `Byte` to 0.

## <a name="literal-assignments"></a>Przydziały dosłowne

Można zadeklarować i `Byte` zainicjować zmienną, przypisując jej literał dziesiętny, szesnastkowy literał, literał ósemkowy lub (zaczynając od języka Visual Basic 2017) literał binarny. Jeśli literał integralny znajduje się `Byte` poza zakresem a (czyli jeśli jest mniejszy <xref:System.Byte.MinValue?displayProperty=nameWithType> lub większy niż), <xref:System.Byte.MaxValue?displayProperty=nameWithType>występuje błąd kompilacji.

W poniższym przykładzie liczby całkowite równe 201, które są reprezentowane jako dziesiętne, szesnastkowe i binarne literały są niejawnie konwertowane z [liczby całkowitej](integer-data-type.md) na `byte` wartości.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> Prefiksu `&h` lub `&H` oznaczasz szesnastkowy literał, `&b` `&B` prefiks lub oznacza literał binarny i prefiks `&o` lub `&O` oznacza literał ósemkowy. Literały dziesiętne nie mają prefiksu.

Począwszy od języka Visual Basic 2017, `_`można również użyć znaku podkreślenia, jako separatora cyfry, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

Począwszy od języka Visual Basic 15.5,`_`można również użyć znaku podkreślenia ( ) jako interełownika wiodącego między prefiksem a cyframi szesnastkowymi, binarnymi lub ósemkowymi. Przykład:

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a>Porady dotyczące programowania

- **Liczby ujemne.** Ponieważ `Byte` jest typem niepodpisanym, nie może reprezentować liczby ujemnej. Jeśli w wyrażeniu, które ma być wpisane, użyjesz operatora unary minus (`-`) w wyrażeniu, które ma być wpisane, `Byte`visual basic konwertuje wyrażenie na `Short` pierwsze.
  
- **Formatowanie konwersji.** Gdy program Visual Basic odczytuje lub zapisuje pliki lub gdy wywołuje biblioteki DLL, metody i właściwości, może automatycznie konwertować między formatami danych. Dane binarne przechowywane w `Byte` zmiennych i tablicach są zachowywane podczas konwersji formatu. Nie należy używać `String` zmiennej dla danych binarnych, ponieważ jej zawartość może być uszkodzona podczas konwersji między formatami ANSI i Unicode.

- **Poszerzenie.** Typ `Byte` danych rozszerza `Short`się `UShort` `Integer`do `UInteger` `Long`, `ULong` `Decimal`, `Single`, `Double`, , , , , lub . Oznacza to, `Byte` że można przekonwertować <xref:System.OverflowException?displayProperty=nameWithType> do dowolnego z tych typów bez napotkania błędu.
  
- **Wpisz znaki.** `Byte`nie ma znaku literału ani znaku typu identyfikatora.

- **Typ struktury.** Odpowiedni typ w .NET Framework <xref:System.Byte?displayProperty=nameWithType> jest strukturą.

## <a name="example"></a>Przykład

 W poniższym `b` przykładzie `Byte` jest zmienną. Instrukcje pokazują zakres zmiennej i zastosowanie operatorów zmiany bitowej do niej.

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a>Zobacz też

- <xref:System.Byte?displayProperty=nameWithType>
- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

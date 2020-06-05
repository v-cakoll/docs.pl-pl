---
title: Byte, typ danych
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 97acd1bc2ff29bac6588216b9ee4a4f187078815
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374320"
---
# <a name="byte-data-type-visual-basic"></a>Byte — typ danych (Visual Basic)

Zawiera 8-bitowe (1-bajtowe) liczby całkowite bez znaku, który ma wartość z zakresu od 0 do 255.

## <a name="remarks"></a>Uwagi

Użyj `Byte` typu danych, aby zawierać dane binarne.  
  
Wartość domyślna `Byte` to 0.

## <a name="literal-assignments"></a>Przypisania literałów

Można zadeklarować i zainicjować `Byte` zmienną, przypisując jej literał dziesiętny, literał szesnastkowy, literał ósemkowy lub (Zaczynając od Visual Basic 2017) literał binarny. Jeśli literał całkowity znajduje się poza zakresem `Byte` (czyli, jeśli jest mniejszy <xref:System.Byte.MinValue?displayProperty=nameWithType> lub równy <xref:System.Byte.MaxValue?displayProperty=nameWithType> ), wystąpi błąd kompilacji.

W poniższym przykładzie liczby całkowite równe 201 są reprezentowane jako literały dziesiętne, szesnastkowe i binarne są niejawnie konwertowane z [liczby całkowitej](integer-data-type.md) na `byte` wartości.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> Używasz prefiksu `&h` lub `&H` do oznaczenia literału szesnastkowego, prefiksu `&b` lub `&B` do oznaczania literału binarnego oraz prefiksu `&o` lub `&O` do określenia literału ósemkowego. Literały dziesiętne nie mają prefiksu.

Począwszy od Visual Basic 2017, można również użyć znaku podkreślenia, `_` jako separatora cyfr, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

Począwszy od Visual Basic 15,5, można również użyć znaku podkreślenia ( `_` ) jako wiodącego separatora między cyframi prefiksu i szesnastkową, binarną lub ósemkową. Przykład:

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a>Porady dotyczące programowania

- **Liczby ujemne.** Ponieważ `Byte` jest typem bez znaku, nie może reprezentować liczby ujemnej. W przypadku użycia jednoargumentowego operatora minus ( `-` ) w wyrażeniu, którego typem jest typ `Byte` , Visual Basic konwertuje wyrażenie na `Short` pierwsze.
  
- **Konwersje formatu.** Gdy Visual Basic odczytuje lub zapisuje pliki, lub gdy wywołuje biblioteki DLL, metody i właściwości, można automatycznie konwertować między formatami danych. Dane binarne przechowywane w `Byte` zmiennych i tablicach są zachowywane podczas konwersji formatowania. Nie należy używać `String` zmiennej dla danych binarnych, ponieważ jej zawartość może być uszkodzona podczas konwersji między formatami ANSI i Unicode.

- **Rozszerzającą.** `Byte`Typ danych jest rozszerzany do,,,,,, `Short` ,, `UShort` `Integer` `UInteger` `Long` `ULong` `Decimal` `Single` lub `Double` . Oznacza to, że można dokonać konwersji `Byte` do dowolnego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.
  
- **Znaki typu.** `Byte`nie ma znaku typu literału lub znaku typu identyfikatora.

- **Typ struktury.** Odpowiedni typ w .NET Framework jest <xref:System.Byte?displayProperty=nameWithType> strukturą.

## <a name="example"></a>Przykład

 W poniższym przykładzie `b` jest `Byte` zmienną. Instrukcje przedstawiają zakres zmiennej i zastosowano do niej operatory przesunięcia bitowego.

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a>Zobacz też

- <xref:System.Byte?displayProperty=nameWithType>
- [Typy danych](index.md)
- [Funkcje konwersji typu](../functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../keywords/conversion-summary.md)
- [Skuteczne stosowanie typów danych](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)

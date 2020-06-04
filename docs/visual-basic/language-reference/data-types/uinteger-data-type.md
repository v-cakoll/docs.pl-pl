---
title: UInteger, typ danych
ms.date: 01/31/2018
f1_keywords:
- vb.uinteger
helpviewer_keywords:
- numbers [Visual Basic], whole
- UInteger data type
- literal type characters [Visual Basic], UI
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- UI literal type characters [Visual Basic]
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
ms.openlocfilehash: 11070f6c7f3259b8c34528eb54d99b031b68f9f9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415547"
---
# <a name="uinteger-data-type"></a>UInteger — Typ danych

Przechowuje niepodpisane liczby całkowite 32-bitowe (4-bajtowe) w zakresie wartości z zakresu od 0 do 4 294 967 295.

## <a name="remarks"></a>Uwagi

`UInteger`Typ danych zapewnia największą wartość bez znaku w najbardziej wydajnej szerokości danych.

Wartość domyślna `UInteger` to 0.

## <a name="literal-assignments"></a>Przypisania literałów

Można zadeklarować i zainicjować `UInteger` zmienną, przypisując jej literał dziesiętny, literał szesnastkowy, literał ósemkowy lub (Zaczynając od Visual Basic 2017) literał binarny. Jeśli literał liczby całkowitej znajduje się poza zakresem `UInteger` (to jest, jeśli jest mniejszy niż <xref:System.UInt32.MinValue?displayProperty=nameWithType> lub większy niż <xref:System.UInt32.MaxValue?displayProperty=nameWithType> , wystąpi błąd kompilacji.

W poniższym przykładzie liczby całkowite równe 3 000 000 000 są reprezentowane jako literały dziesiętne, szesnastkowe i binarne są przypisywane do `UInteger` wartości.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> Używasz prefiksu `&h` lub `&H` do oznaczenia literału szesnastkowego, prefiksu `&b` lub `&B` do oznaczania literału binarnego oraz prefiksu `&o` lub `&O` do określenia literału ósemkowego. Literały dziesiętne nie mają prefiksu.

Począwszy od Visual Basic 2017, można również użyć znaku podkreślenia, `_` jako separatora cyfr, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

Począwszy od Visual Basic 15,5, można również użyć znaku podkreślenia ( `_` ) jako wiodącego separatora między cyframi prefiksu i szesnastkową, binarną lub ósemkową. Przykład:

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literały numeryczne mogą również zawierać `UI` `ui` [znak](../../programming-guide/language-features/data-types/type-characters.md) lub, aby zauważyć `UInteger` Typ danych, jak pokazano w poniższym przykładzie.

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a>Porady dotyczące programowania

`UInteger`Typy i `Integer` zapewniają optymalną wydajność procesora 32-bitowego, ponieważ mniejsze typy całkowite ( `UShort` , `Short` , `Byte` i `SByte` ), nawet jeśli używają mniejszej liczby bitów, poświęć więcej czasu na załadowanie, przechowywanie i pobieranie.

- **Liczby ujemne.** Ponieważ `UInteger` jest typem bez znaku, nie może reprezentować liczby ujemnej. W przypadku użycia jednoargumentowego operatora minus ( `-` ) w wyrażeniu, którego typem jest typ `UInteger` , Visual Basic konwertuje wyrażenie na `Long` pierwsze.

- **Zgodność ze specyfikacją CLS.** `UInteger`Typ danych nie jest częścią [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), więc kod zgodny ze specyfikacją CLS nie może używać składnika, który go używa.

- **Zagadnienia dotyczące międzyoperacyjnych.** Jeśli korzystasz z składników niepisanych dla .NET Framework, na przykład obiektów automatyzacji lub COM, pamiętaj, że typy takie jak `uint` mogą mieć różną szerokość danych (16 bitów) w innych środowiskach. Jeśli przekazujesz argument 16-bitowy do takiego składnika, zadeklaruj go jako `UShort` zamiast `UInteger` w kodzie zarządzanym Visual Basic.

- **Rozszerzającą.** `UInteger`Typ danych poszerza do `Long` ,,, `ULong` `Decimal` `Single` , i `Double` . Oznacza to, że można dokonać konwersji `UInteger` do dowolnego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.

- **Znaki typu.** Dołączanie znaków literału `UI` do literału wymusza jego do `UInteger` typu danych. `UInteger`nie ma znaku typu identyfikatora.

- **Typ struktury.** Odpowiedni typ w .NET Framework jest <xref:System.UInt32?displayProperty=nameWithType> strukturą.

## <a name="see-also"></a>Zobacz też

- <xref:System.UInt32>
- [Typy danych](index.md)
- [Funkcje konwersji typu](../functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../keywords/conversion-summary.md)
- [Instrukcje: Wywoływanie funkcji systemu Windows wykorzystującej typy bez znaku](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Skuteczne stosowanie typów danych](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)

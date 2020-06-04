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
ms.openlocfilehash: aa7b64162308d6af2763b29034c5a7276c973876
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415612"
---
# <a name="integer-data-type-visual-basic"></a>Integer — typ danych (Visual Basic)

Przechowuje 32-bitowe (4-bajtowe) liczby całkowite ze znakiem z zakresu wartości od -2 147 483,648 do 2 147 483 647.  
  
## <a name="remarks"></a>Uwagi

 `Integer`Typ danych zapewnia optymalną wydajność procesora 32-bitowego. Inne typy całkowitoliczbowe wolniej wczytują się z pamięci i są w niej zapisywane.  
  
 Wartość domyślna `Integer` to 0.  

## <a name="literal-assignments"></a>Przypisania literałów

Można zadeklarować i zainicjować `Integer` zmienną, przypisując jej literał dziesiętny, literał szesnastkowy, literał ósemkowy lub (Zaczynając od Visual Basic 2017) literał binarny. Jeśli literał liczby całkowitej znajduje się poza zakresem `Integer` (to jest, jeśli jest mniejszy niż <xref:System.Int32.MinValue?displayProperty=nameWithType> lub większy niż <xref:System.Int32.MaxValue?displayProperty=nameWithType> , wystąpi błąd kompilacji.

W poniższym przykładzie liczby całkowite równe 90 946 są reprezentowane jako literały dziesiętne, szesnastkowe i binarne są przypisywane do `Integer` wartości.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> Używasz prefiksu `&h` lub `&H` do oznaczenia literału szesnastkowego, prefiksu `&b` lub `&B` do oznaczania literału binarnego oraz prefiksu `&o` lub `&O` do określenia literału ósemkowego. Literały dziesiętne nie mają prefiksu.

Począwszy od Visual Basic 2017, można również użyć znaku podkreślenia, `_` jako separatora cyfr, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

Począwszy od Visual Basic 15,5, można również użyć znaku podkreślenia ( `_` ) jako wiodącego separatora między cyframi prefiksu i szesnastkową, binarną lub ósemkową. Przykład:

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literały numeryczne mogą również zawierać `I` [znak typu](../../programming-guide/language-features/data-types/type-characters.md) , aby zauważyć `Integer` Typ danych, jak pokazano w poniższym przykładzie.

```vb
Dim number = &H_035826I
```

## <a name="programming-tips"></a>Porady dotyczące programowania

- **Zagadnienia dotyczące międzyoperacyjnych.** Jeśli korzystasz z składników niepisanych dla .NET Framework, takich jak Automatyzacja lub obiekty COM, pamiętaj, że `Integer` w innych środowiskach ma inną szerokość danych (16 bitów). Jeśli przekazujesz argument 16-bitowy do takiego składnika, zadeklaruj go jako `Short` zamiast `Integer` w nowym kodzie Visual Basic.  
  
- **Rozszerzającą.** `Integer`Typ danych poszerza do `Long` , `Decimal` , `Single` , lub `Double` . Oznacza to, że można przekonwertować `Integer` na jeden z tych typów, bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.  
  
- **Znaki typu.** Dołączanie znaku typu literału `I` do literału wymusza jego `Integer` Typ danych. Dołączanie znaku typu identyfikatora `%` do dowolnego identyfikatora zmusza go do `Integer` .  
  
- **Typ struktury.** Odpowiedni typ w .NET Framework jest <xref:System.Int32?displayProperty=nameWithType> strukturą.  
  
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
- [Typy danych](index.md)
- [Long, typ danych](long-data-type.md)
- [Short, typ danych](short-data-type.md)
- [Funkcje konwersji typu](../functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../keywords/conversion-summary.md)
- [Skuteczne stosowanie typów danych](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)

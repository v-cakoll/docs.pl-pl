---
title: Object — typ danych (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Object
- vb.Variant
helpviewer_keywords:
- object variables [Visual Basic], Object type
- data types [Visual Basic], assigning
- Object data type
- Object data type [Visual Basic], reference
ms.assetid: 61ea4a7c-3b3d-48d4-adc4-eacfa91779b2
ms.openlocfilehash: 1ac906494c49810e3d389591b1044f412e7320bc
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2019
ms.locfileid: "68513049"
---
# <a name="object-data-type"></a>Object — typ danych

Przechowuje adresy odwołujące się do obiektów. Do `Object` zmiennej można przypisać dowolny typ referencyjny (ciąg, tablicę, klasę lub interfejs). Zmienna może również odwoływać się do danych dowolnego typu wartości (numeryczne `Boolean`, `Char`, `Date`,, struktura lub Wyliczenie). `Object`

## <a name="remarks"></a>Uwagi

Typ `Object` danych może wskazywać na dane dowolnego typu danych, łącznie z każdym wystąpieniem obiektu rozpoznawanym przez aplikację. Użyj `Object` , gdy w czasie kompilacji nie wiesz, jaki typ danych może wskazywać zmienna.

Wartość `Object` domyślna to `Nothing` (odwołanie o wartości null).

## <a name="data-types"></a>Typy danych

Do `Object` zmiennej można przypisać zmienną, stałą lub wyrażenie dowolnego typu danych. Aby określić typ `Object` danych, do której obecnie odwołuje się zmienna, można <xref:System.Type.GetTypeCode%2A> użyć metody <xref:System.Type?displayProperty=nameWithType> klasy. Ilustruje to poniższy przykład.

```vb
Dim myObject As Object
' Suppose myObject has now had something assigned to it.
Dim datTyp As Integer
datTyp = Type.GetTypeCode(myObject.GetType())
```

Typ `Object` danych jest typem referencyjnym. Jednakże Visual Basic traktuje `Object` zmienną jako typ wartości, gdy odwołuje się ona do danych typu wartości.

## <a name="storage"></a>Magazyn

Niezależnie od typu danych, do którego się `Object` odwołuje, zmienna nie zawiera samej wartości danych, ale raczej wskaźnikiem do wartości. Zawsze używa czterech bajtów w pamięci komputera, ale nie obejmuje to magazynu dla danych reprezentujących wartość zmiennej. Ze względu na kod, który używa wskaźnika do lokalizowania danych `Object` , zmienne o typach wartości są nieco wolniejsze w celu uzyskania dostępu niż jawnie wpisane zmienne.

## <a name="programming-tips"></a>Porady dla programistów

- **Zagadnienia dotyczące międzyoperacyjnych.** Jeśli masz połączenie ze składnikami niezapisanymi dla .NET Framework, na przykład obiekty automatyzacji lub com, pamiętaj, że typy wskaźnika w innych środowiskach nie są zgodne z typem Visual Basic `Object` .

- **Wydajność.** Zmienna zadeklarowana z `Object` typem jest wystarczająco elastyczny, aby zawierała odwołanie do dowolnych obiektów. Jednak po wywołaniu metody lub właściwości w takiej zmiennej zawsze naliczane są *późne powiązania* (w czasie wykonywania). Aby wymusić *wczesne wiązanie* (w czasie kompilacji) i lepszą wydajność, należy zadeklarować zmienną z określoną nazwą klasy lub rzutować ją na określony typ danych.

  Podczas deklarowania zmiennej obiektu spróbuj użyć konkretnego typu klasy, na przykład <xref:System.OperatingSystem>, zamiast `Object` typu uogólnionego. Należy również użyć najbardziej konkretnej dostępnej klasy, takiej jak <xref:System.Windows.Forms.TextBox> <xref:System.Windows.Forms.Control>zamiast, aby można było uzyskać dostęp do jej właściwości i metod. Zazwyczaj można użyć listy **klas** w **Przeglądarka obiektów** , aby znaleźć dostępne nazwy klas.

- **Rozszerzającą.** Wszystkie typy danych i wszystkie typy odwołań rozszerzają się `Object` do typu danych. Oznacza to, że można skonwertować dowolny typ `Object` do bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.

  Jednak w przypadku konwersji między typami wartości i `Object`, Visual Basic wykonuje operacje nazywane *opakowaniem* i rozpakowywaniem, co powoduje wolniejsze wykonywanie.

- **Znaki typu.** `Object`nie ma znaku typu literału lub znaku typu identyfikatora.

- **Typ struktury.** Odpowiedni typ w .NET Framework jest <xref:System.Object?displayProperty=nameWithType> klasą.

## <a name="example"></a>Przykład

Poniższy przykład ilustruje `Object` zmienną wskazującą wystąpienie obiektu.

```vb
Dim objDb As Object
Dim myCollection As New Collection()
' Suppose myCollection has now been populated.
objDb = myCollection.Item(1)
```

## <a name="see-also"></a>Zobacz także

- <xref:System.Object>
- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Instrukcje: Określanie, czy dwa obiekty są powiązane](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Instrukcje: Określanie, czy dwa obiekty są identyczne](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)

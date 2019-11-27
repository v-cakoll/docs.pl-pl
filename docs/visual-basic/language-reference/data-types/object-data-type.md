---
title: Object — typ danych
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
ms.openlocfilehash: 2ccb9b69b865c259d078ed9642d63c7f83514756
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343964"
---
# <a name="object-data-type"></a>Object — typ danych

Przechowuje adresy odwołujące się do obiektów. Do zmiennej `Object` można przypisać dowolny typ referencyjny (ciąg, tablicę, klasę lub interfejs). Zmienna `Object` może odwoływać się również do danych dowolnego typu wartości (numeryczne, `Boolean`, `Char`, `Date`, struktura lub Wyliczenie).

## <a name="remarks"></a>Uwagi

Typ danych `Object` może wskazywać na dane dowolnego typu danych, łącznie z każdym wystąpieniem obiektu rozpoznawanym przez aplikację. Użyj `Object`, gdy nie wiesz w czasie kompilacji, jakie dane może wskazywać zmienna.

Wartość domyślna `Object` jest `Nothing` (odwołanie o wartości null).

## <a name="data-types"></a>Typy danych

Do zmiennej `Object` można przypisać zmienną, stałą lub wyrażenie dowolnego typu danych. Aby określić typ danych, do których odwołuje się `Object` zmienna, można użyć metody <xref:System.Type.GetTypeCode%2A> klasy <xref:System.Type?displayProperty=nameWithType>. Ilustruje to poniższy przykład.

```vb
Dim myObject As Object
' Suppose myObject has now had something assigned to it.
Dim datTyp As Integer
datTyp = Type.GetTypeCode(myObject.GetType())
```

Typ danych `Object` jest typem referencyjnym. Jednak Visual Basic traktuje zmienną `Object` jako typ wartości, gdy odwołuje się ona do danych typu wartości.

## <a name="storage"></a>Magazyn

Niezależnie od tego, jaki typ danych odwołuje się do, zmienna `Object` nie zawiera samej wartości danych, ale raczej wskaźnikiem do wartości. Zawsze używa czterech bajtów w pamięci komputera, ale nie obejmuje to magazynu dla danych reprezentujących wartość zmiennej. Ze względu na kod, który używa wskaźnika do lokalizowania danych, zmienne `Object` przechowujące typy wartości są nieco wolniejsze w celu uzyskania dostępu niż jawnie wpisane zmienne.

## <a name="programming-tips"></a>Porady dla programistów

- **Zagadnienia dotyczące międzyoperacyjnych.** Jeśli masz połączenie ze składnikami niezapisanymi dla .NET Framework, na przykład obiekty automatyzacji lub COM, pamiętaj, że typy wskaźnika w innych środowiskach nie są zgodne z typem `Object` Visual Basic.

- **Skuteczności.** Zmienna zadeklarowana z typem `Object` jest wystarczająco elastyczna, aby zawierała odwołanie do dowolnego obiektu. Jednak po wywołaniu metody lub właściwości w takiej zmiennej zawsze naliczane są *późne powiązania* (w czasie wykonywania). Aby wymusić *wczesne wiązanie* (w czasie kompilacji) i lepszą wydajność, należy zadeklarować zmienną z określoną nazwą klasy lub rzutować ją na określony typ danych.

  Podczas deklarowania zmiennej obiektu spróbuj użyć konkretnego typu klasy, na przykład <xref:System.OperatingSystem>, zamiast uogólnionego typu `Object`. Należy również użyć najbardziej konkretnej dostępnej klasy, takiej jak <xref:System.Windows.Forms.TextBox>, a nie <xref:System.Windows.Forms.Control>, aby można było uzyskać dostęp do jej właściwości i metod. Zazwyczaj można użyć listy **klas** w **Przeglądarka obiektów** , aby znaleźć dostępne nazwy klas.

- **Rozszerzającą.** Wszystkie typy danych i wszystkie typy odwołań rozszerzają się do typu danych `Object`. Oznacza to, że można skonwertować dowolny typ do `Object` bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.

  Jednak w przypadku konwersji między typami wartości i `Object`, Visual Basic wykonuje operacje nazywane *opakowaniem* i *rozpakowywaniem*, co powoduje wolniejsze wykonywanie.

- **Znaki typu.** `Object` nie ma znaku typu literału lub typu identyfikatora.

- **Typ struktury.** Odpowiedni typ w .NET Framework jest klasą <xref:System.Object?displayProperty=nameWithType>.

## <a name="example"></a>Przykład

Poniższy przykład ilustruje zmienną `Object` wskazującą na wystąpienie obiektu.

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
- [Instrukcje: określanie, czy dwa obiekty są powiązane](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Instrukcje: określanie, czy dwa obiekty są jednakowe](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)

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
ms.openlocfilehash: 14770e74a0169dba3a45a04845dd32323e6201e3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415586"
---
# <a name="object-data-type"></a>Object — typ danych

Przechowuje adresy odwołujące się do obiektów. Do zmiennej można przypisać dowolny typ referencyjny (ciąg, tablicę, klasę lub interfejs) `Object` . `Object`Zmienna może również odwoływać się do danych dowolnego typu wartości (numeryczne, `Boolean` ,,, `Char` `Date` Struktura lub Wyliczenie).

## <a name="remarks"></a>Uwagi

`Object`Typ danych może wskazywać na dane dowolnego typu danych, łącznie z każdym wystąpieniem obiektu rozpoznawanym przez aplikację. Użyj `Object` , gdy w czasie kompilacji nie wiesz, jaki typ danych może wskazywać zmienna.

Wartość domyślna `Object` to `Nothing` (odwołanie o wartości null).

## <a name="data-types"></a>Typy danych

Do zmiennej można przypisać zmienną, stałą lub wyrażenie dowolnego typu danych `Object` . Aby określić typ danych `Object` , do której obecnie odwołuje się zmienna, można użyć <xref:System.Type.GetTypeCode%2A> metody <xref:System.Type?displayProperty=nameWithType> klasy. Ilustruje to poniższy przykład.

```vb
Dim myObject As Object
' Suppose myObject has now had something assigned to it.
Dim datTyp As Integer
datTyp = Type.GetTypeCode(myObject.GetType())
```

`Object`Typ danych jest typem referencyjnym. Jednakże Visual Basic traktuje `Object` zmienną jako typ wartości, gdy odwołuje się ona do danych typu wartości.

## <a name="storage"></a>Magazyn

Niezależnie od typu danych, do którego się odwołuje, `Object` zmienna nie zawiera samej wartości danych, ale raczej wskaźnikiem do wartości. Zawsze używa czterech bajtów w pamięci komputera, ale nie obejmuje to magazynu dla danych reprezentujących wartość zmiennej. Ze względu na kod, który używa wskaźnika do lokalizowania danych, `Object` zmienne o typach wartości są nieco wolniejsze w celu uzyskania dostępu niż jawnie wpisane zmienne.

## <a name="programming-tips"></a>Porady dla programistów

- **Zagadnienia dotyczące międzyoperacyjnych.** Jeśli masz połączenie ze składnikami niezapisanymi dla .NET Framework, na przykład obiekty automatyzacji lub COM, pamiętaj, że typy wskaźnika w innych środowiskach nie są zgodne z `Object` typem Visual Basic.

- **Skuteczności.** Zmienna zadeklarowana z `Object` typem jest wystarczająco elastyczny, aby zawierała odwołanie do dowolnych obiektów. Jednak po wywołaniu metody lub właściwości w takiej zmiennej zawsze naliczane są *późne powiązania* (w czasie wykonywania). Aby wymusić *wczesne wiązanie* (w czasie kompilacji) i lepszą wydajność, należy zadeklarować zmienną z określoną nazwą klasy lub rzutować ją na określony typ danych.

  Podczas deklarowania zmiennej obiektu spróbuj użyć konkretnego typu klasy, na przykład <xref:System.OperatingSystem> , zamiast typu uogólnionego `Object` . Należy również użyć najbardziej konkretnej dostępnej klasy, takiej jak <xref:System.Windows.Forms.TextBox> zamiast <xref:System.Windows.Forms.Control> , aby można było uzyskać dostęp do jej właściwości i metod. Zazwyczaj można użyć listy **klas** w **Przeglądarka obiektów** , aby znaleźć dostępne nazwy klas.

- **Rozszerzającą.** Wszystkie typy danych i wszystkie typy odwołań rozszerzają się do `Object` typu danych. Oznacza to, że można skonwertować dowolny typ do `Object` bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.

  Jednak w przypadku konwersji między typami wartości i `Object` , Visual Basic wykonuje operacje nazywane *opakowaniem* i *rozpakowywaniem*, co powoduje wolniejsze wykonywanie.

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

## <a name="see-also"></a>Zobacz też

- <xref:System.Object>
- [Typy danych](index.md)
- [Funkcje konwersji typu](../functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../keywords/conversion-summary.md)
- [Skuteczne stosowanie typów danych](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Porady: określanie, czy dwa obiekty są powiązane](../../programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Porady: określanie, czy dwa obiekty są jednakowe](../../programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)

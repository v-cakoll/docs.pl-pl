---
title: Definicja typu anonimowego
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: 952eb295cc71eab5d0ad6e18f2b697a9b701b434
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404904"
---
# <a name="anonymous-type-definition-visual-basic"></a>Definicja typu anonimowego (Visual Basic)

W odpowiedzi na deklarację wystąpienia typu anonimowego kompilator tworzy nową definicję klasy, która zawiera określone właściwości dla tego typu.

## <a name="compiler-generated-code"></a>Kod wygenerowany przez kompilator

Dla następującej definicji `product` , kompilator tworzy nową definicję klasy, która zawiera właściwości `Name` , `Price` i `OnHand` .

[!code-vb[VbVbalrAnonymousTypes#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#25)]

Definicja klasy zawiera definicje właściwości podobne do następujących. Zwróć uwagę, że nie ma `Set` metody właściwości klucza. Wartości właściwości klucza są tylko do odczytu.

```vb
Public Class $Anonymous1
    Private _name As String
    Private _price As Double
    Private _onHand As Integer
     Public ReadOnly Property Name() As String
        Get
            Return _name
        End Get
    End Property

    Public ReadOnly Property Price() As Double
        Get
            Return _price
        End Get
    End Property

    Public Property OnHand() As Integer
        Get
            Return _onHand
        End Get
        Set(ByVal Value As Integer)
            _onHand = Value
        End Set
    End Property

End Class
```

Ponadto definicja typu anonimowego zawiera konstruktora bez parametrów. Konstruktory wymagające parametrów są niedozwolone.

Jeśli deklaracja typu anonimowego zawiera co najmniej jedną właściwość klucza, definicja typu przesłania trzy składowe dziedziczone z <xref:System.Object> : <xref:System.Object.Equals%2A> , <xref:System.Object.GetHashCode%2A> , i <xref:System.Object.ToString%2A> . Jeśli nie są zadeklarowane żadne właściwości klucza, tylko <xref:System.Object.ToString%2A> jest zastępowany. Przesłonięcia zapewniają następujące funkcje:

- `Equals`zwraca `True` Jeśli dwa wystąpienia typu anonimowego są tego samego wystąpienia lub spełniają następujące warunki:

  - Mają tę samą liczbę właściwości.

  - Właściwości są deklarowane w tej samej kolejności, z tymi samymi nazwami i tymi samymi typem wywnioskowanym. W porównaniach nazw nie jest rozróżniana wielkość liter.

  - Co najmniej jedna z właściwości jest właściwością klucza, a `Key` słowo kluczowe jest stosowane do tych samych właściwości.

  - Porównanie każdej odpowiadającej pary właściwości klucza zwraca wartość `True` .

    Na przykład, w poniższych przykładach `Equals` zwraca `True` tylko dla `employee01` i `employee08` . Komentarz przed każdym wierszem określa powód, dla którego nowe wystąpienie jest niezgodne `employee01` .

    [!code-vb[VbVbalrAnonymousTypes#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#24)]

- `GetHashcode`zapewnia odpowiedni unikatowy algorytm GetHashCode. Algorytm używa tylko właściwości klucza do obliczenia kodu skrótu.

- `ToString`Zwraca ciąg łączonych wartości właściwości, jak pokazano w poniższym przykładzie. Uwzględniane są zarówno właściwości klucza, jak i niebędących kluczami.

  [!code-vb[VbVbalrAnonymousTypes#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#29)]

Właściwości jawnie nazwane typu anonimowego nie mogą powodować konfliktu z tymi wygenerowanymi metodami. Oznacza to, że nie można `.Equals` użyć `.GetHashCode` `.ToString` właściwości.

Definicje typu anonimowego, które obejmują co najmniej jedną właściwość klucza, również implementują <xref:System.IEquatable%601?displayProperty=nameWithType> interfejs, gdzie `T` jest typem typu anonimowego.

> [!NOTE]
> Deklaracje typu anonimowego tworzą ten sam typ anonimowy tylko wtedy, gdy występują w tym samym zestawie, ich właściwości mają takie same nazwy, jak te same wywnioskowane typy, właściwości są deklarowane w tej samej kolejności, a te same właściwości są oznaczane jako właściwości klucza.

## <a name="see-also"></a>Zobacz też

- [Typy anonimowe](anonymous-types.md)
- [Instrukcje: wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)

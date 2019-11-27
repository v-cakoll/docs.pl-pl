---
title: Definicja typu anonimowego
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: f8ac26577a7fbef865605a7ecf643fa733b2c2c0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344917"
---
# <a name="anonymous-type-definition-visual-basic"></a>Definicja typu anonimowego (Visual Basic)

W odpowiedzi na deklarację wystąpienia typu anonimowego kompilator tworzy nową definicję klasy, która zawiera określone właściwości dla tego typu.

## <a name="compiler-generated-code"></a>Kod wygenerowany przez kompilator

Dla następującej definicji `product`kompilator tworzy nową definicję klasy, która zawiera właściwości `Name`, `Price`i `OnHand`.

[!code-vb[VbVbalrAnonymousTypes#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#25)]

Definicja klasy zawiera definicje właściwości podobne do następujących. Należy zauważyć, że nie ma `Set` metody dla właściwości klucza. Wartości właściwości klucza są tylko do odczytu.

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

Jeśli deklaracja typu anonimowego zawiera co najmniej jedną właściwość klucza, definicja typu przesłania trzy składowe dziedziczone z <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>i <xref:System.Object.ToString%2A>. Jeśli nie zadeklarowano żadnych właściwości klucza, tylko <xref:System.Object.ToString%2A> jest zastępowany. Przesłonięcia zapewniają następujące funkcje:

- `Equals` zwraca `True`, jeśli dwa wystąpienia typu anonimowego są tego samego wystąpienia lub spełniają następujące warunki:

  - Mają tę samą liczbę właściwości.

  - Właściwości są deklarowane w tej samej kolejności, z tymi samymi nazwami i tymi samymi typem wywnioskowanym. W porównaniach nazw nie jest rozróżniana wielkość liter.

  - Co najmniej jedna z właściwości jest właściwością klucza, a słowo kluczowe `Key` jest stosowane do tych samych właściwości.

  - Porównanie każdej odpowiadającej pary właściwości klucza zwraca `True`.

    Na przykład w poniższych przykładach `Equals` zwraca `True` tylko dla `employee01` i `employee08`. Komentarz przed każdym wierszem określa powód, dla którego nowe wystąpienie nie jest zgodne `employee01`.

    [!code-vb[VbVbalrAnonymousTypes#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#24)]

- `GetHashcode` zapewnia odpowiedni unikatowy algorytm GetHashCode. Algorytm używa tylko właściwości klucza do obliczenia kodu skrótu.

- `ToString` zwraca ciąg połączonych wartości właściwości, jak pokazano w poniższym przykładzie. Uwzględniane są zarówno właściwości klucza, jak i niebędących kluczami.

  [!code-vb[VbVbalrAnonymousTypes#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#29)]

Właściwości jawnie nazwane typu anonimowego nie mogą powodować konfliktu z tymi wygenerowanymi metodami. Oznacza to, że nie można użyć `.Equals`, `.GetHashCode`lub `.ToString` do nazwy właściwości.

Definicje typu anonimowego, które obejmują co najmniej jedną właściwość klucza, również implementują interfejs <xref:System.IEquatable%601?displayProperty=nameWithType>, gdzie `T` jest typem typu anonimowego.

> [!NOTE]
> Deklaracje typu anonimowego tworzą ten sam typ anonimowy tylko wtedy, gdy występują w tym samym zestawie, ich właściwości mają takie same nazwy, jak te same wywnioskowane typy, właściwości są deklarowane w tej samej kolejności, a te same właściwości są oznaczane jako właściwości klucza.

## <a name="see-also"></a>Zobacz także

- [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Instrukcje: wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)

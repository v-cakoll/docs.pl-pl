---
title: Definicja typu anonimowego (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: 832d56f5c51aea87185f36ec306c3fec036a40e0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780851"
---
# <a name="anonymous-type-definition-visual-basic"></a>Definicja typu anonimowego (Visual Basic)

W odpowiedzi na deklarację wystąpienia typu anonimowego kompilator utworzy nową definicję klasy, która zawiera określone właściwości typu.

## <a name="compiler-generated-code"></a>Kod wygenerowany przez kompilator

Dla następujących definicji `product`, kompilator utworzy nową definicję klasy, który zawiera właściwości `Name`, `Price`, i `OnHand`.

[!code-vb[VbVbalrAnonymousTypes#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#25)]

Definicja klasy zawiera podobne do następujących definicji właściwości. Zwróć uwagę, że ma nie `Set` metody dla właściwości klucza. Wartości właściwości klucza są tylko do odczytu.

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

Ponadto definicje typów anonimowych zawierać konstruktora domyślnego. Konstruktory, które są wymagane parametry nie są dozwolone.

Jeśli deklaracja typu anonimowego zawiera co najmniej jedną właściwość klucza, definicja typu zastępuje trzech członków dziedziczonych po elemencie <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, i <xref:System.Object.ToString%2A>. Jeśli nie właściwości klucza nie został zadeklarowany, tylko <xref:System.Object.ToString%2A> zostanie zastąpiona. Zastąpienia są dostępne następujące funkcje:

- `Equals` Zwraca `True` czy dwa wystąpienia typu anonimowego są tego samego wystąpienia, czy są spełnione następujące warunki:

  - Mają one taką samą liczbę właściwości.

  - Właściwości są deklarowane w tej samej kolejności, przy użyciu tych samych nazw i wywnioskować takie same typy. Nazwa porównania nie jest rozróżniana wielkość liter.

  - Co najmniej jedna z właściwości jest właściwość klucza i `Key` — słowo kluczowe jest stosowany do tej samej właściwości.

  - Zwraca porównania parom odpowiednie właściwości klucza `True`.

    Na przykład w poniższych przykładach `Equals` zwraca `True` tylko w przypadku `employee01` i `employee08`. Komentarz przed każdy wiersz określa przyczyny, dlaczego nie pasuje nowe wystąpienie `employee01`.

    [!code-vb[VbVbalrAnonymousTypes#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#24)]

- `GetHashcode` zawiera unikatowy odpowiednio algorytm GetHashCode. Algorytm używa tylko właściwości klucza do Oblicz wartość skrótu.

- `ToString` Zwraca ciąg wartości właściwości połączonych, jak pokazano w poniższym przykładzie. Zarówno klucz, jak i właściwości klucza nie są uwzględniane.

  [!code-vb[VbVbalrAnonymousTypes#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#29)]

Jawnie nazwane właściwości typu anonimowego nie może powodować konflikt z tych metod wygenerowany. Oznacza to, że nie można użyć `.Equals`, `.GetHashCode`, lub `.ToString` nazwę właściwości.

Definicje typu anonimowego, które obejmują co najmniej jednej właściwości klucza również implementują <xref:System.IEquatable%601?displayProperty=nameWithType> interfejsu, gdzie `T` to rodzaj typu anonimowego.

> [!NOTE]
> Deklaracjach typu anonimowego utworzyć ten sam typ anonimowy, tylko wtedy, gdy występują one w tym samym zestawie, ich właściwości o tych samych nazwach wywnioskować takie same typy, właściwości są deklarowane w tej samej kolejności i te same właściwości są oznaczone jako właściwości klucza.

## <a name="see-also"></a>Zobacz także

- [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Instrukcje: Wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)

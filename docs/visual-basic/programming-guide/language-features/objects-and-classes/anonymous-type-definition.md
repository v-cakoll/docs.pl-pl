---
title: Definicja typu anonimowego (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: 179fb9773fde2631666498d54894037b2bbfd087
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="anonymous-type-definition-visual-basic"></a>Definicja typu anonimowego (Visual Basic)
W odpowiedzi na deklaracji wystąpienia typu anonimowego kompilator tworzy nową definicję klasy zawierający właściwości określonego typu.  
  
## <a name="compiler-generated-code"></a>Kod wygenerowany przez kompilator  
 Dla następujących definicji `product`, kompilator tworzy nową definicję klasy, który zawiera właściwości `Name`, `Price`, i `OnHand`.  
  
 [!code-vb[VbVbalrAnonymousTypes#25](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_1.vb)]  
  
 Definicja klasy zawiera definicje właściwości podobny do następującego. Należy zauważyć, że istnieje nie `Set` metody dla właściwości klucza. Wartości właściwości klucza są tylko do odczytu.  
  
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
  
 Ponadto definicji typu anonimowego zawierać konstruktora domyślnego. Konstruktory, które są wymagane parametry nie są dozwolone.  
  
 Jeśli w deklaracji typu anonimowego zawiera co najmniej jedną właściwość klucza, definicja typu zastępuje trzy członków dziedziczonych po elemencie <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, i <xref:System.Object.ToString%2A>. Nie właściwości klucza jest zadeklarowana, tylko <xref:System.Object.ToString%2A> zostanie zastąpiona. Zastąpienia są dostępne następujące funkcje:  
  
-   `Equals` Zwraca `True` czy dwa wystąpienia typu anonimowego są tego samego wystąpienia, czy są spełnione następujące warunki:  
  
    -   Mają one taką samą liczbę właściwości.  
  
    -   Właściwości są zadeklarowane w tej samej kolejności, pod tą samą nazwą i wywnioskować takie same typy. Nazwa porównania nie jest rozróżniana.  
  
    -   Co najmniej jedna z właściwości jest właściwością klucza i `Key` — słowo kluczowe jest stosowany do tej samej właściwości.  
  
    -   Zwraca porównania każda para odpowiednie właściwości klucza `True`.  
  
     Na przykład w poniższych przykładach `Equals` zwraca `True` tylko w przypadku `employee01` i `employee08`. Komentarz przed każdym wierszu określa przyczynę, dlaczego nowego wystąpienia nie pasuje `employee01`.  
  
     [!code-vb[VbVbalrAnonymousTypes#24](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_2.vb)]  
  
-   `GetHashcode` zawiera unikatowy odpowiednio algorytmu GetHashCode. Algorytm używa tylko właściwości klucza można obliczyć skrótu.  
  
-   `ToString` Zwraca ciąg o wartości właściwości połączonych, jak pokazano w poniższym przykładzie. Zarówno klucz i niż właściwości klucza są uwzględniane.  
  
     [!code-vb[VbVbalrAnonymousTypes#29](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_3.vb)]  
  
 Jawnie nazwane właściwości typu anonimowego nie powodują konflikt z tych metod wygenerowany. Oznacza to, że nie można użyć `.Equals`, `.GetHashCode`, lub `.ToString` nazwę właściwości.  
  
 Definicje typu anonimowego, które obejmują co najmniej jedna właściwość klucza również wdrożenie <xref:System.IEquatable%601?displayProperty=nameWithType> interfejsu, gdzie `T` to rodzaj typu anonimowego.  
  
> [!NOTE]
>  Deklaracje typu anonimowego tworzenia tego samego typu anonimowego tylko, jeśli występują one w tym samym zestawie, ich właściwości mają takie same nazwy i wywnioskować takie same typy właściwości są zadeklarowane w tej samej kolejności i takie same właściwości są oznaczone jako właściwości klucza.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Instrukcje: wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)

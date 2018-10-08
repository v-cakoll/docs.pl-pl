---
title: Kowariancja i Kontrawariancja (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 59224c46-9931-466b-8c6e-3648c3e609c6
ms.openlocfilehash: 241b8f5864b6e9b3e1caddde25d032a24e4d0bb7
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850455"
---
# <a name="covariance-and-contravariance-visual-basic"></a>Kowariancja i Kontrawariancja (Visual Basic)
Kowariancja i kontrawariancja w języku Visual Basic, Włącz niejawna konwersja odwołania dla typów tablicy, typy delegatów i argumenty typu generycznego. Kowariancja zachowuje zgodność przypisania i kontrawariancja odwraca go.  
  
 Poniższy kod ilustruje różnicę między zgodności przypisania, kowariancji i kontrawariancji.  
  
```vb  
' Assignment compatibility.   
Dim str As String = "test"  
' An object of a more derived type is assigned to an object of a less derived type.   
Dim obj As Object = str  
  
' Covariance.   
Dim strings As IEnumerable(Of String) = New List(Of String)()  
' An object that is instantiated with a more derived type argument   
' is assigned to an object instantiated with a less derived type argument.   
' Assignment compatibility is preserved.   
Dim objects As IEnumerable(Of Object) = strings  
  
' Contravariance.             
' Assume that there is the following method in the class:   
' Shared Sub SetObject(ByVal o As Object)  
' End Sub  
Dim actObject As Action(Of Object) = AddressOf SetObject  
  
' An object that is instantiated with a less derived type argument   
' is assigned to an object instantiated with a more derived type argument.   
' Assignment compatibility is reversed.   
Dim actString As Action(Of String) = actObject  
```  
  
 Kowariancja dla tablic umożliwia niejawną konwersję tablicę typu bardziej pochodnego do tablicy typu mniej pochodnego. Jednak ta operacja nie jest typem bezpiecznym, jak pokazano w poniższym przykładzie kodu.  
  
```vb  
Dim array() As Object = New String(10) {}  
' The following statement produces a run-time exception.  
' array(0) = 10  
```  
  
 Kowariancja i kontrawariancja obsługę grupy metod umożliwia podpisów metod dopasowania z typów obiektów delegowanych. Dzięki temu można przypisać do delegatów nie tylko tych metod, które pasują do sygnatur, ale także metody, które zwracają czy pochodne więcej typów (korelacja) lub że akceptujesz parametry, które mają mniej pochodne typy (kontrawariancja) niż określona przez typ delegata. Aby uzyskać więcej informacji, zobacz [wariancje w Delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) i [przy użyciu wariancje w Delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).  
  
 Poniższy przykład kodu pokazuje obsługę kowariancji i kontrawariancji dla grupy metod.  
  
```vb  
Shared Function GetObject() As Object  
    Return Nothing  
End Function  
  
Shared Sub SetObject(ByVal obj As Object)  
End Sub  
  
Shared Function GetString() As String  
    Return ""  
End Function  
  
Shared Sub SetString(ByVal str As String)  
  
End Sub  
  
Shared Sub Test()  
    ' Covariance. A delegate specifies a return type as object,  
    ' but you can assign a method that returns a string.  
    Dim del As Func(Of Object) = AddressOf GetString  
  
    ' Contravariance. A delegate specifies a parameter type as string,  
    ' but you can assign a method that takes an object.  
    Dim del2 As Action(Of String) = AddressOf SetObject  
End Sub  
```  
  
 W programie .NET Framework 4 lub nowszym Visual Basic obsługuje Kowariancja i kontrawariancja w interfejsach ogólnych i delegatach i umożliwia niejawną konwersję parametrów typu genetycznego. Aby uzyskać więcej informacji, zobacz [wariancje w interfejsach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) i [wariancje w Delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
 Poniższy przykład kodu pokazuje niejawna konwersja odwołania dla interfejsów ogólnych.  
  
```vb  
Dim strings As IEnumerable(Of String) = New List(Of String)  
Dim objects As IEnumerable(Of Object) = strings  
```  
  
 Ogólny interfejs lub delegat jest nazywany *wariant* jeśli jego parametrów ogólnych są deklarowane jako kowariantny lub kontrawariantny. Visual Basic umożliwia tworzenie interfejsów typu variant i delegatów. Aby uzyskać więcej informacji, zobacz [Tworzenie interfejsów ogólnych typu Variant (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) i [wariancje w Delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Wariancje w interfejsach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|W tym artykule omówiono Kowariancja i kontrawariancja w interfejsach ogólnych i zawiera listę interfejsów ogólnych typu variant w programie .NET Framework.|  
|[Tworzenie interfejsów typu Variant (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|Przedstawia sposób tworzenia niestandardowych interfejsów typu variant.|  
|[Korzystanie z wariancji w interfejsach dla kolekcji ogólnych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|Pokazuje, jak obsługiwać kowariancji i kontrawariancji w <xref:System.Collections.Generic.IEnumerable%601> i <xref:System.IComparable%601> interfejsy mogą pomóc ponowne użycie kodu.|  
|[Wariancje w Delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|Omówiono kowariancji i kontrawariancji w delegatach ogólnych i nieogólnych i lista wariantów ogólnych delegatów w programie .NET Framework.|  
|[Korzystanie z wariancji w Delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|Pokazuje, jak korzystać z pomocy technicznej kowariancji i kontrawariancji w delegatach nieogólnego do pasowania podpisy metod typy delegatów.|  
|[Korzystanie z wariancji dla Func i akcji delegatów ogólnych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|Pokazuje, jak obsługiwać kowariancji i kontrawariancji w `Func` i `Action` delegatów mogą pomóc ponowne użycie kodu.|

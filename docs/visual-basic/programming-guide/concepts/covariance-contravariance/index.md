---
title: Kowariancja i Kontrawariancja (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 59224c46-9931-466b-8c6e-3648c3e609c6
ms.openlocfilehash: 322cb452e0a3391812e58b68406657651f7a430f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644046"
---
# <a name="covariance-and-contravariance-visual-basic"></a>Kowariancja i Kontrawariancja (Visual Basic)
Kowariancja i kontrawariancja w języku Visual Basic, Włącz niejawnej konwersji odwołania dla tablic, typów delegowanych i argumentów typu ogólnego. Kowariancja zachowuje zgodność przypisania i kontrawariancja odwraca go.  
  
 Poniższy kod przedstawia różnicę między zgodności przypisania, Kowariancja i kontrawariancja.  
  
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
  
 Kowariancja dla tablic umożliwia niejawna konwersja tablicy typu bardziej pochodnego do tablicy typu mniej pochodnego. Jednak ta operacja nie jest typem bezpieczne, jak pokazano w poniższym przykładzie kodu.  
  
```vb  
Dim array() As Object = New String(10) {}  
' The following statement produces a run-time exception.  
' array(0) = 10  
```  
  
 Kowariancja i kontrawariancja obsługę grupy metod umożliwia dopasowywanie podpisy metod typów delegatów. Ta umożliwia można przypisać do delegatów nie tylko tych metod, które pasują do podpisów, ale również metody, które zwracają się, że więcej pochodnych typów (kowariancja) lub że akceptujesz parametrów, które mają mniej typów pochodnych (kontrawariancja) od określonej przez typ delegata. Aby uzyskać więcej informacji, zobacz [wariancji w Delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) i [przy użyciu wariancji w Delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).  
  
 Poniższy przykład kodu pokazuje Kowariancja i kontrawariancja obsługę dla grupy metod.  
  
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
  
 W .NET Framework 4 lub nowszym Visual Basic obsługuje Kowariancja i kontrawariancja w interfejsach i delegatów i umożliwiają niejawnej konwersji wartości parametrów typu ogólnego. Aby uzyskać więcej informacji, zobacz [wariancje w interfejsach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) i [wariancji w Delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
 Poniższy przykład kodu pokazuje niejawnej konwersji odwołania dla ogólnych interfejsów.  
  
```vb  
Dim strings As IEnumerable(Of String) = New List(Of String)  
Dim objects As IEnumerable(Of Object) = strings  
```  
  
 Ogólny interfejs lub delegat jest nazywany *variant* jeśli jego parametrów ogólnych są deklarowane jako kowariantnego lub kontrawariantnego. Visual Basic umożliwia tworzenie własnych interfejsów typu variant i delegatów. Aby uzyskać więcej informacji, zobacz [Tworzenie interfejsów ogólnych typu Variant (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) i [wariancji w Delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Wariancje w interfejsach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|Zawiera omówienie Kowariancja i kontrawariancja w interfejsach, a także listę interfejsów ogólnych typu variant w programie .NET Framework.|  
|[Tworzenie interfejsów ogólnych typu Variant (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|Przedstawia sposób tworzenia niestandardowych interfejsów typu variant.|  
|[Korzystanie z wariancji w interfejsach dla kolekcji (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|Pokazuje, jak obsługują Kowariancja i kontrawariancja w <xref:System.Collections.Generic.IEnumerable%601> i <xref:System.IComparable%601> interfejsy ułatwia ponowne użycie kodu.|  
|[Wariancje w Delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|Zawiera omówienie Kowariancja i kontrawariancja w delegatach ogólne i inny niż ogólny, a także listę variant delegatów w programie .NET Framework.|  
|[Korzystanie z wariancji w Delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|Pokazano, jak korzystać z obsługi Kowariancja i kontrawariancja w delegatach nieogólnego odpowiadać podpisy metod typów delegatów.|  
|[Korzystanie z wariancji dla Func i akcji Delegaty ogólne (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|Pokazuje, jak obsługują Kowariancja i kontrawariancja w `Func` i `Action` delegatów ułatwia ponowne użycie kodu.|

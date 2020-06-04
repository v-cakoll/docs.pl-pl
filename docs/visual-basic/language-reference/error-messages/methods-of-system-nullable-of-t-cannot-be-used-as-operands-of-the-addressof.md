---
title: Nie można używać metod typu „System.Nullable(Of T)” jako operandów operatora „AddressOf”.
ms.date: 07/20/2015
f1_keywords:
- vbc32126
- bc32126
helpviewer_keywords:
- BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
ms.openlocfilehash: 61c6fe7c33b3292066e653304ded43a863413723
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397223"
---
# <a name="methods-of-systemnullableof-t-cannot-be-used-as-operands-of-the-addressof-operator"></a><span data-ttu-id="f8a15-102">Nie można używać metod typu „System.Nullable(Of T)” jako operandów operatora „AddressOf”.</span><span class="sxs-lookup"><span data-stu-id="f8a15-102">Methods of 'System.Nullable(Of T)' cannot be used as operands of the 'AddressOf' operator</span></span>
<span data-ttu-id="f8a15-103">Instrukcja używa `AddressOf` operatora z operandem, który reprezentuje procedurę <xref:System.Nullable%601> struktury.</span><span class="sxs-lookup"><span data-stu-id="f8a15-103">A statement uses the `AddressOf` operator with an operand that represents a procedure of the <xref:System.Nullable%601> structure.</span></span>  
  
 <span data-ttu-id="f8a15-104">**Identyfikator błędu:** BC32126</span><span class="sxs-lookup"><span data-stu-id="f8a15-104">**Error ID:** BC32126</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f8a15-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="f8a15-105">To correct this error</span></span>  
  
- <span data-ttu-id="f8a15-106">Zastąp nazwę procedury w `AddressOf` klauzuli argumentem, który nie jest elementem członkowskim <xref:System.Nullable%601> .</span><span class="sxs-lookup"><span data-stu-id="f8a15-106">Replace the procedure name in the `AddressOf` clause with an operand that is not a member of <xref:System.Nullable%601>.</span></span>  
  
- <span data-ttu-id="f8a15-107">Napisz klasę, która otacza metodę <xref:System.Nullable%601> , której chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="f8a15-107">Write a class that wraps the method of <xref:System.Nullable%601> that you want to use.</span></span> <span data-ttu-id="f8a15-108">W poniższym przykładzie `NullableWrapper` Klasa definiuje nową metodę o nazwie `GetValueOrDefault` .</span><span class="sxs-lookup"><span data-stu-id="f8a15-108">In the following example, the `NullableWrapper` class defines a new method named `GetValueOrDefault`.</span></span> <span data-ttu-id="f8a15-109">Ponieważ ta nowa metoda nie jest elementem członkowskim <xref:System.Nullable%601> , można jej zastosować do `nullInstance` , wystąpienia typu dopuszczającego wartość null, aby utworzyć argument dla `AddressOf` .</span><span class="sxs-lookup"><span data-stu-id="f8a15-109">Because this new method is not a member of <xref:System.Nullable%601>, it can be applied to `nullInstance`, an instance of a nullable type, to form an argument for `AddressOf`.</span></span>  
  
```vb  
Module Module1  
  
    Delegate Function Deleg() As Integer  
  
    Sub Main()  
        Dim nullInstance As New Nullable(Of Integer)(1)  
  
        Dim del As Deleg  
  
        ' GetValueOrDefault is a method of the Nullable generic  
        ' type. It cannot be used as an operand of AddressOf.  
        ' del = AddressOf nullInstance.GetValueOrDefault  
  
        ' The following line uses the GetValueOrDefault method  
        ' defined in the NullableWrapper class.  
        del = AddressOf (New NullableWrapper(  
            Of Integer)(nullInstance)).GetValueOrDefault  
  
        Console.WriteLine(del.Invoke())  
    End Sub  
  
    Class NullableWrapper(Of T As Structure)  
        Private m_Value As Nullable(Of T)  
  
        Sub New(ByVal Value As Nullable(Of T))  
            m_Value = Value  
        End Sub  
  
        Public Function GetValueOrDefault() As T  
            Return m_Value.Value  
        End Function  
    End Class  
End Module  
```  
  
## <a name="see-also"></a><span data-ttu-id="f8a15-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f8a15-110">See also</span></span>

- <xref:System.Nullable%601>
- [<span data-ttu-id="f8a15-111">AddressOf, operator</span><span class="sxs-lookup"><span data-stu-id="f8a15-111">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="f8a15-112">Typy wartości null</span><span class="sxs-lookup"><span data-stu-id="f8a15-112">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="f8a15-113">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f8a15-113">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)

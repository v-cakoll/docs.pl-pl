---
title: Nie można używać metod typu „System.Nullable(Of T)” jako operandów operatora „AddressOf”.
ms.date: 07/20/2015
f1_keywords:
- vbc32126
- bc32126
helpviewer_keywords:
- BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
ms.openlocfilehash: 59e89b24eca6a034dc1df2216f6f0d68e8191a18
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278567"
---
# <a name="methods-of-systemnullableof-t-cannot-be-used-as-operands-of-the-addressof-operator"></a><span data-ttu-id="6e8b9-102">Nie można używać metod typu „System.Nullable(Of T)” jako operandów operatora „AddressOf”.</span><span class="sxs-lookup"><span data-stu-id="6e8b9-102">Methods of 'System.Nullable(Of T)' cannot be used as operands of the 'AddressOf' operator</span></span>
<span data-ttu-id="6e8b9-103">Instrukcja używa `AddressOf` operatora z argumentem, który reprezentuje procedurę <xref:System.Nullable%601> struktury.</span><span class="sxs-lookup"><span data-stu-id="6e8b9-103">A statement uses the `AddressOf` operator with an operand that represents a procedure of the <xref:System.Nullable%601> structure.</span></span>  
  
 <span data-ttu-id="6e8b9-104">**Identyfikator błędu:** BC32126</span><span class="sxs-lookup"><span data-stu-id="6e8b9-104">**Error ID:** BC32126</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6e8b9-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="6e8b9-105">To correct this error</span></span>  
  
-   <span data-ttu-id="6e8b9-106">Zamień nazwę procedury w `AddressOf` klauzuli z argumentem, który nie jest członkiem <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="6e8b9-106">Replace the procedure name in the `AddressOf` clause with an operand that is not a member of <xref:System.Nullable%601>.</span></span>  
  
-   <span data-ttu-id="6e8b9-107">Napisać klasę, która otacza metody <xref:System.Nullable%601> , którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="6e8b9-107">Write a class that wraps the method of <xref:System.Nullable%601> that you want to use.</span></span> <span data-ttu-id="6e8b9-108">W poniższym przykładzie `NullableWrapper` klasa definiuje nową metodę o nazwie `GetValueOrDefault`.</span><span class="sxs-lookup"><span data-stu-id="6e8b9-108">In the following example, the `NullableWrapper` class defines a new method named `GetValueOrDefault`.</span></span> <span data-ttu-id="6e8b9-109">Ponieważ ta nowa metoda nie jest członkiem <xref:System.Nullable%601>, mogą być stosowane do `nullInstance`, wystąpienie typu dopuszczającego wartość null w celu utworzenia argument `AddressOf`.</span><span class="sxs-lookup"><span data-stu-id="6e8b9-109">Because this new method is not a member of <xref:System.Nullable%601>, it can be applied to `nullInstance`, an instance of a nullable type, to form an argument for `AddressOf`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6e8b9-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6e8b9-110">See also</span></span>
- <xref:System.Nullable%601>
- [<span data-ttu-id="6e8b9-111">AddressOf, operator</span><span class="sxs-lookup"><span data-stu-id="6e8b9-111">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="6e8b9-112">Typy wartości dopuszczających wartości null</span><span class="sxs-lookup"><span data-stu-id="6e8b9-112">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="6e8b9-113">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6e8b9-113">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)

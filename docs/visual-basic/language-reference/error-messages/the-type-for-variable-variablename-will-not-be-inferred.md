---
title: Typ zmiennej „<variablename>” nie zostanie wywnioskowany, ponieważ jest powiązany z polem w zakresie otaczającym
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: bcd142785d8ee736c6a1b41950fae80e4d26fa18
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013650"
---
# <a name="the-type-for-variable-variablename-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a><span data-ttu-id="1bd5c-102">Typ zmiennej "\<nazwa_zmiennej >' nie zostanie wywnioskowany, ponieważ jest on powiązany z polem w zakresie otaczającym</span><span class="sxs-lookup"><span data-stu-id="1bd5c-102">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope</span></span>
<span data-ttu-id="1bd5c-103">Typ zmiennej "\<nazwa_zmiennej >' nie zostanie wywnioskowany, ponieważ jest on powiązany z polem w zakresie otaczającym.</span><span class="sxs-lookup"><span data-stu-id="1bd5c-103">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope.</span></span> <span data-ttu-id="1bd5c-104">Zmień nazwę "\<nazwa_zmiennej >", lub użyj w pełni kwalifikowana nazwa (na przykład "Me.variablename" lub "MyBase.variablename").</span><span class="sxs-lookup"><span data-stu-id="1bd5c-104">Either change the name of '\<variablename>', or use the fully qualified name (for example, 'Me.variablename' or 'MyBase.variablename').</span></span>  
  
 <span data-ttu-id="1bd5c-105">Zmienna sterująca pętli w kodzie ma taką samą nazwę jako pola klasy lub innego zasięgu.</span><span class="sxs-lookup"><span data-stu-id="1bd5c-105">A loop control variable in your code has the same name as a field of the class or other enclosing scope.</span></span> <span data-ttu-id="1bd5c-106">Ponieważ zmienna sterująca jest używany bez `As` klauzula jest powiązany z polem w zasięgu, a kompilator nie tworzy nową zmienną dla niego ani nie wywnioskować jej typu.</span><span class="sxs-lookup"><span data-stu-id="1bd5c-106">Because the control variable is used without an `As` clause, it is bound to the field in the enclosing scope, and the compiler does not create a new variable for it or infer its type.</span></span>  
  
 <span data-ttu-id="1bd5c-107">W poniższym przykładzie `Index`, zmienna sterująca w `For` instrukcji, jest powiązany z `Index` pole `Customer` klasy.</span><span class="sxs-lookup"><span data-stu-id="1bd5c-107">In the following example, `Index`, the control variable in the `For` statement, is bound to the `Index` field in the `Customer` class.</span></span> <span data-ttu-id="1bd5c-108">Kompilator nie tworzy nową zmienną dla zmienna sterująca `Index` lub wywnioskować jej typu.</span><span class="sxs-lookup"><span data-stu-id="1bd5c-108">The compiler does not create a new variable for the control variable `Index` or infer its type.</span></span>  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
    ' The following line will raise this warning.  
        For Index = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="1bd5c-109">Domyślnie ta wiadomość jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="1bd5c-109">By default, this message is a warning.</span></span> <span data-ttu-id="1bd5c-110">Aby uzyskać informacji na temat sposobu Ukryj ostrzeżenia lub jak Traktuj ostrzeżenia jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="1bd5c-110">For information about how to hide warnings or how to treat warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="1bd5c-111">**Identyfikator błędu:** BC42110</span><span class="sxs-lookup"><span data-stu-id="1bd5c-111">**Error ID:** BC42110</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="1bd5c-112">Aby rozwiązać tego ostrzeżenia</span><span class="sxs-lookup"><span data-stu-id="1bd5c-112">To address this warning</span></span>  
  
- <span data-ttu-id="1bd5c-113">Zmienna sterująca pętli należy lokalnych, zmieniając jej nazwę na identyfikator, który nie jest również nazwę pola klasy.</span><span class="sxs-lookup"><span data-stu-id="1bd5c-113">Make the loop control variable local by changing its name to an identifier that is not also the name of a field of the class.</span></span>  
  
    ```  
    For I = 1 To 10  
    ```  
  
- <span data-ttu-id="1bd5c-114">Wyjaśnienie, że zmienna sterująca pętli wiąże pola klasy przez dodanie przedrostka `Me.` do nazwy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="1bd5c-114">Clarify that the loop control variable binds to the class field by prefixing `Me.` to the variable name.</span></span>  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
- <span data-ttu-id="1bd5c-115">Zamiast polegania na wnioskowanie o typie lokalnym, użyj `As` klauzuli, aby określić typ zmienna sterująca pętli.</span><span class="sxs-lookup"><span data-stu-id="1bd5c-115">Instead of relying on local type inference, use an `As` clause to specify a type for the loop control variable.</span></span>  
  
    ```  
    For Index As Integer = 1 To 10  
    ```  
  
## <a name="example"></a><span data-ttu-id="1bd5c-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="1bd5c-116">Example</span></span>  
 <span data-ttu-id="1bd5c-117">Poniższy kod przedstawia wcześniejszy przykład przy pierwszym korekcji w miejscu.</span><span class="sxs-lookup"><span data-stu-id="1bd5c-117">The following code shows the earlier example with the first correction in place.</span></span>  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
        For I = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
```  
  
## <a name="see-also"></a><span data-ttu-id="1bd5c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1bd5c-118">See also</span></span>

- [<span data-ttu-id="1bd5c-119">Option Infer, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1bd5c-119">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="1bd5c-120">For Each...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1bd5c-120">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="1bd5c-121">For...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1bd5c-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="1bd5c-122">Instrukcje: Odwoływanie się do bieżącego wystąpienia obiektu</span><span class="sxs-lookup"><span data-stu-id="1bd5c-122">How to: Refer to the Current Instance of an Object</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [<span data-ttu-id="1bd5c-123">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="1bd5c-123">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="1bd5c-124">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="1bd5c-124">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)

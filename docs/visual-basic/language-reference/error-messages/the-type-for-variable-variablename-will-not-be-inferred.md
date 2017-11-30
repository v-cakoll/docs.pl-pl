---
title: "Typ zmiennej &#39; &lt;nazwa_zmiennej&gt;&#39; nie będzie można wywnioskować, ponieważ jest on powiązany z polem w otaczającym zakresie"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords: BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 39968407f4de5436df324320c99dede4d72e2808
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="the-type-for-variable-39ltvariablenamegt39-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a><span data-ttu-id="f357b-102">Typ zmiennej &#39; &lt;nazwa_zmiennej&gt;&#39; nie będzie można wywnioskować, ponieważ jest on powiązany z polem w otaczającym zakresie</span><span class="sxs-lookup"><span data-stu-id="f357b-102">The type for variable &#39;&lt;variablename&gt;&#39; will not be inferred because it is bound to a field in an enclosing scope</span></span>
<span data-ttu-id="f357b-103">Typ zmiennej "\<nazwa_zmiennej >' nie będzie można wywnioskować, ponieważ jest on powiązany z polem w otaczającym zakresie.</span><span class="sxs-lookup"><span data-stu-id="f357b-103">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope.</span></span> <span data-ttu-id="f357b-104">Zmień nazwę "\<nazwa_zmiennej >", lub użyj w pełni kwalifikowaną nazwę (na przykład "Me.variablename" lub "MyBase.variablename").</span><span class="sxs-lookup"><span data-stu-id="f357b-104">Either change the name of '\<variablename>', or use the fully qualified name (for example, 'Me.variablename' or 'MyBase.variablename').</span></span>  
  
 <span data-ttu-id="f357b-105">Zmienna sterująca pętli w kodzie ma taką samą nazwę pola klasy lub innych otaczającego zakresu.</span><span class="sxs-lookup"><span data-stu-id="f357b-105">A loop control variable in your code has the same name as a field of the class or other enclosing scope.</span></span> <span data-ttu-id="f357b-106">Ponieważ zmiennej formantu jest używana bez `As` klauzuli jest powiązany z polem w otaczającym zakresie, a kompilator nie jest w stanie utworzyć nową zmienną dla niego lub wywnioskować jej typu.</span><span class="sxs-lookup"><span data-stu-id="f357b-106">Because the control variable is used without an `As` clause, it is bound to the field in the enclosing scope, and the compiler does not create a new variable for it or infer its type.</span></span>  
  
 <span data-ttu-id="f357b-107">W poniższym przykładzie `Index`, zmienna sterująca w `For` instrukcji, jest powiązany z `Index` w `Customer` klasy.</span><span class="sxs-lookup"><span data-stu-id="f357b-107">In the following example, `Index`, the control variable in the `For` statement, is bound to the `Index` field in the `Customer` class.</span></span> <span data-ttu-id="f357b-108">Kompilator nie tworzy nową zmienną dla zmiennej formantu `Index` lub wywnioskować jej typu.</span><span class="sxs-lookup"><span data-stu-id="f357b-108">The compiler does not create a new variable for the control variable `Index` or infer its type.</span></span>  
  
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
  
 <span data-ttu-id="f357b-109">Domyślnie ten komunikat jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="f357b-109">By default, this message is a warning.</span></span> <span data-ttu-id="f357b-110">Informacje o Ukryj ostrzeżenia lub Traktuj ostrzeżenia jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="f357b-110">For information about how to hide warnings or how to treat warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="f357b-111">**Identyfikator błędu:** BC42110</span><span class="sxs-lookup"><span data-stu-id="f357b-111">**Error ID:** BC42110</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="f357b-112">W celu rozwiązania tego ostrzeżenia</span><span class="sxs-lookup"><span data-stu-id="f357b-112">To address this warning</span></span>  
  
-   <span data-ttu-id="f357b-113">Zmienna sterująca pętli należy lokalnego, zmieniając jej nazwę na identyfikator, który nie jest również nazwę pola klasy.</span><span class="sxs-lookup"><span data-stu-id="f357b-113">Make the loop control variable local by changing its name to an identifier that is not also the name of a field of the class.</span></span>  
  
    ```  
    For I = 1 To 10  
    ```  
  
-   <span data-ttu-id="f357b-114">Wyjaśnienie, że zmienna sterująca pętli for jest powiązany z pola klasy, prefiksu `Me.` do nazwy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f357b-114">Clarify that the loop control variable binds to the class field by prefixing `Me.` to the variable name.</span></span>  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
-   <span data-ttu-id="f357b-115">Zamiast polegania na wnioskowanie o typie lokalnym, użyj `As` klauzuli, aby określić typ dla zmienna sterująca pętli for.</span><span class="sxs-lookup"><span data-stu-id="f357b-115">Instead of relying on local type inference, use an `As` clause to specify a type for the loop control variable.</span></span>  
  
    ```  
    For Index As Integer = 1 To 10  
    ```  
  
## <a name="example"></a><span data-ttu-id="f357b-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="f357b-116">Example</span></span>  
 <span data-ttu-id="f357b-117">Poniższy kod przedstawia wcześniejszego przykładu z pierwszego korekty w miejscu.</span><span class="sxs-lookup"><span data-stu-id="f357b-117">The following code shows the earlier example with the first correction in place.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f357b-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f357b-118">See Also</span></span>  
 [<span data-ttu-id="f357b-119">Option Infer — instrukcja</span><span class="sxs-lookup"><span data-stu-id="f357b-119">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="f357b-120">For Each... Next — instrukcja</span><span class="sxs-lookup"><span data-stu-id="f357b-120">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="f357b-121">Dla... Next — instrukcja</span><span class="sxs-lookup"><span data-stu-id="f357b-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="f357b-122">Porady: odwoływanie się do bieżącego wystąpienia obiektu</span><span class="sxs-lookup"><span data-stu-id="f357b-122">How to: Refer to the Current Instance of an Object</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)  
 [<span data-ttu-id="f357b-123">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="f357b-123">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="f357b-124">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="f357b-124">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)

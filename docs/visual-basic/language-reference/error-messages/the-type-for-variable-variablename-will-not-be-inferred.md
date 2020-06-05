---
title: Typ zmiennej „<variablename>” nie zostanie wywnioskowany, ponieważ jest powiązany z polem w zakresie otaczającym
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: 98aeb5699fdd5e5e538a205acd37436019c3fc03
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363049"
---
# <a name="the-type-for-variable-variablename-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a><span data-ttu-id="729d4-102">Typ zmiennej „\<variablename>” nie zostanie wywnioskowany, ponieważ jest powiązany z polem w zakresie otaczającym</span><span class="sxs-lookup"><span data-stu-id="729d4-102">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope</span></span>

<span data-ttu-id="729d4-103">Typ zmiennej " \<variablename> " nie zostanie wywnioskowany, ponieważ jest powiązany z polem w otaczającym zakresie.</span><span class="sxs-lookup"><span data-stu-id="729d4-103">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope.</span></span> <span data-ttu-id="729d4-104">Zmień nazwę " \<variablename> " lub użyj w pełni kwalifikowanej nazwy (na przykład "Me. VariableName" lub "MyBase. VariableName").</span><span class="sxs-lookup"><span data-stu-id="729d4-104">Either change the name of '\<variablename>', or use the fully qualified name (for example, 'Me.variablename' or 'MyBase.variablename').</span></span>

<span data-ttu-id="729d4-105">Zmienna sterująca pętli w kodzie ma taką samą nazwę jak pole klasy lub innego zakresu otaczającego.</span><span class="sxs-lookup"><span data-stu-id="729d4-105">A loop control variable in your code has the same name as a field of the class or other enclosing scope.</span></span> <span data-ttu-id="729d4-106">Ponieważ zmienna kontroli jest używana bez `As` klauzuli, jest ona powiązana z polem w otaczającym zakresie i kompilator nie tworzy dla niego nowej zmiennej ani nie wystawia jego typu.</span><span class="sxs-lookup"><span data-stu-id="729d4-106">Because the control variable is used without an `As` clause, it is bound to the field in the enclosing scope, and the compiler does not create a new variable for it or infer its type.</span></span>

<span data-ttu-id="729d4-107">W poniższym przykładzie `Index` Zmienna sterująca w `For` instrukcji jest powiązana z `Index` polem w `Customer` klasie.</span><span class="sxs-lookup"><span data-stu-id="729d4-107">In the following example, `Index`, the control variable in the `For` statement, is bound to the `Index` field in the `Customer` class.</span></span> <span data-ttu-id="729d4-108">Kompilator nie tworzy nowej zmiennej dla zmiennej kontroli `Index` ani nie wywnioskuje jej typu.</span><span class="sxs-lookup"><span data-stu-id="729d4-108">The compiler does not create a new variable for the control variable `Index` or infer its type.</span></span>

```vb
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

<span data-ttu-id="729d4-109">Domyślnie ten komunikat jest ostrzeżeniem.</span><span class="sxs-lookup"><span data-stu-id="729d4-109">By default, this message is a warning.</span></span> <span data-ttu-id="729d4-110">Aby uzyskać informacje o sposobach ukrycia ostrzeżeń lub sposobie traktowania ostrzeżeń jako błędów, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="729d4-110">For information about how to hide warnings or how to treat warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

<span data-ttu-id="729d4-111">**Identyfikator błędu:** BC42110</span><span class="sxs-lookup"><span data-stu-id="729d4-111">**Error ID:** BC42110</span></span>

### <a name="to-address-this-warning"></a><span data-ttu-id="729d4-112">Aby rozwiązać ten komunikat ostrzegawczy</span><span class="sxs-lookup"><span data-stu-id="729d4-112">To address this warning</span></span>

- <span data-ttu-id="729d4-113">Ustaw zmienną sterującą pętli jako lokalną, zmieniając jej nazwę na identyfikator, który nie jest również nazwą pola klasy.</span><span class="sxs-lookup"><span data-stu-id="729d4-113">Make the loop control variable local by changing its name to an identifier that is not also the name of a field of the class.</span></span>

  ```vb
  For I = 1 To 10
  ```

- <span data-ttu-id="729d4-114">Wyjaśnij, że Zmienna sterująca pętli jest powiązana z polem klasy przez prefiks `Me.` do nazwy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="729d4-114">Clarify that the loop control variable binds to the class field by prefixing `Me.` to the variable name.</span></span>

  ```vb
  For Me.Index = 1 To 10
  ```

- <span data-ttu-id="729d4-115">Zamiast polegać na wnioskach o typie lokalnym, należy użyć `As` klauzuli, aby określić typ dla zmiennej kontroli pętli.</span><span class="sxs-lookup"><span data-stu-id="729d4-115">Instead of relying on local type inference, use an `As` clause to specify a type for the loop control variable.</span></span>

  ```vb
  For Index As Integer = 1 To 10
  ```

## <a name="example"></a><span data-ttu-id="729d4-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="729d4-116">Example</span></span>
 <span data-ttu-id="729d4-117">Poniższy kod ilustruje poprzedni przykład przy pierwszej korekcie.</span><span class="sxs-lookup"><span data-stu-id="729d4-117">The following code shows the earlier example with the first correction in place.</span></span>

```vb
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

## <a name="see-also"></a><span data-ttu-id="729d4-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="729d4-118">See also</span></span>

- [<span data-ttu-id="729d4-119">Option Infer — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="729d4-119">Option Infer Statement</span></span>](../statements/option-infer-statement.md)
- [<span data-ttu-id="729d4-120">For Each...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="729d4-120">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
- [<span data-ttu-id="729d4-121">For...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="729d4-121">For...Next Statement</span></span>](../statements/for-next-statement.md)
- [<span data-ttu-id="729d4-122">Instrukcje: odwoływanie się do bieżącego wystąpienia obiektu</span><span class="sxs-lookup"><span data-stu-id="729d4-122">How to: Refer to the Current Instance of an Object</span></span>](../../programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [<span data-ttu-id="729d4-123">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="729d4-123">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="729d4-124">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="729d4-124">Me, My, MyBase, and MyClass</span></span>](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)

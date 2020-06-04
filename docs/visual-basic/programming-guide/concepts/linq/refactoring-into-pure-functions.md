---
title: Refaktoryzacja do czystych funkcji
ms.date: 07/20/2015
ms.assetid: 99e7d27b-a3ff-4577-bdb2-5a8278d6d7af
ms.openlocfilehash: 415b088661eca347330f4776901d68ee514d8dad
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413482"
---
# <a name="refactoring-into-pure-functions-visual-basic"></a><span data-ttu-id="8f1f4-102">Refaktoryzacja do czystych funkcji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8f1f4-102">Refactoring Into Pure Functions (Visual Basic)</span></span>

<span data-ttu-id="8f1f4-103">Ważnym aspektem czystych transformacji funkcjonalnych jest uczenie się, jak kod refaktoryzacji przy użyciu czystych funkcji.</span><span class="sxs-lookup"><span data-stu-id="8f1f4-103">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>

<span data-ttu-id="8f1f4-104">Jak wspomniano wcześniej w tej sekcji, czysta funkcja ma dwie przydatne cechy:</span><span class="sxs-lookup"><span data-stu-id="8f1f4-104">As noted previously in this section, a pure function has two useful characteristics:</span></span>

- <span data-ttu-id="8f1f4-105">Nie ma żadnych efektów ubocznych.</span><span class="sxs-lookup"><span data-stu-id="8f1f4-105">It has no side effects.</span></span> <span data-ttu-id="8f1f4-106">Funkcja nie zmienia żadnych zmiennych ani danych dowolnego typu poza funkcją.</span><span class="sxs-lookup"><span data-stu-id="8f1f4-106">The function does not change any variables or the data of any type outside of the function.</span></span>

- <span data-ttu-id="8f1f4-107">Jest ona spójna.</span><span class="sxs-lookup"><span data-stu-id="8f1f4-107">It is consistent.</span></span> <span data-ttu-id="8f1f4-108">Mając ten sam zestaw danych wejściowych, zawsze zwróci tę samą wartość wyjściową.</span><span class="sxs-lookup"><span data-stu-id="8f1f4-108">Given the same set of input data, it will always return the same output value.</span></span>

 <span data-ttu-id="8f1f4-109">Jednym ze sposobów przejścia do programowania funkcjonalnego jest Refaktoryzacja istniejącego kodu w celu wyeliminowania zbędnych efektów ubocznych i zewnętrznych zależności.</span><span class="sxs-lookup"><span data-stu-id="8f1f4-109">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="8f1f4-110">W ten sposób można utworzyć czystą wersję funkcji istniejącego kodu.</span><span class="sxs-lookup"><span data-stu-id="8f1f4-110">In this way, you can create pure function versions of existing code.</span></span>

<span data-ttu-id="8f1f4-111">W tym temacie omówiono czystą funkcję i jej znaczenie.</span><span class="sxs-lookup"><span data-stu-id="8f1f4-111">This topic discusses what a pure function is and what it is not.</span></span> <span data-ttu-id="8f1f4-112">[Samouczek: manipulowanie zawartością w samouczku WordprocessingML Document (Visual Basic)](tutorial-manipulating-content-in-a-wordprocessingml-document.md) pokazuje, jak manipulować dokumentem WordprocessingML i zawiera dwa przykłady sposobu refaktoryzacji przy użyciu czystej funkcji.</span><span class="sxs-lookup"><span data-stu-id="8f1f4-112">The [Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)](tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>

## <a name="eliminating-side-effects-and-external-dependencies"></a><span data-ttu-id="8f1f4-113">Eliminowanie efektów ubocznych i zależności zewnętrznych</span><span class="sxs-lookup"><span data-stu-id="8f1f4-113">Eliminating Side Effects and External Dependencies</span></span>

<span data-ttu-id="8f1f4-114">Poniższe przykłady różnią się dwoma nieczystymi funkcjami i czystą funkcją.</span><span class="sxs-lookup"><span data-stu-id="8f1f4-114">The following examples contrast two non-pure functions and a pure function.</span></span>

### <a name="non-pure-function-that-changes-a-class-member"></a><span data-ttu-id="8f1f4-115">Nieczysta funkcja, która zmienia element członkowski klasy</span><span class="sxs-lookup"><span data-stu-id="8f1f4-115">Non-Pure Function that Changes a Class Member</span></span>

<span data-ttu-id="8f1f4-116">W poniższym kodzie `HyphenatedConcat` Funkcja nie jest czystą funkcją, ponieważ modyfikuje `aMember` element członkowski danych w klasie:</span><span class="sxs-lookup"><span data-stu-id="8f1f4-116">In the following code, the `HyphenatedConcat` function is not a pure function, because it modifies the `aMember` data member in the class:</span></span>

```vb
Module Module1
    Dim aMember As String = "StringOne"

    Public Sub HyphenatedConcat(ByVal appendStr As String)
        aMember = aMember & "-" & appendStr
    End Sub

    Sub Main()
        HyphenatedConcat("StringTwo")
        Console.WriteLine(aMember)
    End Sub
End Module
```

<span data-ttu-id="8f1f4-117">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="8f1f4-117">This code produces the following output:</span></span>

```console
StringOne-StringTwo
```

<span data-ttu-id="8f1f4-118">Należy zauważyć, że nie ma znaczenia, czy modyfikowane dane mają dostęp, czy też jest członkiem `public` `private` `shared` lub wystąpieniem.</span><span class="sxs-lookup"><span data-stu-id="8f1f4-118">Note that it is irrelevant whether the data being modified has `public` or `private` access, or is a  `shared` member or an instance member.</span></span> <span data-ttu-id="8f1f4-119">Czysta funkcja nie zmienia żadnych danych poza funkcją.</span><span class="sxs-lookup"><span data-stu-id="8f1f4-119">A pure function does not change any data outside of the function.</span></span>

### <a name="non-pure-function-that-changes-an-argument"></a><span data-ttu-id="8f1f4-120">Nieczysta funkcja, która zmienia argument</span><span class="sxs-lookup"><span data-stu-id="8f1f4-120">Non-Pure Function that Changes an Argument</span></span>

<span data-ttu-id="8f1f4-121">Ponadto następująca wersja tej samej funkcji nie jest czysta, ponieważ modyfikuje zawartość jej parametru, `sb` .</span><span class="sxs-lookup"><span data-stu-id="8f1f4-121">Furthermore, the following version of this same function is not pure because it modifies the contents of its parameter, `sb`.</span></span>

```vb
Module Module1
    Public Sub HyphenatedConcat(ByVal sb As StringBuilder, ByVal appendStr As String)
        sb.Append("-" & appendStr)
    End Sub

    Sub Main()
        Dim sb1 As StringBuilder = New StringBuilder("StringOne")
        HyphenatedConcat(sb1, "StringTwo")
        Console.WriteLine(sb1)
    End Sub
End Module
```

<span data-ttu-id="8f1f4-122">Ta wersja programu daje te same dane wyjściowe co pierwsza wersja, ponieważ `HyphenatedConcat` Funkcja zmieniła wartość (stan) pierwszego parametru przez wywołanie <xref:System.Text.StringBuilder.Append%2A> funkcji członkowskiej.</span><span class="sxs-lookup"><span data-stu-id="8f1f4-122">This version of the program produces the same output as the first version, because the `HyphenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="8f1f4-123">Należy zauważyć, że ta zmiana występuje pomimo tego faktu, który `HyphenatedConcat` używa przekazywania parametrów wywołania przez wartość.</span><span class="sxs-lookup"><span data-stu-id="8f1f4-123">Note that this alteration occurs despite that fact that `HyphenatedConcat` uses call-by-value parameter passing.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8f1f4-124">W przypadku typów referencyjnych, Jeśli przekażesz parametr według wartości, wynikiem jest kopia odwołania do obiektu, który jest przekazywany.</span><span class="sxs-lookup"><span data-stu-id="8f1f4-124">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="8f1f4-125">Ta kopia jest nadal skojarzona z tymi samymi danymi wystąpienia co oryginalne odwołanie (do momentu przypisania zmiennej odniesienia do nowego obiektu).</span><span class="sxs-lookup"><span data-stu-id="8f1f4-125">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="8f1f4-126">Wywołanie przez odwołanie nie musi być wymagane do zmodyfikowania parametru przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="8f1f4-126">Call-by-reference is not necessarily required for a function to modify a parameter.</span></span>

### <a name="pure-function"></a><span data-ttu-id="8f1f4-127">Czysta funkcja</span><span class="sxs-lookup"><span data-stu-id="8f1f4-127">Pure Function</span></span>

<span data-ttu-id="8f1f4-128">Ta Następna wersja programu hows, jak zaimplementować `HyphenatedConcat` funkcję jako czystą funkcję.</span><span class="sxs-lookup"><span data-stu-id="8f1f4-128">This next version of the program hows how to implement the `HyphenatedConcat` function as a pure function.</span></span>

```vb
Module Module1
    Public Function HyphenatedConcat(ByVal s As String, ByVal appendStr As String) As String
        Return (s & "-" & appendStr)
    End Function

    Sub Main()
        Dim s1 As String = "StringOne"
        Dim s2 As String = HyphenatedConcat(s1, "StringTwo")
        Console.WriteLine(s2)
    End Sub
End Module
```

<span data-ttu-id="8f1f4-129">Ta wersja generuje ten sam wiersz danych wyjściowych: `StringOne-StringTwo` .</span><span class="sxs-lookup"><span data-stu-id="8f1f4-129">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="8f1f4-130">Należy pamiętać, że aby zachować łączną wartość, jest ona przechowywana w zmiennej pośredniej `s2` .</span><span class="sxs-lookup"><span data-stu-id="8f1f4-130">Note that to retain the concatenated value, it is stored in the intermediate variable `s2`.</span></span>

<span data-ttu-id="8f1f4-131">Jednym z metod, które może być bardzo przydatne, jest zapisanie funkcji, które są w sposób nieczysty (to oznacza, że deklarują i modyfikują zmienne lokalne), ale są globalnie czyste.</span><span class="sxs-lookup"><span data-stu-id="8f1f4-131">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="8f1f4-132">Takie funkcje mają wiele pożądanych cech tworzenia, ale unikają niektórych bardziej zawiłeych idiomy programowania, takich jak korzystanie z rekursji, gdy pętla prosta osiągnie tę samą wartość.</span><span class="sxs-lookup"><span data-stu-id="8f1f4-132">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>

## <a name="standard-query-operators"></a><span data-ttu-id="8f1f4-133">Standardowe operatory zapytań</span><span class="sxs-lookup"><span data-stu-id="8f1f4-133">Standard Query Operators</span></span>

<span data-ttu-id="8f1f4-134">Ważną cechą standardowych operatorów zapytań jest zaimplementowanie ich jako czystych funkcji.</span><span class="sxs-lookup"><span data-stu-id="8f1f4-134">An important characteristic of the standard query operators is that they are implemented as pure functions.</span></span>

<span data-ttu-id="8f1f4-135">Aby uzyskać więcej informacji, zobacz [standardowe operatory zapytań — Omówienie (Visual Basic)](standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8f1f4-135">For more information, see [Standard Query Operators Overview (Visual Basic)](standard-query-operators-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8f1f4-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8f1f4-136">See also</span></span>

- [<span data-ttu-id="8f1f4-137">Wprowadzenie do czystych transformacji funkcjonalnych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8f1f4-137">Introduction to Pure Functional Transformations (Visual Basic)</span></span>](introduction-to-pure-functional-transformations.md)
- [<span data-ttu-id="8f1f4-138">Programowanie funkcjonalne a programowanie bezwzględne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8f1f4-138">Functional Programming vs. Imperative Programming (Visual Basic)</span></span>](functional-programming-vs-imperative-programming.md)

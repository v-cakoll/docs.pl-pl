---
title: Refaktoryzacja do czystych funkcji (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 99e7d27b-a3ff-4577-bdb2-5a8278d6d7af
ms.openlocfilehash: 207b77ff50cd2aaeede758db69b48c8f29a16ab1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="refactoring-into-pure-functions-visual-basic"></a><span data-ttu-id="afb1a-102">Refaktoryzacja do czystych funkcji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afb1a-102">Refactoring Into Pure Functions (Visual Basic)</span></span>
<span data-ttu-id="afb1a-103">Ważnym aspektem czysty przekształcenia funkcjonalności jest poznanie Refaktoryzuj kodu za pomocą czystych funkcji.</span><span class="sxs-lookup"><span data-stu-id="afb1a-103">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>  
  
 <span data-ttu-id="afb1a-104">Jak już wspomniano w tej sekcji, czystej funkcji ma dwie przydatne cechy:</span><span class="sxs-lookup"><span data-stu-id="afb1a-104">As noted previously in this section, a pure function has two useful characteristics:</span></span>  
  
-   <span data-ttu-id="afb1a-105">Go nie ma skutków ubocznych.</span><span class="sxs-lookup"><span data-stu-id="afb1a-105">It has no side effects.</span></span> <span data-ttu-id="afb1a-106">Funkcja nie zmienia żadnych zmiennych lub danych dowolnego typu poza funkcję.</span><span class="sxs-lookup"><span data-stu-id="afb1a-106">The function does not change any variables or the data of any type outside of the function.</span></span>  
  
-   <span data-ttu-id="afb1a-107">Jest ona zgodna.</span><span class="sxs-lookup"><span data-stu-id="afb1a-107">It is consistent.</span></span> <span data-ttu-id="afb1a-108">Biorąc pod uwagę ten sam zestaw danych wejściowych, zawsze zwróci taką samą wartość w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="afb1a-108">Given the same set of input data, it will always return the same output value.</span></span>  
  
 <span data-ttu-id="afb1a-109">Jednym ze sposobów przechodzenia do programowania funkcyjnego jest Refaktoryzuj istniejący kod, aby wyeliminować niepotrzebne efektów ubocznych i zależnościami zewnętrznymi.</span><span class="sxs-lookup"><span data-stu-id="afb1a-109">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="afb1a-110">W ten sposób można utworzyć wersji czystej funkcji istniejącego kodu.</span><span class="sxs-lookup"><span data-stu-id="afb1a-110">In this way, you can create pure function versions of existing code.</span></span>  
  
 <span data-ttu-id="afb1a-111">W tym temacie omówiono jest funkcja czysty i co nie jest.</span><span class="sxs-lookup"><span data-stu-id="afb1a-111">This topic discusses what a pure function is and what it is not.</span></span> <span data-ttu-id="afb1a-112">[Samouczek: manipulowanie zawartości w dokumencie schemat WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) samouczek przedstawia sposób modyfikowania dokumentu schemat WordprocessingML i zawiera dwa przykłady do refaktoryzacji przy użyciu czystej funkcji.</span><span class="sxs-lookup"><span data-stu-id="afb1a-112">The [Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a><span data-ttu-id="afb1a-113">Wyeliminowanie efektów ubocznych i zależnościami zewnętrznymi</span><span class="sxs-lookup"><span data-stu-id="afb1a-113">Eliminating Side Effects and External Dependencies</span></span>  
 <span data-ttu-id="afb1a-114">Poniższe przykłady kontrastu dwóch funkcji nie jest czysty i czystej funkcji.</span><span class="sxs-lookup"><span data-stu-id="afb1a-114">The following examples contrast two non-pure functions and a pure function.</span></span>  
  
### <a name="non-pure-function-that-changes-a-class-member"></a><span data-ttu-id="afb1a-115">Czystej funkcji, która zmienia elementu członkowskiego klasy</span><span class="sxs-lookup"><span data-stu-id="afb1a-115">Non-Pure Function that Changes a Class Member</span></span>  
 <span data-ttu-id="afb1a-116">W poniższym kodzie `HypenatedConcat` funkcja nie jest czystej funkcji, ponieważ modyfikuje `aMember` element członkowski danych klasy:</span><span class="sxs-lookup"><span data-stu-id="afb1a-116">In the following code, the `HypenatedConcat` function is not a pure function, because it modifies the `aMember` data member in the class:</span></span>  
  
```vb  
Module Module1  
    Dim aMember As String = "StringOne"  
  
    Public Sub HypenatedConcat(ByVal appendStr As String)  
        aMember = aMember & "-" & appendStr  
    End Sub  
  
    Sub Main()  
        HypenatedConcat("StringTwo")  
        Console.WriteLine(aMember)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="afb1a-117">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="afb1a-117">This code produces the following output:</span></span>  
  
```  
StringOne-StringTwo  
```  
  
 <span data-ttu-id="afb1a-118">Zwróć uwagę, że jego nie znaczenia czy dane są modyfikowane ma `public` lub `private` dostępu lub jest `shared` elementu członkowskiego lub elementu członkowskiego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="afb1a-118">Note that it is irrelevant whether the data being modified has `public` or `private` access, or is a  `shared` member or an instance member.</span></span> <span data-ttu-id="afb1a-119">Czystej funkcji nie zmienia żadnych danych poza funkcję.</span><span class="sxs-lookup"><span data-stu-id="afb1a-119">A pure function does not change any data outside of the function.</span></span>  
  
### <a name="non-pure-function-that-changes-an-argument"></a><span data-ttu-id="afb1a-120">Czystej funkcji, która zmienia argumentu</span><span class="sxs-lookup"><span data-stu-id="afb1a-120">Non-Pure Function that Changes an Argument</span></span>  
 <span data-ttu-id="afb1a-121">Ponadto następujące wersja tej samej funkcji nie jest czysty ponieważ modyfikuje zawartość jej parametr `sb`.</span><span class="sxs-lookup"><span data-stu-id="afb1a-121">Furthermore, the following version of this same function is not pure because it modifies the contents of its parameter, `sb`.</span></span>  
  
```vb  
Module Module1  
    Public Sub HypenatedConcat(ByVal sb As StringBuilder, ByVal appendStr As String)  
        sb.Append("-" & appendStr)  
    End Sub  
  
    Sub Main()  
        Dim sb1 As StringBuilder = New StringBuilder("StringOne")  
        HypenatedConcat(sb1, "StringTwo")  
        Console.WriteLine(sb1)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="afb1a-122">Ta wersja programu daje takie same dane wyjściowe jako pierwszej wersji, ponieważ `HypenatedConcat` funkcja została zmieniona wartość (stan) jej pierwszy parametr wywołując <xref:System.Text.StringBuilder.Append%2A> funkcję elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="afb1a-122">This version of the program produces the same output as the first version, because the `HypenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="afb1a-123">Należy pamiętać, że ta zmiana występuje mimo fakt który `HypenatedConcat` używa przekazywanie parametru wywołania przez wartość.</span><span class="sxs-lookup"><span data-stu-id="afb1a-123">Note that this alteration occurs despite that fact that `HypenatedConcat` uses call-by-value parameter passing.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="afb1a-124">Dla typów referencyjnych Jeśli parametr zostanie przekazany przez wartość, jej wynikiem kopię odwołanie do obiektu przekazywany.</span><span class="sxs-lookup"><span data-stu-id="afb1a-124">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="afb1a-125">Ta kopia nadal jest skojarzona z tych samych danych wystąpienia co oryginalny odwołania (do czasu zmienna odwołania jest przypisana do nowego obiektu).</span><span class="sxs-lookup"><span data-stu-id="afb1a-125">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="afb1a-126">Wywołanie przez odwołanie nie jest zawsze wymagane dla funkcji zmodyfikować parametr.</span><span class="sxs-lookup"><span data-stu-id="afb1a-126">Call-by-reference is not necessarily required for a function to modify a parameter.</span></span>  
  
### <a name="pure-function"></a><span data-ttu-id="afb1a-127">Czystej funkcji</span><span class="sxs-lookup"><span data-stu-id="afb1a-127">Pure Function</span></span>  
 <span data-ttu-id="afb1a-128">Ta następnej wersji programu hows implementowania `HypenatedConcat` działać jako czystej funkcji.</span><span class="sxs-lookup"><span data-stu-id="afb1a-128">This next version of the program hows how to implement the `HypenatedConcat` function as a pure function.</span></span>  
  
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
  
 <span data-ttu-id="afb1a-129">Ponownie, ta wersja tworzy w tym samym wierszu danych wyjściowych: `StringOne-StringTwo`.</span><span class="sxs-lookup"><span data-stu-id="afb1a-129">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="afb1a-130">Należy pamiętać, że aby zachować wartości połączonych, jest ona przechowywana w zmiennej pośredniego `s2`.</span><span class="sxs-lookup"><span data-stu-id="afb1a-130">Note that to retain the concatenated value, it is stored in the intermediate variable `s2`.</span></span>  
  
 <span data-ttu-id="afb1a-131">Jedno podejście, które mogą być bardzo przydatne jest napisanie funkcje, które są lokalnie oczyścić zanieczyszczony (to, że ich zadeklarować i modyfikowanie zmiennych lokalnych), ale są globalnie czysty.</span><span class="sxs-lookup"><span data-stu-id="afb1a-131">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="afb1a-132">Takie funkcje ma wiele cech możliwości pożądane, ale uniknąć kilku więcej zwichrowanych funkcjonalności idioms programowania, np. konieczności rekursję podczas proste pętli będzie wykonywać samo.</span><span class="sxs-lookup"><span data-stu-id="afb1a-132">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>  
  
## <a name="standard-query-operators"></a><span data-ttu-id="afb1a-133">Standardowe operatory zapytań</span><span class="sxs-lookup"><span data-stu-id="afb1a-133">Standard Query Operators</span></span>  
 <span data-ttu-id="afb1a-134">Istotne cechy standardowych operatorów zapytań jest, że są one zaimplementowane jako czystych funkcji.</span><span class="sxs-lookup"><span data-stu-id="afb1a-134">An important characteristic of the standard query operators is that they are implemented as pure functions.</span></span>  
  
 <span data-ttu-id="afb1a-135">Aby uzyskać więcej informacji, zobacz [standardowe operatory zapytań — omówienie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="afb1a-135">For more information, see [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afb1a-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="afb1a-136">See Also</span></span>  
 [<span data-ttu-id="afb1a-137">Wprowadzenie do przekształcenia funkcjonalności czysty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afb1a-137">Introduction to Pure Functional Transformations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [<span data-ttu-id="afb1a-138">Programowanie funkcjonalne a Programowanie imperatywnych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afb1a-138">Functional Programming vs. Imperative Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)

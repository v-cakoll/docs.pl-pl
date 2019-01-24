---
title: Refaktoryzacja do czystych funkcji (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 99e7d27b-a3ff-4577-bdb2-5a8278d6d7af
ms.openlocfilehash: 9c4be0c3574f2bd3171b8f5a86359d3181fe8731
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54644468"
---
# <a name="refactoring-into-pure-functions-visual-basic"></a><span data-ttu-id="82854-102">Refaktoryzacja do czystych funkcji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82854-102">Refactoring Into Pure Functions (Visual Basic)</span></span>
<span data-ttu-id="82854-103">Ważnym aspektem czystych przekształceń funkcjonalnych jest nauki refaktoryzacji kodu przy użyciu czystej funkcji.</span><span class="sxs-lookup"><span data-stu-id="82854-103">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>  
  
 <span data-ttu-id="82854-104">Jak wspomniano wcześniej w tej sekcji, czystej funkcji ma dwie właściwości przydatne:</span><span class="sxs-lookup"><span data-stu-id="82854-104">As noted previously in this section, a pure function has two useful characteristics:</span></span>  
  
-   <span data-ttu-id="82854-105">Nie ma żadnych efektów ubocznych.</span><span class="sxs-lookup"><span data-stu-id="82854-105">It has no side effects.</span></span> <span data-ttu-id="82854-106">Funkcja nie zmienia żadnych zmiennych lub danych dowolnego typu spoza tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="82854-106">The function does not change any variables or the data of any type outside of the function.</span></span>  
  
-   <span data-ttu-id="82854-107">Jest ona zgodna.</span><span class="sxs-lookup"><span data-stu-id="82854-107">It is consistent.</span></span> <span data-ttu-id="82854-108">Biorąc pod uwagę ten sam zestaw danych wejściowych, która zawsze zwraca tę samą wartość w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="82854-108">Given the same set of input data, it will always return the same output value.</span></span>  
  
 <span data-ttu-id="82854-109">Jednym ze sposobów przechodzenia do programowania funkcyjnego jest Przeprowadź refaktoryzację istniejącego kodu, aby wyeliminować niepotrzebne efekty uboczne i zależności zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="82854-109">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="82854-110">W ten sposób można utworzyć wersji czystą funkcję istniejącego kodu.</span><span class="sxs-lookup"><span data-stu-id="82854-110">In this way, you can create pure function versions of existing code.</span></span>  
  
 <span data-ttu-id="82854-111">W tym temacie omówiono funkcja czystego jest i co nie jest.</span><span class="sxs-lookup"><span data-stu-id="82854-111">This topic discusses what a pure function is and what it is not.</span></span> <span data-ttu-id="82854-112">[Samouczka: Manipulowanie zawartością w dokumencie WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) samouczek przedstawia sposób modyfikowania dokumentu WordprocessingML i zawiera dwa przykłady jak Refaktoryzacja, przy użyciu czystej funkcji.</span><span class="sxs-lookup"><span data-stu-id="82854-112">The [Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a><span data-ttu-id="82854-113">Eliminując skutki uboczne i zależności zewnętrznych</span><span class="sxs-lookup"><span data-stu-id="82854-113">Eliminating Side Effects and External Dependencies</span></span>  
 <span data-ttu-id="82854-114">Poniższe przykłady porównać dwie funkcje — czyste i czystą funkcję.</span><span class="sxs-lookup"><span data-stu-id="82854-114">The following examples contrast two non-pure functions and a pure function.</span></span>  
  
### <a name="non-pure-function-that-changes-a-class-member"></a><span data-ttu-id="82854-115">Czystej funkcji, która zmienia składowej klasy</span><span class="sxs-lookup"><span data-stu-id="82854-115">Non-Pure Function that Changes a Class Member</span></span>  
 <span data-ttu-id="82854-116">W poniższym kodzie `HypenatedConcat` funkcja nie jest funkcją czystego, ponieważ modyfikuje `aMember` element członkowski danych w klasie:</span><span class="sxs-lookup"><span data-stu-id="82854-116">In the following code, the `HypenatedConcat` function is not a pure function, because it modifies the `aMember` data member in the class:</span></span>  
  
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
  
 <span data-ttu-id="82854-117">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="82854-117">This code produces the following output:</span></span>  
  
```  
StringOne-StringTwo  
```  
  
 <span data-ttu-id="82854-118">Zwróć uwagę, że jej nie ma znaczenia tego, czy ma modyfikacji danych `public` lub `private` dostępu lub jest `shared` elementu członkowskiego lub elementu członkowskiego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="82854-118">Note that it is irrelevant whether the data being modified has `public` or `private` access, or is a  `shared` member or an instance member.</span></span> <span data-ttu-id="82854-119">Czystą funkcję nie zmienia żadnych danych poza funkcją.</span><span class="sxs-lookup"><span data-stu-id="82854-119">A pure function does not change any data outside of the function.</span></span>  
  
### <a name="non-pure-function-that-changes-an-argument"></a><span data-ttu-id="82854-120">Czystej funkcji, która zmienia argumentu</span><span class="sxs-lookup"><span data-stu-id="82854-120">Non-Pure Function that Changes an Argument</span></span>  
 <span data-ttu-id="82854-121">Ponadto, następująca wersja tej samej funkcji nie jest czysty ponieważ modyfikuje zawartość jako parametr `sb`.</span><span class="sxs-lookup"><span data-stu-id="82854-121">Furthermore, the following version of this same function is not pure because it modifies the contents of its parameter, `sb`.</span></span>  
  
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
  
 <span data-ttu-id="82854-122">Ta wersja programu daje takie same dane wyjściowe jako pierwsza wersja, ponieważ `HypenatedConcat` funkcja została zmieniona wartość (stan) jako pierwszy parametr, wywołując <xref:System.Text.StringBuilder.Append%2A> funkcja elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="82854-122">This version of the program produces the same output as the first version, because the `HypenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="82854-123">Uwaga występowanie tej zmiany, pomimo faktu, `HypenatedConcat` używa wywołań przez wartość parametru przekazywania.</span><span class="sxs-lookup"><span data-stu-id="82854-123">Note that this alteration occurs despite that fact that `HypenatedConcat` uses call-by-value parameter passing.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="82854-124">Dla typów odwołań w przypadku przekazania parametr przez wartość, jej powoduje kopię odwołanie do obiektu przekazywana.</span><span class="sxs-lookup"><span data-stu-id="82854-124">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="82854-125">Ta kopia jest nadal skojarzone z tymi samymi danymi wystąpienia jako odwołanie do oryginalnego (aż do zmiennej odwołania jest przypisany do nowego obiektu).</span><span class="sxs-lookup"><span data-stu-id="82854-125">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="82854-126">Wywołanie przez odwołanie nie jest zawsze wymagane dla funkcji zmodyfikować parametr.</span><span class="sxs-lookup"><span data-stu-id="82854-126">Call-by-reference is not necessarily required for a function to modify a parameter.</span></span>  
  
### <a name="pure-function"></a><span data-ttu-id="82854-127">Czystej funkcji</span><span class="sxs-lookup"><span data-stu-id="82854-127">Pure Function</span></span>  
 <span data-ttu-id="82854-128">Ten następnej wersji programu, jak wybierać sposób implementacji `HypenatedConcat` pełnią czystą funkcję.</span><span class="sxs-lookup"><span data-stu-id="82854-128">This next version of the program hows how to implement the `HypenatedConcat` function as a pure function.</span></span>  
  
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
  
 <span data-ttu-id="82854-129">Ponownie generuje ten sam wiersz danych wyjściowych w tej wersji: `StringOne-StringTwo`.</span><span class="sxs-lookup"><span data-stu-id="82854-129">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="82854-130">Należy pamiętać, aby zachować wartość połączone, jest on przechowywany w zmiennej pośrednich `s2`.</span><span class="sxs-lookup"><span data-stu-id="82854-130">Note that to retain the concatenated value, it is stored in the intermediate variable `s2`.</span></span>  
  
 <span data-ttu-id="82854-131">Jedno podejście, które mogą być bardzo przydatne jest napisanie funkcje, które są lokalnie oczyścić zanieczyszczony (oznacza to, mogą zadeklarować i modyfikowanie zmiennych lokalnych), ale są globalnie czysty.</span><span class="sxs-lookup"><span data-stu-id="82854-131">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="82854-132">Takie funkcje, ma wiele cech pożądane możliwości tworzenia, ale uniknąć niektórych bardziej zawiłe funkcjonalności idiomy programowania, takich jak konieczności rekursję, gdy prostej pętli może osiągnąć to samo.</span><span class="sxs-lookup"><span data-stu-id="82854-132">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>  
  
## <a name="standard-query-operators"></a><span data-ttu-id="82854-133">Standardowe operatory zapytań</span><span class="sxs-lookup"><span data-stu-id="82854-133">Standard Query Operators</span></span>  
 <span data-ttu-id="82854-134">Ważną cechą standardowych operatorów zapytań jest, że są implementowane jako czystych funkcji.</span><span class="sxs-lookup"><span data-stu-id="82854-134">An important characteristic of the standard query operators is that they are implemented as pure functions.</span></span>  
  
 <span data-ttu-id="82854-135">Aby uzyskać więcej informacji, zobacz [standardowe operatory zapytań — Przegląd (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="82854-135">For more information, see [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82854-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="82854-136">See also</span></span>
- [<span data-ttu-id="82854-137">Wprowadzenie do czystych przekształceń funkcjonalnych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82854-137">Introduction to Pure Functional Transformations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [<span data-ttu-id="82854-138">Programowanie funkcjonalne a Programowanie imperatywne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82854-138">Functional Programming vs. Imperative Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)

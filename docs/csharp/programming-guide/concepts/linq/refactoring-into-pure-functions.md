---
title: Refaktoryzacja do czystych funkcji (C#)
ms.date: 07/20/2015
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: fcb396984d58b5601d278a860b272211e785dcfb
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43801102"
---
# <a name="refactoring-into-pure-functions-c"></a><span data-ttu-id="2faaf-102">Refaktoryzacja do czystych funkcji (C#)</span><span class="sxs-lookup"><span data-stu-id="2faaf-102">Refactoring Into Pure Functions (C#)</span></span>

<span data-ttu-id="2faaf-103">Ważnym aspektem czystych przekształceń funkcjonalnych jest nauki refaktoryzacji kodu przy użyciu czystej funkcji.</span><span class="sxs-lookup"><span data-stu-id="2faaf-103">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2faaf-104">Powszechne nazewnictwo w programowania funkcjonalnego jest Refaktoryzacja programach przy użyciu czystych funkcji.</span><span class="sxs-lookup"><span data-stu-id="2faaf-104">The common nomenclature in functional programming is that you refactor programs using pure functions.</span></span> <span data-ttu-id="2faaf-105">W języku Visual Basic i C++ to zgodne z korzystania z funkcji w odpowiednich języków.</span><span class="sxs-lookup"><span data-stu-id="2faaf-105">In Visual Basic and C++, this aligns with the use of functions in the respective languages.</span></span> <span data-ttu-id="2faaf-106">Jednak w języku C#, funkcje są wywoływane metody.</span><span class="sxs-lookup"><span data-stu-id="2faaf-106">However, in C#, functions are called methods.</span></span> <span data-ttu-id="2faaf-107">Dla celów tej dyskusji czystej funkcji jest wdrażany jako metoda w języku C#.</span><span class="sxs-lookup"><span data-stu-id="2faaf-107">For the purposes of this discussion, a pure function is implemented as a method in C#.</span></span>  
  
 <span data-ttu-id="2faaf-108">Jak wspomniano wcześniej w tej sekcji, czystej funkcji ma dwie właściwości przydatne:</span><span class="sxs-lookup"><span data-stu-id="2faaf-108">As noted previously in this section, a pure function has two useful characteristics:</span></span>  
  
-   <span data-ttu-id="2faaf-109">Nie ma żadnych efektów ubocznych.</span><span class="sxs-lookup"><span data-stu-id="2faaf-109">It has no side effects.</span></span> <span data-ttu-id="2faaf-110">Funkcja nie zmienia żadnych zmiennych lub danych dowolnego typu spoza tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="2faaf-110">The function does not change any variables or the data of any type outside of the function.</span></span>  
  
-   <span data-ttu-id="2faaf-111">Jest ona zgodna.</span><span class="sxs-lookup"><span data-stu-id="2faaf-111">It is consistent.</span></span> <span data-ttu-id="2faaf-112">Biorąc pod uwagę ten sam zestaw danych wejściowych, która zawsze zwraca tę samą wartość w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="2faaf-112">Given the same set of input data, it will always return the same output value.</span></span>  
  
 <span data-ttu-id="2faaf-113">Jednym ze sposobów przechodzenia do programowania funkcyjnego jest Przeprowadź refaktoryzację istniejącego kodu, aby wyeliminować niepotrzebne efekty uboczne i zależności zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="2faaf-113">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="2faaf-114">W ten sposób można utworzyć wersji czystą funkcję istniejącego kodu.</span><span class="sxs-lookup"><span data-stu-id="2faaf-114">In this way, you can create pure function versions of existing code.</span></span>  
  
 <span data-ttu-id="2faaf-115">W tym temacie omówiono funkcja czystego jest i co nie jest.</span><span class="sxs-lookup"><span data-stu-id="2faaf-115">This topic discusses what a pure function is and what it is not.</span></span> <span data-ttu-id="2faaf-116">[Samouczek: manipulowanie zawartością w dokumencie WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) samouczek przedstawia sposób modyfikowania dokumentu WordprocessingML i zawiera dwa przykłady jak Refaktoryzacja, przy użyciu czystej funkcji.</span><span class="sxs-lookup"><span data-stu-id="2faaf-116">The [Tutorial: Manipulating Content in a WordprocessingML Document (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a><span data-ttu-id="2faaf-117">Eliminując skutki uboczne i zależności zewnętrznych</span><span class="sxs-lookup"><span data-stu-id="2faaf-117">Eliminating Side Effects and External Dependencies</span></span>  
 <span data-ttu-id="2faaf-118">Poniższe przykłady porównać dwie funkcje — czyste i czystą funkcję.</span><span class="sxs-lookup"><span data-stu-id="2faaf-118">The following examples contrast two non-pure functions and a pure function.</span></span>  
  
### <a name="non-pure-function-that-changes-a-class-member"></a><span data-ttu-id="2faaf-119">Czystej funkcji, która zmienia składowej klasy</span><span class="sxs-lookup"><span data-stu-id="2faaf-119">Non-Pure Function that Changes a Class Member</span></span>  
 <span data-ttu-id="2faaf-120">W poniższym kodzie `HyphenatedConcat` funkcja nie jest funkcją czystego, ponieważ modyfikuje `aMember` element członkowski danych w klasie:</span><span class="sxs-lookup"><span data-stu-id="2faaf-120">In the following code, the `HyphenatedConcat` function is not a pure function, because it modifies the `aMember` data member in the class:</span></span>  
  
```csharp  
public class Program  
{  
    private static string aMember = "StringOne";  
  
    public static void HyphenatedConcat(string appendStr)  
    {  
        aMember += '-' + appendStr;  
    }  
  
    public static void Main()  
    {  
        HyphenatedConcat("StringTwo");  
        Console.WriteLine(aMember);  
    }  
}  
```  
  
 <span data-ttu-id="2faaf-121">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="2faaf-121">This code produces the following output:</span></span>  
  
```  
StringOne-StringTwo  
```  
  
 <span data-ttu-id="2faaf-122">Zwróć uwagę, że jej nie ma znaczenia tego, czy ma modyfikacji danych `public` lub `private` dostępu lub jest `static` elementu członkowskiego lub elementu członkowskiego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="2faaf-122">Note that it is irrelevant whether the data being modified has `public` or `private` access, or is a `static` member or an instance member.</span></span> <span data-ttu-id="2faaf-123">Czystą funkcję nie zmienia żadnych danych poza funkcją.</span><span class="sxs-lookup"><span data-stu-id="2faaf-123">A pure function does not change any data outside of the function.</span></span>  
  
### <a name="non-pure-function-that-changes-an-argument"></a><span data-ttu-id="2faaf-124">Czystej funkcji, która zmienia argumentu</span><span class="sxs-lookup"><span data-stu-id="2faaf-124">Non-Pure Function that Changes an Argument</span></span>  
 <span data-ttu-id="2faaf-125">Ponadto, następująca wersja tej samej funkcji nie jest czysty ponieważ modyfikuje zawartość jako parametr `sb`.</span><span class="sxs-lookup"><span data-stu-id="2faaf-125">Furthermore, the following version of this same function is not pure because it modifies the contents of its parameter, `sb`.</span></span>  
  
```csharp  
public class Program  
{  
    public static void HyphenatedConcat(StringBuilder sb, String appendStr)  
    {  
        sb.Append('-' + appendStr);  
    }  
  
    public static void Main()  
    {  
        StringBuilder sb1 = new StringBuilder("StringOne");  
        HyphenatedConcat(sb1, "StringTwo");  
        Console.WriteLine(sb1);  
    }  
}  
```  
  
 <span data-ttu-id="2faaf-126">Ta wersja programu daje takie same dane wyjściowe jako pierwsza wersja, ponieważ `HyphenatedConcat` funkcja została zmieniona wartość (stan) jako pierwszy parametr, wywołując <xref:System.Text.StringBuilder.Append%2A> funkcja elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="2faaf-126">This version of the program produces the same output as the first version, because the `HyphenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="2faaf-127">Uwaga występowanie tej zmiany, pomimo faktu, `HyphenatedConcat` używa wywołań przez wartość parametru przekazywania.</span><span class="sxs-lookup"><span data-stu-id="2faaf-127">Note that this alteration occurs despite that fact that `HyphenatedConcat` uses call-by-value parameter passing.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2faaf-128">Dla typów odwołań w przypadku przekazania parametr przez wartość, jej powoduje kopię odwołanie do obiektu przekazywana.</span><span class="sxs-lookup"><span data-stu-id="2faaf-128">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="2faaf-129">Ta kopia jest nadal skojarzone z tymi samymi danymi wystąpienia jako odwołanie do oryginalnego (aż do zmiennej odwołania jest przypisany do nowego obiektu).</span><span class="sxs-lookup"><span data-stu-id="2faaf-129">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="2faaf-130">Wywołanie przez odwołanie nie jest zawsze wymagane dla funkcji zmodyfikować parametr.</span><span class="sxs-lookup"><span data-stu-id="2faaf-130">Call-by-reference is not necessarily required for a function to modify a parameter.</span></span>  
  
### <a name="pure-function"></a><span data-ttu-id="2faaf-131">Czystej funkcji</span><span class="sxs-lookup"><span data-stu-id="2faaf-131">Pure Function</span></span>  
<span data-ttu-id="2faaf-132">Ta następnej wersji programu przedstawia sposób implementowania `HyphenatedConcat` pełnią czystą funkcję.</span><span class="sxs-lookup"><span data-stu-id="2faaf-132">This next version of the program shows how to implement the `HyphenatedConcat` function as a pure function.</span></span>  
  
```csharp  
class Program  
{  
    public static string HyphenatedConcat(string s, string appendStr)  
    {  
        return (s + '-' + appendStr);  
    }  
  
    public static void Main(string[] args)  
    {  
        string s1 = "StringOne";  
        string s2 = HyphenatedConcat(s1, "StringTwo");  
        Console.WriteLine(s2);  
    }  
}  
```  
  
 <span data-ttu-id="2faaf-133">Ponownie generuje ten sam wiersz danych wyjściowych w tej wersji: `StringOne-StringTwo`.</span><span class="sxs-lookup"><span data-stu-id="2faaf-133">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="2faaf-134">Należy pamiętać, aby zachować wartość połączone, jest on przechowywany w zmiennej pośrednich `s2`.</span><span class="sxs-lookup"><span data-stu-id="2faaf-134">Note that to retain the concatenated value, it is stored in the intermediate variable `s2`.</span></span>  
  
 <span data-ttu-id="2faaf-135">Jedno podejście, które mogą być bardzo przydatne jest napisanie funkcje, które są lokalnie oczyścić zanieczyszczony (oznacza to, mogą zadeklarować i modyfikowanie zmiennych lokalnych), ale są globalnie czysty.</span><span class="sxs-lookup"><span data-stu-id="2faaf-135">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="2faaf-136">Takie funkcje, ma wiele cech pożądane możliwości tworzenia, ale uniknąć niektórych bardziej zawiłe funkcjonalności idiomy programowania, takich jak konieczności rekursję, gdy prostej pętli może osiągnąć to samo.</span><span class="sxs-lookup"><span data-stu-id="2faaf-136">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>  
  
## <a name="standard-query-operators"></a><span data-ttu-id="2faaf-137">Standardowe operatory zapytań</span><span class="sxs-lookup"><span data-stu-id="2faaf-137">Standard Query Operators</span></span>  
 <span data-ttu-id="2faaf-138">Ważną cechą standardowych operatorów zapytań jest, że są implementowane jako czystych funkcji.</span><span class="sxs-lookup"><span data-stu-id="2faaf-138">An important characteristic of the standard query operators is that they are implemented as pure functions.</span></span>  
  
 <span data-ttu-id="2faaf-139">Aby uzyskać więcej informacji, zobacz [standardowe operatory zapytań — Przegląd (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2faaf-139">For more information, see [Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2faaf-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2faaf-140">See Also</span></span>

- [<span data-ttu-id="2faaf-141">Wprowadzenie do czystych przekształceń funkcjonalnych (C#)</span><span class="sxs-lookup"><span data-stu-id="2faaf-141">Introduction to Pure Functional Transformations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
- [<span data-ttu-id="2faaf-142">Programowanie funkcjonalne a Programowanie imperatywne (C#)</span><span class="sxs-lookup"><span data-stu-id="2faaf-142">Functional Programming vs. Imperative Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)

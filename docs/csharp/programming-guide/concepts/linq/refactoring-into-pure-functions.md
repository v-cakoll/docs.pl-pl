---
title: Refaktoryzacja do czystych funkcji (C#)
ms.date: 07/20/2015
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: 4cf91ff078bd1c4582daa05475a91c4a4ecaba3e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253109"
---
# <a name="refactoring-into-pure-functions-c"></a><span data-ttu-id="bc6ca-102">Refaktoryzacja do czystych funkcji (C#)</span><span class="sxs-lookup"><span data-stu-id="bc6ca-102">Refactoring Into Pure Functions (C#)</span></span>

<span data-ttu-id="bc6ca-103">Ważnym aspektem czystej transformacji funkcjonalnych jest uczenie się refaktoryzacji kodu przy użyciu czystych funkcji.</span><span class="sxs-lookup"><span data-stu-id="bc6ca-103">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bc6ca-104">Powszechną nomenklaturą w programowaniu funkcjonalnym jest to, że refaktoryzujesz programy przy użyciu czystych funkcji.</span><span class="sxs-lookup"><span data-stu-id="bc6ca-104">The common nomenclature in functional programming is that you refactor programs using pure functions.</span></span> <span data-ttu-id="bc6ca-105">W językach Visual Basic i C++ jest to zgodne z użyciem funkcji w odpowiednich językach.</span><span class="sxs-lookup"><span data-stu-id="bc6ca-105">In Visual Basic and C++, this aligns with the use of functions in the respective languages.</span></span> <span data-ttu-id="bc6ca-106">Jednak w języku C#, funkcje są nazywane metodami.</span><span class="sxs-lookup"><span data-stu-id="bc6ca-106">However, in C#, functions are called methods.</span></span> <span data-ttu-id="bc6ca-107">Na potrzeby tej dyskusji czysta funkcja jest implementowana jako metoda w języku C#.</span><span class="sxs-lookup"><span data-stu-id="bc6ca-107">For the purposes of this discussion, a pure function is implemented as a method in C#.</span></span>  
  
 <span data-ttu-id="bc6ca-108">Jak wspomniano wcześniej w tej sekcji, czysta funkcja ma dwie użyteczne cechy:</span><span class="sxs-lookup"><span data-stu-id="bc6ca-108">As noted previously in this section, a pure function has two useful characteristics:</span></span>  
  
- <span data-ttu-id="bc6ca-109">Nie ma skutków ubocznych.</span><span class="sxs-lookup"><span data-stu-id="bc6ca-109">It has no side effects.</span></span> <span data-ttu-id="bc6ca-110">Funkcja nie zmienia żadnych zmiennych ani danych dowolnego typu poza funkcją.</span><span class="sxs-lookup"><span data-stu-id="bc6ca-110">The function does not change any variables or the data of any type outside of the function.</span></span>  
  
- <span data-ttu-id="bc6ca-111">Jest spójny.</span><span class="sxs-lookup"><span data-stu-id="bc6ca-111">It is consistent.</span></span> <span data-ttu-id="bc6ca-112">Biorąc pod uwagę ten sam zestaw danych wejściowych, zawsze będzie zwracać tę samą wartość danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="bc6ca-112">Given the same set of input data, it will always return the same output value.</span></span>  
  
 <span data-ttu-id="bc6ca-113">Jednym ze sposobów przejścia do programowania funkcjonalnego jest refaktoryzacji istniejącego kodu w celu wyeliminowania niepotrzebnych skutków ubocznych i zależności zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="bc6ca-113">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="bc6ca-114">W ten sposób można utworzyć czyste wersje funkcji istniejącego kodu.</span><span class="sxs-lookup"><span data-stu-id="bc6ca-114">In this way, you can create pure function versions of existing code.</span></span>  
  
 <span data-ttu-id="bc6ca-115">W tym temacie omówiono, czym jest czysta funkcja, a czym nie.</span><span class="sxs-lookup"><span data-stu-id="bc6ca-115">This topic discusses what a pure function is and what it is not.</span></span> <span data-ttu-id="bc6ca-116">[Samouczek: Manipulowanie zawartością w dokumencie WordprocessingML (C#)](./shape-of-wordprocessingml-documents.md) samouczek pokazuje, jak manipulować dokumentem WordprocessingML i zawiera dwa przykłady refaktoryzacji przy użyciu czystej funkcji.</span><span class="sxs-lookup"><span data-stu-id="bc6ca-116">The [Tutorial: Manipulating Content in a WordprocessingML Document (C#)](./shape-of-wordprocessingml-documents.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a><span data-ttu-id="bc6ca-117">Eliminowanie skutków ubocznych i zależności zewnętrznych</span><span class="sxs-lookup"><span data-stu-id="bc6ca-117">Eliminating Side Effects and External Dependencies</span></span>  
 <span data-ttu-id="bc6ca-118">Poniższe przykłady kontrastują dwie funkcje nieczyste i czystą funkcję.</span><span class="sxs-lookup"><span data-stu-id="bc6ca-118">The following examples contrast two non-pure functions and a pure function.</span></span>  
  
### <a name="non-pure-function-that-changes-a-class-member"></a><span data-ttu-id="bc6ca-119">Funkcja nieczysta, która zmienia element członkowski klasy</span><span class="sxs-lookup"><span data-stu-id="bc6ca-119">Non-Pure Function that Changes a Class Member</span></span>  
 <span data-ttu-id="bc6ca-120">W poniższym kodzie `HyphenatedConcat` funkcja nie jest czystą funkcją, `aMember` ponieważ modyfikuje element członkowski danych w klasie:</span><span class="sxs-lookup"><span data-stu-id="bc6ca-120">In the following code, the `HyphenatedConcat` function is not a pure function, because it modifies the `aMember` data member in the class:</span></span>  
  
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
  
 <span data-ttu-id="bc6ca-121">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="bc6ca-121">This code produces the following output:</span></span>  
  
```output  
StringOne-StringTwo  
```  
  
 <span data-ttu-id="bc6ca-122">Należy zauważyć, że nie ma `public` znaczenia, czy modyfikowane dane ma lub `private` dostępu, lub jest członkiem `static` członkowskim lub elementem członkowskim wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="bc6ca-122">Note that it is irrelevant whether the data being modified has `public` or `private` access, or is a `static` member or an instance member.</span></span> <span data-ttu-id="bc6ca-123">Czysta funkcja nie zmienia żadnych danych poza funkcją.</span><span class="sxs-lookup"><span data-stu-id="bc6ca-123">A pure function does not change any data outside of the function.</span></span>  
  
### <a name="non-pure-function-that-changes-an-argument"></a><span data-ttu-id="bc6ca-124">Funkcja nieczysta, która zmienia argument</span><span class="sxs-lookup"><span data-stu-id="bc6ca-124">Non-Pure Function that Changes an Argument</span></span>  
 <span data-ttu-id="bc6ca-125">Ponadto, następująca wersja tej samej funkcji nie jest czysta, ponieważ modyfikuje zawartość jej parametru, `sb`.</span><span class="sxs-lookup"><span data-stu-id="bc6ca-125">Furthermore, the following version of this same function is not pure because it modifies the contents of its parameter, `sb`.</span></span>  
  
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
  
 <span data-ttu-id="bc6ca-126">Ta wersja programu generuje takie same dane wyjściowe jak `HyphenatedConcat` pierwsza wersja, ponieważ funkcja zmieniła wartość (stan) swojego pierwszego parametru, wywołując funkcję elementu członkowskiego. <xref:System.Text.StringBuilder.Append%2A></span><span class="sxs-lookup"><span data-stu-id="bc6ca-126">This version of the program produces the same output as the first version, because the `HyphenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="bc6ca-127">Należy zauważyć, że ta zmiana `HyphenatedConcat` występuje pomimo tego, że używa przekazywanie parametru wywołania według wartości.</span><span class="sxs-lookup"><span data-stu-id="bc6ca-127">Note that this alteration occurs despite that fact that `HyphenatedConcat` uses call-by-value parameter passing.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bc6ca-128">Dla typów odwołań, jeśli przekażesz parametr według wartości, powoduje to kopię odwołania do obiektu przekazywane.</span><span class="sxs-lookup"><span data-stu-id="bc6ca-128">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="bc6ca-129">Ta kopia jest nadal skojarzona z tymi samymi danymi wystąpienia co oryginalne odwołanie (dopóki zmienna referencyjna nie zostanie przypisana do nowego obiektu).</span><span class="sxs-lookup"><span data-stu-id="bc6ca-129">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="bc6ca-130">Odwołanie nie musi być wymagane, aby funkcja zmodyfikowała parametr.</span><span class="sxs-lookup"><span data-stu-id="bc6ca-130">Call-by-reference is not necessarily required for a function to modify a parameter.</span></span>  
  
### <a name="pure-function"></a><span data-ttu-id="bc6ca-131">Czysta funkcja</span><span class="sxs-lookup"><span data-stu-id="bc6ca-131">Pure Function</span></span>  
<span data-ttu-id="bc6ca-132">Ta następna wersja programu pokazuje, `HyphenatedConcat` jak zaimplementować funkcję jako czystą funkcję.</span><span class="sxs-lookup"><span data-stu-id="bc6ca-132">This next version of the program shows how to implement the `HyphenatedConcat` function as a pure function.</span></span>  
  
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
  
 <span data-ttu-id="bc6ca-133">Ponownie, ta wersja daje ten sam `StringOne-StringTwo`wiersz danych wyjściowych: .</span><span class="sxs-lookup"><span data-stu-id="bc6ca-133">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="bc6ca-134">Należy zauważyć, że aby zachować połączoną wartość, `s2`jest ona przechowywana w zmiennej pośredniej .</span><span class="sxs-lookup"><span data-stu-id="bc6ca-134">Note that to retain the concatenated value, it is stored in the intermediate variable `s2`.</span></span>  
  
 <span data-ttu-id="bc6ca-135">Jednym z podejść, które mogą być bardzo przydatne jest pisanie funkcji, które są lokalnie nieczyste (oznacza to, że deklarują i modyfikują zmienne lokalne), ale są globalnie czyste.</span><span class="sxs-lookup"><span data-stu-id="bc6ca-135">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="bc6ca-136">Takie funkcje mają wiele pożądanych cech komposability, ale uniknąć niektórych bardziej zawiłe funkcjonalne idiomy programowania, takich jak konieczności korzystania z rekursji, gdy prosta pętla będzie osiągnąć to samo.</span><span class="sxs-lookup"><span data-stu-id="bc6ca-136">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>  
  
## <a name="standard-query-operators"></a><span data-ttu-id="bc6ca-137">Standardowe operatory zapytań</span><span class="sxs-lookup"><span data-stu-id="bc6ca-137">Standard Query Operators</span></span>  
 <span data-ttu-id="bc6ca-138">Ważną cechą standardowych operatorów zapytań jest to, że są one implementowane jako czyste funkcje.</span><span class="sxs-lookup"><span data-stu-id="bc6ca-138">An important characteristic of the standard query operators is that they are implemented as pure functions.</span></span>  
  
 <span data-ttu-id="bc6ca-139">Aby uzyskać więcej informacji, zobacz [Omówienie standardowych operatorów zapytań (C#)](./standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bc6ca-139">For more information, see [Standard Query Operators Overview (C#)](./standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc6ca-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bc6ca-140">See also</span></span>

- [<span data-ttu-id="bc6ca-141">Wprowadzenie do czystych przemian funkcjonalnych (C#)</span><span class="sxs-lookup"><span data-stu-id="bc6ca-141">Introduction to Pure Functional Transformations (C#)</span></span>](./introduction-to-pure-functional-transformations.md)
- [<span data-ttu-id="bc6ca-142">Programowanie funkcjonalne a programowanie imperatywne (C#)</span><span class="sxs-lookup"><span data-stu-id="bc6ca-142">Functional Programming vs. Imperative Programming (C#)</span></span>](./functional-programming-vs-imperative-programming.md)

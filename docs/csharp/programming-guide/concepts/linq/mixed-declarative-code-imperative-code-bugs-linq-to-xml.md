---
title: Mieszany kod deklaracyjnej usterki kodu (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
ms.openlocfilehash: 30760999a264c81e16104c0c9b112d442ce66121
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591624"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-c"></a><span data-ttu-id="2043e-102">Mieszany kod deklaratywny/niezbędny kod (LINQ to XMLC#) ()</span><span class="sxs-lookup"><span data-stu-id="2043e-102">Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="2043e-103">zawiera różne metody, które umożliwiają bezpośrednie modyfikowanie drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="2043e-103">contains various methods that allow you to modify an XML tree directly.</span></span> <span data-ttu-id="2043e-104">Możesz dodać elementy, usunąć elementy, zmienić zawartość elementu, dodać atrybuty i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="2043e-104">You can add elements, delete elements, change the contents of an element, add attributes, and so on.</span></span> <span data-ttu-id="2043e-105">Ten interfejs programowania został opisany w temacie [Modyfikowanie drzew XML (LINQ to XML)C#()](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2043e-105">This programming interface is described in [Modifying XML Trees (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span> <span data-ttu-id="2043e-106">Jeśli dokonujesz iteracji przez jedną z osi, na <xref:System.Xml.Linq.XContainer.Elements%2A>przykład, i modyfikujesz drzewo XML podczas iteracji przez oś, możesz zakończyć z niektórymi niektórymi usterkami.</span><span class="sxs-lookup"><span data-stu-id="2043e-106">If you are iterating through one of the axes, such as <xref:System.Xml.Linq.XContainer.Elements%2A>, and you are modifying the XML tree as you iterate through the axis, you can end up with some strange bugs.</span></span>  
  
 <span data-ttu-id="2043e-107">Ten problem jest czasami znany jako "problem z Halloween".</span><span class="sxs-lookup"><span data-stu-id="2043e-107">This problem is sometimes known as "The Halloween Problem".</span></span>  
  
## <a name="definition-of-the-problem"></a><span data-ttu-id="2043e-108">Definicja problemu</span><span class="sxs-lookup"><span data-stu-id="2043e-108">Definition of the Problem</span></span>  
 <span data-ttu-id="2043e-109">Podczas pisania kodu przy użyciu LINQ, który wykonuje iterację kolekcji, piszesz kod w stylu deklaratywnym.</span><span class="sxs-lookup"><span data-stu-id="2043e-109">When you write some code using LINQ that iterates through a collection, you are writing code in a declarative style.</span></span> <span data-ttu-id="2043e-110">Więcej informacji o tym, *co* chcesz zrobić, jest bardziej zbliżone, a tym samym, *jak* chcesz go wykonać.</span><span class="sxs-lookup"><span data-stu-id="2043e-110">It is more akin to describing *what* you want, rather that *how* you want to get it done.</span></span> <span data-ttu-id="2043e-111">Jeśli napiszesz kod, który 1) pobierze pierwszy element, 2) testuje go w pewnym stanie, 3) modyfikuje go, a 4) umieszcza go z powrotem na liście, wówczas będzie to kod zapasowy.</span><span class="sxs-lookup"><span data-stu-id="2043e-111">If you write code that 1) gets the first element, 2) tests it for some condition, 3) modifies it, and 4) puts it back into the list, then this would be imperative code.</span></span> <span data-ttu-id="2043e-112">Poinformujesz o tym, *jak* to zrobić.</span><span class="sxs-lookup"><span data-stu-id="2043e-112">You are telling the computer *how* to do what you want done.</span></span>  
  
 <span data-ttu-id="2043e-113">Mieszanie tych stylów kodu w tej samej operacji polega na tym, co prowadzi do problemów.</span><span class="sxs-lookup"><span data-stu-id="2043e-113">Mixing these styles of code in the same operation is what leads to problems.</span></span> <span data-ttu-id="2043e-114">Rozważ następujące opcje:</span><span class="sxs-lookup"><span data-stu-id="2043e-114">Consider the following:</span></span>  
  
 <span data-ttu-id="2043e-115">Załóżmy, że masz połączoną listę z trzema elementami (a, b i c):</span><span class="sxs-lookup"><span data-stu-id="2043e-115">Suppose you have a linked list with three items in it (a, b, and c):</span></span>  
  
 `a -> b -> c`  
  
 <span data-ttu-id="2043e-116">Teraz Załóżmy, że chcesz przejść przez połączoną listę, dodając trzy nowe elementy (a ", b" i c ").</span><span class="sxs-lookup"><span data-stu-id="2043e-116">Now, suppose that you want to move through the linked list, adding three new items (a', b', and c').</span></span> <span data-ttu-id="2043e-117">Chcesz, aby połączona lista wyglądała następująco:</span><span class="sxs-lookup"><span data-stu-id="2043e-117">You want the resulting linked list to look like this:</span></span>  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 <span data-ttu-id="2043e-118">Dlatego Napisz kod, który wykonuje iterację na liście, i dla każdego elementu, dodaje nowy element po nim.</span><span class="sxs-lookup"><span data-stu-id="2043e-118">So you write code that iterates through the list, and for every item, adds a new item right after it.</span></span> <span data-ttu-id="2043e-119">Co się dzieje, gdy Twój kod będzie najpierw widział `a` element i Wstaw `a'` po nim.</span><span class="sxs-lookup"><span data-stu-id="2043e-119">What happens is that your code will first see the `a` element, and insert `a'` after it.</span></span> <span data-ttu-id="2043e-120">Teraz kod zostanie przeniesiony do następnego węzła na liście, który jest teraz `a'`!</span><span class="sxs-lookup"><span data-stu-id="2043e-120">Now, your code will move to the next node in the list, which is now `a'`!</span></span> <span data-ttu-id="2043e-121">Happily IT dodaje nowy element do listy `a''`.</span><span class="sxs-lookup"><span data-stu-id="2043e-121">It happily adds a new item to the list, `a''`.</span></span>  
  
 <span data-ttu-id="2043e-122">Jak rozwiązać ten problem w świecie rzeczywistym?</span><span class="sxs-lookup"><span data-stu-id="2043e-122">How would you solve this in the real world?</span></span> <span data-ttu-id="2043e-123">Można również utworzyć kopię pierwotnej połączonej listy oraz zupełnie nową listę.</span><span class="sxs-lookup"><span data-stu-id="2043e-123">Well, you might make a copy of the original linked list, and create a completely new list.</span></span> <span data-ttu-id="2043e-124">Lub jeśli piszesz czysty kod, możesz znaleźć pierwszy element, dodać nowy element, a następnie dwukrotnie wykonać dwa razy na liście połączonej, przenosząc nad element, który właśnie został dodany.</span><span class="sxs-lookup"><span data-stu-id="2043e-124">Or if you are writing purely imperative code, you might find the first item, add the new item, and then advance twice in the linked list, advancing over the element that you just added.</span></span>  
  
## <a name="adding-while-iterating"></a><span data-ttu-id="2043e-125">Dodawanie podczas iteracji</span><span class="sxs-lookup"><span data-stu-id="2043e-125">Adding While Iterating</span></span>  
 <span data-ttu-id="2043e-126">Załóżmy na przykład, że chcesz napisać jakiś kod dla każdego elementu w drzewie, chcesz utworzyć zduplikowany element:</span><span class="sxs-lookup"><span data-stu-id="2043e-126">For example, suppose you want to write some code that for every element in a tree, you want to create a duplicate element:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    root.Add(new XElement(e.Name, (string)e));  
```  
  
 <span data-ttu-id="2043e-127">Ten kod przechodzi do nieskończonej pętli.</span><span class="sxs-lookup"><span data-stu-id="2043e-127">This code goes into an infinite loop.</span></span> <span data-ttu-id="2043e-128">Instrukcja iteruje `Elements()` przez oś, `doc` dodając nowe elementy do elementu. `foreach`</span><span class="sxs-lookup"><span data-stu-id="2043e-128">The `foreach` statement iterates through the `Elements()` axis, adding new elements to the `doc` element.</span></span> <span data-ttu-id="2043e-129">Zostanie ona zakończona również za pomocą elementów, które właśnie dodał.</span><span class="sxs-lookup"><span data-stu-id="2043e-129">It ends up iterating also through the elements it just added.</span></span> <span data-ttu-id="2043e-130">I ponieważ przydziela nowe obiekty do każdej iteracji pętli, ostatecznie zużywa całą dostępną pamięć.</span><span class="sxs-lookup"><span data-stu-id="2043e-130">And because it allocates new objects with every iteration of the loop, it will eventually consume all available memory.</span></span>  
  
 <span data-ttu-id="2043e-131">Ten problem można rozwiązać, pobierając kolekcję do pamięci przy użyciu <xref:System.Linq.Enumerable.ToList%2A> standardowego operatora zapytania w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="2043e-131">You can fix this problem by pulling the collection into memory using the <xref:System.Linq.Enumerable.ToList%2A> standard query operator, as follows:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements().ToList())  
    root.Add(new XElement(e.Name, (string)e));  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="2043e-132">Teraz kod działa.</span><span class="sxs-lookup"><span data-stu-id="2043e-132">Now the code works.</span></span> <span data-ttu-id="2043e-133">Utworzone drzewo XML jest następujące:</span><span class="sxs-lookup"><span data-stu-id="2043e-133">The resulting XML tree is the following:</span></span>  
  
```xml  
<Root>  
  <A>1</A>  
  <B>2</B>  
  <C>3</C>  
  <A>1</A>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
## <a name="deleting-while-iterating"></a><span data-ttu-id="2043e-134">Usuwanie podczas iteracji</span><span class="sxs-lookup"><span data-stu-id="2043e-134">Deleting While Iterating</span></span>  
 <span data-ttu-id="2043e-135">Jeśli chcesz usunąć wszystkie węzły na określonym poziomie, być może chcesz napisać kod podobny do poniższego:</span><span class="sxs-lookup"><span data-stu-id="2043e-135">If you want to delete all nodes at a certain level, you might be tempted to write code like the following:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    e.Remove();  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="2043e-136">Nie jest to jednak wykonywane.</span><span class="sxs-lookup"><span data-stu-id="2043e-136">However, this does not do what you want.</span></span> <span data-ttu-id="2043e-137">W tej sytuacji po usunięciu pierwszego elementu, jest on usuwany z drzewa XML zawartego w katalogu głównym, a kod w metodzie element, który wykonuje iterację nie może znaleźć następnego elementu.</span><span class="sxs-lookup"><span data-stu-id="2043e-137">In this situation, after you have removed the first element, A, it is removed from the XML tree contained in root, and the code in the Elements method that is doing the iterating cannot find the next element.</span></span>  
  
 <span data-ttu-id="2043e-138">Poprzedni kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="2043e-138">The preceding code produces the following output:</span></span>  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 <span data-ttu-id="2043e-139">Rozwiązanie to ponownie wywołuje <xref:System.Linq.Enumerable.ToList%2A> zmaterializowania kolekcji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="2043e-139">The solution again is to call <xref:System.Linq.Enumerable.ToList%2A> to materialize the collection, as follows:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements().ToList())  
    e.Remove();  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="2043e-140">Spowoduje to utworzenie następujących danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="2043e-140">This produces the following output:</span></span>  
  
```xml  
<Root />  
```  
  
 <span data-ttu-id="2043e-141">Alternatywnie można wyeliminować iterację całkowicie poprzez wywołanie <xref:System.Xml.Linq.XElement.RemoveAll%2A> elementu nadrzędnego:</span><span class="sxs-lookup"><span data-stu-id="2043e-141">Alternatively, you can eliminate the iteration altogether by calling <xref:System.Xml.Linq.XElement.RemoveAll%2A> on the parent element:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
root.RemoveAll();  
Console.WriteLine(root);  
```  
  
## <a name="why-cant-linq-automatically-handle-this"></a><span data-ttu-id="2043e-142">Dlaczego nie można automatycznie obsłużyć LINQ?</span><span class="sxs-lookup"><span data-stu-id="2043e-142">Why Can't LINQ Automatically Handle This?</span></span>  
 <span data-ttu-id="2043e-143">Jednym z metod jest zawsze umieszczenie wszystkiego w pamięci zamiast oceny z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="2043e-143">One approach would be to always bring everything into memory instead of doing lazy evaluation.</span></span> <span data-ttu-id="2043e-144">Jest to jednak bardzo kosztowne pod względem wydajności i użycia pamięci.</span><span class="sxs-lookup"><span data-stu-id="2043e-144">However, it would be very expensive in terms of performance and memory use.</span></span> <span data-ttu-id="2043e-145">W rzeczywistości, jeśli LINQ i (LINQ to XML) miały przyjąć takie podejście, wystąpi niepowodzenie w rzeczywistych sytuacjach.</span><span class="sxs-lookup"><span data-stu-id="2043e-145">In fact, if LINQ and (LINQ to XML) were to take this approach, it would fail in real-world situations.</span></span>  
  
 <span data-ttu-id="2043e-146">Innym możliwym podejściem jest umieszczenie w kodzie LINQ składni transakcji, a kompilator próbuje analizować kod i ustalić, czy jakakolwiek konkretna kolekcja jest wymagana do materiału.</span><span class="sxs-lookup"><span data-stu-id="2043e-146">Another possible approach would be to put in some sort of transaction syntax into LINQ, and have the compiler attempt to analyze the code and determine if any particular collection needed to be materialized.</span></span> <span data-ttu-id="2043e-147">Jednak próba ustalenia całego kodu, który ma efekty uboczne, to niezwykle Complex.</span><span class="sxs-lookup"><span data-stu-id="2043e-147">However, attempting to determine all code that has side-effects is incredibly complex.</span></span> <span data-ttu-id="2043e-148">Rozważmy następujący kod:</span><span class="sxs-lookup"><span data-stu-id="2043e-148">Consider the following code:</span></span>  
  
```csharp  
var z =  
    from e in root.Elements()  
    where TestSomeCondition(e)  
    select DoMyProjection(e);  
```  
  
 <span data-ttu-id="2043e-149">Taki kod analizy musi analizować metody TestSomeCondition i DoMyProjection, a także wszystkie metody wywoływane przez te metody, aby określić, czy dowolny kod ma efekty uboczne.</span><span class="sxs-lookup"><span data-stu-id="2043e-149">Such analysis code would need to analyze the methods TestSomeCondition and DoMyProjection, and all methods that those methods called, to determine if any code had side-effects.</span></span> <span data-ttu-id="2043e-150">Jednak kod analizy nie może wyszukać żadnego kodu, który miał skutki uboczne.</span><span class="sxs-lookup"><span data-stu-id="2043e-150">But the analysis code could not just look for any code that had side-effects.</span></span> <span data-ttu-id="2043e-151">Należy wybrać tylko kod, który miał skutki uboczne w elementach `root` podrzędnych w tej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="2043e-151">It would need to select for just the code that had side-effects on the child elements of `root` in this situation.</span></span>  
  
 <span data-ttu-id="2043e-152">LINQ to XML nie próbuje wykonać żadnej takiej analizy.</span><span class="sxs-lookup"><span data-stu-id="2043e-152">LINQ to XML does not attempt to do any such analysis.</span></span>  
  
 <span data-ttu-id="2043e-153">Pozwala to uniknąć tych problemów.</span><span class="sxs-lookup"><span data-stu-id="2043e-153">It is up to you to avoid these problems.</span></span>  
  
## <a name="guidance"></a><span data-ttu-id="2043e-154">Wskazówki</span><span class="sxs-lookup"><span data-stu-id="2043e-154">Guidance</span></span>  
 <span data-ttu-id="2043e-155">Najpierw nie należy mieszać kodu deklaratywnego i bezwzględnego.</span><span class="sxs-lookup"><span data-stu-id="2043e-155">First, do not mix declarative and imperative code.</span></span>  
  
 <span data-ttu-id="2043e-156">Nawet jeśli znasz dokładnie semantykę kolekcji i semantykę metod, które modyfikują drzewo XML, jeśli piszesz jakiś kod sprytne, który pozwala uniknąć tych kategorii problemów, kod będzie musiał być obsługiwany przez innych deweloperów w przyszłości. i mogą nie być jasne w przypadku problemów.</span><span class="sxs-lookup"><span data-stu-id="2043e-156">Even if you know exactly the semantics of your collections and the semantics of the methods that modify the XML tree, if you write some clever code that avoids these categories of problems, your code will need to be maintained by other developers in the future, and they may not be as clear on the issues.</span></span> <span data-ttu-id="2043e-157">Jeśli Mieszasz deklaratywne i bezwzględne style kodowania, kod będzie bardziej kruchy.</span><span class="sxs-lookup"><span data-stu-id="2043e-157">If you mix declarative and imperative coding styles, your code will be more brittle.</span></span>  
  
 <span data-ttu-id="2043e-158">Jeśli napiszesz kod, który materializuje kolekcję, aby uniknąć tych problemów, zwróć uwagę na to, że komentarze są odpowiednie w kodzie, dzięki czemu programiści mogą zrozumieć problem.</span><span class="sxs-lookup"><span data-stu-id="2043e-158">If you write code that materializes a collection so that these problems are avoided, note it with comments as appropriate in your code, so that maintenance programmers will understand the issue.</span></span>  
  
 <span data-ttu-id="2043e-159">Jeśli na przykład wydajność i inne zagadnienia są dozwolone, należy użyć tylko kodu deklaratywnego.</span><span class="sxs-lookup"><span data-stu-id="2043e-159">Second, if performance and other considerations allow, use only declarative code.</span></span> <span data-ttu-id="2043e-160">Nie należy modyfikować istniejącego drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="2043e-160">Don't modify your existing XML tree.</span></span> <span data-ttu-id="2043e-161">Generuj nowy.</span><span class="sxs-lookup"><span data-stu-id="2043e-161">Generate a new one.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
XElement newRoot = new XElement("Root",  
    root.Elements(),  
    root.Elements()  
);  
Console.WriteLine(newRoot);  
```  
 
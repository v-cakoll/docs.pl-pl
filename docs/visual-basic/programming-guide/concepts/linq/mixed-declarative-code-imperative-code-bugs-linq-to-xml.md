---
title: Mieszane błędy kod deklaratywny kodu i Imperatywnego (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: f12b1ab4-bb92-4b92-a648-0525e45b3ce7
ms.openlocfilehash: e7b3b624bb91525d2cda9477c29291e25eba1b07
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842281"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-visual-basic"></a><span data-ttu-id="db264-102">Mieszane błędy kodu deklaratywnego/Imperatywne (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db264-102">Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="db264-103">zawiera różne metody, które umożliwiają modyfikowanie drzewa XML bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="db264-103">contains various methods that allow you to modify an XML tree directly.</span></span> <span data-ttu-id="db264-104">Można dodać elementy, usuwanie elementów, zmienić zawartość elementu, dodawanie atrybutów i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="db264-104">You can add elements, delete elements, change the contents of an element, add attributes, and so on.</span></span> <span data-ttu-id="db264-105">Ten interfejs programowania jest opisana w [modyfikowanie drzew XML (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="db264-105">This programming interface is described in [Modifying XML Trees (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span></span> <span data-ttu-id="db264-106">Jeśli użytkownik są iteracji w jednej osi, takie jak <xref:System.Xml.Linq.XContainer.Elements%2A>i są modyfikowanie drzewa XML jako iterację osi, użytkownik może wystąpić pewne błędy otrzymano nieoczekiwany.</span><span class="sxs-lookup"><span data-stu-id="db264-106">If you are iterating through one of the axes, such as <xref:System.Xml.Linq.XContainer.Elements%2A>, and you are modifying the XML tree as you iterate through the axis, you can end up with some strange bugs.</span></span>  
  
 <span data-ttu-id="db264-107">Ten problem jest czasami określany jako "Halloween Problem".</span><span class="sxs-lookup"><span data-stu-id="db264-107">This problem is sometimes known as "The Halloween Problem".</span></span>  
  
## <a name="definition-of-the-problem"></a><span data-ttu-id="db264-108">Definicja problemu</span><span class="sxs-lookup"><span data-stu-id="db264-108">Definition of the Problem</span></span>  
 <span data-ttu-id="db264-109">Podczas pisania kodu za pomocą LINQ, który iteruje po kolekcji pisania kodu w stylu deklaratywnego.</span><span class="sxs-lookup"><span data-stu-id="db264-109">When you write some code using LINQ that iterates through a collection, you are writing code in a declarative style.</span></span> <span data-ttu-id="db264-110">Jest więcej podobnie opisujące *co* chcesz, a które *jak* chcesz wykonywania pracy.</span><span class="sxs-lookup"><span data-stu-id="db264-110">It is more akin to describing *what* you want, rather that *how* you want to get it done.</span></span> <span data-ttu-id="db264-111">Jeśli piszesz kod, który (1) pierwszego elementu, 2) testy dla jakiś warunek 3) modyfikuje je i 4) umieszcza go z powrotem do listy, a następnie będzie to kodu imperatywnego.</span><span class="sxs-lookup"><span data-stu-id="db264-111">If you write code that 1) gets the first element, 2) tests it for some condition, 3) modifies it, and 4) puts it back into the list, then this would be imperative code.</span></span> <span data-ttu-id="db264-112">Sprawi, że komputer *jak* zrobić lepiej będzie gotowe.</span><span class="sxs-lookup"><span data-stu-id="db264-112">You are telling the computer *how* to do what you want done.</span></span>  
  
 <span data-ttu-id="db264-113">Mieszanie te style kodu w tej samej operacji jest o tym, co prowadzi do problemów.</span><span class="sxs-lookup"><span data-stu-id="db264-113">Mixing these styles of code in the same operation is what leads to problems.</span></span> <span data-ttu-id="db264-114">Rozważ następujące opcje:</span><span class="sxs-lookup"><span data-stu-id="db264-114">Consider the following:</span></span>  
  
 <span data-ttu-id="db264-115">Załóżmy, że masz listę połączoną z trzema elementami w nim (, b i c):</span><span class="sxs-lookup"><span data-stu-id="db264-115">Suppose you have a linked list with three items in it (a, b, and c):</span></span>  
  
 `a -> b -> c`  
  
 <span data-ttu-id="db264-116">Załóżmy, że chcesz przenieść za pośrednictwem połączonej listy dodawania trzech nowych elementów (", b", a c ").</span><span class="sxs-lookup"><span data-stu-id="db264-116">Now, suppose that you want to move through the linked list, adding three new items (a', b', and c').</span></span> <span data-ttu-id="db264-117">Chcesz, aby wynikowe listy dwukierunkowej, aby wyglądał następująco:</span><span class="sxs-lookup"><span data-stu-id="db264-117">You want the resulting linked list to look like this:</span></span>  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 <span data-ttu-id="db264-118">Dlatego napisać kod, który wykonuje iterację na liście, a następnie dla każdego elementu dodaje nowe uprawnienie elementu po nim.</span><span class="sxs-lookup"><span data-stu-id="db264-118">So you write code that iterates through the list, and for every item, adds a new item right after it.</span></span> <span data-ttu-id="db264-119">Co się stanie, to najpierw zostanie wyświetlony kod `a` elementu i Wstaw `a'` po nim.</span><span class="sxs-lookup"><span data-stu-id="db264-119">What happens is that your code will first see the `a` element, and insert `a'` after it.</span></span> <span data-ttu-id="db264-120">Teraz kod przejdzie do kolejnego węzła na liście, która jest teraz `a'`!</span><span class="sxs-lookup"><span data-stu-id="db264-120">Now, your code will move to the next node in the list, which is now `a'`!</span></span> <span data-ttu-id="db264-121">Trafem korzysta dodaje nowy element do listy, `a''`.</span><span class="sxs-lookup"><span data-stu-id="db264-121">It happily adds a new item to the list, `a''`.</span></span>  
  
 <span data-ttu-id="db264-122">Jak będzie można rozwiązać ten problem w rzeczywistych warunkach?</span><span class="sxs-lookup"><span data-stu-id="db264-122">How would you solve this in the real world?</span></span> <span data-ttu-id="db264-123">Dobrze Utwórz kopię oryginalnego połączonej listy i Utwórz całkowicie nową listę.</span><span class="sxs-lookup"><span data-stu-id="db264-123">Well, you might make a copy of the original linked list, and create a completely new list.</span></span> <span data-ttu-id="db264-124">Lub jeśli piszesz kodu czysto imperatywnego, może się okazać, pierwszy element, Dodaj nowy element, a następnie przejdź dwa razy na liście połączonej, przesuwania nad elementem, który właśnie został dodany.</span><span class="sxs-lookup"><span data-stu-id="db264-124">Or if you are writing purely imperative code, you might find the first item, add the new item, and then advance twice in the linked list, advancing over the element that you just added.</span></span>  
  
## <a name="adding-while-iterating"></a><span data-ttu-id="db264-125">Dodawanie podczas iteracja</span><span class="sxs-lookup"><span data-stu-id="db264-125">Adding While Iterating</span></span>  
 <span data-ttu-id="db264-126">Na przykład załóżmy, że chcesz pisanie kodu dla każdego elementu w drzewie chcesz utworzyć zduplikowany element:</span><span class="sxs-lookup"><span data-stu-id="db264-126">For example, suppose you want to write some code that for every element in a tree, you want to create a duplicate element:</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
For Each e As XElement In root.Elements()  
    root.Add(New XElement(e.Name, e.Value))  
Next  
```  
  
 <span data-ttu-id="db264-127">Ten kod przechodzi w pętli nieskończonej.</span><span class="sxs-lookup"><span data-stu-id="db264-127">This code goes into an infinite loop.</span></span> <span data-ttu-id="db264-128">`foreach` Iteruje po instrukcji `Elements()` osi, dodawanie nowych elementów do `doc` elementu.</span><span class="sxs-lookup"><span data-stu-id="db264-128">The `foreach` statement iterates through the `Elements()` axis, adding new elements to the `doc` element.</span></span> <span data-ttu-id="db264-129">Kończy się ono również iteracji na elementach, który właśnie został dodany.</span><span class="sxs-lookup"><span data-stu-id="db264-129">It ends up iterating also through the elements it just added.</span></span> <span data-ttu-id="db264-130">A ponieważ są przydzielane nowych obiektów wraz z każdą iteracją pętli, po pewnym czasie zużyje całą dostępną pamięć.</span><span class="sxs-lookup"><span data-stu-id="db264-130">And because it allocates new objects with every iteration of the loop, it will eventually consume all available memory.</span></span>  
  
 <span data-ttu-id="db264-131">Możesz rozwiązać ten problem przez pobieranie kolekcji w pamięci, używając <xref:System.Linq.Enumerable.ToList%2A> standardowego operatora zapytania, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="db264-131">You can fix this problem by pulling the collection into memory using the <xref:System.Linq.Enumerable.ToList%2A> standard query operator, as follows:</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
For Each e As XElement In root.Elements().ToList()  
    root.Add(New XElement(e.Name, e.Value))  
Next  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="db264-132">Teraz kod działa.</span><span class="sxs-lookup"><span data-stu-id="db264-132">Now the code works.</span></span> <span data-ttu-id="db264-133">Wynikowe drzewo składni XML jest następująca:</span><span class="sxs-lookup"><span data-stu-id="db264-133">The resulting XML tree is the following:</span></span>  
  
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
  
## <a name="deleting-while-iterating"></a><span data-ttu-id="db264-134">Usuwanie podczas iteracja</span><span class="sxs-lookup"><span data-stu-id="db264-134">Deleting While Iterating</span></span>  
 <span data-ttu-id="db264-135">Jeśli chcesz usunąć wszystkie węzły, na pewnym etapie, możesz chcieć wykorzystać do pisania kodu, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="db264-135">If you want to delete all nodes at a certain level, you might be tempted to write code like the following:</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
For Each e As XElement In root.Elements()  
    e.Remove()  
Next  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="db264-136">Jednak to nie należy.</span><span class="sxs-lookup"><span data-stu-id="db264-136">However, this does not do what you want.</span></span> <span data-ttu-id="db264-137">W takiej sytuacji po usunięciu pierwszy element, A, zostanie on usunięty z drzewa XML znajdujących się w katalogu głównym, a kod w metodzie elementów, który wykonuje iteracja nie można odnaleźć następnego elementu.</span><span class="sxs-lookup"><span data-stu-id="db264-137">In this situation, after you have removed the first element, A, it is removed from the XML tree contained in root, and the code in the Elements method that is doing the iterating cannot find the next element.</span></span>  
  
 <span data-ttu-id="db264-138">Powyższy kod generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="db264-138">The preceding code produces the following output:</span></span>  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 <span data-ttu-id="db264-139">To rozwiązanie jest ponownie wywołanie <xref:System.Linq.Enumerable.ToList%2A> do zmaterializowania kolekcji, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="db264-139">The solution again is to call <xref:System.Linq.Enumerable.ToList%2A> to materialize the collection, as follows:</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
For Each e As XElement In root.Elements().ToList()  
    e.Remove()  
Next  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="db264-140">To generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="db264-140">This produces the following output:</span></span>  
  
```xml  
<Root />  
```  
  
 <span data-ttu-id="db264-141">Alternatywnie, można wyeliminować iteracji całkowicie przez wywołanie metody <xref:System.Xml.Linq.XElement.RemoveAll%2A> elementu nadrzędnego:</span><span class="sxs-lookup"><span data-stu-id="db264-141">Alternatively, you can eliminate the iteration altogether by calling <xref:System.Xml.Linq.XElement.RemoveAll%2A> on the parent element:</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
root.RemoveAll()  
Console.WriteLine(root)  
```  
  
## <a name="why-cant-linq-automatically-handle-this"></a><span data-ttu-id="db264-142">Dlaczego nie mogę LINQ automatycznie obsługiwać to?</span><span class="sxs-lookup"><span data-stu-id="db264-142">Why Can't LINQ Automatically Handle This?</span></span>  
 <span data-ttu-id="db264-143">Jedno z podejść jest zawsze Przenieś wszystko do pamięci, zamiast wykonywania obliczanie z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="db264-143">One approach would be to always bring everything into memory instead of doing lazy evaluation.</span></span> <span data-ttu-id="db264-144">Jednakże może być bardzo kosztowna pod względem wydajności i użycia pamięci.</span><span class="sxs-lookup"><span data-stu-id="db264-144">However, it would be very expensive in terms of performance and memory use.</span></span> <span data-ttu-id="db264-145">W rzeczywistości gdyby LINQ i (LINQ to XML) do zastosowania tego podejścia, przestaną działać w rzeczywistych warunkach.</span><span class="sxs-lookup"><span data-stu-id="db264-145">In fact, if LINQ and (LINQ to XML) were to take this approach, it would fail in real-world situations.</span></span>  
  
 <span data-ttu-id="db264-146">Innym podejściem możliwe będzie umieścić w jakieś składni transakcji na składnika LINQ i mają kompilatora próba przeanalizowania kodu i określenia, czy żadnej określonej kolekcji jest wymagana do być zmaterializowany.</span><span class="sxs-lookup"><span data-stu-id="db264-146">Another possible approach would be to put in some sort of transaction syntax into LINQ, and have the compiler attempt to analyze the code and determine if any particular collection needed to be materialized.</span></span> <span data-ttu-id="db264-147">Próba ustalenia cały kod, który ma efekty uboczne jest jednak bardzo złożone.</span><span class="sxs-lookup"><span data-stu-id="db264-147">However, attempting to determine all code that has side-effects is incredibly complex.</span></span> <span data-ttu-id="db264-148">Rozważmy poniższy kod:</span><span class="sxs-lookup"><span data-stu-id="db264-148">Consider the following code:</span></span>  
  
```vb  
Dim z = _  
    From e In root.Elements() _  
    Where (TestSomeCondition(e)) _  
    Select DoMyProjection(e)  
```  
  
 <span data-ttu-id="db264-149">Taki kod analizy należałoby analizowanie metod TestSomeCondition i DoMyProjection i wszystkie metody, które wywołały tych metod, aby określić, jeśli dowolny kod ma efekty uboczne.</span><span class="sxs-lookup"><span data-stu-id="db264-149">Such analysis code would need to analyze the methods TestSomeCondition and DoMyProjection, and all methods that those methods called, to determine if any code had side-effects.</span></span> <span data-ttu-id="db264-150">Jednak kod analizy nie można po prostu szukać wszelki kod, który ma efekty uboczne.</span><span class="sxs-lookup"><span data-stu-id="db264-150">But the analysis code could not just look for any code that had side-effects.</span></span> <span data-ttu-id="db264-151">Należałoby w celu wybrania tylko kod, który ma efekty uboczne na elementy podrzędne `root` w takiej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="db264-151">It would need to select for just the code that had side-effects on the child elements of `root` in this situation.</span></span>  
  
 <span data-ttu-id="db264-152">LINQ to XML nie próbuje wykonywać takie analizę.</span><span class="sxs-lookup"><span data-stu-id="db264-152">LINQ to XML does not attempt to do any such analysis.</span></span>  
  
 <span data-ttu-id="db264-153">Jest on do Ciebie, aby uniknąć tych problemów.</span><span class="sxs-lookup"><span data-stu-id="db264-153">It is up to you to avoid these problems.</span></span>  
  
## <a name="guidance"></a><span data-ttu-id="db264-154">Wskazówki</span><span class="sxs-lookup"><span data-stu-id="db264-154">Guidance</span></span>  
 <span data-ttu-id="db264-155">Po pierwsze nie należy mieszać kodu deklaratywnego i imperatywnego.</span><span class="sxs-lookup"><span data-stu-id="db264-155">First, do not mix declarative and imperative code.</span></span>  
  
 <span data-ttu-id="db264-156">Nawet wtedy, gdy znasz dokładnie semantyki kolekcji i semantyka metody, które modyfikowanie drzewa XML, jeśli piszesz niektóre inteligentne kod, który pozwala uniknąć tych kategorii problemów, Twój kod będzie muszą być przechowywane przez innych programistów w przyszłości , i nie może być jako zwykły na problemy.</span><span class="sxs-lookup"><span data-stu-id="db264-156">Even if you know exactly the semantics of your collections and the semantics of the methods that modify the XML tree, if you write some clever code that avoids these categories of problems, your code will need to be maintained by other developers in the future, and they may not be as clear on the issues.</span></span> <span data-ttu-id="db264-157">Po przemieszaniu deklaratywnego i imperatywnego kodowania style, Twój kod będzie bardziej kruchy.</span><span class="sxs-lookup"><span data-stu-id="db264-157">If you mix declarative and imperative coding styles, your code will be more brittle.</span></span>  
  
 <span data-ttu-id="db264-158">Jeśli piszesz kod, który materializuje kolekcji, tak aby uniknąć tych problemów, należy pamiętać, go z komentarzami, zgodnie z potrzebami w swoim kodzie, aby programiści obsługi będzie zrozumiałe dla problemu.</span><span class="sxs-lookup"><span data-stu-id="db264-158">If you write code that materializes a collection so that these problems are avoided, note it with comments as appropriate in your code, so that maintenance programmers will understand the issue.</span></span>  
  
 <span data-ttu-id="db264-159">Po drugie jeśli zezwala na wydajność i innych zagadnień, należy użyć tylko kod deklaratywny.</span><span class="sxs-lookup"><span data-stu-id="db264-159">Second, if performance and other considerations allow, use only declarative code.</span></span> <span data-ttu-id="db264-160">Nie należy modyfikować swoje istniejące drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="db264-160">Don't modify your existing XML tree.</span></span> <span data-ttu-id="db264-161">Generuj nowe hasło.</span><span class="sxs-lookup"><span data-stu-id="db264-161">Generate a new one.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
Dim newRoot As XElement = New XElement("Root", _  
    root.Elements(), root.Elements())  
Console.WriteLine(newRoot)  
```  
  
## <a name="see-also"></a><span data-ttu-id="db264-162">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db264-162">See also</span></span>

- [<span data-ttu-id="db264-163">Zaawansowane LINQ to XML programowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db264-163">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

---
title: Mieszane usterki deklaratywne kodu Imperatywne kodu (LINQ do XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: f12b1ab4-bb92-4b92-a648-0525e45b3ce7
ms.openlocfilehash: 797866514a2f290a98d1a75e92f850e96d28dabd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650823"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-visual-basic"></a><span data-ttu-id="f23f0-102">Mieszane usterki kodu deklaratywne kodu/Imperatywne (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f23f0-102">Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="f23f0-103"> zawiera różne metody, dzięki którym można bezpośrednio modyfikować drzewo XML.</span><span class="sxs-lookup"><span data-stu-id="f23f0-103"> contains various methods that allow you to modify an XML tree directly.</span></span> <span data-ttu-id="f23f0-104">Można dodawać elementów, usuń elementy, zmienić zawartość elementu, dodać atrybuty i itd.</span><span class="sxs-lookup"><span data-stu-id="f23f0-104">You can add elements, delete elements, change the contents of an element, add attributes, and so on.</span></span> <span data-ttu-id="f23f0-105">Ten interfejs programowania jest opisany w [modyfikowanie drzew XML (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="f23f0-105">This programming interface is described in [Modifying XML Trees (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span></span> <span data-ttu-id="f23f0-106">Jeśli użytkownik są iteracji w jednej osi, takie jak <xref:System.Xml.Linq.XContainer.Elements%2A>i modyfikujesz drzewa XML jako iterację osi, można na końcu niektóre dziwne usterki.</span><span class="sxs-lookup"><span data-stu-id="f23f0-106">If you are iterating through one of the axes, such as <xref:System.Xml.Linq.XContainer.Elements%2A>, and you are modifying the XML tree as you iterate through the axis, you can end up with some strange bugs.</span></span>  
  
 <span data-ttu-id="f23f0-107">Ten problem jest czasami określany jako "Problemu Halloween".</span><span class="sxs-lookup"><span data-stu-id="f23f0-107">This problem is sometimes known as "The Halloween Problem".</span></span>  
  
## <a name="definition-of-the-problem"></a><span data-ttu-id="f23f0-108">Definicja problemu</span><span class="sxs-lookup"><span data-stu-id="f23f0-108">Definition of the Problem</span></span>  
 <span data-ttu-id="f23f0-109">Podczas pisania kodu za pomocą LINQ, który iteruje po kolekcji deklaratywne styl pisania kodu.</span><span class="sxs-lookup"><span data-stu-id="f23f0-109">When you write some code using LINQ that iterates through a collection, you are writing code in a declarative style.</span></span> <span data-ttu-id="f23f0-110">Jest więcej podobnie opisujące *co* ma, a nie że *jak* chcesz pobrać go wykonać.</span><span class="sxs-lookup"><span data-stu-id="f23f0-110">It is more akin to describing *what* you want, rather that *how* you want to get it done.</span></span> <span data-ttu-id="f23f0-111">Podczas pisania kodu, który 1) jest pierwszym elementem, testy 2) dla niektórych warunku 3) modyfikuje go i 4) umieszcza je z powrotem do listy, a następnie będzie to konieczne kodu.</span><span class="sxs-lookup"><span data-stu-id="f23f0-111">If you write code that 1) gets the first element, 2) tests it for some condition, 3) modifies it, and 4) puts it back into the list, then this would be imperative code.</span></span> <span data-ttu-id="f23f0-112">Sprawi, że komputer *jak* zrobić, co ma gotowe.</span><span class="sxs-lookup"><span data-stu-id="f23f0-112">You are telling the computer *how* to do what you want done.</span></span>  
  
 <span data-ttu-id="f23f0-113">Mieszanie te style kodu w tej samej operacji jest, co prowadzi do problemów.</span><span class="sxs-lookup"><span data-stu-id="f23f0-113">Mixing these styles of code in the same operation is what leads to problems.</span></span> <span data-ttu-id="f23f0-114">Rozważ następujące opcje:</span><span class="sxs-lookup"><span data-stu-id="f23f0-114">Consider the following:</span></span>  
  
 <span data-ttu-id="f23f0-115">Załóżmy, że masz listy połączonej z trzema elementami w nim (, b i c):</span><span class="sxs-lookup"><span data-stu-id="f23f0-115">Suppose you have a linked list with three items in it (a, b, and c):</span></span>  
  
 `a -> b -> c`  
  
 <span data-ttu-id="f23f0-116">Załóżmy, że chcesz przenieść za pomocą listy połączonej, dodawania trzech nowych elementów (", b" i c').</span><span class="sxs-lookup"><span data-stu-id="f23f0-116">Now, suppose that you want to move through the linked list, adding three new items (a', b', and c').</span></span> <span data-ttu-id="f23f0-117">Ma wynikowej listy połączonej, aby wyglądały następująco:</span><span class="sxs-lookup"><span data-stu-id="f23f0-117">You want the resulting linked list to look like this:</span></span>  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 <span data-ttu-id="f23f0-118">Tak pisania kodu, który iteruje po za pośrednictwem listy, a każdy element dodaje nowe prawo elementu po nim.</span><span class="sxs-lookup"><span data-stu-id="f23f0-118">So you write code that iterates through the list, and for every item, adds a new item right after it.</span></span> <span data-ttu-id="f23f0-119">Co się stanie, to najpierw zostanie wyświetlony kod `a` elementu i Wstaw `a'` po nim.</span><span class="sxs-lookup"><span data-stu-id="f23f0-119">What happens is that your code will first see the `a` element, and insert `a'` after it.</span></span> <span data-ttu-id="f23f0-120">Teraz, kodu przechodzi do następnego węzła na liście, który jest obecnie `a'`!</span><span class="sxs-lookup"><span data-stu-id="f23f0-120">Now, your code will move to the next node in the list, which is now `a'`!</span></span> <span data-ttu-id="f23f0-121">Happily dodaje nowy element do listy, `a''`.</span><span class="sxs-lookup"><span data-stu-id="f23f0-121">It happily adds a new item to the list, `a''`.</span></span>  
  
 <span data-ttu-id="f23f0-122">Jak będzie można rozwiązać ten problem w świecie rzeczywistym?</span><span class="sxs-lookup"><span data-stu-id="f23f0-122">How would you solve this in the real world?</span></span> <span data-ttu-id="f23f0-123">Utwórz kopię oryginalnej listy połączonej i Utwórz całkowicie nową listę.</span><span class="sxs-lookup"><span data-stu-id="f23f0-123">Well, you might make a copy of the original linked list, and create a completely new list.</span></span> <span data-ttu-id="f23f0-124">Lub jeśli są pisanie kodu czysto konieczne może okazać się pierwszy element Dodaj nowy element, a następnie przejść dwa razy w listy połączonej, zaawansowane nad elementem, który właśnie został dodany.</span><span class="sxs-lookup"><span data-stu-id="f23f0-124">Or if you are writing purely imperative code, you might find the first item, add the new item, and then advance twice in the linked list, advancing over the element that you just added.</span></span>  
  
## <a name="adding-while-iterating"></a><span data-ttu-id="f23f0-125">Dodawanie podczas iteracja</span><span class="sxs-lookup"><span data-stu-id="f23f0-125">Adding While Iterating</span></span>  
 <span data-ttu-id="f23f0-126">Na przykład załóżmy, że chcesz pisania kodu dla każdego elementu w drzewie chcesz utworzyć zduplikowany element:</span><span class="sxs-lookup"><span data-stu-id="f23f0-126">For example, suppose you want to write some code that for every element in a tree, you want to create a duplicate element:</span></span>  
  
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
  
 <span data-ttu-id="f23f0-127">Ten kod przechodzi w pętli nieskończonej.</span><span class="sxs-lookup"><span data-stu-id="f23f0-127">This code goes into an infinite loop.</span></span> <span data-ttu-id="f23f0-128">`foreach` Iteruje po instrukcji `Elements()` osi, dodawanie nowych elementów do `doc` elementu.</span><span class="sxs-lookup"><span data-stu-id="f23f0-128">The `foreach` statement iterates through the `Elements()` axis, adding new elements to the `doc` element.</span></span> <span data-ttu-id="f23f0-129">Kończy się ono również iteracja elementy, które go dodać.</span><span class="sxs-lookup"><span data-stu-id="f23f0-129">It ends up iterating also through the elements it just added.</span></span> <span data-ttu-id="f23f0-130">I ponieważ przydzielania nowych obiektów z każdej iteracji pętli, po pewnym czasie zużyje całą dostępną pamięć.</span><span class="sxs-lookup"><span data-stu-id="f23f0-130">And because it allocates new objects with every iteration of the loop, it will eventually consume all available memory.</span></span>  
  
 <span data-ttu-id="f23f0-131">Można rozwiązać ten problem przez ściąganie kolekcji do pamięci przy użyciu <xref:System.Linq.Enumerable.ToList%2A> operator standardowej kwerendy, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f23f0-131">You can fix this problem by pulling the collection into memory using the <xref:System.Linq.Enumerable.ToList%2A> standard query operator, as follows:</span></span>  
  
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
  
 <span data-ttu-id="f23f0-132">Teraz kod działa.</span><span class="sxs-lookup"><span data-stu-id="f23f0-132">Now the code works.</span></span> <span data-ttu-id="f23f0-133">Wynikowe drzewo składni XML jest następująca:</span><span class="sxs-lookup"><span data-stu-id="f23f0-133">The resulting XML tree is the following:</span></span>  
  
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
  
## <a name="deleting-while-iterating"></a><span data-ttu-id="f23f0-134">Usuwanie podczas iteracja</span><span class="sxs-lookup"><span data-stu-id="f23f0-134">Deleting While Iterating</span></span>  
 <span data-ttu-id="f23f0-135">Jeśli chcesz usunąć wszystkie węzły na określonym poziomie, może się wydawać do pisania kodu podobne do poniższych:</span><span class="sxs-lookup"><span data-stu-id="f23f0-135">If you want to delete all nodes at a certain level, you might be tempted to write code like the following:</span></span>  
  
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
  
 <span data-ttu-id="f23f0-136">Jednak to nie chcesz.</span><span class="sxs-lookup"><span data-stu-id="f23f0-136">However, this does not do what you want.</span></span> <span data-ttu-id="f23f0-137">Po usunięciu elementu pierwszy, A, w takiej sytuacji jest usuwany z drzewa XML zawarte w katalogu głównym, a kod w metodzie elementy obsługującym iteracja nie można odnaleźć następnego elementu.</span><span class="sxs-lookup"><span data-stu-id="f23f0-137">In this situation, after you have removed the first element, A, it is removed from the XML tree contained in root, and the code in the Elements method that is doing the iterating cannot find the next element.</span></span>  
  
 <span data-ttu-id="f23f0-138">Poprzedni kod tworzy następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f23f0-138">The preceding code produces the following output:</span></span>  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 <span data-ttu-id="f23f0-139">Rozwiązanie to ponownie wywołać <xref:System.Linq.Enumerable.ToList%2A> do zmaterializowania kolekcji, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f23f0-139">The solution again is to call <xref:System.Linq.Enumerable.ToList%2A> to materialize the collection, as follows:</span></span>  
  
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
  
 <span data-ttu-id="f23f0-140">Spowoduje to utworzenie następujących danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="f23f0-140">This produces the following output:</span></span>  
  
```xml  
<Root />  
```  
  
 <span data-ttu-id="f23f0-141">Alternatywnie można wyeliminować iteracji całkowicie przez wywołanie metody <xref:System.Xml.Linq.XElement.RemoveAll%2A> na element nadrzędny:</span><span class="sxs-lookup"><span data-stu-id="f23f0-141">Alternatively, you can eliminate the iteration altogether by calling <xref:System.Xml.Linq.XElement.RemoveAll%2A> on the parent element:</span></span>  
  
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
  
## <a name="why-cant-linq-automatically-handle-this"></a><span data-ttu-id="f23f0-142">Dlaczego nie LINQ automatycznie rozwiązać?</span><span class="sxs-lookup"><span data-stu-id="f23f0-142">Why Can't LINQ Automatically Handle This?</span></span>  
 <span data-ttu-id="f23f0-143">Jednym z podejść jest zawsze Przełącz wszystko do pamięci zamiast podczas oceny opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="f23f0-143">One approach would be to always bring everything into memory instead of doing lazy evaluation.</span></span> <span data-ttu-id="f23f0-144">Jednakże może być bardzo kosztowna pod względem wydajności i użycia pamięci.</span><span class="sxs-lookup"><span data-stu-id="f23f0-144">However, it would be very expensive in terms of performance and memory use.</span></span> <span data-ttu-id="f23f0-145">W rzeczywistości gdyby LINQ i (LINQ do XML) o zastosowaniu takiego podejścia, spowoduje niepowodzenie w rzeczywistych sytuacji.</span><span class="sxs-lookup"><span data-stu-id="f23f0-145">In fact, if LINQ and (LINQ to XML) were to take this approach, it would fail in real-world situations.</span></span>  
  
 <span data-ttu-id="f23f0-146">Innym rozwiązaniem możliwe będzie umieścić w jakieś składni transakcji do składnika LINQ i mieć kompilatora próba analiza kodu i określenia, czy żadnej określonej kolekcji jest wymagana można było zmaterializować.</span><span class="sxs-lookup"><span data-stu-id="f23f0-146">Another possible approach would be to put in some sort of transaction syntax into LINQ, and have the compiler attempt to analyze the code and determine if any particular collection needed to be materialized.</span></span> <span data-ttu-id="f23f0-147">Jednak próby ustalenia całego kodu, który ma efekty uboczne jest niezwykle złożonych.</span><span class="sxs-lookup"><span data-stu-id="f23f0-147">However, attempting to determine all code that has side-effects is incredibly complex.</span></span> <span data-ttu-id="f23f0-148">Rozważmy następujący kod:</span><span class="sxs-lookup"><span data-stu-id="f23f0-148">Consider the following code:</span></span>  
  
```vb  
Dim z = _  
    From e In root.Elements() _  
    Where (TestSomeCondition(e)) _  
    Select DoMyProjection(e)  
```  
  
 <span data-ttu-id="f23f0-149">Taki kod analizy należy przeanalizować metod TestSomeCondition i DoMyProjection i wszystkie metody, które wywołuje tych metod, aby określić, jeśli kod ma efekty uboczne.</span><span class="sxs-lookup"><span data-stu-id="f23f0-149">Such analysis code would need to analyze the methods TestSomeCondition and DoMyProjection, and all methods that those methods called, to determine if any code had side-effects.</span></span> <span data-ttu-id="f23f0-150">Jednak kod analizy nie można po prostu szukał kodu, który ma efekty uboczne.</span><span class="sxs-lookup"><span data-stu-id="f23f0-150">But the analysis code could not just look for any code that had side-effects.</span></span> <span data-ttu-id="f23f0-151">Będzie konieczne wybierz tylko kod, który ma efekty uboczne na elementy podrzędne `root` w takiej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="f23f0-151">It would need to select for just the code that had side-effects on the child elements of `root` in this situation.</span></span>  
  
 <span data-ttu-id="f23f0-152">LINQ do XML nie próbuje wykonać takie analizy.</span><span class="sxs-lookup"><span data-stu-id="f23f0-152">LINQ to XML does not attempt to do any such analysis.</span></span>  
  
 <span data-ttu-id="f23f0-153">Jest od użytkownika, aby uniknąć tych problemów.</span><span class="sxs-lookup"><span data-stu-id="f23f0-153">It is up to you to avoid these problems.</span></span>  
  
## <a name="guidance"></a><span data-ttu-id="f23f0-154">Wskazówki</span><span class="sxs-lookup"><span data-stu-id="f23f0-154">Guidance</span></span>  
 <span data-ttu-id="f23f0-155">Najpierw niemieszanie deklaratywne i bezwzględne kodu.</span><span class="sxs-lookup"><span data-stu-id="f23f0-155">First, do not mix declarative and imperative code.</span></span>  
  
 <span data-ttu-id="f23f0-156">Nawet jeśli znasz dokładnie semantykę kolekcji i semantykę metod, które modyfikują drzewie XML podczas pisania niektórych inteligentne kod, który pozwala uniknąć problemów z tych kategorii kodu musi pozostać w przyszłości przez innych , a nie może być jako zwykły na problemy.</span><span class="sxs-lookup"><span data-stu-id="f23f0-156">Even if you know exactly the semantics of your collections and the semantics of the methods that modify the XML tree, if you write some clever code that avoids these categories of problems, your code will need to be maintained by other developers in the future, and they may not be as clear on the issues.</span></span> <span data-ttu-id="f23f0-157">Jeśli można mieszać deklaratywne i bezwzględne kodowania style, kod będzie bardziej łamliwa.</span><span class="sxs-lookup"><span data-stu-id="f23f0-157">If you mix declarative and imperative coding styles, your code will be more brittle.</span></span>  
  
 <span data-ttu-id="f23f0-158">Podczas pisania kodu, który zostaje kolekcję tak, aby uniknąć tych problemów, należy pamiętać, go z komentarzami zgodnie z potrzebami w kodzie, dzięki czemu programistów konserwacji zostanie zrozumieć problem.</span><span class="sxs-lookup"><span data-stu-id="f23f0-158">If you write code that materializes a collection so that these problems are avoided, note it with comments as appropriate in your code, so that maintenance programmers will understand the issue.</span></span>  
  
 <span data-ttu-id="f23f0-159">Po drugie Jeśli umożliwiają wydajności oraz inne kwestie, użyj tylko deklaratywne kodu.</span><span class="sxs-lookup"><span data-stu-id="f23f0-159">Second, if performance and other considerations allow, use only declarative code.</span></span> <span data-ttu-id="f23f0-160">Nie należy modyfikować swoje istniejące drzewo XML.</span><span class="sxs-lookup"><span data-stu-id="f23f0-160">Don't modify your existing XML tree.</span></span> <span data-ttu-id="f23f0-161">Wygenerować nowy.</span><span class="sxs-lookup"><span data-stu-id="f23f0-161">Generate a new one.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f23f0-162">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f23f0-162">See Also</span></span>  
 [<span data-ttu-id="f23f0-163">Zaawansowane LINQ do XML programowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f23f0-163">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

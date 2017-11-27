---
title: Mieszane usterki deklaratywne kodu Imperatywne kodu (LINQ do XML) (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 328a266d910e57dc089991ead5fe09a87e722688
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-c"></a><span data-ttu-id="1bd2b-102">Mieszane usterki kodu deklaratywne kodu/Imperatywne (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="1bd2b-102">Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="1bd2b-103">zawiera różne metody, dzięki którym można bezpośrednio modyfikować drzewo XML.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-103"> contains various methods that allow you to modify an XML tree directly.</span></span> <span data-ttu-id="1bd2b-104">Można dodawać elementów, usuń elementy, zmienić zawartość elementu, dodać atrybuty i itd.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-104">You can add elements, delete elements, change the contents of an element, add attributes, and so on.</span></span> <span data-ttu-id="1bd2b-105">Ten interfejs programowania jest opisany w [modyfikowanie drzew XML (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1bd2b-105">This programming interface is described in [Modifying XML Trees (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span></span> <span data-ttu-id="1bd2b-106">Jeśli użytkownik są iteracji w jednej osi, takie jak <xref:System.Xml.Linq.XContainer.Elements%2A>i modyfikujesz drzewa XML jako iterację osi, można na końcu niektóre dziwne usterki.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-106">If you are iterating through one of the axes, such as <xref:System.Xml.Linq.XContainer.Elements%2A>, and you are modifying the XML tree as you iterate through the axis, you can end up with some strange bugs.</span></span>  
  
 <span data-ttu-id="1bd2b-107">Ten problem jest czasami określany jako "Problemu Halloween".</span><span class="sxs-lookup"><span data-stu-id="1bd2b-107">This problem is sometimes known as "The Halloween Problem".</span></span>  
  
## <a name="definition-of-the-problem"></a><span data-ttu-id="1bd2b-108">Definicja problemu</span><span class="sxs-lookup"><span data-stu-id="1bd2b-108">Definition of the Problem</span></span>  
 <span data-ttu-id="1bd2b-109">Podczas pisania kodu za pomocą LINQ, który iteruje po kolekcji deklaratywne styl pisania kodu.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-109">When you write some code using LINQ that iterates through a collection, you are writing code in a declarative style.</span></span> <span data-ttu-id="1bd2b-110">Jest więcej podobnie opisujące *co* ma, a nie że *jak* chcesz pobrać go wykonać.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-110">It is more akin to describing *what* you want, rather that *how* you want to get it done.</span></span> <span data-ttu-id="1bd2b-111">Podczas pisania kodu, który 1) jest pierwszym elementem, testy 2) dla niektórych warunku 3) modyfikuje go i 4) umieszcza je z powrotem do listy, a następnie będzie to konieczne kodu.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-111">If you write code that 1) gets the first element, 2) tests it for some condition, 3) modifies it, and 4) puts it back into the list, then this would be imperative code.</span></span> <span data-ttu-id="1bd2b-112">Sprawi, że komputer *jak* zrobić, co ma gotowe.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-112">You are telling the computer *how* to do what you want done.</span></span>  
  
 <span data-ttu-id="1bd2b-113">Mieszanie te style kodu w tej samej operacji jest, co prowadzi do problemów.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-113">Mixing these styles of code in the same operation is what leads to problems.</span></span> <span data-ttu-id="1bd2b-114">Rozważ następujące opcje:</span><span class="sxs-lookup"><span data-stu-id="1bd2b-114">Consider the following:</span></span>  
  
 <span data-ttu-id="1bd2b-115">Załóżmy, że masz listy połączonej z trzema elementami w nim (, b i c):</span><span class="sxs-lookup"><span data-stu-id="1bd2b-115">Suppose you have a linked list with three items in it (a, b, and c):</span></span>  
  
 `a -> b -> c`  
  
 <span data-ttu-id="1bd2b-116">Załóżmy, że chcesz przenieść za pomocą listy połączonej, dodawania trzech nowych elementów (", b" i c').</span><span class="sxs-lookup"><span data-stu-id="1bd2b-116">Now, suppose that you want to move through the linked list, adding three new items (a', b', and c').</span></span> <span data-ttu-id="1bd2b-117">Ma wynikowej listy połączonej, aby wyglądały następująco:</span><span class="sxs-lookup"><span data-stu-id="1bd2b-117">You want the resulting linked list to look like this:</span></span>  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 <span data-ttu-id="1bd2b-118">Tak pisania kodu, który iteruje po za pośrednictwem listy, a każdy element dodaje nowe prawo elementu po nim.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-118">So you write code that iterates through the list, and for every item, adds a new item right after it.</span></span> <span data-ttu-id="1bd2b-119">Co się stanie, to najpierw zostanie wyświetlony kod `a` elementu i Wstaw `a'` po nim.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-119">What happens is that your code will first see the `a` element, and insert `a'` after it.</span></span> <span data-ttu-id="1bd2b-120">Teraz, kodu przechodzi do następnego węzła na liście, który jest obecnie `a'`!</span><span class="sxs-lookup"><span data-stu-id="1bd2b-120">Now, your code will move to the next node in the list, which is now `a'`!</span></span> <span data-ttu-id="1bd2b-121">Happily dodaje nowy element do listy, `a''`.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-121">It happily adds a new item to the list, `a''`.</span></span>  
  
 <span data-ttu-id="1bd2b-122">Jak będzie można rozwiązać ten problem w świecie rzeczywistym?</span><span class="sxs-lookup"><span data-stu-id="1bd2b-122">How would you solve this in the real world?</span></span> <span data-ttu-id="1bd2b-123">Utwórz kopię oryginalnej listy połączonej i Utwórz całkowicie nową listę.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-123">Well, you might make a copy of the original linked list, and create a completely new list.</span></span> <span data-ttu-id="1bd2b-124">Lub jeśli są pisanie kodu czysto konieczne może okazać się pierwszy element Dodaj nowy element, a następnie przejść dwa razy w listy połączonej, zaawansowane nad elementem, który właśnie został dodany.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-124">Or if you are writing purely imperative code, you might find the first item, add the new item, and then advance twice in the linked list, advancing over the element that you just added.</span></span>  
  
## <a name="adding-while-iterating"></a><span data-ttu-id="1bd2b-125">Dodawanie podczas iteracja</span><span class="sxs-lookup"><span data-stu-id="1bd2b-125">Adding While Iterating</span></span>  
 <span data-ttu-id="1bd2b-126">Na przykład załóżmy, że chcesz pisania kodu dla każdego elementu w drzewie chcesz utworzyć zduplikowany element:</span><span class="sxs-lookup"><span data-stu-id="1bd2b-126">For example, suppose you want to write some code that for every element in a tree, you want to create a duplicate element:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    root.Add(new XElement(e.Name, (string)e));  
```  
  
 <span data-ttu-id="1bd2b-127">Ten kod przechodzi w pętli nieskończonej.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-127">This code goes into an infinite loop.</span></span> <span data-ttu-id="1bd2b-128">`foreach` Iteruje po instrukcji `Elements()` osi, dodawanie nowych elementów do `doc` elementu.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-128">The `foreach` statement iterates through the `Elements()` axis, adding new elements to the `doc` element.</span></span> <span data-ttu-id="1bd2b-129">Kończy się ono również iteracja elementy, które go dodać.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-129">It ends up iterating also through the elements it just added.</span></span> <span data-ttu-id="1bd2b-130">I ponieważ przydzielania nowych obiektów z każdej iteracji pętli, po pewnym czasie zużyje całą dostępną pamięć.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-130">And because it allocates new objects with every iteration of the loop, it will eventually consume all available memory.</span></span>  
  
 <span data-ttu-id="1bd2b-131">Można rozwiązać ten problem przez ściąganie kolekcji do pamięci przy użyciu <xref:System.Linq.Enumerable.ToList%2A> operator standardowej kwerendy, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1bd2b-131">You can fix this problem by pulling the collection into memory using the <xref:System.Linq.Enumerable.ToList%2A> standard query operator, as follows:</span></span>  
  
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
  
 <span data-ttu-id="1bd2b-132">Teraz kod działa.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-132">Now the code works.</span></span> <span data-ttu-id="1bd2b-133">Wynikowe drzewo składni XML jest następująca:</span><span class="sxs-lookup"><span data-stu-id="1bd2b-133">The resulting XML tree is the following:</span></span>  
  
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
  
## <a name="deleting-while-iterating"></a><span data-ttu-id="1bd2b-134">Usuwanie podczas iteracja</span><span class="sxs-lookup"><span data-stu-id="1bd2b-134">Deleting While Iterating</span></span>  
 <span data-ttu-id="1bd2b-135">Jeśli chcesz usunąć wszystkie węzły na określonym poziomie, może się wydawać do pisania kodu podobne do poniższych:</span><span class="sxs-lookup"><span data-stu-id="1bd2b-135">If you want to delete all nodes at a certain level, you might be tempted to write code like the following:</span></span>  
  
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
  
 <span data-ttu-id="1bd2b-136">Jednak to nie chcesz.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-136">However, this does not do what you want.</span></span> <span data-ttu-id="1bd2b-137">Po usunięciu elementu pierwszy, A, w takiej sytuacji jest usuwany z drzewa XML zawarte w katalogu głównym, a kod w metodzie elementy obsługującym iteracja nie można odnaleźć następnego elementu.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-137">In this situation, after you have removed the first element, A, it is removed from the XML tree contained in root, and the code in the Elements method that is doing the iterating cannot find the next element.</span></span>  
  
 <span data-ttu-id="1bd2b-138">Poprzedni kod tworzy następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="1bd2b-138">The preceding code produces the following output:</span></span>  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 <span data-ttu-id="1bd2b-139">Rozwiązanie to ponownie wywołać <xref:System.Linq.Enumerable.ToList%2A> do zmaterializowania kolekcji, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1bd2b-139">The solution again is to call <xref:System.Linq.Enumerable.ToList%2A> to materialize the collection, as follows:</span></span>  
  
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
  
 <span data-ttu-id="1bd2b-140">Spowoduje to utworzenie następujących danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="1bd2b-140">This produces the following output:</span></span>  
  
```xml  
<Root />  
```  
  
 <span data-ttu-id="1bd2b-141">Alternatywnie można wyeliminować iteracji całkowicie przez wywołanie metody <xref:System.Xml.Linq.XElement.RemoveAll%2A> na element nadrzędny:</span><span class="sxs-lookup"><span data-stu-id="1bd2b-141">Alternatively, you can eliminate the iteration altogether by calling <xref:System.Xml.Linq.XElement.RemoveAll%2A> on the parent element:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
root.RemoveAll();  
Console.WriteLine(root);  
```  
  
## <a name="why-cant-linq-automatically-handle-this"></a><span data-ttu-id="1bd2b-142">Dlaczego nie LINQ automatycznie rozwiązać?</span><span class="sxs-lookup"><span data-stu-id="1bd2b-142">Why Can't LINQ Automatically Handle This?</span></span>  
 <span data-ttu-id="1bd2b-143">Jednym z podejść jest zawsze Przełącz wszystko do pamięci zamiast podczas oceny opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-143">One approach would be to always bring everything into memory instead of doing lazy evaluation.</span></span> <span data-ttu-id="1bd2b-144">Jednakże może być bardzo kosztowna pod względem wydajności i użycia pamięci.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-144">However, it would be very expensive in terms of performance and memory use.</span></span> <span data-ttu-id="1bd2b-145">W rzeczywistości gdyby LINQ i (LINQ do XML) o zastosowaniu takiego podejścia, spowoduje niepowodzenie w rzeczywistych sytuacji.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-145">In fact, if LINQ and (LINQ to XML) were to take this approach, it would fail in real-world situations.</span></span>  
  
 <span data-ttu-id="1bd2b-146">Innym rozwiązaniem możliwe będzie umieścić w jakieś składni transakcji do składnika LINQ i mieć kompilatora próba analiza kodu i określenia, czy żadnej określonej kolekcji jest wymagana można było zmaterializować.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-146">Another possible approach would be to put in some sort of transaction syntax into LINQ, and have the compiler attempt to analyze the code and determine if any particular collection needed to be materialized.</span></span> <span data-ttu-id="1bd2b-147">Jednak próby ustalenia całego kodu, który ma efekty uboczne jest niezwykle złożonych.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-147">However, attempting to determine all code that has side-effects is incredibly complex.</span></span> <span data-ttu-id="1bd2b-148">Rozważmy następujący kod:</span><span class="sxs-lookup"><span data-stu-id="1bd2b-148">Consider the following code:</span></span>  
  
```csharp  
var z =  
    from e in root.Elements()  
    where TestSomeCondition(e)  
    select DoMyProjection(e);  
```  
  
 <span data-ttu-id="1bd2b-149">Taki kod analizy należy przeanalizować metod TestSomeCondition i DoMyProjection i wszystkie metody, które wywołuje tych metod, aby określić, jeśli kod ma efekty uboczne.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-149">Such analysis code would need to analyze the methods TestSomeCondition and DoMyProjection, and all methods that those methods called, to determine if any code had side-effects.</span></span> <span data-ttu-id="1bd2b-150">Jednak kod analizy nie można po prostu szukał kodu, który ma efekty uboczne.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-150">But the analysis code could not just look for any code that had side-effects.</span></span> <span data-ttu-id="1bd2b-151">Będzie konieczne wybierz tylko kod, który ma efekty uboczne na elementy podrzędne `root` w takiej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-151">It would need to select for just the code that had side-effects on the child elements of `root` in this situation.</span></span>  
  
 <span data-ttu-id="1bd2b-152">LINQ do XML nie próbuje wykonać takie analizy.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-152">LINQ to XML does not attempt to do any such analysis.</span></span>  
  
 <span data-ttu-id="1bd2b-153">Jest od użytkownika, aby uniknąć tych problemów.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-153">It is up to you to avoid these problems.</span></span>  
  
## <a name="guidance"></a><span data-ttu-id="1bd2b-154">Wskazówki</span><span class="sxs-lookup"><span data-stu-id="1bd2b-154">Guidance</span></span>  
 <span data-ttu-id="1bd2b-155">Najpierw niemieszanie deklaratywne i bezwzględne kodu.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-155">First, do not mix declarative and imperative code.</span></span>  
  
 <span data-ttu-id="1bd2b-156">Nawet jeśli znasz dokładnie semantykę kolekcji i semantykę metod, które modyfikują drzewie XML podczas pisania niektórych inteligentne kod, który pozwala uniknąć problemów z tych kategorii kodu musi pozostać w przyszłości przez innych , a nie może być jako zwykły na problemy.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-156">Even if you know exactly the semantics of your collections and the semantics of the methods that modify the XML tree, if you write some clever code that avoids these categories of problems, your code will need to be maintained by other developers in the future, and they may not be as clear on the issues.</span></span> <span data-ttu-id="1bd2b-157">Jeśli można mieszać deklaratywne i bezwzględne kodowania style, kod będzie bardziej łamliwa.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-157">If you mix declarative and imperative coding styles, your code will be more brittle.</span></span>  
  
 <span data-ttu-id="1bd2b-158">Podczas pisania kodu, który zostaje kolekcję tak, aby uniknąć tych problemów, należy pamiętać, go z komentarzami zgodnie z potrzebami w kodzie, dzięki czemu programistów konserwacji zostanie zrozumieć problem.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-158">If you write code that materializes a collection so that these problems are avoided, note it with comments as appropriate in your code, so that maintenance programmers will understand the issue.</span></span>  
  
 <span data-ttu-id="1bd2b-159">Po drugie Jeśli umożliwiają wydajności oraz inne kwestie, użyj tylko deklaratywne kodu.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-159">Second, if performance and other considerations allow, use only declarative code.</span></span> <span data-ttu-id="1bd2b-160">Nie należy modyfikować swoje istniejące drzewo XML.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-160">Don't modify your existing XML tree.</span></span> <span data-ttu-id="1bd2b-161">Wygenerować nowy.</span><span class="sxs-lookup"><span data-stu-id="1bd2b-161">Generate a new one.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1bd2b-162">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1bd2b-162">See Also</span></span>  
 [<span data-ttu-id="1bd2b-163">Zaawansowane LINQ do XML programowania (C#)</span><span class="sxs-lookup"><span data-stu-id="1bd2b-163">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

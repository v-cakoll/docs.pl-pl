---
title: Finalizatory (C# przewodnik programowania w języku)
ms.date: 05/10/2017
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: fc15818883736015419f8599d482185bbab5120a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33313969"
---
# <a name="finalizers-c-programming-guide"></a><span data-ttu-id="1df03-102">Finalizatory (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="1df03-102">Finalizers (C# Programming Guide)</span></span>
<span data-ttu-id="1df03-103">Finalizatory są używane do destruct wystąpień klas.</span><span class="sxs-lookup"><span data-stu-id="1df03-103">Finalizers are used to destruct instances of classes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1df03-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1df03-104">Remarks</span></span>  
  
-   <span data-ttu-id="1df03-105">Finalizatory nie może być zdefiniowana w strukturach.</span><span class="sxs-lookup"><span data-stu-id="1df03-105">Finalizers cannot be defined in structs.</span></span> <span data-ttu-id="1df03-106">Są one używane tylko z klasami.</span><span class="sxs-lookup"><span data-stu-id="1df03-106">They are only used with classes.</span></span>  
  
-   <span data-ttu-id="1df03-107">Klasa może zawierać tylko jeden finalizatora.</span><span class="sxs-lookup"><span data-stu-id="1df03-107">A class can only have one finalizer.</span></span>  
  
-   <span data-ttu-id="1df03-108">Finalizatory nie może być dziedziczona ani przeciążony.</span><span class="sxs-lookup"><span data-stu-id="1df03-108">Finalizers cannot be inherited or overloaded.</span></span>  
  
-   <span data-ttu-id="1df03-109">Nie można wywoływać finalizatory.</span><span class="sxs-lookup"><span data-stu-id="1df03-109">Finalizers cannot be called.</span></span> <span data-ttu-id="1df03-110">Są wywoływane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="1df03-110">They are invoked automatically.</span></span>  
  
-   <span data-ttu-id="1df03-111">Finalizator podjąć Modyfikatory lub nie ma parametrów.</span><span class="sxs-lookup"><span data-stu-id="1df03-111">A finalizer does not take modifiers or have parameters.</span></span>  
  
 <span data-ttu-id="1df03-112">Na przykład poniżej przedstawiono deklaracji finalizatora dla `Car` klasy.</span><span class="sxs-lookup"><span data-stu-id="1df03-112">For example, the following is a declaration of a finalizer for the `Car` class.</span></span>
  
 [!code-csharp[csProgGuideObjects#86](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_1.cs)]  

<span data-ttu-id="1df03-113">Finalizator może być wykonany również jako definicja treść wyrażenia, jak przedstawiono na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1df03-113">A finalizer can also be implemented as an expression body definition, as the following example shows.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 <span data-ttu-id="1df03-114">Finalizator niejawnie wywołuje <xref:System.Object.Finalize%2A> dla klasy podstawowej obiektu.</span><span class="sxs-lookup"><span data-stu-id="1df03-114">The finalizer implicitly calls <xref:System.Object.Finalize%2A> on the base class of the object.</span></span> <span data-ttu-id="1df03-115">W związku z tym wywołaniu finalizator jest niejawnie przekonwertowana na następujący kod:</span><span class="sxs-lookup"><span data-stu-id="1df03-115">Therefore, a call to a finalizer is implicitly translated to the following code:</span></span>  
  
```csharp  
protected override void Finalize()  
{  
    try  
    {  
        // Cleanup statements...  
    }  
    finally  
    {  
        base.Finalize();  
    }  
}  
```  
  
 <span data-ttu-id="1df03-116">Oznacza to, że `Finalize` metoda jest wywoływana rekursywnie dla wszystkich wystąpień w łańcuch dziedziczenia z większość opartych na najmniejszą pochodny.</span><span class="sxs-lookup"><span data-stu-id="1df03-116">This means that the `Finalize` method is called recursively for all instances in the inheritance chain, from the most-derived to the least-derived.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1df03-117">Nie należy używać puste finalizatory.</span><span class="sxs-lookup"><span data-stu-id="1df03-117">Empty finalizers should not be used.</span></span> <span data-ttu-id="1df03-118">Jeśli klasa zawiera finalizator, wpis jest tworzony w `Finalize` kolejki.</span><span class="sxs-lookup"><span data-stu-id="1df03-118">When a class contains a finalizer, an entry is created in the `Finalize` queue.</span></span> <span data-ttu-id="1df03-119">Po wywołaniu finalizator moduł garbage collector jest wywoływane w celu przetworzenia kolejki.</span><span class="sxs-lookup"><span data-stu-id="1df03-119">When the finalizer is called, the garbage collector is invoked to process the queue.</span></span> <span data-ttu-id="1df03-120">Pusty finalizator tylko powoduje, że zbędne spadek wydajności.</span><span class="sxs-lookup"><span data-stu-id="1df03-120">An empty finalizer just causes a needless loss of performance.</span></span>  
  
 <span data-ttu-id="1df03-121">Programista nie ma kontroli nad, gdy jest wywoływana finalizator, ponieważ jest to określane przez moduł garbage collector.</span><span class="sxs-lookup"><span data-stu-id="1df03-121">The programmer has no control over when the finalizer is called because this is determined by the garbage collector.</span></span> <span data-ttu-id="1df03-122">Moduł zbierający elementy bezużyteczne sprawdza, czy obiekty, które są już używane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="1df03-122">The garbage collector checks for objects that are no longer being used by the application.</span></span> <span data-ttu-id="1df03-123">Jeśli obiekt uzna uprawnia do skorzystania z finalizacji, wywołuje finalizatora (jeśli istnieje) i zwraca pamięć używana do przechowywania obiektu.</span><span class="sxs-lookup"><span data-stu-id="1df03-123">If it considers an object eligible for finalization, it calls the finalizer (if any) and reclaims the memory used to store the object.</span></span> <span data-ttu-id="1df03-124">Finalizatory są również nazywane, gdy program jest kończona.</span><span class="sxs-lookup"><span data-stu-id="1df03-124">Finalizers are also called when the program exits.</span></span>  
  
 <span data-ttu-id="1df03-125">Można wymusić wyrzucanie elementów bezużytecznych przez wywołanie metody <xref:System.GC.Collect%2A>, ale w większości przypadków, to należy unikać, ponieważ może spowodować problemy z wydajnością.</span><span class="sxs-lookup"><span data-stu-id="1df03-125">It is possible to force garbage collection by calling <xref:System.GC.Collect%2A>, but most of the time, this should be avoided because it may create performance issues.</span></span>  
  
## <a name="using-finalizers-to-release-resources"></a><span data-ttu-id="1df03-126">Przy użyciu finalizatory do zwolnienia zasobów</span><span class="sxs-lookup"><span data-stu-id="1df03-126">Using Finalizers to Release Resources</span></span>  
 <span data-ttu-id="1df03-127">Ogólnie rzecz biorąc C# nie wymaga tyle zarządzania pamięcią, ile potrzeba podczas pracy z językiem, który nie ma środowiska wykonawczego o wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="1df03-127">In general, C# does not require as much memory management as is needed when you develop with a language that does not target a runtime with garbage collection.</span></span> <span data-ttu-id="1df03-128">Jest to spowodowane modułu zbierającego elementy bezużyteczne .NET Framework niejawnie zarządza alokacji i wersji pamięci dla obiektów.</span><span class="sxs-lookup"><span data-stu-id="1df03-128">This is because the .NET Framework garbage collector implicitly manages the allocation and release of memory for your objects.</span></span> <span data-ttu-id="1df03-129">Jednak gdy aplikacja hermetyzuje niezarządzane zasoby, takie jak windows, plików i połączenia sieciowe, należy używać finalizatory aby zwolnić zasoby.</span><span class="sxs-lookup"><span data-stu-id="1df03-129">However, when your application encapsulates unmanaged resources such as windows, files, and network connections, you should use finalizers to free those resources.</span></span> <span data-ttu-id="1df03-130">Gdy obiekt jest uprawniona do finalizacji, moduł zbierający elementy bezużyteczne uruchamia `Finalize` metody obiektu.</span><span class="sxs-lookup"><span data-stu-id="1df03-130">When the object is eligible for finalization, the garbage collector runs the `Finalize` method of the object.</span></span>  
  
## <a name="explicit-release-of-resources"></a><span data-ttu-id="1df03-131">Jawnego zwolnienia zasobów</span><span class="sxs-lookup"><span data-stu-id="1df03-131">Explicit Release of Resources</span></span>  
 <span data-ttu-id="1df03-132">Jeśli aplikacja używa kosztowne zewnętrzny zasób, zalecamy również musisz zapewnić sposób jawnego zwolnienia zasobu przed moduł garbage collector zwolnienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="1df03-132">If your application is using an expensive external resource, we also recommend that you provide a way to explicitly release the resource before the garbage collector frees the object.</span></span> <span data-ttu-id="1df03-133">Aby to zrobić, implementacja `Dispose` metody z <xref:System.IDisposable> interfejsu, który wykonuje cleanup konieczne dla obiekt.</span><span class="sxs-lookup"><span data-stu-id="1df03-133">You do this by implementing a `Dispose` method from the <xref:System.IDisposable> interface that performs the necessary cleanup for the object.</span></span> <span data-ttu-id="1df03-134">Może to znacznie zwiększyć wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1df03-134">This can considerably improve the performance of the application.</span></span> <span data-ttu-id="1df03-135">Nawet w przypadku tego jawną kontrolę zasobów finalizator staje się zabezpieczenia, aby wyczyścić zasoby, jeśli wywołanie `Dispose` metody nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="1df03-135">Even with this explicit control over resources, the finalizer becomes a safeguard to clean up resources if the call to the `Dispose` method failed.</span></span>  
  
 <span data-ttu-id="1df03-136">Aby uzyskać więcej informacji na temat Oczyszczanie zasobów zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="1df03-136">For more details about cleaning up resources, see the following topics:</span></span>  
  
-   [<span data-ttu-id="1df03-137">Oczyszczanie zasobów niezarządzanych</span><span class="sxs-lookup"><span data-stu-id="1df03-137">Cleaning Up Unmanaged Resources</span></span>](../../../standard/garbage-collection/unmanaged.md)  
  
-   [<span data-ttu-id="1df03-138">Implementacja metody Dispose</span><span class="sxs-lookup"><span data-stu-id="1df03-138">Implementing a Dispose Method</span></span>](../../../standard/garbage-collection/implementing-dispose.md)  
  
-   [<span data-ttu-id="1df03-139">using, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1df03-139">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)  
  
## <a name="example"></a><span data-ttu-id="1df03-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="1df03-140">Example</span></span>  
 <span data-ttu-id="1df03-141">Poniższy przykład tworzy trzech klas, które łańcuch dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="1df03-141">The following example creates three classes that make a chain of inheritance.</span></span> <span data-ttu-id="1df03-142">Klasa `First` jest klasą bazową `Second` jest pochodną `First`, i `Third` jest pochodną `Second`.</span><span class="sxs-lookup"><span data-stu-id="1df03-142">The class `First` is the base class, `Second` is derived from `First`, and `Third` is derived from `Second`.</span></span> <span data-ttu-id="1df03-143">Wszystkie trzy ma finalizatory.</span><span class="sxs-lookup"><span data-stu-id="1df03-143">All three have finalizers.</span></span> <span data-ttu-id="1df03-144">W `Main`, tworzone jest wystąpienie klasy pochodnej większość.</span><span class="sxs-lookup"><span data-stu-id="1df03-144">In `Main`, an instance of the most-derived class is created.</span></span> <span data-ttu-id="1df03-145">Po uruchomieniu tego programu, zwróć uwagę, że finalizatory dla trzech klas zostaną wywołane automatycznie i w kolejności, większość opartych na najmniejszą pochodny.</span><span class="sxs-lookup"><span data-stu-id="1df03-145">When the program runs, notice that the finalizers for the three classes are called automatically, and in order, from the most-derived to the least-derived.</span></span>  
  
 [!code-csharp[csProgGuideObjects#85](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="1df03-146">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1df03-146">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1df03-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1df03-147">See Also</span></span>  
 <xref:System.IDisposable>  
 [<span data-ttu-id="1df03-148">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1df03-148">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1df03-149">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="1df03-149">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [<span data-ttu-id="1df03-150">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="1df03-150">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)

---
title: Finalizatory — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: 9936d56582afd160bf3464d18efd3acf47c7af60
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924496"
---
# <a name="finalizers-c-programming-guide"></a><span data-ttu-id="c9173-102">Finalizatory (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="c9173-102">Finalizers (C# Programming Guide)</span></span>
<span data-ttu-id="c9173-103">Finalizatory (nazywane również destruktorami) służą do wykonywania wszelkich niezbędnych ostatecznych oczyszczeniów, gdy wystąpienie klasy jest zbierane przez moduł wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c9173-103">Finalizers (which are also called **destructors**) are used to perform any necessary final clean-up when a class instance is being collected by the garbage collector.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9173-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c9173-104">Remarks</span></span>  
  
- <span data-ttu-id="c9173-105">Finalizatory nie mogą być zdefiniowane w strukturach.</span><span class="sxs-lookup"><span data-stu-id="c9173-105">Finalizers cannot be defined in structs.</span></span> <span data-ttu-id="c9173-106">Są one używane tylko z klasami.</span><span class="sxs-lookup"><span data-stu-id="c9173-106">They are only used with classes.</span></span>  
  
- <span data-ttu-id="c9173-107">Klasa może mieć tylko jeden finalizator.</span><span class="sxs-lookup"><span data-stu-id="c9173-107">A class can only have one finalizer.</span></span>  
  
- <span data-ttu-id="c9173-108">Finalizatory nie mogą być dziedziczone ani przeciążone.</span><span class="sxs-lookup"><span data-stu-id="c9173-108">Finalizers cannot be inherited or overloaded.</span></span>  
  
- <span data-ttu-id="c9173-109">Nie można wywołać finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="c9173-109">Finalizers cannot be called.</span></span> <span data-ttu-id="c9173-110">Są one wywoływane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="c9173-110">They are invoked automatically.</span></span>  
  
- <span data-ttu-id="c9173-111">Finalizator nie przyjmuje modyfikatorów ani nie ma parametrów.</span><span class="sxs-lookup"><span data-stu-id="c9173-111">A finalizer does not take modifiers or have parameters.</span></span>  
  
 <span data-ttu-id="c9173-112">Na przykład poniżej znajduje się deklaracja finalizatora dla `Car` klasy.</span><span class="sxs-lookup"><span data-stu-id="c9173-112">For example, the following is a declaration of a finalizer for the `Car` class.</span></span>
  
 [!code-csharp[csProgGuideObjects#86](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#86)]  

<span data-ttu-id="c9173-113">Finalizator może być również zaimplementowany jako definicja treści wyrażenia, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c9173-113">A finalizer can also be implemented as an expression body definition, as the following example shows.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 <span data-ttu-id="c9173-114">Finalizator niejawnie wywołuje <xref:System.Object.Finalize%2A> klasę bazową obiektu.</span><span class="sxs-lookup"><span data-stu-id="c9173-114">The finalizer implicitly calls <xref:System.Object.Finalize%2A> on the base class of the object.</span></span> <span data-ttu-id="c9173-115">W związku z tym wywołanie finalizatora jest niejawnie tłumaczone na następujący kod:</span><span class="sxs-lookup"><span data-stu-id="c9173-115">Therefore, a call to a finalizer is implicitly translated to the following code:</span></span>  
  
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
  
 <span data-ttu-id="c9173-116">Oznacza to, że `Finalize` Metoda jest wywoływana cyklicznie dla wszystkich wystąpień w łańcuchu dziedziczenia, od najbardziej pochodnego do najmniej pochodnego.</span><span class="sxs-lookup"><span data-stu-id="c9173-116">This means that the `Finalize` method is called recursively for all instances in the inheritance chain, from the most-derived to the least-derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c9173-117">Nie należy używać pustych finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="c9173-117">Empty finalizers should not be used.</span></span> <span data-ttu-id="c9173-118">Gdy Klasa zawiera finalizator, w `Finalize` kolejce zostaje utworzony wpis.</span><span class="sxs-lookup"><span data-stu-id="c9173-118">When a class contains a finalizer, an entry is created in the `Finalize` queue.</span></span> <span data-ttu-id="c9173-119">Gdy finalizator jest wywoływany, Moduł wyrzucania elementów bezużytecznych jest wywoływany w celu przetworzenia kolejki.</span><span class="sxs-lookup"><span data-stu-id="c9173-119">When the finalizer is called, the garbage collector is invoked to process the queue.</span></span> <span data-ttu-id="c9173-120">Pusty finalizator powoduje jedynie niepotrzebną utratę wydajności.</span><span class="sxs-lookup"><span data-stu-id="c9173-120">An empty finalizer just causes a needless loss of performance.</span></span>  
  
 <span data-ttu-id="c9173-121">Programista nie ma kontroli nad tym, gdy finalizator jest wywoływany, ponieważ jest określany przez moduł wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c9173-121">The programmer has no control over when the finalizer is called because this is determined by the garbage collector.</span></span> <span data-ttu-id="c9173-122">Moduł wyrzucania elementów bezużytecznych sprawdza obiekty, które nie są już używane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="c9173-122">The garbage collector checks for objects that are no longer being used by the application.</span></span> <span data-ttu-id="c9173-123">Jeśli uzna, że obiekt kwalifikuje się do finalizacji, wywołuje finalizator (jeśli istnieje) i ponownie przejmuje pamięć używaną do przechowywania obiektu.</span><span class="sxs-lookup"><span data-stu-id="c9173-123">If it considers an object eligible for finalization, it calls the finalizer (if any) and reclaims the memory used to store the object.</span></span> 
 
 <span data-ttu-id="c9173-124">W aplikacjach .NET Framework (ale nie w aplikacjach .NET Core) finalizatory są również wywoływane po zakończeniu działania programu.</span><span class="sxs-lookup"><span data-stu-id="c9173-124">In .NET Framework applications (but not in .NET Core applications), finalizers are also called when the program exits.</span></span> 
  
 <span data-ttu-id="c9173-125">Istnieje możliwość wymuszenia wyrzucania elementów <xref:System.GC.Collect%2A>bezużytecznych przez wywoływanie, ale większość czasu, należy to uniknąć, ponieważ może to spowodować problemy z wydajnością.</span><span class="sxs-lookup"><span data-stu-id="c9173-125">It is possible to force garbage collection by calling <xref:System.GC.Collect%2A>, but most of the time, this should be avoided because it may create performance issues.</span></span>  
  
## <a name="using-finalizers-to-release-resources"></a><span data-ttu-id="c9173-126">Korzystanie z finalizatorów do zwolnienia zasobów</span><span class="sxs-lookup"><span data-stu-id="c9173-126">Using finalizers to release resources</span></span>  
 <span data-ttu-id="c9173-127">Ogólnie rzecz biorąc C# , nie wymaga tak dużo zarządzania pamięcią, ile jest potrzebne podczas tworzenia w języku, który nie jest przeznaczony dla środowiska uruchomieniowego z odzyskiwaniem pamięci.</span><span class="sxs-lookup"><span data-stu-id="c9173-127">In general, C# does not require as much memory management as is needed when you develop with a language that does not target a runtime with garbage collection.</span></span> <span data-ttu-id="c9173-128">Dzieje się tak, ponieważ .NET Framework Moduł wyrzucania elementów bezużytecznych niejawnie zarządza alokacją i ilością pamięci dla obiektów.</span><span class="sxs-lookup"><span data-stu-id="c9173-128">This is because the .NET Framework garbage collector implicitly manages the allocation and release of memory for your objects.</span></span> <span data-ttu-id="c9173-129">Jeśli jednak aplikacja hermetyzuje niezarządzane zasoby, takie jak Windows, pliki i połączenia sieciowe, należy używać finalizatorów do zwolnienia tych zasobów.</span><span class="sxs-lookup"><span data-stu-id="c9173-129">However, when your application encapsulates unmanaged resources such as windows, files, and network connections, you should use finalizers to free those resources.</span></span> <span data-ttu-id="c9173-130">Gdy obiekt kwalifikuje się do finalizacji, Moduł wyrzucania elementów `Finalize` bezużytecznych uruchamia metodę obiektu.</span><span class="sxs-lookup"><span data-stu-id="c9173-130">When the object is eligible for finalization, the garbage collector runs the `Finalize` method of the object.</span></span>  
  
## <a name="explicit-release-of-resources"></a><span data-ttu-id="c9173-131">Jawne wydanie zasobów</span><span class="sxs-lookup"><span data-stu-id="c9173-131">Explicit release of resources</span></span>  
 <span data-ttu-id="c9173-132">Jeśli aplikacja korzysta z kosztownych zasobów zewnętrznych, zalecamy również zapewnienie jawnie zwolnienia zasobu, zanim moduł wyrzucania elementów bezużytecznych zwolni obiekt.</span><span class="sxs-lookup"><span data-stu-id="c9173-132">If your application is using an expensive external resource, we also recommend that you provide a way to explicitly release the resource before the garbage collector frees the object.</span></span> <span data-ttu-id="c9173-133">Można to zrobić przez zaimplementowanie `Dispose` metody <xref:System.IDisposable> z interfejsu, który wykonuje niezbędne czyszczenie dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="c9173-133">You do this by implementing a `Dispose` method from the <xref:System.IDisposable> interface that performs the necessary cleanup for the object.</span></span> <span data-ttu-id="c9173-134">Może to znacząco poprawić wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c9173-134">This can considerably improve the performance of the application.</span></span> <span data-ttu-id="c9173-135">Nawet w przypadku tej jawnej kontroli nad zasobami finalizator jest środkiem do czyszczenia zasobów, jeśli wywołanie `Dispose` metody nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="c9173-135">Even with this explicit control over resources, the finalizer becomes a safeguard to clean up resources if the call to the `Dispose` method failed.</span></span>  
  
 <span data-ttu-id="c9173-136">Więcej informacji o czyszczeniu zasobów znajduje się w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="c9173-136">For more details about cleaning up resources, see the following topics:</span></span>  
  
- [<span data-ttu-id="c9173-137">Oczyszczanie zasobów niezarządzanych</span><span class="sxs-lookup"><span data-stu-id="c9173-137">Cleaning Up Unmanaged Resources</span></span>](../../../standard/garbage-collection/unmanaged.md)  
  
- [<span data-ttu-id="c9173-138">Implementacja metody Dispose</span><span class="sxs-lookup"><span data-stu-id="c9173-138">Implementing a Dispose Method</span></span>](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [<span data-ttu-id="c9173-139">using, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c9173-139">using Statement</span></span>](../../language-reference/keywords/using-statement.md)  
  
## <a name="example"></a><span data-ttu-id="c9173-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="c9173-140">Example</span></span>  
 <span data-ttu-id="c9173-141">Poniższy przykład tworzy trzy klasy, które tworzą łańcuch dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="c9173-141">The following example creates three classes that make a chain of inheritance.</span></span> <span data-ttu-id="c9173-142">Klasa `First` jest klasą bazową, `Second` pochodzi od `First`, i `Third` pochodzi od `Second`.</span><span class="sxs-lookup"><span data-stu-id="c9173-142">The class `First` is the base class, `Second` is derived from `First`, and `Third` is derived from `Second`.</span></span> <span data-ttu-id="c9173-143">Wszystkie trzy mają finalizatory.</span><span class="sxs-lookup"><span data-stu-id="c9173-143">All three have finalizers.</span></span> <span data-ttu-id="c9173-144">W `Main`programie tworzone jest wystąpienie klasy najczęściej pochodnej.</span><span class="sxs-lookup"><span data-stu-id="c9173-144">In `Main`, an instance of the most-derived class is created.</span></span> <span data-ttu-id="c9173-145">Po uruchomieniu programu należy zauważyć, że finalizatory dla trzech klas są wywoływane automatycznie i w kolejności, od najbardziej pochodnego do najmniej pochodnego.</span><span class="sxs-lookup"><span data-stu-id="c9173-145">When the program runs, notice that the finalizers for the three classes are called automatically, and in order, from the most-derived to the least-derived.</span></span>  
  
 [!code-csharp[csProgGuideObjects#85](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#85)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="c9173-146">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c9173-146">C# language specification</span></span>  

<span data-ttu-id="c9173-147">Aby uzyskać więcej informacji, zobacz [](~/_csharplang/spec/classes.md#destructors) sekcję destruktory [ C# specyfikacji języka](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="c9173-147">For more information, see the [Destructors](~/_csharplang/spec/classes.md#destructors) section of the [C# language specification](../../language-reference/language-specification/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c9173-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c9173-148">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="c9173-149">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c9173-149">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c9173-150">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="c9173-150">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="c9173-151">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="c9173-151">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)

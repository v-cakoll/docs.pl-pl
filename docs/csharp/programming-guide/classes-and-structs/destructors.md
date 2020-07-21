---
title: Finalizatory — Przewodnik programowania w języku C#
description: Finalizatory w języku C#, które są nazywane destruktorami, wykonują wszelkie niezbędne końcowe czyszczenie, gdy wystąpienie klasy jest zbierane przez moduł wyrzucania elementów bezużytecznych.
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: 392b69633e596f0682fdfb4a5875f46755203ff7
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474894"
---
# <a name="finalizers-c-programming-guide"></a><span data-ttu-id="68aae-103">Finalizatory (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="68aae-103">Finalizers (C# Programming Guide)</span></span>
<span data-ttu-id="68aae-104">Finalizatory (nazywane również **destruktorami**) służą do wykonywania wszelkich niezbędnych ostatecznych oczyszczeniów, gdy wystąpienie klasy jest zbierane przez moduł wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="68aae-104">Finalizers (which are also called **destructors**) are used to perform any necessary final clean-up when a class instance is being collected by the garbage collector.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68aae-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="68aae-105">Remarks</span></span>  
  
- <span data-ttu-id="68aae-106">Finalizatory nie mogą być zdefiniowane w strukturach.</span><span class="sxs-lookup"><span data-stu-id="68aae-106">Finalizers cannot be defined in structs.</span></span> <span data-ttu-id="68aae-107">Są one używane tylko z klasami.</span><span class="sxs-lookup"><span data-stu-id="68aae-107">They are only used with classes.</span></span>  
  
- <span data-ttu-id="68aae-108">Klasa może mieć tylko jeden finalizator.</span><span class="sxs-lookup"><span data-stu-id="68aae-108">A class can only have one finalizer.</span></span>  
  
- <span data-ttu-id="68aae-109">Finalizatory nie mogą być dziedziczone ani przeciążone.</span><span class="sxs-lookup"><span data-stu-id="68aae-109">Finalizers cannot be inherited or overloaded.</span></span>  
  
- <span data-ttu-id="68aae-110">Nie można wywołać finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="68aae-110">Finalizers cannot be called.</span></span> <span data-ttu-id="68aae-111">Są one wywoływane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="68aae-111">They are invoked automatically.</span></span>  
  
- <span data-ttu-id="68aae-112">Finalizator nie przyjmuje modyfikatorów ani nie ma parametrów.</span><span class="sxs-lookup"><span data-stu-id="68aae-112">A finalizer does not take modifiers or have parameters.</span></span>  
  
 <span data-ttu-id="68aae-113">Na przykład poniżej znajduje się deklaracja finalizatora dla `Car` klasy.</span><span class="sxs-lookup"><span data-stu-id="68aae-113">For example, the following is a declaration of a finalizer for the `Car` class.</span></span>
  
 [!code-csharp[csProgGuideObjects#86](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#86)]  

<span data-ttu-id="68aae-114">Finalizator może być również zaimplementowany jako definicja treści wyrażenia, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="68aae-114">A finalizer can also be implemented as an expression body definition, as the following example shows.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 <span data-ttu-id="68aae-115">Finalizator niejawnie wywołuje <xref:System.Object.Finalize%2A> klasę bazową obiektu.</span><span class="sxs-lookup"><span data-stu-id="68aae-115">The finalizer implicitly calls <xref:System.Object.Finalize%2A> on the base class of the object.</span></span> <span data-ttu-id="68aae-116">W związku z tym wywołanie finalizatora jest niejawnie tłumaczone na następujący kod:</span><span class="sxs-lookup"><span data-stu-id="68aae-116">Therefore, a call to a finalizer is implicitly translated to the following code:</span></span>  
  
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
  
 <span data-ttu-id="68aae-117">Ten projekt oznacza, że `Finalize` Metoda jest wywoływana cyklicznie dla wszystkich wystąpień w łańcuchu dziedziczenia, od najbardziej pochodnego do najmniej pochodnego.</span><span class="sxs-lookup"><span data-stu-id="68aae-117">This design means that the `Finalize` method is called recursively for all instances in the inheritance chain, from the most-derived to the least-derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="68aae-118">Nie należy używać pustych finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="68aae-118">Empty finalizers should not be used.</span></span> <span data-ttu-id="68aae-119">Gdy Klasa zawiera finalizator, w kolejce zostaje utworzony wpis `Finalize` .</span><span class="sxs-lookup"><span data-stu-id="68aae-119">When a class contains a finalizer, an entry is created in the `Finalize` queue.</span></span> <span data-ttu-id="68aae-120">Gdy finalizator jest wywoływany, Moduł wyrzucania elementów bezużytecznych jest wywoływany w celu przetworzenia kolejki.</span><span class="sxs-lookup"><span data-stu-id="68aae-120">When the finalizer is called, the garbage collector is invoked to process the queue.</span></span> <span data-ttu-id="68aae-121">Pusty finalizator powoduje jedynie niepotrzebną utratę wydajności.</span><span class="sxs-lookup"><span data-stu-id="68aae-121">An empty finalizer just causes a needless loss of performance.</span></span>  
  
 <span data-ttu-id="68aae-122">Programista nie ma kontroli nad tym, kiedy finalizator jest wywoływany; Moduł zbierający elementy bezużyteczne decyduje o tym, kiedy ma być wywoływana.</span><span class="sxs-lookup"><span data-stu-id="68aae-122">The programmer has no control over when the finalizer is called; the garbage collector decides when to call it.</span></span> <span data-ttu-id="68aae-123">Moduł wyrzucania elementów bezużytecznych sprawdza obiekty, które nie są już używane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="68aae-123">The garbage collector checks for objects that are no longer being used by the application.</span></span> <span data-ttu-id="68aae-124">Jeśli uzna, że obiekt kwalifikuje się do finalizacji, wywołuje finalizator (jeśli istnieje) i ponownie przejmuje pamięć używaną do przechowywania obiektu.</span><span class="sxs-lookup"><span data-stu-id="68aae-124">If it considers an object eligible for finalization, it calls the finalizer (if any) and reclaims the memory used to store the object.</span></span>

 <span data-ttu-id="68aae-125">W aplikacjach .NET Framework (ale nie w aplikacjach .NET Core) finalizatory są również wywoływane po zakończeniu działania programu.</span><span class="sxs-lookup"><span data-stu-id="68aae-125">In .NET Framework applications (but not in .NET Core applications), finalizers are also called when the program exits.</span></span>
  
 <span data-ttu-id="68aae-126">Istnieje możliwość wymuszenia wyrzucania elementów bezużytecznych przez wywołanie <xref:System.GC.Collect%2A> , ale większość czasu, należy unikać tego wywołania, ponieważ może to spowodować problemy z wydajnością.</span><span class="sxs-lookup"><span data-stu-id="68aae-126">It's possible to force garbage collection by calling <xref:System.GC.Collect%2A>, but most of the time, this call should be avoided because it may create performance issues.</span></span>  
  
## <a name="using-finalizers-to-release-resources"></a><span data-ttu-id="68aae-127">Korzystanie z finalizatorów do zwolnienia zasobów</span><span class="sxs-lookup"><span data-stu-id="68aae-127">Using finalizers to release resources</span></span>  
 <span data-ttu-id="68aae-128">Ogólnie rzecz biorąc, język C# nie wymaga jak dużo zarządzania pamięcią w ramach dewelopera jako języków, które nie są przeznaczone do środowiska uruchomieniowego z wyrzucaniem elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="68aae-128">In general, C# does not require as much memory management on the part of the developer as languages that don't target a runtime with garbage collection.</span></span> <span data-ttu-id="68aae-129">Dzieje się tak, ponieważ moduł wyrzucania elementów bezużytecznych platformy .NET niejawnie zarządza alokacją i ilością pamięci dla obiektów.</span><span class="sxs-lookup"><span data-stu-id="68aae-129">This is because the .NET garbage collector implicitly manages the allocation and release of memory for your objects.</span></span> <span data-ttu-id="68aae-130">Jeśli jednak aplikacja hermetyzuje niezarządzane zasoby, takie jak Windows, pliki i połączenia sieciowe, należy użyć finalizatorów do zwolnienia tych zasobów.</span><span class="sxs-lookup"><span data-stu-id="68aae-130">However, when your application encapsulates unmanaged resources, such as windows, files, and network connections, you should use finalizers to free those resources.</span></span> <span data-ttu-id="68aae-131">Gdy obiekt kwalifikuje się do finalizacji, Moduł wyrzucania elementów bezużytecznych uruchamia `Finalize` metodę obiektu.</span><span class="sxs-lookup"><span data-stu-id="68aae-131">When the object is eligible for finalization, the garbage collector runs the `Finalize` method of the object.</span></span>
  
## <a name="explicit-release-of-resources"></a><span data-ttu-id="68aae-132">Jawne wydanie zasobów</span><span class="sxs-lookup"><span data-stu-id="68aae-132">Explicit release of resources</span></span>  
 <span data-ttu-id="68aae-133">Jeśli aplikacja korzysta z kosztownych zasobów zewnętrznych, zalecamy również zapewnienie jawnie zwolnienia zasobu, zanim moduł wyrzucania elementów bezużytecznych zwolni obiekt.</span><span class="sxs-lookup"><span data-stu-id="68aae-133">If your application is using an expensive external resource, we also recommend that you provide a way to explicitly release the resource before the garbage collector frees the object.</span></span> <span data-ttu-id="68aae-134">Aby zwolnić zasób, zaimplementuj `Dispose` metodę z <xref:System.IDisposable> interfejsu, który wykonuje niezbędne czyszczenie dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="68aae-134">To release the resource, implement a `Dispose` method from the <xref:System.IDisposable> interface that performs the necessary cleanup for the object.</span></span> <span data-ttu-id="68aae-135">Może to znacząco poprawić wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="68aae-135">This can considerably improve the performance of the application.</span></span> <span data-ttu-id="68aae-136">Nawet w przypadku tej jawnej kontroli nad zasobami finalizator jest środkiem do czyszczenia zasobów, jeśli wywołanie `Dispose` metody zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="68aae-136">Even with this explicit control over resources, the finalizer becomes a safeguard to clean up resources if the call to the `Dispose` method fails.</span></span>  
  
 <span data-ttu-id="68aae-137">Więcej informacji o czyszczeniu zasobów znajduje się w następujących artykułach:</span><span class="sxs-lookup"><span data-stu-id="68aae-137">For more information about cleaning up resources, see the following articles:</span></span>  
  
- [<span data-ttu-id="68aae-138">Oczyszczanie zasobów niezarządzanych</span><span class="sxs-lookup"><span data-stu-id="68aae-138">Cleaning Up Unmanaged Resources</span></span>](../../../standard/garbage-collection/unmanaged.md)  
  
- [<span data-ttu-id="68aae-139">Implementacja metody Dispose</span><span class="sxs-lookup"><span data-stu-id="68aae-139">Implementing a Dispose Method</span></span>](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [<span data-ttu-id="68aae-140">using, instrukcja</span><span class="sxs-lookup"><span data-stu-id="68aae-140">using Statement</span></span>](../../language-reference/keywords/using-statement.md)  
  
## <a name="example"></a><span data-ttu-id="68aae-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="68aae-141">Example</span></span>  
 <span data-ttu-id="68aae-142">Poniższy przykład tworzy trzy klasy, które tworzą łańcuch dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="68aae-142">The following example creates three classes that make a chain of inheritance.</span></span> <span data-ttu-id="68aae-143">Klasa `First` jest klasą bazową, pochodzi `Second` od `First` , i pochodzi `Third` od `Second` .</span><span class="sxs-lookup"><span data-stu-id="68aae-143">The class `First` is the base class, `Second` is derived from `First`, and `Third` is derived from `Second`.</span></span> <span data-ttu-id="68aae-144">Wszystkie trzy mają finalizatory.</span><span class="sxs-lookup"><span data-stu-id="68aae-144">All three have finalizers.</span></span> <span data-ttu-id="68aae-145">W programie `Main` tworzone jest wystąpienie klasy najczęściej pochodnej.</span><span class="sxs-lookup"><span data-stu-id="68aae-145">In `Main`, an instance of the most-derived class is created.</span></span> <span data-ttu-id="68aae-146">Po uruchomieniu programu należy zauważyć, że finalizatory dla trzech klas są wywoływane automatycznie i w kolejności, od najbardziej pochodnego do najmniej pochodnego.</span><span class="sxs-lookup"><span data-stu-id="68aae-146">When the program runs, notice that the finalizers for the three classes are called automatically, and in order, from the most-derived to the least-derived.</span></span>  
  
 [!code-csharp[csProgGuideObjects#85](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#85)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="68aae-147">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="68aae-147">C# language specification</span></span>  

<span data-ttu-id="68aae-148">Aby uzyskać więcej informacji, zobacz sekcję [destruktory](~/_csharplang/spec/classes.md#destructors) w [specyfikacji języka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="68aae-148">For more information, see the [Destructors](~/_csharplang/spec/classes.md#destructors) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="68aae-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="68aae-149">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="68aae-150">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="68aae-150">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="68aae-151">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="68aae-151">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="68aae-152">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="68aae-152">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)

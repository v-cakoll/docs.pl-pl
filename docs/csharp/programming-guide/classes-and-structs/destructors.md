---
title: Finalizatory - Przewodnik programowania C#
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: c8ad738baa3ff76cf9ae8367f2fd2a1fb44a79d6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170302"
---
# <a name="finalizers-c-programming-guide"></a><span data-ttu-id="e7a69-102">Finalizatory (Przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="e7a69-102">Finalizers (C# Programming Guide)</span></span>
<span data-ttu-id="e7a69-103">Finalizatory (które są również nazywane **destruktory)** są używane do wykonywania wszelkich niezbędnych oczyszczania końcowego, gdy wystąpienie klasy jest zbierane przez moduł zbierający elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="e7a69-103">Finalizers (which are also called **destructors**) are used to perform any necessary final clean-up when a class instance is being collected by the garbage collector.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7a69-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e7a69-104">Remarks</span></span>  
  
- <span data-ttu-id="e7a69-105">Finalizatorów nie można zdefiniować w strukturach.</span><span class="sxs-lookup"><span data-stu-id="e7a69-105">Finalizers cannot be defined in structs.</span></span> <span data-ttu-id="e7a69-106">Są one używane tylko z klasami.</span><span class="sxs-lookup"><span data-stu-id="e7a69-106">They are only used with classes.</span></span>  
  
- <span data-ttu-id="e7a69-107">Klasa może mieć tylko jeden finalizator.</span><span class="sxs-lookup"><span data-stu-id="e7a69-107">A class can only have one finalizer.</span></span>  
  
- <span data-ttu-id="e7a69-108">Finalizatorów nie można dziedziczyć lub przeciążony.</span><span class="sxs-lookup"><span data-stu-id="e7a69-108">Finalizers cannot be inherited or overloaded.</span></span>  
  
- <span data-ttu-id="e7a69-109">Finalizatorów nie można wywołać.</span><span class="sxs-lookup"><span data-stu-id="e7a69-109">Finalizers cannot be called.</span></span> <span data-ttu-id="e7a69-110">Są one wywoływane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="e7a69-110">They are invoked automatically.</span></span>  
  
- <span data-ttu-id="e7a69-111">Finalizator nie ma modyfikatorów lub parametry.</span><span class="sxs-lookup"><span data-stu-id="e7a69-111">A finalizer does not take modifiers or have parameters.</span></span>  
  
 <span data-ttu-id="e7a69-112">Na przykład poniżej jest deklaracja finalizatora `Car` dla klasy.</span><span class="sxs-lookup"><span data-stu-id="e7a69-112">For example, the following is a declaration of a finalizer for the `Car` class.</span></span>
  
 [!code-csharp[csProgGuideObjects#86](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#86)]  

<span data-ttu-id="e7a69-113">Finalizator można również zaimplementować jako definicję treści wyrażenia, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e7a69-113">A finalizer can also be implemented as an expression body definition, as the following example shows.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 <span data-ttu-id="e7a69-114">Finalizator niejawnie wywołuje <xref:System.Object.Finalize%2A> klasy podstawowej obiektu.</span><span class="sxs-lookup"><span data-stu-id="e7a69-114">The finalizer implicitly calls <xref:System.Object.Finalize%2A> on the base class of the object.</span></span> <span data-ttu-id="e7a69-115">W związku z tym wywołanie finalizatora jest niejawnie tłumaczone na następujący kod:</span><span class="sxs-lookup"><span data-stu-id="e7a69-115">Therefore, a call to a finalizer is implicitly translated to the following code:</span></span>  
  
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
  
 <span data-ttu-id="e7a69-116">Oznacza to, `Finalize` że metoda jest wywoływana cyklicznie dla wszystkich wystąpień w łańcuchu dziedziczenia, od najbardziej pochodnych do najmniej pochodnych.</span><span class="sxs-lookup"><span data-stu-id="e7a69-116">This means that the `Finalize` method is called recursively for all instances in the inheritance chain, from the most-derived to the least-derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e7a69-117">Puste finalizatory nie powinny być używane.</span><span class="sxs-lookup"><span data-stu-id="e7a69-117">Empty finalizers should not be used.</span></span> <span data-ttu-id="e7a69-118">Gdy klasa zawiera finalizator, wpis jest `Finalize` tworzony w kolejce.</span><span class="sxs-lookup"><span data-stu-id="e7a69-118">When a class contains a finalizer, an entry is created in the `Finalize` queue.</span></span> <span data-ttu-id="e7a69-119">Gdy finalizator jest wywoływana, moduł zbierający elementy bezużyteczne jest wywoływany do przetwarzania kolejki.</span><span class="sxs-lookup"><span data-stu-id="e7a69-119">When the finalizer is called, the garbage collector is invoked to process the queue.</span></span> <span data-ttu-id="e7a69-120">Pusty finalizator powoduje tylko niepotrzebną utratę wydajności.</span><span class="sxs-lookup"><span data-stu-id="e7a69-120">An empty finalizer just causes a needless loss of performance.</span></span>  
  
 <span data-ttu-id="e7a69-121">Programista nie ma kontroli nad, gdy finalizator jest wywoływana, ponieważ jest to określane przez moduł zbierający elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="e7a69-121">The programmer has no control over when the finalizer is called because this is determined by the garbage collector.</span></span> <span data-ttu-id="e7a69-122">Moduł zbierający elementy bezużyteczne sprawdza obiekty, które nie są już używane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="e7a69-122">The garbage collector checks for objects that are no longer being used by the application.</span></span> <span data-ttu-id="e7a69-123">Jeśli uzna obiekt kwalifikujących się do finalizacji, wywołuje finalizator (jeśli istnieje) i odzyskuje pamięć używaną do przechowywania obiektu.</span><span class="sxs-lookup"><span data-stu-id="e7a69-123">If it considers an object eligible for finalization, it calls the finalizer (if any) and reclaims the memory used to store the object.</span></span>

 <span data-ttu-id="e7a69-124">W aplikacjach .NET Framework (ale nie w aplikacjach .NET Core) finalizatory są również wywoływane po zakończeniu programu.</span><span class="sxs-lookup"><span data-stu-id="e7a69-124">In .NET Framework applications (but not in .NET Core applications), finalizers are also called when the program exits.</span></span>
  
 <span data-ttu-id="e7a69-125">Istnieje możliwość wymuszenia <xref:System.GC.Collect%2A>wyrzucania elementów bezużytecznych przez wywołanie , ale przez większość czasu należy tego unikać, ponieważ może to spowodować problemy z wydajnością.</span><span class="sxs-lookup"><span data-stu-id="e7a69-125">It is possible to force garbage collection by calling <xref:System.GC.Collect%2A>, but most of the time, this should be avoided because it may create performance issues.</span></span>  
  
## <a name="using-finalizers-to-release-resources"></a><span data-ttu-id="e7a69-126">Korzystanie z finalizatorów do zwalniania zasobów</span><span class="sxs-lookup"><span data-stu-id="e7a69-126">Using finalizers to release resources</span></span>  
 <span data-ttu-id="e7a69-127">Ogólnie rzecz biorąc C# nie wymaga tyle zarządzania pamięcią, ile jest potrzebne podczas tworzenia z językiem, który nie jest docelowy w czasie wykonywania z wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e7a69-127">In general, C# does not require as much memory management as is needed when you develop with a language that does not target a runtime with garbage collection.</span></span> <span data-ttu-id="e7a69-128">Dzieje się tak, ponieważ moduł zbierający elementy bezużyteczne programu .NET Framework niejawnie zarządza alokacją i zwalnianiem pamięci dla obiektów.</span><span class="sxs-lookup"><span data-stu-id="e7a69-128">This is because the .NET Framework garbage collector implicitly manages the allocation and release of memory for your objects.</span></span> <span data-ttu-id="e7a69-129">Jednak gdy aplikacja hermetyzuje zasoby niezarządzane, takie jak okna, pliki i połączenia sieciowe, należy użyć finalizatorów, aby zwolnić te zasoby.</span><span class="sxs-lookup"><span data-stu-id="e7a69-129">However, when your application encapsulates unmanaged resources such as windows, files, and network connections, you should use finalizers to free those resources.</span></span> <span data-ttu-id="e7a69-130">Gdy obiekt kwalifikuje się do finalizacji, moduł `Finalize` zbierający elementy bezużyteczne uruchamia metodę obiektu.</span><span class="sxs-lookup"><span data-stu-id="e7a69-130">When the object is eligible for finalization, the garbage collector runs the `Finalize` method of the object.</span></span>  
  
## <a name="explicit-release-of-resources"></a><span data-ttu-id="e7a69-131">Jawne uwolnienie zasobów</span><span class="sxs-lookup"><span data-stu-id="e7a69-131">Explicit release of resources</span></span>  
 <span data-ttu-id="e7a69-132">Jeśli aplikacja używa drogiego zasobu zewnętrznego, zaleca się również zapewnienie sposobu jawnie zwolnić zasób przed moduł zbierający elementy bezużyteczne zwalnia obiekt.</span><span class="sxs-lookup"><span data-stu-id="e7a69-132">If your application is using an expensive external resource, we also recommend that you provide a way to explicitly release the resource before the garbage collector frees the object.</span></span> <span data-ttu-id="e7a69-133">Można to zrobić, `Dispose` implementując <xref:System.IDisposable> metodę z interfejsu, który wykonuje niezbędne oczyszczania dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="e7a69-133">You do this by implementing a `Dispose` method from the <xref:System.IDisposable> interface that performs the necessary cleanup for the object.</span></span> <span data-ttu-id="e7a69-134">Może to znacznie poprawić wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e7a69-134">This can considerably improve the performance of the application.</span></span> <span data-ttu-id="e7a69-135">Nawet przy tej jawnej kontroli nad zasobami finalizator staje się `Dispose` zabezpieczeniem, aby oczyścić zasoby, jeśli wywołanie metody nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="e7a69-135">Even with this explicit control over resources, the finalizer becomes a safeguard to clean up resources if the call to the `Dispose` method failed.</span></span>  
  
 <span data-ttu-id="e7a69-136">Aby uzyskać więcej informacji na temat oczyszczania zasobów, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="e7a69-136">For more details about cleaning up resources, see the following topics:</span></span>  
  
- [<span data-ttu-id="e7a69-137">Oczyszczanie zasobów niezarządzanych</span><span class="sxs-lookup"><span data-stu-id="e7a69-137">Cleaning Up Unmanaged Resources</span></span>](../../../standard/garbage-collection/unmanaged.md)  
  
- [<span data-ttu-id="e7a69-138">Implementacja metody Dispose</span><span class="sxs-lookup"><span data-stu-id="e7a69-138">Implementing a Dispose Method</span></span>](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [<span data-ttu-id="e7a69-139">za pomocą instrukcji</span><span class="sxs-lookup"><span data-stu-id="e7a69-139">using Statement</span></span>](../../language-reference/keywords/using-statement.md)  
  
## <a name="example"></a><span data-ttu-id="e7a69-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="e7a69-140">Example</span></span>  
 <span data-ttu-id="e7a69-141">Poniższy przykład tworzy trzy klasy, które tworzą łańcuch dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="e7a69-141">The following example creates three classes that make a chain of inheritance.</span></span> <span data-ttu-id="e7a69-142">Klasa `First` jest klasą `Second` podstawową, `First`pochodzi `Third` od , `Second`i pochodzi od .</span><span class="sxs-lookup"><span data-stu-id="e7a69-142">The class `First` is the base class, `Second` is derived from `First`, and `Third` is derived from `Second`.</span></span> <span data-ttu-id="e7a69-143">Wszystkie trzy mają finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="e7a69-143">All three have finalizers.</span></span> <span data-ttu-id="e7a69-144">W `Main`przypadku wystąpienia klasy najbardziej pochodnych jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="e7a69-144">In `Main`, an instance of the most-derived class is created.</span></span> <span data-ttu-id="e7a69-145">Po uruchomieniu programu należy zauważyć, że finalizatory dla trzech klas są wywoływane automatycznie i w kolejności, od najbardziej pochodnych do najmniej pochodnych.</span><span class="sxs-lookup"><span data-stu-id="e7a69-145">When the program runs, notice that the finalizers for the three classes are called automatically, and in order, from the most-derived to the least-derived.</span></span>  
  
 [!code-csharp[csProgGuideObjects#85](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#85)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="e7a69-146">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="e7a69-146">C# language specification</span></span>  

<span data-ttu-id="e7a69-147">Aby uzyskać więcej informacji, zobacz [Destruktory](~/_csharplang/spec/classes.md#destructors) sekcji [specyfikacji języka Języka C#.](/dotnet/csharp/language-reference/language-specification/introduction)</span><span class="sxs-lookup"><span data-stu-id="e7a69-147">For more information, see the [Destructors](~/_csharplang/spec/classes.md#destructors) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e7a69-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7a69-148">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="e7a69-149">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="e7a69-149">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e7a69-150">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="e7a69-150">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="e7a69-151">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="e7a69-151">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)

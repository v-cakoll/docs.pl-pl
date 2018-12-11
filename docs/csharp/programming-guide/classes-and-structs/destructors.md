---
title: Finalizatory (C# Programming Guide)
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: 2b24884d2650a5e799eda630bc65f3c5a5c2508a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127267"
---
# <a name="finalizers-c-programming-guide"></a><span data-ttu-id="71750-102">Finalizatory (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="71750-102">Finalizers (C# Programming Guide)</span></span>
<span data-ttu-id="71750-103">Finalizatory (są one również nazywane **destruktory**) są używane do wykonywania wszelkich niezbędnych końcowego oczyszczania, gdy wystąpienie klasy są gromadzone przez moduł odśmiecania pamięci.</span><span class="sxs-lookup"><span data-stu-id="71750-103">Finalizers (which are also called **destructors**) are used to perform any necessary final clean-up when a class instance is being collected by the garbage collector.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71750-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="71750-104">Remarks</span></span>  
  
-   <span data-ttu-id="71750-105">Nie można zdefiniować finalizatory w strukturach.</span><span class="sxs-lookup"><span data-stu-id="71750-105">Finalizers cannot be defined in structs.</span></span> <span data-ttu-id="71750-106">Są one używane tylko z klasami.</span><span class="sxs-lookup"><span data-stu-id="71750-106">They are only used with classes.</span></span>  
  
-   <span data-ttu-id="71750-107">Klasa może mieć tylko jedną finalizatora.</span><span class="sxs-lookup"><span data-stu-id="71750-107">A class can only have one finalizer.</span></span>  
  
-   <span data-ttu-id="71750-108">Finalizatory nie może być dziedziczona ani przeciążone.</span><span class="sxs-lookup"><span data-stu-id="71750-108">Finalizers cannot be inherited or overloaded.</span></span>  
  
-   <span data-ttu-id="71750-109">Nie można wywołać finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="71750-109">Finalizers cannot be called.</span></span> <span data-ttu-id="71750-110">Są one wywoływane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="71750-110">They are invoked automatically.</span></span>  
  
-   <span data-ttu-id="71750-111">Finalizator zająć Modyfikatory lub nie mieć parametrów.</span><span class="sxs-lookup"><span data-stu-id="71750-111">A finalizer does not take modifiers or have parameters.</span></span>  
  
 <span data-ttu-id="71750-112">Na przykład Oto deklaracja finalizatora dla `Car` klasy.</span><span class="sxs-lookup"><span data-stu-id="71750-112">For example, the following is a declaration of a finalizer for the `Car` class.</span></span>
  
 [!code-csharp[csProgGuideObjects#86](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_1.cs)]  

<span data-ttu-id="71750-113">Finalizator może też być implementowany jako definicja treści wyrażenia, co ilustruje poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="71750-113">A finalizer can also be implemented as an expression body definition, as the following example shows.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 <span data-ttu-id="71750-114">Niejawnie wywołuje finalizator <xref:System.Object.Finalize%2A> w klasie bazowej obiektu.</span><span class="sxs-lookup"><span data-stu-id="71750-114">The finalizer implicitly calls <xref:System.Object.Finalize%2A> on the base class of the object.</span></span> <span data-ttu-id="71750-115">W związku z tym wywołanie finalizator niejawnie jest tłumaczona na następujący kod:</span><span class="sxs-lookup"><span data-stu-id="71750-115">Therefore, a call to a finalizer is implicitly translated to the following code:</span></span>  
  
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
  
 <span data-ttu-id="71750-116">Oznacza to, że `Finalize` metoda jest wywoływana rekursywnie dla wszystkich wystąpień w łańcuch dziedziczenia z najbardziej pochodnego do najmniej pochodnego.</span><span class="sxs-lookup"><span data-stu-id="71750-116">This means that the `Finalize` method is called recursively for all instances in the inheritance chain, from the most-derived to the least-derived.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="71750-117">Nie należy używać puste finalizatory.</span><span class="sxs-lookup"><span data-stu-id="71750-117">Empty finalizers should not be used.</span></span> <span data-ttu-id="71750-118">Gdy klasa zawiera finalizator, zapis jest tworzony w `Finalize` kolejki.</span><span class="sxs-lookup"><span data-stu-id="71750-118">When a class contains a finalizer, an entry is created in the `Finalize` queue.</span></span> <span data-ttu-id="71750-119">Wywołanego finalizator moduł odśmiecania pamięci jest wywoływana, aby przetworzyć kolejkę.</span><span class="sxs-lookup"><span data-stu-id="71750-119">When the finalizer is called, the garbage collector is invoked to process the queue.</span></span> <span data-ttu-id="71750-120">Pusty finalizator powoduje po prostu niepotrzebnego utrata wydajności.</span><span class="sxs-lookup"><span data-stu-id="71750-120">An empty finalizer just causes a needless loss of performance.</span></span>  
  
 <span data-ttu-id="71750-121">Programistę nie ma kontroli nad po wywołaniu finalizatora, ponieważ jest to określane przez moduł odśmiecania pamięci.</span><span class="sxs-lookup"><span data-stu-id="71750-121">The programmer has no control over when the finalizer is called because this is determined by the garbage collector.</span></span> <span data-ttu-id="71750-122">Moduł zbierający elementy bezużyteczne sprawdza, czy obiekty nie są już używane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="71750-122">The garbage collector checks for objects that are no longer being used by the application.</span></span> <span data-ttu-id="71750-123">Jeśli obiekt kwalifikuje się do finalizacji, wywołuje finalizator (jeśli istnieje) i odzyskuje pamięć używaną do przechowywania obiektu.</span><span class="sxs-lookup"><span data-stu-id="71750-123">If it considers an object eligible for finalization, it calls the finalizer (if any) and reclaims the memory used to store the object.</span></span> 
 
 <span data-ttu-id="71750-124">W aplikacjach .NET Framework (ale nie w aplikacjach platformy .NET Core) finalizatory są również nazywane, gdy zamyka program.</span><span class="sxs-lookup"><span data-stu-id="71750-124">In .NET Framework applications (but not in .NET Core applications), finalizers are also called when the program exits.</span></span> 
  
 <span data-ttu-id="71750-125">Istnieje możliwość wymuszenia wyrzucania elementów bezużytecznych przez wywołanie metody <xref:System.GC.Collect%2A>, ale w większości przypadków, to należy unikać, ponieważ mogą one stanowić problemy z wydajnością.</span><span class="sxs-lookup"><span data-stu-id="71750-125">It is possible to force garbage collection by calling <xref:System.GC.Collect%2A>, but most of the time, this should be avoided because it may create performance issues.</span></span>  
  
## <a name="using-finalizers-to-release-resources"></a><span data-ttu-id="71750-126">Aby zwolnić zasoby przy użyciu finalizatory</span><span class="sxs-lookup"><span data-stu-id="71750-126">Using finalizers to release resources</span></span>  
 <span data-ttu-id="71750-127">Ogólnie rzecz biorąc C# nie wymaga tak dużej ilości pamięci zarządzania zgodnie z potrzebami, podczas pracy z językiem, który nie jest przeznaczony do aparatu plików wykonywalnych wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="71750-127">In general, C# does not require as much memory management as is needed when you develop with a language that does not target a runtime with garbage collection.</span></span> <span data-ttu-id="71750-128">To dlatego moduł odśmiecania pamięci środowiska .NET Framework niejawnie zarządza alokacją i zwolnieniem pamięci dla obiektów.</span><span class="sxs-lookup"><span data-stu-id="71750-128">This is because the .NET Framework garbage collector implicitly manages the allocation and release of memory for your objects.</span></span> <span data-ttu-id="71750-129">Jednak w przypadku aplikacji hermetyzuje niezarządzane zasoby, takie jak windows, pliki i połączenia sieciowe, należy używać finalizatory zwolnienie tych zasobów.</span><span class="sxs-lookup"><span data-stu-id="71750-129">However, when your application encapsulates unmanaged resources such as windows, files, and network connections, you should use finalizers to free those resources.</span></span> <span data-ttu-id="71750-130">Gdy obiekt jest uprawniona do finalizacji, wyrzucanie elementów bezużytecznych działa `Finalize` metody obiektu.</span><span class="sxs-lookup"><span data-stu-id="71750-130">When the object is eligible for finalization, the garbage collector runs the `Finalize` method of the object.</span></span>  
  
## <a name="explicit-release-of-resources"></a><span data-ttu-id="71750-131">Jawnego zwolnienia zasobów</span><span class="sxs-lookup"><span data-stu-id="71750-131">Explicit release of resources</span></span>  
 <span data-ttu-id="71750-132">Jeśli aplikacja używa kosztowne zewnętrznego zasobu, zalecamy również, zapewniają sposób jawnie zwalniać zasobu, zanim moduł odśmiecania pamięci zwalnia obiektu.</span><span class="sxs-lookup"><span data-stu-id="71750-132">If your application is using an expensive external resource, we also recommend that you provide a way to explicitly release the resource before the garbage collector frees the object.</span></span> <span data-ttu-id="71750-133">Możesz to zrobić poprzez implementację `Dispose` metody z <xref:System.IDisposable> interfejsu, który wykonuje niezbędne czyszczenia dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="71750-133">You do this by implementing a `Dispose` method from the <xref:System.IDisposable> interface that performs the necessary cleanup for the object.</span></span> <span data-ttu-id="71750-134">Może to znacznie poprawić wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="71750-134">This can considerably improve the performance of the application.</span></span> <span data-ttu-id="71750-135">Nawet w przypadku tego jawną kontrolę nad zasobami finalizator będzie odpowiadać za czyszczenie zasobów, jeśli wywołanie `Dispose` metody nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="71750-135">Even with this explicit control over resources, the finalizer becomes a safeguard to clean up resources if the call to the `Dispose` method failed.</span></span>  
  
 <span data-ttu-id="71750-136">Aby uzyskać więcej informacji na temat Oczyszczanie zasobów zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="71750-136">For more details about cleaning up resources, see the following topics:</span></span>  
  
-   [<span data-ttu-id="71750-137">Oczyszczanie zasobów niezarządzanych</span><span class="sxs-lookup"><span data-stu-id="71750-137">Cleaning Up Unmanaged Resources</span></span>](../../../standard/garbage-collection/unmanaged.md)  
  
-   [<span data-ttu-id="71750-138">Implementacja metody Dispose</span><span class="sxs-lookup"><span data-stu-id="71750-138">Implementing a Dispose Method</span></span>](../../../standard/garbage-collection/implementing-dispose.md)  
  
-   [<span data-ttu-id="71750-139">using, instrukcja</span><span class="sxs-lookup"><span data-stu-id="71750-139">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)  
  
## <a name="example"></a><span data-ttu-id="71750-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="71750-140">Example</span></span>  
 <span data-ttu-id="71750-141">Poniższy przykład tworzy trzy klasy, które w łańcuchu dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="71750-141">The following example creates three classes that make a chain of inheritance.</span></span> <span data-ttu-id="71750-142">Klasa `First` jest klasą bazową `Second` jest tworzony na podstawie `First`, i `Third` jest tworzony na podstawie `Second`.</span><span class="sxs-lookup"><span data-stu-id="71750-142">The class `First` is the base class, `Second` is derived from `First`, and `Third` is derived from `Second`.</span></span> <span data-ttu-id="71750-143">Wszystkie trzy mają finalizatory.</span><span class="sxs-lookup"><span data-stu-id="71750-143">All three have finalizers.</span></span> <span data-ttu-id="71750-144">W `Main`, tworzone jest wystąpienie klasy najbardziej pochodnego.</span><span class="sxs-lookup"><span data-stu-id="71750-144">In `Main`, an instance of the most-derived class is created.</span></span> <span data-ttu-id="71750-145">Po uruchomieniu program, zwróć uwagę, że finalizatory dla trzech klas są wywoływane automatycznie i w kolejności, z najbardziej pochodnego do najmniej pochodnego.</span><span class="sxs-lookup"><span data-stu-id="71750-145">When the program runs, notice that the finalizers for the three classes are called automatically, and in order, from the most-derived to the least-derived.</span></span>  
  
 [!code-csharp[csProgGuideObjects#85](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="71750-146">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="71750-146">C# language specification</span></span>  

<span data-ttu-id="71750-147">Aby uzyskać więcej informacji, zobacz [destruktory](~/_csharplang/spec/classes.md#destructors) części [ C# specyfikacji języka](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="71750-147">For more information, see the [Destructors](~/_csharplang/spec/classes.md#destructors) section of the [C# language specification](../../language-reference/language-specification/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="71750-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="71750-148">See also</span></span>

- <xref:System.IDisposable>  
- [<span data-ttu-id="71750-149">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="71750-149">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="71750-150">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="71750-150">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
- [<span data-ttu-id="71750-151">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="71750-151">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)

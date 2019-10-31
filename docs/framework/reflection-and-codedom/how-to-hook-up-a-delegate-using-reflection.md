---
title: 'Porady: podłączanie delegata za pomocą odbicia'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], adding event handlers with reflection
- reflection, adding event-handler delegates
- delegates [.NET Framework], adding event handlers with reflection
ms.assetid: 076ee62d-a964-449e-a447-c31b33518b81
ms.openlocfilehash: 14a9694708b36b23ecef453d530ad3b939a046ba
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130115"
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="4f3b6-102">Porady: podłączanie delegata za pomocą odbicia</span><span class="sxs-lookup"><span data-stu-id="4f3b6-102">How to: Hook Up a Delegate Using Reflection</span></span>
<span data-ttu-id="4f3b6-103">W przypadku używania odbicia do ładowania i uruchamiania zestawów nie można użyć funkcji języka, takich C# jak operator `+=` lub Visual Basic [AddHandler](../../visual-basic/language-reference/statements/addhandler-statement.md) , aby podłączyć zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-103">When you use reflection to load and run assemblies, you cannot use language features like the C# `+=` operator or the Visual Basic [AddHandler statement](../../visual-basic/language-reference/statements/addhandler-statement.md) to hook up events.</span></span> <span data-ttu-id="4f3b6-104">W poniższych procedurach pokazano, jak podłączyć istniejącą metodę do zdarzenia, pobierając wszystkie niezbędne typy poprzez odbicie i jak utworzyć metodę dynamiczną przy użyciu emisji odbicia i podłączyć ją do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-104">The following procedures show how to hook up an existing method to an event by getting all the necessary types through reflection, and how to create a dynamic method using reflection emit and hook it up to an event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4f3b6-105">Aby uzyskać inny sposób, aby podłączyć delegata obsługi zdarzeń, zobacz przykład kodu dla metody <xref:System.Reflection.EventInfo.AddEventHandler%2A> klasy <xref:System.Reflection.EventInfo>.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-105">For another way to hook up an event-handling delegate, see the code example for the <xref:System.Reflection.EventInfo.AddEventHandler%2A> method of the <xref:System.Reflection.EventInfo> class.</span></span>  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="4f3b6-106">Aby podłączyć delegata przy użyciu odbicia</span><span class="sxs-lookup"><span data-stu-id="4f3b6-106">To hook up a delegate using reflection</span></span>  
  
1. <span data-ttu-id="4f3b6-107">Załaduj zestaw, który zawiera typ, który wywołuje zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-107">Load an assembly that contains a type that raises events.</span></span> <span data-ttu-id="4f3b6-108">Zestawy są zwykle ładowane przy użyciu metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-108">Assemblies are usually loaded with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4f3b6-109">Aby zachować ten przykład prosty, używany jest formularz pochodny w bieżącym zestawie, dlatego Metoda <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> jest używana do ładowania bieżącego zestawu.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-109">To keep this example simple, a derived form in the current assembly is used, so the <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method is used to load the current assembly.</span></span>  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2. <span data-ttu-id="4f3b6-110">Pobierz obiekt <xref:System.Type> reprezentujący typ i Utwórz wystąpienie typu.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-110">Get a <xref:System.Type> object representing the type, and create an instance of the type.</span></span> <span data-ttu-id="4f3b6-111">Metoda <xref:System.Activator.CreateInstance%28System.Type%29> jest używana w poniższym kodzie, ponieważ formularz zawiera konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-111">The <xref:System.Activator.CreateInstance%28System.Type%29> method is used in the following code because the form has a parameterless constructor.</span></span> <span data-ttu-id="4f3b6-112">Istnieje kilka innych przeciążeń metody <xref:System.Activator.CreateInstance%2A>, których można użyć, jeśli tworzony typ nie ma konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-112">There are several other overloads of the <xref:System.Activator.CreateInstance%2A> method that you can use if the type you are creating does not have a parameterless constructor.</span></span> <span data-ttu-id="4f3b6-113">Nowe wystąpienie jest przechowywane jako typ <xref:System.Object>, aby zachować fikcyjny, że nic nie jest znane o zestawie.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-113">The new instance is stored as type <xref:System.Object> to maintain the fiction that nothing is known about the assembly.</span></span> <span data-ttu-id="4f3b6-114">(Odbicie umożliwia uzyskanie typów w zestawie bez poznania ich nazw z góry).</span><span class="sxs-lookup"><span data-stu-id="4f3b6-114">(Reflection allows you to get the types in an assembly without knowing their names in advance.)</span></span>  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3. <span data-ttu-id="4f3b6-115">Pobierz obiekt <xref:System.Reflection.EventInfo> reprezentujący zdarzenie i Użyj właściwości <xref:System.Reflection.EventInfo.EventHandlerType%2A>, aby uzyskać typ delegata używanego do obsługi zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-115">Get an <xref:System.Reflection.EventInfo> object representing the event, and use the <xref:System.Reflection.EventInfo.EventHandlerType%2A> property to get the type of delegate used to handle the event.</span></span> <span data-ttu-id="4f3b6-116">W poniższym kodzie zostanie uzyskany <xref:System.Reflection.EventInfo> dla zdarzenia <xref:System.Windows.Forms.Control.Click>.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-116">In the following code, an <xref:System.Reflection.EventInfo> for the <xref:System.Windows.Forms.Control.Click> event is obtained.</span></span>  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4. <span data-ttu-id="4f3b6-117">Pobierz obiekt <xref:System.Reflection.MethodInfo> reprezentujący metodę, która obsługuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-117">Get a <xref:System.Reflection.MethodInfo> object representing the method that handles the event.</span></span> <span data-ttu-id="4f3b6-118">Pełny kod programu w sekcji przykład w dalszej części tego tematu zawiera metodę, która pasuje do sygnatury delegata <xref:System.EventHandler>, który obsługuje zdarzenie <xref:System.Windows.Forms.Control.Click>, ale można również generować metody dynamiczne w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-118">The complete program code in the Example section later in this topic contains a method that matches the signature of the <xref:System.EventHandler> delegate, which handles the <xref:System.Windows.Forms.Control.Click> event, but you can also generate dynamic methods at run time.</span></span> <span data-ttu-id="4f3b6-119">Aby uzyskać szczegółowe informacje, zobacz procedurę towarzyszącą w celu wygenerowania programu obsługi zdarzeń w czasie wykonywania przy użyciu metody dynamicznej.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-119">For details, see the accompanying procedure, for generating an event handler at run time by using a dynamic method.</span></span>  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5. <span data-ttu-id="4f3b6-120">Utwórz wystąpienie delegata przy użyciu metody <xref:System.Delegate.CreateDelegate%2A>.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-120">Create an instance of the delegate, using the <xref:System.Delegate.CreateDelegate%2A> method.</span></span> <span data-ttu-id="4f3b6-121">Ta metoda jest statyczna (`Shared` w Visual Basic), więc należy podać typ delegata.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-121">This method is static (`Shared` in Visual Basic), so the delegate type must be supplied.</span></span> <span data-ttu-id="4f3b6-122">Zalecane jest używanie przeciążeń <xref:System.Delegate.CreateDelegate%2A>, które pobierają <xref:System.Reflection.MethodInfo>.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-122">Using the overloads of <xref:System.Delegate.CreateDelegate%2A> that take a <xref:System.Reflection.MethodInfo> is recommended.</span></span>  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6. <span data-ttu-id="4f3b6-123">Pobierz metodę dostępu `add` i Wywołaj ją, aby podłączyć zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-123">Get the `add` accessor method and invoke it to hook up the event.</span></span> <span data-ttu-id="4f3b6-124">Wszystkie zdarzenia mają metodę dostępu `add` i metodę dostępu `remove`, która jest ukryta przez składnię języków wysokiego poziomu.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-124">All events have an `add` accessor and a `remove` accessor, which are hidden by the syntax of high-level languages.</span></span> <span data-ttu-id="4f3b6-125">Na przykład C# używa operatora `+=`, aby podłączyć zdarzenia, a Visual Basic używa [instrukcji AddHandler](../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4f3b6-125">For example, C# uses the `+=` operator to hook up events, and Visual Basic uses the [AddHandler statement](../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="4f3b6-126">Poniższy kod pobiera metodę dostępu `add` zdarzenia <xref:System.Windows.Forms.Control.Click> i wywołuje ją z późnym wiązaniem, przekazując w wystąpieniu delegata.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-126">The following code gets the `add` accessor of the <xref:System.Windows.Forms.Control.Click> event and invokes it late-bound, passing in the delegate instance.</span></span> <span data-ttu-id="4f3b6-127">Argumenty muszą być przekazane jako tablica.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-127">The arguments must be passed as an array.</span></span>  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7. <span data-ttu-id="4f3b6-128">Przetestuj zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-128">Test the event.</span></span> <span data-ttu-id="4f3b6-129">Poniższy kod przedstawia formularz zdefiniowany w przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-129">The following code shows the form defined in the code example.</span></span> <span data-ttu-id="4f3b6-130">Kliknięcie formularza wywołuje program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-130">Clicking the form invokes the event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>   
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a><span data-ttu-id="4f3b6-131">Aby wygenerować procedurę obsługi zdarzeń w czasie wykonywania przy użyciu metody dynamicznej</span><span class="sxs-lookup"><span data-stu-id="4f3b6-131">To generate an event handler at run time by using a dynamic method</span></span>  
  
1. <span data-ttu-id="4f3b6-132">Metody obsługi zdarzeń mogą być generowane w czasie wykonywania przy użyciu uproszczonych metod dynamicznych i emisji odbicia.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-132">Event-handler methods can be generated at run time, using lightweight dynamic methods and reflection emit.</span></span> <span data-ttu-id="4f3b6-133">Do skonstruowania procedury obsługi zdarzeń wymagany jest typ zwracany i typy parametrów delegata.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-133">To construct an event handler, you need the return type and parameter types of the delegate.</span></span> <span data-ttu-id="4f3b6-134">Można je uzyskać, badając metodę `Invoke` delegata.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-134">These can be obtained by examining the delegate's `Invoke` method.</span></span> <span data-ttu-id="4f3b6-135">Poniższy kod używa metod `GetDelegateReturnType` i `GetDelegateParameterTypes`, aby uzyskać te informacje.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-135">The following code uses the `GetDelegateReturnType` and `GetDelegateParameterTypes` methods to obtain this information.</span></span> <span data-ttu-id="4f3b6-136">Kod dla tych metod można znaleźć w sekcji przykład w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-136">The code for these methods can be found in the Example section later in this topic.</span></span>  
  
     <span data-ttu-id="4f3b6-137">Nie trzeba określać nazwy <xref:System.Reflection.Emit.DynamicMethod>, więc można użyć pustego ciągu.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-137">It is not necessary to name a <xref:System.Reflection.Emit.DynamicMethod>, so the empty string can be used.</span></span> <span data-ttu-id="4f3b6-138">W poniższym kodzie, ostatni argument kojarzy metodę dynamiczną z bieżącym typem, dając delegata dostęp do wszystkich publicznych i prywatnych członków klasy `Example`.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-138">In the following code, the last argument associates the dynamic method with the current type, giving the delegate access to all the public and private members of the `Example` class.</span></span>  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2. <span data-ttu-id="4f3b6-139">Generuj treść metody.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-139">Generate a method body.</span></span> <span data-ttu-id="4f3b6-140">Ta metoda ładuje ciąg, wywołuje Przeciążenie metody <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType>, która pobiera ciąg, wyświetla wartość zwracaną przez stos (ponieważ program obsługi nie ma zwracanego typu) i zwraca.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-140">This method loads a string, calls the overload of the <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> method that takes a string, pops the return value off the stack (because the handler has no return type), and returns.</span></span> <span data-ttu-id="4f3b6-141">Aby dowiedzieć się więcej o emitowaniu metod dynamicznych, zobacz [How to: define and Execute Dynamic Methods](how-to-define-and-execute-dynamic-methods.md).</span><span class="sxs-lookup"><span data-stu-id="4f3b6-141">To learn more about emitting dynamic methods, see [How to: Define and Execute Dynamic Methods](how-to-define-and-execute-dynamic-methods.md).</span></span>  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3. <span data-ttu-id="4f3b6-142">Ukończ metodę dynamiczną, wywołując metodę <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A>.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-142">Complete the dynamic method by calling its <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method.</span></span> <span data-ttu-id="4f3b6-143">Użyj metody dostępu `add`, aby dodać delegata do listy wywołań dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-143">Use the `add` accessor to add the delegate to the invocation list for the event.</span></span>  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4. <span data-ttu-id="4f3b6-144">Przetestuj zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-144">Test the event.</span></span> <span data-ttu-id="4f3b6-145">Poniższy kod ładuje formularz zdefiniowany w przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-145">The following code loads the form defined in the code example.</span></span> <span data-ttu-id="4f3b6-146">Kliknięcie formularza wywołuje zarówno wstępnie zdefiniowaną procedurę obsługi zdarzeń, jak i wyemitowaną procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-146">Clicking the form invokes both the predefined event handler and the emitted event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="4f3b6-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="4f3b6-147">Example</span></span>  
 <span data-ttu-id="4f3b6-148">Poniższy przykład kodu pokazuje, jak podłączyć istniejącą metodę do zdarzenia przy użyciu odbicia, a także jak użyć klasy <xref:System.Reflection.Emit.DynamicMethod> do emisji metody w czasie wykonywania i podłączania jej do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4f3b6-148">The following code example shows how to hook up an existing method to an event using reflection, and also how to use the <xref:System.Reflection.Emit.DynamicMethod> class to emit a method at run time and hook it up to an event.</span></span>  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4f3b6-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4f3b6-149">See also</span></span>

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Emit.DynamicMethod>
- <xref:System.Activator.CreateInstance%2A>
- <xref:System.Delegate.CreateDelegate%2A>
- [<span data-ttu-id="4f3b6-150">Instrukcje: definiowanie i wykonywanie metod dynamicznych</span><span class="sxs-lookup"><span data-stu-id="4f3b6-150">How to: Define and Execute Dynamic Methods</span></span>](how-to-define-and-execute-dynamic-methods.md)
- [<span data-ttu-id="4f3b6-151">Odbicie</span><span class="sxs-lookup"><span data-stu-id="4f3b6-151">Reflection</span></span>](reflection.md)

---
title: 'Instrukcje: Podłączanie delegata za pomocą odbicia'
description: Zobacz jak podłączyć delegata przy użyciu odbicia w programie .NET. Połącz istniejącą metodę ze zdarzeniem, pobierając niezbędne typy poprzez odbicie.
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
ms.openlocfilehash: b5d93efd278a53a4e6382f2321918e58ead55899
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865089"
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="0f89e-104">Instrukcje: Podłączanie delegata za pomocą odbicia</span><span class="sxs-lookup"><span data-stu-id="0f89e-104">How to: Hook Up a Delegate Using Reflection</span></span>
<span data-ttu-id="0f89e-105">W przypadku używania odbicia do ładowania i uruchamiania zestawów nie można użyć funkcji języka, takich jak `+=` operator języka C# lub Visual Basic [AddHandler](../../visual-basic/language-reference/statements/addhandler-statement.md) , aby podłączyć zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="0f89e-105">When you use reflection to load and run assemblies, you cannot use language features like the C# `+=` operator or the Visual Basic [AddHandler statement](../../visual-basic/language-reference/statements/addhandler-statement.md) to hook up events.</span></span> <span data-ttu-id="0f89e-106">W poniższych procedurach pokazano, jak podłączyć istniejącą metodę do zdarzenia, pobierając wszystkie niezbędne typy poprzez odbicie i jak utworzyć metodę dynamiczną przy użyciu emisji odbicia i podłączyć ją do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="0f89e-106">The following procedures show how to hook up an existing method to an event by getting all the necessary types through reflection, and how to create a dynamic method using reflection emit and hook it up to an event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0f89e-107">Aby móc podłączyć delegata obsługi zdarzeń, zobacz przykład kodu dla <xref:System.Reflection.EventInfo.AddEventHandler%2A> metody <xref:System.Reflection.EventInfo> klasy.</span><span class="sxs-lookup"><span data-stu-id="0f89e-107">For another way to hook up an event-handling delegate, see the code example for the <xref:System.Reflection.EventInfo.AddEventHandler%2A> method of the <xref:System.Reflection.EventInfo> class.</span></span>  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="0f89e-108">Aby podłączyć delegata przy użyciu odbicia</span><span class="sxs-lookup"><span data-stu-id="0f89e-108">To hook up a delegate using reflection</span></span>  
  
1. <span data-ttu-id="0f89e-109">Załaduj zestaw, który zawiera typ, który wywołuje zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="0f89e-109">Load an assembly that contains a type that raises events.</span></span> <span data-ttu-id="0f89e-110">Zestawy są zwykle ładowane przy użyciu <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="0f89e-110">Assemblies are usually loaded with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0f89e-111">Aby zachować ten przykład prosty, używany jest formularz pochodny w bieżącym zestawie, dlatego <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> Metoda jest używana do ładowania bieżącego zestawu.</span><span class="sxs-lookup"><span data-stu-id="0f89e-111">To keep this example simple, a derived form in the current assembly is used, so the <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method is used to load the current assembly.</span></span>  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2. <span data-ttu-id="0f89e-112">Pobierz <xref:System.Type> obiekt reprezentujący typ i Utwórz wystąpienie typu.</span><span class="sxs-lookup"><span data-stu-id="0f89e-112">Get a <xref:System.Type> object representing the type, and create an instance of the type.</span></span> <span data-ttu-id="0f89e-113"><xref:System.Activator.CreateInstance%28System.Type%29>Metoda jest używana w poniższym kodzie, ponieważ formularz zawiera konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="0f89e-113">The <xref:System.Activator.CreateInstance%28System.Type%29> method is used in the following code because the form has a parameterless constructor.</span></span> <span data-ttu-id="0f89e-114">Istnieje kilka innych przeciążeń <xref:System.Activator.CreateInstance%2A> metody, których można użyć, jeśli tworzony typ nie ma konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="0f89e-114">There are several other overloads of the <xref:System.Activator.CreateInstance%2A> method that you can use if the type you are creating does not have a parameterless constructor.</span></span> <span data-ttu-id="0f89e-115">Nowe wystąpienie jest przechowywane jako typ <xref:System.Object> do obsługi fikcyjnego, który nie jest znany o zestawie.</span><span class="sxs-lookup"><span data-stu-id="0f89e-115">The new instance is stored as type <xref:System.Object> to maintain the fiction that nothing is known about the assembly.</span></span> <span data-ttu-id="0f89e-116">(Odbicie umożliwia uzyskanie typów w zestawie bez poznania ich nazw z góry).</span><span class="sxs-lookup"><span data-stu-id="0f89e-116">(Reflection allows you to get the types in an assembly without knowing their names in advance.)</span></span>  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3. <span data-ttu-id="0f89e-117">Pobierz <xref:System.Reflection.EventInfo> obiekt reprezentujący zdarzenie i Użyj <xref:System.Reflection.EventInfo.EventHandlerType%2A> właściwości, aby uzyskać typ delegata użytego do obsłużenia zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="0f89e-117">Get an <xref:System.Reflection.EventInfo> object representing the event, and use the <xref:System.Reflection.EventInfo.EventHandlerType%2A> property to get the type of delegate used to handle the event.</span></span> <span data-ttu-id="0f89e-118">W poniższym kodzie <xref:System.Reflection.EventInfo> <xref:System.Windows.Forms.Control.Click> jest uzyskiwany dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="0f89e-118">In the following code, an <xref:System.Reflection.EventInfo> for the <xref:System.Windows.Forms.Control.Click> event is obtained.</span></span>  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4. <span data-ttu-id="0f89e-119">Pobierz <xref:System.Reflection.MethodInfo> obiekt reprezentujący metodę, która obsługuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="0f89e-119">Get a <xref:System.Reflection.MethodInfo> object representing the method that handles the event.</span></span> <span data-ttu-id="0f89e-120">Pełny kod programu w sekcji przykład w dalszej części tego tematu zawiera metodę, która pasuje do podpisu <xref:System.EventHandler> delegata, który obsługuje <xref:System.Windows.Forms.Control.Click> zdarzenie, ale można również generować metody dynamiczne w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0f89e-120">The complete program code in the Example section later in this topic contains a method that matches the signature of the <xref:System.EventHandler> delegate, which handles the <xref:System.Windows.Forms.Control.Click> event, but you can also generate dynamic methods at run time.</span></span> <span data-ttu-id="0f89e-121">Aby uzyskać szczegółowe informacje, zobacz procedurę towarzyszącą w celu wygenerowania programu obsługi zdarzeń w czasie wykonywania przy użyciu metody dynamicznej.</span><span class="sxs-lookup"><span data-stu-id="0f89e-121">For details, see the accompanying procedure, for generating an event handler at run time by using a dynamic method.</span></span>  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5. <span data-ttu-id="0f89e-122">Utwórz wystąpienie delegata przy użyciu <xref:System.Delegate.CreateDelegate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0f89e-122">Create an instance of the delegate, using the <xref:System.Delegate.CreateDelegate%2A> method.</span></span> <span data-ttu-id="0f89e-123">Ta metoda jest statyczna ( `Shared` w Visual Basic), więc należy podać typ delegata.</span><span class="sxs-lookup"><span data-stu-id="0f89e-123">This method is static (`Shared` in Visual Basic), so the delegate type must be supplied.</span></span> <span data-ttu-id="0f89e-124">Zalecane jest użycie przeciążenia <xref:System.Delegate.CreateDelegate%2A> , które to zajmie <xref:System.Reflection.MethodInfo> .</span><span class="sxs-lookup"><span data-stu-id="0f89e-124">Using the overloads of <xref:System.Delegate.CreateDelegate%2A> that take a <xref:System.Reflection.MethodInfo> is recommended.</span></span>  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6. <span data-ttu-id="0f89e-125">Pobierz `add` metodę dostępu i Wywołaj ją, aby podłączyć zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="0f89e-125">Get the `add` accessor method and invoke it to hook up the event.</span></span> <span data-ttu-id="0f89e-126">Wszystkie zdarzenia mają `add` akcesor i `remove` metodę dostępu, która jest ukryta przez składnię języków wysokiego poziomu.</span><span class="sxs-lookup"><span data-stu-id="0f89e-126">All events have an `add` accessor and a `remove` accessor, which are hidden by the syntax of high-level languages.</span></span> <span data-ttu-id="0f89e-127">Na przykład, C# używa `+=` operatora, aby podłączyć zdarzenia, a Visual Basic używa [instrukcji AddHandler](../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0f89e-127">For example, C# uses the `+=` operator to hook up events, and Visual Basic uses the [AddHandler statement](../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="0f89e-128">Poniższy kod pobiera `add` metodę dostępu dla <xref:System.Windows.Forms.Control.Click> zdarzenia i wywołuje ją z późnym wiązaniem, przekazując w wystąpieniu delegata.</span><span class="sxs-lookup"><span data-stu-id="0f89e-128">The following code gets the `add` accessor of the <xref:System.Windows.Forms.Control.Click> event and invokes it late-bound, passing in the delegate instance.</span></span> <span data-ttu-id="0f89e-129">Argumenty muszą być przekazane jako tablica.</span><span class="sxs-lookup"><span data-stu-id="0f89e-129">The arguments must be passed as an array.</span></span>  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7. <span data-ttu-id="0f89e-130">Przetestuj zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="0f89e-130">Test the event.</span></span> <span data-ttu-id="0f89e-131">Poniższy kod przedstawia formularz zdefiniowany w przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="0f89e-131">The following code shows the form defined in the code example.</span></span> <span data-ttu-id="0f89e-132">Kliknięcie formularza wywołuje program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0f89e-132">Clicking the form invokes the event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a><span data-ttu-id="0f89e-133">Aby wygenerować procedurę obsługi zdarzeń w czasie wykonywania przy użyciu metody dynamicznej</span><span class="sxs-lookup"><span data-stu-id="0f89e-133">To generate an event handler at run time by using a dynamic method</span></span>  
  
1. <span data-ttu-id="0f89e-134">Metody obsługi zdarzeń mogą być generowane w czasie wykonywania przy użyciu uproszczonych metod dynamicznych i emisji odbicia.</span><span class="sxs-lookup"><span data-stu-id="0f89e-134">Event-handler methods can be generated at run time, using lightweight dynamic methods and reflection emit.</span></span> <span data-ttu-id="0f89e-135">Do skonstruowania procedury obsługi zdarzeń wymagany jest typ zwracany i typy parametrów delegata.</span><span class="sxs-lookup"><span data-stu-id="0f89e-135">To construct an event handler, you need the return type and parameter types of the delegate.</span></span> <span data-ttu-id="0f89e-136">Można je uzyskać, badając metodę delegata `Invoke` .</span><span class="sxs-lookup"><span data-stu-id="0f89e-136">These can be obtained by examining the delegate's `Invoke` method.</span></span> <span data-ttu-id="0f89e-137">Poniższy kod używa `GetDelegateReturnType` metod i, `GetDelegateParameterTypes` Aby uzyskać te informacje.</span><span class="sxs-lookup"><span data-stu-id="0f89e-137">The following code uses the `GetDelegateReturnType` and `GetDelegateParameterTypes` methods to obtain this information.</span></span> <span data-ttu-id="0f89e-138">Kod dla tych metod można znaleźć w sekcji przykład w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="0f89e-138">The code for these methods can be found in the Example section later in this topic.</span></span>  
  
     <span data-ttu-id="0f89e-139">Nazwa nie jest konieczna <xref:System.Reflection.Emit.DynamicMethod> , więc można użyć pustego ciągu.</span><span class="sxs-lookup"><span data-stu-id="0f89e-139">It is not necessary to name a <xref:System.Reflection.Emit.DynamicMethod>, so the empty string can be used.</span></span> <span data-ttu-id="0f89e-140">W poniższym kodzie, ostatni argument kojarzy metodę dynamiczną z bieżącym typem, dając delegata dostęp do wszystkich publicznych i prywatnych członków `Example` klasy.</span><span class="sxs-lookup"><span data-stu-id="0f89e-140">In the following code, the last argument associates the dynamic method with the current type, giving the delegate access to all the public and private members of the `Example` class.</span></span>  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2. <span data-ttu-id="0f89e-141">Generuj treść metody.</span><span class="sxs-lookup"><span data-stu-id="0f89e-141">Generate a method body.</span></span> <span data-ttu-id="0f89e-142">Ta metoda ładuje ciąg, wywołuje Przeciążenie <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> metody, która pobiera ciąg znaków, wyświetla wartość zwracaną przez stos (ponieważ program obsługi nie ma zwracanego typu) i zwraca.</span><span class="sxs-lookup"><span data-stu-id="0f89e-142">This method loads a string, calls the overload of the <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> method that takes a string, pops the return value off the stack (because the handler has no return type), and returns.</span></span> <span data-ttu-id="0f89e-143">Aby dowiedzieć się więcej o emitowaniu metod dynamicznych, zobacz [How to: define and Execute Dynamic Methods](how-to-define-and-execute-dynamic-methods.md).</span><span class="sxs-lookup"><span data-stu-id="0f89e-143">To learn more about emitting dynamic methods, see [How to: Define and Execute Dynamic Methods](how-to-define-and-execute-dynamic-methods.md).</span></span>  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3. <span data-ttu-id="0f89e-144">Ukończ metodę dynamiczną, wywołując <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="0f89e-144">Complete the dynamic method by calling its <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method.</span></span> <span data-ttu-id="0f89e-145">Użyj `add` metody dostępu, aby dodać delegata do listy wywołań dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="0f89e-145">Use the `add` accessor to add the delegate to the invocation list for the event.</span></span>  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4. <span data-ttu-id="0f89e-146">Przetestuj zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="0f89e-146">Test the event.</span></span> <span data-ttu-id="0f89e-147">Poniższy kod ładuje formularz zdefiniowany w przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="0f89e-147">The following code loads the form defined in the code example.</span></span> <span data-ttu-id="0f89e-148">Kliknięcie formularza wywołuje zarówno wstępnie zdefiniowaną procedurę obsługi zdarzeń, jak i wyemitowaną procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0f89e-148">Clicking the form invokes both the predefined event handler and the emitted event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="0f89e-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="0f89e-149">Example</span></span>  
 <span data-ttu-id="0f89e-150">Poniższy przykład kodu pokazuje, jak podłączyć istniejącą metodę do zdarzenia przy użyciu odbicia, a także jak użyć <xref:System.Reflection.Emit.DynamicMethod> klasy do emisji metody w czasie wykonywania i podłączania do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="0f89e-150">The following code example shows how to hook up an existing method to an event using reflection, and also how to use the <xref:System.Reflection.Emit.DynamicMethod> class to emit a method at run time and hook it up to an event.</span></span>  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0f89e-151">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f89e-151">See also</span></span>

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Emit.DynamicMethod>
- <xref:System.Activator.CreateInstance%2A>
- <xref:System.Delegate.CreateDelegate%2A>
- [<span data-ttu-id="0f89e-152">Instrukcje: Definiowanie i wykonywanie metod dynamicznych</span><span class="sxs-lookup"><span data-stu-id="0f89e-152">How to: Define and Execute Dynamic Methods</span></span>](how-to-define-and-execute-dynamic-methods.md)
- [<span data-ttu-id="0f89e-153">Odbicie</span><span class="sxs-lookup"><span data-stu-id="0f89e-153">Reflection</span></span>](reflection.md)

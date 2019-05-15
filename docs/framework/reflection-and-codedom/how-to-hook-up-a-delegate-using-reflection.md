---
title: 'Instrukcje: Podłączanie delegata za pomocą odbicia'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4640e776cc76ef56227858f6a4aa04e77ecbbdc
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586003"
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="80e74-102">Instrukcje: Podłączanie delegata za pomocą odbicia</span><span class="sxs-lookup"><span data-stu-id="80e74-102">How to: Hook Up a Delegate Using Reflection</span></span>
<span data-ttu-id="80e74-103">Gdy używasz odbicia można załadować i uruchomić zestawów, nie można używać funkcji języka, takich jak C# `+=` operatora lub Visual Basic [AddHandler — instrukcja](~/docs/visual-basic/language-reference/statements/addhandler-statement.md) do podłączania zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="80e74-103">When you use reflection to load and run assemblies, you cannot use language features like the C# `+=` operator or the Visual Basic [AddHandler statement](~/docs/visual-basic/language-reference/statements/addhandler-statement.md) to hook up events.</span></span> <span data-ttu-id="80e74-104">Poniższe procedury pokazują, jak dołączyć istniejącą metodę do zdarzenia przez pobranie wszystkich typów wymaganych przez odbicie, a także jak utworzyć metodę dynamiczną za pomocą odbicia emisji i podłączyć ją do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80e74-104">The following procedures show how to hook up an existing method to an event by getting all the necessary types through reflection, and how to create a dynamic method using reflection emit and hook it up to an event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="80e74-105">Innym sposobem Podłączanie delegata obsługi zdarzeń, zobacz przykład kodu dla <xref:System.Reflection.EventInfo.AddEventHandler%2A> metody <xref:System.Reflection.EventInfo> klasy.</span><span class="sxs-lookup"><span data-stu-id="80e74-105">For another way to hook up an event-handling delegate, see the code example for the <xref:System.Reflection.EventInfo.AddEventHandler%2A> method of the <xref:System.Reflection.EventInfo> class.</span></span>  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="80e74-106">Aby Podłączanie delegata za pomocą odbicia</span><span class="sxs-lookup"><span data-stu-id="80e74-106">To hook up a delegate using reflection</span></span>  
  
1. <span data-ttu-id="80e74-107">Załaduj zestaw, który zawiera typ, który wywołuje zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80e74-107">Load an assembly that contains a type that raises events.</span></span> <span data-ttu-id="80e74-108">Zestawy są zazwyczaj załadowane <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="80e74-108">Assemblies are usually loaded with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="80e74-109">W celu uproszczenia w tym przykładzie zastosowano pochodnej formularza w bieżącym zestawie, więc <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> metoda jest używana do ładowania bieżącego zestawu.</span><span class="sxs-lookup"><span data-stu-id="80e74-109">To keep this example simple, a derived form in the current assembly is used, so the <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method is used to load the current assembly.</span></span>  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2. <span data-ttu-id="80e74-110">Pobierz <xref:System.Type> obiekt reprezentujący typ i utworzyć wystąpienie typu.</span><span class="sxs-lookup"><span data-stu-id="80e74-110">Get a <xref:System.Type> object representing the type, and create an instance of the type.</span></span> <span data-ttu-id="80e74-111"><xref:System.Activator.CreateInstance%28System.Type%29> Metoda jest używana w poniższym kodzie, ponieważ formularza ma domyślnego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="80e74-111">The <xref:System.Activator.CreateInstance%28System.Type%29> method is used in the following code because the form has a default constructor.</span></span> <span data-ttu-id="80e74-112">Istnieje kilka innych przeciążeń <xref:System.Activator.CreateInstance%2A> metody można użyć, jeśli typ tworzenia nie ma domyślnego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="80e74-112">There are several other overloads of the <xref:System.Activator.CreateInstance%2A> method that you can use if the type you are creating does not have a default constructor.</span></span> <span data-ttu-id="80e74-113">Nowe wystąpienie jest przechowywany jako typ <xref:System.Object> do utrzymania fikcja że żaden element nie jest znany o zestawie.</span><span class="sxs-lookup"><span data-stu-id="80e74-113">The new instance is stored as type <xref:System.Object> to maintain the fiction that nothing is known about the assembly.</span></span> <span data-ttu-id="80e74-114">(Odbicie umożliwia pobieranie typów w zestawie, nie wiedząc o tym ich nazwy z wyprzedzeniem.)</span><span class="sxs-lookup"><span data-stu-id="80e74-114">(Reflection allows you to get the types in an assembly without knowing their names in advance.)</span></span>  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3. <span data-ttu-id="80e74-115">Pobierz <xref:System.Reflection.EventInfo> obiekt reprezentujący zdarzenia, a następnie użyj <xref:System.Reflection.EventInfo.EventHandlerType%2A> właściwości, aby uzyskać typ delegata używany do obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="80e74-115">Get an <xref:System.Reflection.EventInfo> object representing the event, and use the <xref:System.Reflection.EventInfo.EventHandlerType%2A> property to get the type of delegate used to handle the event.</span></span> <span data-ttu-id="80e74-116">W poniższym kodzie <xref:System.Reflection.EventInfo> dla <xref:System.Windows.Forms.Control.Click> uzyskuje się zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="80e74-116">In the following code, an <xref:System.Reflection.EventInfo> for the <xref:System.Windows.Forms.Control.Click> event is obtained.</span></span>  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4. <span data-ttu-id="80e74-117">Pobierz <xref:System.Reflection.MethodInfo> obiekt reprezentujący metodę, która obsługuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="80e74-117">Get a <xref:System.Reflection.MethodInfo> object representing the method that handles the event.</span></span> <span data-ttu-id="80e74-118">Kod programu ukończone w części przykładu w dalszej części tego tematu zawiera metodę, która pasuje do podpisu <xref:System.EventHandler> delegować, która obsługuje <xref:System.Windows.Forms.Control.Click> zdarzenia, ale można również wygenerować metod dynamicznych w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="80e74-118">The complete program code in the Example section later in this topic contains a method that matches the signature of the <xref:System.EventHandler> delegate, which handles the <xref:System.Windows.Forms.Control.Click> event, but you can also generate dynamic methods at run time.</span></span> <span data-ttu-id="80e74-119">Aby uzyskać szczegółowe informacje zobacz procedurę towarzyszących do wygenerowania procedury obsługi zdarzeń w czasie wykonywania przy użyciu dynamicznej metody.</span><span class="sxs-lookup"><span data-stu-id="80e74-119">For details, see the accompanying procedure, for generating an event handler at run time by using a dynamic method.</span></span>  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5. <span data-ttu-id="80e74-120">Utwórz wystąpienie delegata, za pomocą <xref:System.Delegate.CreateDelegate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="80e74-120">Create an instance of the delegate, using the <xref:System.Delegate.CreateDelegate%2A> method.</span></span> <span data-ttu-id="80e74-121">Ta metoda jest statyczna (`Shared` w języku Visual Basic), dlatego wymagane jest podanie typu delegata.</span><span class="sxs-lookup"><span data-stu-id="80e74-121">This method is static (`Shared` in Visual Basic), so the delegate type must be supplied.</span></span> <span data-ttu-id="80e74-122">Za pomocą przeciążenia <xref:System.Delegate.CreateDelegate%2A> o <xref:System.Reflection.MethodInfo> jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="80e74-122">Using the overloads of <xref:System.Delegate.CreateDelegate%2A> that take a <xref:System.Reflection.MethodInfo> is recommended.</span></span>  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6. <span data-ttu-id="80e74-123">Pobierz `add` metody dostępu i wywoływanie aby zaczepić zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="80e74-123">Get the `add` accessor method and invoke it to hook up the event.</span></span> <span data-ttu-id="80e74-124">Wszystkie zdarzenia mają `add` metody dostępu i `remove` metody dostępu są ukrywane w składni języków wysokiego poziomu.</span><span class="sxs-lookup"><span data-stu-id="80e74-124">All events have an `add` accessor and a `remove` accessor, which are hidden by the syntax of high-level languages.</span></span> <span data-ttu-id="80e74-125">Na przykład C# używa `+=` podpinanie zdarzeń i Visual Basic używa operatora [AddHandler — instrukcja](~/docs/visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="80e74-125">For example, C# uses the `+=` operator to hook up events, and Visual Basic uses the [AddHandler statement](~/docs/visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="80e74-126">Poniższy kod pobiera `add` akcesor <xref:System.Windows.Forms.Control.Click> zdarzeń, a następnie wywołuje on z późnym wiązaniem, przekazując to wystąpienie delegata.</span><span class="sxs-lookup"><span data-stu-id="80e74-126">The following code gets the `add` accessor of the <xref:System.Windows.Forms.Control.Click> event and invokes it late-bound, passing in the delegate instance.</span></span> <span data-ttu-id="80e74-127">Argumenty muszą być przekazywane jako tablica.</span><span class="sxs-lookup"><span data-stu-id="80e74-127">The arguments must be passed as an array.</span></span>  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7. <span data-ttu-id="80e74-128">Przetestuj zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80e74-128">Test the event.</span></span> <span data-ttu-id="80e74-129">Poniższy kod przedstawia formularz zdefiniowany w przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="80e74-129">The following code shows the form defined in the code example.</span></span> <span data-ttu-id="80e74-130">Klikając formularz wywołuje program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="80e74-130">Clicking the form invokes the event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>   
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a><span data-ttu-id="80e74-131">Aby wygenerować procedurę obsługi zdarzeń w czasie wykonywania przy użyciu dynamicznej metody</span><span class="sxs-lookup"><span data-stu-id="80e74-131">To generate an event handler at run time by using a dynamic method</span></span>  
  
1. <span data-ttu-id="80e74-132">W czasie wykonywania za pomocą uproszczonego metody dynamiczne mogą być generowane metody obsługi zdarzeń i emisji odbicia.</span><span class="sxs-lookup"><span data-stu-id="80e74-132">Event-handler methods can be generated at run time, using lightweight dynamic methods and reflection emit.</span></span> <span data-ttu-id="80e74-133">Do utworzenia programu obsługi zdarzeń, potrzebne jest typ zwracany i typy parametrów delegata.</span><span class="sxs-lookup"><span data-stu-id="80e74-133">To construct an event handler, you need the return type and parameter types of the delegate.</span></span> <span data-ttu-id="80e74-134">Te można uzyskać, sprawdzając pełnomocnika `Invoke` metody.</span><span class="sxs-lookup"><span data-stu-id="80e74-134">These can be obtained by examining the delegate's `Invoke` method.</span></span> <span data-ttu-id="80e74-135">Poniższy kod używa `GetDelegateReturnType` i `GetDelegateParameterTypes` metody, aby uzyskać te informacje.</span><span class="sxs-lookup"><span data-stu-id="80e74-135">The following code uses the `GetDelegateReturnType` and `GetDelegateParameterTypes` methods to obtain this information.</span></span> <span data-ttu-id="80e74-136">Kod dla tych metod można znaleźć w części przykładu w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="80e74-136">The code for these methods can be found in the Example section later in this topic.</span></span>  
  
     <span data-ttu-id="80e74-137">Nie jest konieczne nazwanie <xref:System.Reflection.Emit.DynamicMethod>, więc pusty ciąg może być używany.</span><span class="sxs-lookup"><span data-stu-id="80e74-137">It is not necessary to name a <xref:System.Reflection.Emit.DynamicMethod>, so the empty string can be used.</span></span> <span data-ttu-id="80e74-138">W poniższym kodzie, ostatni argument kojarzy metodę dynamiczną z bieżącym typem, zapewniając obiektu delegowanego dostępu do wszystkich publicznych i prywatnych składowych `Example` klasy.</span><span class="sxs-lookup"><span data-stu-id="80e74-138">In the following code, the last argument associates the dynamic method with the current type, giving the delegate access to all the public and private members of the `Example` class.</span></span>  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2. <span data-ttu-id="80e74-139">Generowanie treści metody.</span><span class="sxs-lookup"><span data-stu-id="80e74-139">Generate a method body.</span></span> <span data-ttu-id="80e74-140">Ta metoda ładuje ciągu, wywołuje przeciążenia <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> metody, która przyjmuje ciąg, pojawi się wartość zwracaną ze stosu (ponieważ program obsługi nie ma zwracanego typu), a następnie zwraca.</span><span class="sxs-lookup"><span data-stu-id="80e74-140">This method loads a string, calls the overload of the <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> method that takes a string, pops the return value off the stack (because the handler has no return type), and returns.</span></span> <span data-ttu-id="80e74-141">Aby dowiedzieć się więcej na temat emitowanie metod dynamicznych, zobacz [jak: Definiowanie i wykonywanie metod dynamicznych](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md).</span><span class="sxs-lookup"><span data-stu-id="80e74-141">To learn more about emitting dynamic methods, see [How to: Define and Execute Dynamic Methods](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md).</span></span>  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3. <span data-ttu-id="80e74-142">Wykonaj metodę dynamiczną, wywołując jego <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="80e74-142">Complete the dynamic method by calling its <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method.</span></span> <span data-ttu-id="80e74-143">Użyj `add` dostępu, aby dodać delegata do listy wywołań dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80e74-143">Use the `add` accessor to add the delegate to the invocation list for the event.</span></span>  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4. <span data-ttu-id="80e74-144">Przetestuj zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80e74-144">Test the event.</span></span> <span data-ttu-id="80e74-145">Poniższy kod ładuje formularz zdefiniowany w przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="80e74-145">The following code loads the form defined in the code example.</span></span> <span data-ttu-id="80e74-146">Klikając formularz wywołuje program obsługi zdarzeń wstępnie zdefiniowanych i program obsługi zdarzeń emitowany.</span><span class="sxs-lookup"><span data-stu-id="80e74-146">Clicking the form invokes both the predefined event handler and the emitted event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="80e74-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="80e74-147">Example</span></span>  
 <span data-ttu-id="80e74-148">Poniższy przykład kodu pokazuje, jak dołączyć istniejącą metodę do zdarzenia przy użyciu odbicia, a także jak używać <xref:System.Reflection.Emit.DynamicMethod> klasy, aby emitować metodę w czasie wykonywania i podłączyć ją do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="80e74-148">The following code example shows how to hook up an existing method to an event using reflection, and also how to use the <xref:System.Reflection.Emit.DynamicMethod> class to emit a method at run time and hook it up to an event.</span></span>  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="80e74-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80e74-149">See also</span></span>

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Emit.DynamicMethod>
- <xref:System.Activator.CreateInstance%2A>
- <xref:System.Delegate.CreateDelegate%2A>
- [<span data-ttu-id="80e74-150">Instrukcje: Definiowanie i wykonywanie metod dynamicznych</span><span class="sxs-lookup"><span data-stu-id="80e74-150">How to: Define and Execute Dynamic Methods</span></span>](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md)
- [<span data-ttu-id="80e74-151">Odbicie</span><span class="sxs-lookup"><span data-stu-id="80e74-151">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)

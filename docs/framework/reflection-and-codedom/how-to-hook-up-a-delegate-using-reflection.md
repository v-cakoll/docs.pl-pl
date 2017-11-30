---
title: "Porady: podłączanie delegata za pomocą odbicia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], adding event handlers with reflection
- reflection, adding event-handler delegates
- delegates [.NET Framework], adding event handlers with reflection
ms.assetid: 076ee62d-a964-449e-a447-c31b33518b81
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 72d2061d8e4432422eeb2a30c916af7e254b4f81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="7a777-102">Porady: podłączanie delegata za pomocą odbicia</span><span class="sxs-lookup"><span data-stu-id="7a777-102">How to: Hook Up a Delegate Using Reflection</span></span>
<span data-ttu-id="7a777-103">Gdy używasz odbicia do ładowania i uruchamiania zestawy, nie można używać funkcji języka, takich jak C# `+=` operator lub Visual Basic [AddHandler — instrukcja](~/docs/visual-basic/language-reference/statements/addhandler-statement.md) do podpinanie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7a777-103">When you use reflection to load and run assemblies, you cannot use language features like the C# `+=` operator or the Visual Basic [AddHandler statement](~/docs/visual-basic/language-reference/statements/addhandler-statement.md) to hook up events.</span></span> <span data-ttu-id="7a777-104">Poniższe procedury pokazują, jak Podłączanie istniejącą metodę do zdarzenia, uzyskując wszystkie wymagane typy przez odbicie i tworzenie dynamicznych metoda, za pomocą odbicia Emituj i podłącz go do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="7a777-104">The following procedures show how to hook up an existing method to an event by getting all the necessary types through reflection, and how to create a dynamic method using reflection emit and hook it up to an event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a777-105">Innym sposobem Podłączanie delegata obsługi zdarzeń, zobacz przykład kodu <xref:System.Reflection.EventInfo.AddEventHandler%2A> metody <xref:System.Reflection.EventInfo> klasy.</span><span class="sxs-lookup"><span data-stu-id="7a777-105">For another way to hook up an event-handling delegate, see the code example for the <xref:System.Reflection.EventInfo.AddEventHandler%2A> method of the <xref:System.Reflection.EventInfo> class.</span></span>  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="7a777-106">Aby Podłączanie delegata za pomocą odbicia</span><span class="sxs-lookup"><span data-stu-id="7a777-106">To hook up a delegate using reflection</span></span>  
  
1.  <span data-ttu-id="7a777-107">Załaduj zestaw, który zawiera typ, który informuje o zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="7a777-107">Load an assembly that contains a type that raises events.</span></span> <span data-ttu-id="7a777-108">Zestawy są zazwyczaj ładowane z <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="7a777-108">Assemblies are usually loaded with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7a777-109">Aby zachować w tym przykładzie jest proste, pochodnych formularza w bieżącym zestawie jest używana, więc <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> metoda jest używana do załadowania bieżącego zestawu.</span><span class="sxs-lookup"><span data-stu-id="7a777-109">To keep this example simple, a derived form in the current assembly is used, so the <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method is used to load the current assembly.</span></span>  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2.  <span data-ttu-id="7a777-110">Pobierz <xref:System.Type> obiekt reprezentujący typ i utworzyć wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="7a777-110">Get a <xref:System.Type> object representing the type, and create an instance of the type.</span></span> <span data-ttu-id="7a777-111"><xref:System.Activator.CreateInstance%28System.Type%29> Metoda jest używana w poniższym kodzie, ponieważ formularz ma konstruktora domyślnego.</span><span class="sxs-lookup"><span data-stu-id="7a777-111">The <xref:System.Activator.CreateInstance%28System.Type%29> method is used in the following code because the form has a default constructor.</span></span> <span data-ttu-id="7a777-112">Istnieje kilka przeciążeń z <xref:System.Activator.CreateInstance%2A> metody można użyć, jeśli tworzysz typ nie ma domyślnego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="7a777-112">There are several other overloads of the <xref:System.Activator.CreateInstance%2A> method that you can use if the type you are creating does not have a default constructor.</span></span> <span data-ttu-id="7a777-113">Nowe wystąpienie jest przechowywana jako typ <xref:System.Object> do obsługi fikcja że żaden element nie jest znany o zestawie.</span><span class="sxs-lookup"><span data-stu-id="7a777-113">The new instance is stored as type <xref:System.Object> to maintain the fiction that nothing is known about the assembly.</span></span> <span data-ttu-id="7a777-114">(Odbicia umożliwia pobieranie typów w zestawie bez wiedzy o nazwach z wyprzedzeniem.)</span><span class="sxs-lookup"><span data-stu-id="7a777-114">(Reflection allows you to get the types in an assembly without knowing their names in advance.)</span></span>  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3.  <span data-ttu-id="7a777-115">Pobierz <xref:System.Reflection.EventInfo> obiekt reprezentujący zdarzenia, a następnie użyj <xref:System.Reflection.EventInfo.EventHandlerType%2A> właściwości można pobrać typu delegata używane do obsługi zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="7a777-115">Get an <xref:System.Reflection.EventInfo> object representing the event, and use the <xref:System.Reflection.EventInfo.EventHandlerType%2A> property to get the type of delegate used to handle the event.</span></span> <span data-ttu-id="7a777-116">W poniższym kodzie <xref:System.Reflection.EventInfo> dla <xref:System.Windows.Forms.Control.Click> są uzyskiwane zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7a777-116">In the following code, an <xref:System.Reflection.EventInfo> for the <xref:System.Windows.Forms.Control.Click> event is obtained.</span></span>  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4.  <span data-ttu-id="7a777-117">Pobierz <xref:System.Reflection.MethodInfo> obiekt reprezentujący metodę, która obsługuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="7a777-117">Get a <xref:System.Reflection.MethodInfo> object representing the method that handles the event.</span></span> <span data-ttu-id="7a777-118">Kod programu pełną w sekcji przykład w dalszej części tego tematu zawiera metodę, która pasuje do podpisu <xref:System.EventHandler> delegata, która obsługuje <xref:System.Windows.Forms.Control.Click> zdarzeń, ale można również generować metod dynamicznych w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7a777-118">The complete program code in the Example section later in this topic contains a method that matches the signature of the <xref:System.EventHandler> delegate, which handles the <xref:System.Windows.Forms.Control.Click> event, but you can also generate dynamic methods at run time.</span></span> <span data-ttu-id="7a777-119">Aby uzyskać więcej informacji zobacz procedurę towarzyszący generowania program obsługi zdarzeń w czasie wykonywania za pomocą metody dynamicznej.</span><span class="sxs-lookup"><span data-stu-id="7a777-119">For details, see the accompanying procedure, for generating an event handler at run time by using a dynamic method.</span></span>  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5.  <span data-ttu-id="7a777-120">Utwórz wystąpienie obiektu delegowanego, przy użyciu <xref:System.Delegate.CreateDelegate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="7a777-120">Create an instance of the delegate, using the <xref:System.Delegate.CreateDelegate%2A> method.</span></span> <span data-ttu-id="7a777-121">Ta metoda jest statyczna (`Shared` w języku Visual Basic), dlatego należy podać typ delegata.</span><span class="sxs-lookup"><span data-stu-id="7a777-121">This method is static (`Shared` in Visual Basic), so the delegate type must be supplied.</span></span> <span data-ttu-id="7a777-122">Przy użyciu przeciążeń <xref:System.Delegate.CreateDelegate%2A> które trwają <xref:System.Reflection.MethodInfo> jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="7a777-122">Using the overloads of <xref:System.Delegate.CreateDelegate%2A> that take a <xref:System.Reflection.MethodInfo> is recommended.</span></span>  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6.  <span data-ttu-id="7a777-123">Pobierz `add` metodę dostępu i wywołać go do podłączenie zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="7a777-123">Get the `add` accessor method and invoke it to hook up the event.</span></span> <span data-ttu-id="7a777-124">Wszystkie zdarzenia mają `add` metody dostępu i `remove` dostępu, które zostały ukryte za składnię języków wysokiego poziomu.</span><span class="sxs-lookup"><span data-stu-id="7a777-124">All events have an `add` accessor and a `remove` accessor, which are hidden by the syntax of high-level languages.</span></span> <span data-ttu-id="7a777-125">Na przykład C# używa `+=` operatora podpinanie zdarzeń i używa języka Visual Basic [AddHandler — instrukcja](~/docs/visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7a777-125">For example, C# uses the `+=` operator to hook up events, and Visual Basic uses the [AddHandler statement](~/docs/visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="7a777-126">Poniższy kod pobiera `add` akcesor <xref:System.Windows.Forms.Control.Click> zdarzeń i wywołuje ona późnym wiązaniem, przekazując to wystąpienie obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="7a777-126">The following code gets the `add` accessor of the <xref:System.Windows.Forms.Control.Click> event and invokes it late-bound, passing in the delegate instance.</span></span> <span data-ttu-id="7a777-127">Argumenty muszą być przekazywane jako tablica.</span><span class="sxs-lookup"><span data-stu-id="7a777-127">The arguments must be passed as an array.</span></span>  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7.  <span data-ttu-id="7a777-128">Przetestuj zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="7a777-128">Test the event.</span></span> <span data-ttu-id="7a777-129">Poniższy kod przedstawia formularz zdefiniowany w przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="7a777-129">The following code shows the form defined in the code example.</span></span> <span data-ttu-id="7a777-130">Klikając formularz wywołuje program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7a777-130">Clicking the form invokes the event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>   
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a><span data-ttu-id="7a777-131">Aby wygenerować program obsługi zdarzeń w czasie wykonywania za pomocą metody dynamiczne</span><span class="sxs-lookup"><span data-stu-id="7a777-131">To generate an event handler at run time by using a dynamic method</span></span>  
  
1.  <span data-ttu-id="7a777-132">Metody obsługi zdarzeń mogą być generowane w czasie wykonywania za pomocą uproszczonego metod dynamicznych i emisja odbicia.</span><span class="sxs-lookup"><span data-stu-id="7a777-132">Event-handler methods can be generated at run time, using lightweight dynamic methods and reflection emit.</span></span> <span data-ttu-id="7a777-133">Aby utworzyć program obsługi zdarzeń, należy typ zwracany i typy parametrów delegata.</span><span class="sxs-lookup"><span data-stu-id="7a777-133">To construct an event handler, you need the return type and parameter types of the delegate.</span></span> <span data-ttu-id="7a777-134">Te można uzyskać, sprawdzając delegata `Invoke` metody.</span><span class="sxs-lookup"><span data-stu-id="7a777-134">These can be obtained by examining the delegate's `Invoke` method.</span></span> <span data-ttu-id="7a777-135">Poniższy kod używa `GetDelegateReturnType` i `GetDelegateParameterTypes` metody, aby uzyskać te informacje.</span><span class="sxs-lookup"><span data-stu-id="7a777-135">The following code uses the `GetDelegateReturnType` and `GetDelegateParameterTypes` methods to obtain this information.</span></span> <span data-ttu-id="7a777-136">Kod dla tych metod można znaleźć w sekcji przykład w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="7a777-136">The code for these methods can be found in the Example section later in this topic.</span></span>  
  
     <span data-ttu-id="7a777-137">Nie jest konieczne nazwanie <xref:System.Reflection.Emit.DynamicMethod>, więc można pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="7a777-137">It is not necessary to name a <xref:System.Reflection.Emit.DynamicMethod>, so the empty string can be used.</span></span> <span data-ttu-id="7a777-138">W poniższym kodzie ostatni argument kojarzy z bieżącym typem, podając delegat dostęp do wszystkich publicznych i prywatnych elementów członkowskich z metody dynamicznej `Example` klasy.</span><span class="sxs-lookup"><span data-stu-id="7a777-138">In the following code, the last argument associates the dynamic method with the current type, giving the delegate access to all the public and private members of the `Example` class.</span></span>  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2.  <span data-ttu-id="7a777-139">Generowanie treści metody.</span><span class="sxs-lookup"><span data-stu-id="7a777-139">Generate a method body.</span></span> <span data-ttu-id="7a777-140">Ta metoda ładuje ciągiem, wywołują przeciążenia <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> metody pobierającej ciąg, będzie wyświetlana wartość zwracana ze stosu (ponieważ program obsługi nie ma zwracanego typu) i zwraca.</span><span class="sxs-lookup"><span data-stu-id="7a777-140">This method loads a string, calls the overload of the <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> method that takes a string, pops the return value off the stack (because the handler has no return type), and returns.</span></span> <span data-ttu-id="7a777-141">Aby dowiedzieć się więcej na temat emitowanie metod dynamicznych, zobacz [porady: definiowanie i wykonywanie metod dynamicznych](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md).</span><span class="sxs-lookup"><span data-stu-id="7a777-141">To learn more about emitting dynamic methods, see [How to: Define and Execute Dynamic Methods](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md).</span></span>  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3.  <span data-ttu-id="7a777-142">Zakończenie metody dynamicznej przez wywołanie jego <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="7a777-142">Complete the dynamic method by calling its <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method.</span></span> <span data-ttu-id="7a777-143">Użyj `add` dostępu, aby dodać do listy wywołania zdarzenia delegata.</span><span class="sxs-lookup"><span data-stu-id="7a777-143">Use the `add` accessor to add the delegate to the invocation list for the event.</span></span>  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4.  <span data-ttu-id="7a777-144">Przetestuj zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="7a777-144">Test the event.</span></span> <span data-ttu-id="7a777-145">Poniższy kod załaduje formularz zdefiniowany w przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="7a777-145">The following code loads the form defined in the code example.</span></span> <span data-ttu-id="7a777-146">Klikając formularz wywołuje zarówno programu obsługi zdarzeń wstępnie zdefiniowanych i obsługi zdarzeń emitowany.</span><span class="sxs-lookup"><span data-stu-id="7a777-146">Clicking the form invokes both the predefined event handler and the emitted event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="7a777-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="7a777-147">Example</span></span>  
 <span data-ttu-id="7a777-148">Poniższy przykład kodu pokazuje, jak podłączenie istniejącą metodę ze zdarzeniem przy użyciu odbicia, a także sposób użycia <xref:System.Reflection.Emit.DynamicMethod> klasy Emituj metody w czasie wykonywania i podłącz go do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="7a777-148">The following code example shows how to hook up an existing method to an event using reflection, and also how to use the <xref:System.Reflection.Emit.DynamicMethod> class to emit a method at run time and hook it up to an event.</span></span>  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7a777-149">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="7a777-149">Compiling the Code</span></span>  
  
-   <span data-ttu-id="7a777-150">Zawiera kod C# `using` instrukcje (`Imports` w języku Visual Basic) niezbędne do kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7a777-150">The code contains the C# `using` statements (`Imports` in Visual Basic) necessary for compilation.</span></span>  
  
-   <span data-ttu-id="7a777-151">Nie odwołania do zestawów dodatkowe są niezbędne do kompilacji z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="7a777-151">No additional assembly references are required for compiling from the command line.</span></span> <span data-ttu-id="7a777-152">W programie Visual Studio możesz dodać odwołania do System.Windows.Forms.dll, ponieważ w tym przykładzie jest aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="7a777-152">In Visual Studio you must add a reference to System.Windows.Forms.dll because this example is a console application.</span></span>  
  
-   <span data-ttu-id="7a777-153">Kompilowanie kodu w wierszu polecenia przy użyciu csc.exe, vbc.exe lub cl.exe.</span><span class="sxs-lookup"><span data-stu-id="7a777-153">Compile the code at the command line using csc.exe, vbc.exe, or cl.exe.</span></span> <span data-ttu-id="7a777-154">Aby skompilować kod w programie Visual Studio, należy umieścić w szablonie Projekt aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="7a777-154">To compile the code in Visual Studio, place it in a console application project template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a777-155">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7a777-155">See Also</span></span>  
 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.Emit.DynamicMethod>  
 <xref:System.Activator.CreateInstance%2A>  
 <xref:System.Delegate.CreateDelegate%2A>  
 [<span data-ttu-id="7a777-156">Porady: definiowanie i wykonywanie metod dynamicznych</span><span class="sxs-lookup"><span data-stu-id="7a777-156">How to: Define and Execute Dynamic Methods</span></span>](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md)  
 [<span data-ttu-id="7a777-157">Odbicie</span><span class="sxs-lookup"><span data-stu-id="7a777-157">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)

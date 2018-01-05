---
title: Migrowanie aplikacji ze Sklepu Windows do architektury .NET Native
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
caps.latest.revision: "29"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ce23d66f79f94af74250cff137499f6c8b1582ac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="migrating-your-windows-store-app-to-net-native"></a><span data-ttu-id="06383-102">Migrowanie aplikacji ze Sklepu Windows do architektury .NET Native</span><span class="sxs-lookup"><span data-stu-id="06383-102">Migrating Your Windows Store App to .NET Native</span></span>
[!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="06383-103">zawiera statyczny kompilacji aplikacji w Sklepie Windows lub na komputerze dewelopera.</span><span class="sxs-lookup"><span data-stu-id="06383-103"> provides static compilation of apps in the Windows Store or on the developer’s computer.</span></span> <span data-ttu-id="06383-104">Ta różni się od kompilacji dynamicznej wykonywane dla aplikacji ze Sklepu Windows za pomocą kompilatora just-in-time (JIT) lub [Generator obrazu natywnego (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) na urządzeniu.</span><span class="sxs-lookup"><span data-stu-id="06383-104">This differs from the dynamic compilation performed for Windows Store apps by the just-in-time (JIT) compiler or the [Native Image Generator (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) on the device.</span></span> <span data-ttu-id="06383-105">Pomimo różnic [!INCLUDE[net_native](../../../includes/net-native-md.md)] próbuje zachować zgodność z [.NET dla Sklepu Windows apps](http://msdn.microsoft.com/library/windows/apps/br230302.aspx).</span><span class="sxs-lookup"><span data-stu-id="06383-105">Despite the differences, [!INCLUDE[net_native](../../../includes/net-native-md.md)] tries to maintain compatibility with the [.NET for Windows Store apps](http://msdn.microsoft.com/library/windows/apps/br230302.aspx).</span></span> <span data-ttu-id="06383-106">W większości przypadków rzeczy, które działają w aplikacjach .NET dla Sklepu Windows również współpracować z [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="06383-106">For the most part, things that work on the .NET for Windows Store apps also work with [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  <span data-ttu-id="06383-107">Jednak w niektórych przypadkach może się pojawić zmiany zachowania.</span><span class="sxs-lookup"><span data-stu-id="06383-107">However, in some cases, you may encounter behavioral changes.</span></span> <span data-ttu-id="06383-108">W tym dokumencie omówiono następujące różnice między standardowych aplikacji .NET dla Sklepu Windows i [!INCLUDE[net_native](../../../includes/net-native-md.md)] w następujących obszarach:</span><span class="sxs-lookup"><span data-stu-id="06383-108">This document discusses these differences between the standard .NET for Windows Store apps and [!INCLUDE[net_native](../../../includes/net-native-md.md)] in the following areas:</span></span>  
  
-   [<span data-ttu-id="06383-109">Różnice ogólne w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="06383-109">General runtime differences</span></span>](#Runtime)  
  
-   [<span data-ttu-id="06383-110">Dynamiczne różnice programowania</span><span class="sxs-lookup"><span data-stu-id="06383-110">Dynamic programming differences</span></span>](#Dynamic)  
  
-   [<span data-ttu-id="06383-111">Inne różnice związane z odbiciem</span><span class="sxs-lookup"><span data-stu-id="06383-111">Other reflection-related differences</span></span>](#Reflection)  
  
-   [<span data-ttu-id="06383-112">Nieobsługiwane scenariusze i interfejsów API</span><span class="sxs-lookup"><span data-stu-id="06383-112">Unsupported scenarios and APIs</span></span>](#Unsupported)  
  
-   [<span data-ttu-id="06383-113">Różnice w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="06383-113">Visual Studio differences</span></span>](#VS)  
  
<a name="Runtime"></a>   
## <a name="general-runtime-differences"></a><span data-ttu-id="06383-114">Różnice ogólne w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="06383-114">General runtime differences</span></span>  
  
-   <span data-ttu-id="06383-115">Wyjątki, takich jak <xref:System.TypeLoadException>, który zgłoszony przez kompilator JIT, gdy aplikacja jest uruchamiana na wspólnej aparatu plików wykonywalnych języka (wspólnego CLR) zwykle spowodować błędy kompilacji podczas przetwarzania przez [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="06383-115">Exceptions, such as <xref:System.TypeLoadException>, that are thrown by the JIT compiler when an app runs on the common language runtime (CLR) generally result in compile-time errors when processed by [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
-   <span data-ttu-id="06383-116">Nie wywołuj <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> metody z wątku interfejsu użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="06383-116">Don't call the <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method from an app's UI thread.</span></span> <span data-ttu-id="06383-117">Może to doprowadzić do zakleszczenia w [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="06383-117">This can result in a deadlock on [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
-   <span data-ttu-id="06383-118">Nie należy polegać na porządkowanie wywołania konstruktora klasy statycznej.</span><span class="sxs-lookup"><span data-stu-id="06383-118">Don't rely on static class constructor invocation ordering.</span></span> <span data-ttu-id="06383-119">W [!INCLUDE[net_native](../../../includes/net-native-md.md)], kolejność wywołania jest inna niż kolejność na standardowe środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="06383-119">In [!INCLUDE[net_native](../../../includes/net-native-md.md)], the invocation order is different from the order on the standard runtime.</span></span> <span data-ttu-id="06383-120">(Nawet w przypadku standardowego środowiska uruchomieniowego, nie należy traktować rzędu wykonywania konstruktorów statycznych klas.)</span><span class="sxs-lookup"><span data-stu-id="06383-120">(Even with the standard runtime, you shouldn't rely on the order of execution of static class constructors.)</span></span>  
  
-   <span data-ttu-id="06383-121">Nieskończone pętle bez nawiązywania połączenia (na przykład `while(true);`) w którymkolwiek wątku mogą powodować aplikacji do zatrzymania.</span><span class="sxs-lookup"><span data-stu-id="06383-121">Infinite looping without making a call (for example, `while(true);`) on any thread may bring the app to a halt.</span></span> <span data-ttu-id="06383-122">Podobnie duża lub nieskończone czeka może zwrócić aplikacji do zatrzymania.</span><span class="sxs-lookup"><span data-stu-id="06383-122">Similarly, large or infinite waits may bring the app to a halt.</span></span>  
  
-   <span data-ttu-id="06383-123">Niektórych cykle ogólne inicjowanie nie zgłaszają wyjątki [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="06383-123">Certain generic initialization cycles don't throw exceptions in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="06383-124">Na przykład poniższy kod zgłasza <xref:System.TypeLoadException> wyjątek na standardowe środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="06383-124">For example, the following code throws a <xref:System.TypeLoadException> exception on the standard CLR.</span></span> <span data-ttu-id="06383-125">W [!INCLUDE[net_native](../../../includes/net-native-md.md)], nie.</span><span class="sxs-lookup"><span data-stu-id="06383-125">In [!INCLUDE[net_native](../../../includes/net-native-md.md)], it doesn't.</span></span>  
  
     [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]  
  
-   <span data-ttu-id="06383-126">W niektórych przypadkach [!INCLUDE[net_native](../../../includes/net-native-md.md)] zapewnia różne implementacje bibliotek klas .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="06383-126">In some cases, [!INCLUDE[net_native](../../../includes/net-native-md.md)] provides different implementations of .NET Framework class libraries.</span></span> <span data-ttu-id="06383-127">Obiektu zwróconego z metody zawsze będzie implementować członków zwrócony typ.</span><span class="sxs-lookup"><span data-stu-id="06383-127">An object returned from a method will always implement the members of the returned type.</span></span> <span data-ttu-id="06383-128">Jednak ponieważ jego implementacja zapasowego jest inny, nie można rzutować na ten sam zestaw typów, jak na innych platformach, .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="06383-128">However, since its backing implementation is different, you may not be able to cast it to the same set of types as you could on other .NET Framework platforms.</span></span> <span data-ttu-id="06383-129">Na przykład w niektórych przypadkach nie można rzutować <xref:System.Collections.Generic.IEnumerable%601> obiektu interfejsu zwracane przez metody takie jak <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> lub <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> do `T[]`.</span><span class="sxs-lookup"><span data-stu-id="06383-129">For example, in some cases, you may not be able to cast the <xref:System.Collections.Generic.IEnumerable%601> interface object returned by methods such as <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> or <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> to `T[]`.</span></span>  
  
-   <span data-ttu-id="06383-130">Pamięć podręczna WinInet nie jest włączona domyślnie w aplikacjach .NET dla Sklepu Windows, ale nie znajduje się na [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="06383-130">The WinInet cache isn't enabled by default on .NET for Windows Store apps, but it is on [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="06383-131">Zwiększa wydajność, ale ma wpływ zestawu pracy.</span><span class="sxs-lookup"><span data-stu-id="06383-131">This improves performance but has working set implications.</span></span> <span data-ttu-id="06383-132">Nie są wymagane nie akcje projektanta.</span><span class="sxs-lookup"><span data-stu-id="06383-132">No developer action is necessary.</span></span>  
  
<a name="Dynamic"></a>   
## <a name="dynamic-programming-differences"></a><span data-ttu-id="06383-133">Dynamiczne różnice programowania</span><span class="sxs-lookup"><span data-stu-id="06383-133">Dynamic programming differences</span></span>  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="06383-134">statycznie łączy w kodzie z programu .NET Framework, aby kod lokalnej dla aplikacji o maksymalnej wydajności.</span><span class="sxs-lookup"><span data-stu-id="06383-134"> statically links in code from the .NET Framework to make the code app-local for maximum performance.</span></span> <span data-ttu-id="06383-135">Rozmiary binarne jednak pozostają mały, całą .NET Framework nie można przełączyć.</span><span class="sxs-lookup"><span data-stu-id="06383-135">However, binary sizes have to remain small, so the entire .NET Framework can't be brought in.</span></span> <span data-ttu-id="06383-136">[!INCLUDE[net_native](../../../includes/net-native-md.md)] Kompilatora usuwa to ograniczenie przy użyciu reduktor zależności, która usuwa odwołania do nieużywanych kodu.</span><span class="sxs-lookup"><span data-stu-id="06383-136">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler resolves this limitation by using a dependency reducer that removes references to unused code.</span></span> <span data-ttu-id="06383-137">Jednak [!INCLUDE[net_native](../../../includes/net-native-md.md)] nie może zachować lub generowania niektóre informacje o typie i kod tych informacji nie można wywnioskować statycznie w czasie kompilacji, ale zamiast tego jest pobierany dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="06383-137">However, [!INCLUDE[net_native](../../../includes/net-native-md.md)] might not maintain or generate some type information and code when that information can't be inferred statically at compile time, but instead is retrieved dynamically at runtime.</span></span>  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="06383-138">Włącz dynamiczne programowanie i odbicia.</span><span class="sxs-lookup"><span data-stu-id="06383-138"> does enable reflection and dynamic programming.</span></span> <span data-ttu-id="06383-139">Jednak nie wszystkie typy mogą być oznaczane w celu odbicia, ponieważ może to być rozmiarowi wygenerowanego kodu za duży (szczególnie, ponieważ jest obsługiwana w czasie wykonywania odbicia w publicznych interfejsach API w programie .NET Framework).</span><span class="sxs-lookup"><span data-stu-id="06383-139">However, not all types can be marked for reflection, because this would make the generated code size too large (especially because reflecting on public APIs in the .NET Framework is supported).</span></span> <span data-ttu-id="06383-140">[!INCLUDE[net_native](../../../includes/net-native-md.md)] Kompilatora sprawia, że inteligentne wybory dotyczące typów powinna obsługiwać odbicia, a zachowuje metadane i generuje kod tylko w przypadku tych typów.</span><span class="sxs-lookup"><span data-stu-id="06383-140">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler makes smart choices about which types should support reflection, and it keeps the metadata and generates code only for those types.</span></span>  
  
 <span data-ttu-id="06383-141">Powiązanie danych wymaga na przykład aplikacja może mieć możliwość mapowania nazw właściwości do funkcji.</span><span class="sxs-lookup"><span data-stu-id="06383-141">For example, data binding requires an app to be able to map property names to functions.</span></span> <span data-ttu-id="06383-142">Środowisko uruchomieniowe języka wspólnego .NET dla aplikacji ze Sklepu Windows, jest automatycznie używa odbicia mieli tej możliwości typy zarządzane i publicznie dostępnych typów natywnych.</span><span class="sxs-lookup"><span data-stu-id="06383-142">In .NET for Windows Store apps, the common language runtime automatically uses reflection to provide this capability for managed types and publicly available native types.</span></span> <span data-ttu-id="06383-143">W [!INCLUDE[net_native](../../../includes/net-native-md.md)], kompilator automatycznie uwzględnia metadanych dla typów, do których powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="06383-143">In [!INCLUDE[net_native](../../../includes/net-native-md.md)], the compiler automatically includes metadata for types to which you bind data.</span></span>  
  
 <span data-ttu-id="06383-144">[!INCLUDE[net_native](../../../includes/net-native-md.md)] Kompilatora może obsługiwać również często używanych typów ogólnych, takich jak <xref:System.Collections.Generic.List%601> i <xref:System.Collections.Generic.Dictionary%602>, która pracy bez żadnych wskazówek dotyczących serwerów lub dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="06383-144">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler can also handle commonly used generic types such as <xref:System.Collections.Generic.List%601> and <xref:System.Collections.Generic.Dictionary%602>, which work without requiring any hints or directives.</span></span> <span data-ttu-id="06383-145">[Dynamiczne](~/docs/csharp/language-reference/keywords/dynamic.md) — słowo kluczowe jest również obsługiwany w ramach pewnych ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="06383-145">The [dynamic](~/docs/csharp/language-reference/keywords/dynamic.md) keyword is also supported within certain limits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06383-146">Należy przetestować wszystkie ścieżki kodu dynamiczne dokładnie podczas przenoszenia aplikacji [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="06383-146">You should test all dynamic code paths thoroughly when porting your app to [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
 <span data-ttu-id="06383-147">Konfigurację domyślną dla [!INCLUDE[net_native](../../../includes/net-native-md.md)] jest wystarczająca dla większość deweloperów, ale niektórzy deweloperzy mogą chcieć dokładnej strojenia ich konfiguracji przy użyciu dyrektyw środowiska uruchomieniowego (. rd.xml) pliku.</span><span class="sxs-lookup"><span data-stu-id="06383-147">The default configuration for [!INCLUDE[net_native](../../../includes/net-native-md.md)] is sufficient for most developers, but some developers might want to fine- tune their configurations by using a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="06383-148">Ponadto, w niektórych przypadkach [!INCLUDE[net_native](../../../includes/net-native-md.md)] kompilatora jest nie można ustalić metadanych, które muszą być dostępne w celu odbicia i zależy od wskazówek, szczególnie w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="06383-148">In addition, in some cases, the [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler is unable to determine which metadata must be available for reflection and relies on hints, particularly in the following cases:</span></span>  
  
-   <span data-ttu-id="06383-149">Niektóre konstrukcje, takich jak <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> i <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> nie można ustalić statycznie.</span><span class="sxs-lookup"><span data-stu-id="06383-149">Some constructs like <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> and <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> can't be determined statically.</span></span>  
  
-   <span data-ttu-id="06383-150">Kompilator nie może ustalić wystąpień, typu ogólnego, który chcesz uwzględnić musi być określony przez dyrektyw środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="06383-150">Because the compiler can't determine the instantiations, a generic type that you want to reflect on has to be specified by runtime directives.</span></span> <span data-ttu-id="06383-151">To nie jest tak, ponieważ cały kod musi być uwzględniony, ale ponieważ odbicia na typach ogólnych utworzenia nieskończone cyklu (na przykład po wywołaniu metody rodzajowej w ramach typu ogólnego).</span><span class="sxs-lookup"><span data-stu-id="06383-151">This isn't just because all code must be included, but because reflection on generic types can form an infinite cycle (for example, when a generic method is invoked on a generic type).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06383-152">Dyrektyw środowiska uruchomieniowego są definiowane w dyrektyw środowiska uruchomieniowego (. rd.xml) pliku.</span><span class="sxs-lookup"><span data-stu-id="06383-152">Runtime directives are defined in a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="06383-153">Aby uzyskać ogólne informacje o korzystaniu z tego pliku, zobacz [wprowadzenie](../../../docs/framework/net-native/getting-started-with-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="06383-153">For general information about using this file, see [Getting Started](../../../docs/framework/net-native/getting-started-with-net-native.md).</span></span> <span data-ttu-id="06383-154">Aby uzyskać informacje na temat dyrektyw środowiska uruchomieniowego, zobacz [dyrektyw środowiska uruchomieniowego (rd.xml) odwołanie do pliku konfiguracji](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="06383-154">For information about the runtime directives, see [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="06383-155">zawiera również narzędzia, które pomagają ustalić, jakie typy poza domyślny zestaw powinien obsługiwać odbicia dewelopera profilowania.</span><span class="sxs-lookup"><span data-stu-id="06383-155"> also includes profiling tools that help the developer determine which types outside the default set should support reflection.</span></span>  
  
<a name="Reflection"></a>   
## <a name="other-reflection-related-differences"></a><span data-ttu-id="06383-156">Inne różnice związane z odbiciem</span><span class="sxs-lookup"><span data-stu-id="06383-156">Other reflection-related differences</span></span>  
 <span data-ttu-id="06383-157">Liczba innych poszczególnych związanych z odbiciem różnice w zachowaniu między aplikacji .NET dla Sklepu Windows i [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="06383-157">There are a number of other individual reflection-related differences in behavior between the .NET for Windows Store apps and [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
 <span data-ttu-id="06383-158">W [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="06383-158">In [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span></span>  
  
-   <span data-ttu-id="06383-159">Odbicie prywatnej przez typy i składniki w bibliotece klas programu .NET Framework nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="06383-159">Private reflection over types and members in the .NET Framework class library is not supported.</span></span> <span data-ttu-id="06383-160">Można jednak uwzględnić, za pośrednictwem własnych prywatnych typów i członków, jak również typy i składniki w bibliotekach innych firm.</span><span class="sxs-lookup"><span data-stu-id="06383-160">You can, however, reflect over your own private types and members, as well as types and members in third-party libraries.</span></span>  
  
-   <span data-ttu-id="06383-161"><xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> Właściwość poprawnie zwraca `false` dla <xref:System.Reflection.ParameterInfo> obiekt, który reprezentuje zwracaną wartość.</span><span class="sxs-lookup"><span data-stu-id="06383-161">The <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> property correctly returns `false` for a <xref:System.Reflection.ParameterInfo> object that represents a return value.</span></span> <span data-ttu-id="06383-162">W aplikacjach .NET dla Sklepu Windows zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="06383-162">In the .NET for Windows Store apps, it returns `true`.</span></span> <span data-ttu-id="06383-163">Język pośredni (IL) nie obsługuje tej bezpośrednio i pozostanie interpretacji języka.</span><span class="sxs-lookup"><span data-stu-id="06383-163">Intermediate language (IL) doesn’t support this directly, and interpretation is left to the language.</span></span>  
  
-   <span data-ttu-id="06383-164">Publiczne elementy członkowskie na <xref:System.RuntimeFieldHandle> i <xref:System.RuntimeMethodHandle> struktur nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="06383-164">Public members on the <xref:System.RuntimeFieldHandle> and <xref:System.RuntimeMethodHandle> structures aren't supported.</span></span> <span data-ttu-id="06383-165">Te typy są obsługiwane tylko w przypadku LINQ, drzew wyrażeń i Inicjowanie statyczne tablicy.</span><span class="sxs-lookup"><span data-stu-id="06383-165">These types are supported only for LINQ, expression trees, and static array initialization.</span></span>  
  
-   <span data-ttu-id="06383-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType>i <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> obejmują ukrytych elementów członkowskich w klasach podstawowych i w związku z tym mogą być zastępowane bez jawnego przesłonięcia.</span><span class="sxs-lookup"><span data-stu-id="06383-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> and <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> include hidden members in base classes and thus may be overridden without explicit overrides.</span></span> <span data-ttu-id="06383-167">Dotyczy to również innych [RuntimeReflectionExtensions.GetRuntime*](http://msdn.microsoft.com/library/system.reflection.runtimereflectionextensions_methods.aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="06383-167">This is also true of other [RuntimeReflectionExtensions.GetRuntime*](http://msdn.microsoft.com/library/system.reflection.runtimereflectionextensions_methods.aspx) methods.</span></span>  
  
-   <span data-ttu-id="06383-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType>i <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> nie zakończyć się niepowodzeniem podczas próby utworzenia niektórych kombinacji (na przykład tablicę ByRef).</span><span class="sxs-lookup"><span data-stu-id="06383-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> don't fail when you try to create certain combinations (for example, an array of byrefs).</span></span>  
  
-   <span data-ttu-id="06383-169">Odbicie nie można użyć do wywołania elementów członkowskich, które mają parametry wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="06383-169">You can't use reflection to invoke members that have pointer parameters.</span></span>  
  
-   <span data-ttu-id="06383-170">Za pomocą odbicia nie można pobrać lub ustawić pole wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="06383-170">You can't use reflection to get or set a pointer field.</span></span>  
  
-   <span data-ttu-id="06383-171">Jeśli liczba argumentów jest nieprawidłowa i typ jednego z argumentów jest nieprawidłowa, [!INCLUDE[net_native](../../../includes/net-native-md.md)] zgłasza <xref:System.ArgumentException> zamiast <xref:System.Reflection.TargetParameterCountException>.</span><span class="sxs-lookup"><span data-stu-id="06383-171">When the argument count is wrong and the type of one of the arguments is incorrect, [!INCLUDE[net_native](../../../includes/net-native-md.md)] throws an <xref:System.ArgumentException> instead of a <xref:System.Reflection.TargetParameterCountException>.</span></span>  
  
-   <span data-ttu-id="06383-172">Ogólnie rzecz biorąc serializacji binarnej wyjątków nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="06383-172">Binary serialization of exceptions is generally not supported.</span></span> <span data-ttu-id="06383-173">W związku z tym nie można serializować obiektów mogą być dodawane do <xref:System.Exception.Data%2A?displayProperty=nameWithType> słownika.</span><span class="sxs-lookup"><span data-stu-id="06383-173">As a result, non-serializable objects can be added to the <xref:System.Exception.Data%2A?displayProperty=nameWithType> dictionary.</span></span>  
  
<a name="Unsupported"></a>   
## <a name="unsupported-scenarios-and-apis"></a><span data-ttu-id="06383-174">Nieobsługiwane scenariusze i interfejsów API</span><span class="sxs-lookup"><span data-stu-id="06383-174">Unsupported scenarios and APIs</span></span>  
 <span data-ttu-id="06383-175">W poniższych sekcjach wymieniono nieobsługiwane scenariusze i interfejsy API umożliwiające tworzenie ogólne, współdziałanie i technologii, takich jak HTTPClient i Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="06383-175">The following sections list unsupported scenarios and APIs for general development, interop, and technologies such as HTTPClient and Windows Communication Foundation (WCF):</span></span>  
  
-   [<span data-ttu-id="06383-176">Programowanie ogólne</span><span class="sxs-lookup"><span data-stu-id="06383-176">General development</span></span>](#General)  
  
-   [<span data-ttu-id="06383-177">HttpClient</span><span class="sxs-lookup"><span data-stu-id="06383-177">HttpClient</span></span>](#HttpClient)  
  
-   [<span data-ttu-id="06383-178">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="06383-178">Interop</span></span>](#Interop)  
  
-   [<span data-ttu-id="06383-179">Nieobsługiwany interfejsów API</span><span class="sxs-lookup"><span data-stu-id="06383-179">Unsupported APIs</span></span>](#APIs)  
  
<a name="General"></a>   
### <a name="general-development-differences"></a><span data-ttu-id="06383-180">Programowanie Ogólne różnice</span><span class="sxs-lookup"><span data-stu-id="06383-180">General development differences</span></span>  
 <span data-ttu-id="06383-181">**Typy wartości**</span><span class="sxs-lookup"><span data-stu-id="06383-181">**Value types**</span></span>  
  
-   <span data-ttu-id="06383-182">Jeśli można zastąpić <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> i <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> metody dla typu wartości nie mogą wywoływać implementacji klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="06383-182">If you override the <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> and <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> methods for a value type, don't call the base class implementations.</span></span> <span data-ttu-id="06383-183">W aplikacjach .NET dla Sklepu Windows metody te zależą od odbicia.</span><span class="sxs-lookup"><span data-stu-id="06383-183">In .NET for Windows Store apps, these methods rely on reflection.</span></span> <span data-ttu-id="06383-184">W czasie kompilacji [!INCLUDE[net_native](../../../includes/net-native-md.md)] generuje implementację, która nie działają na podstawie czasu wykonywania odbicia.</span><span class="sxs-lookup"><span data-stu-id="06383-184">At compile time, [!INCLUDE[net_native](../../../includes/net-native-md.md)] generates an implementation that doesn't rely on runtime reflection.</span></span> <span data-ttu-id="06383-185">Oznacza to, że jeśli nie można zastąpić te dwie metody, będą one działać zgodnie z oczekiwaniami, ponieważ [!INCLUDE[net_native](../../../includes/net-native-md.md)] generuje implementacji w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="06383-185">This means that if you don't override these two methods, they will work as expected, because [!INCLUDE[net_native](../../../includes/net-native-md.md)] generates the implementation at compile time.</span></span> <span data-ttu-id="06383-186">Jednak zastępowanie tych metod, ale wywołanie implementacji klasy podstawowej powoduje wygenerowanie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="06383-186">However, overriding these methods but calling the base class implementation results in an exception.</span></span>  
  
-   <span data-ttu-id="06383-187">Typy wartości jest większy niż 1 megabajt nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="06383-187">Value types larger than one megabyte aren't supported.</span></span>  
  
-   <span data-ttu-id="06383-188">Typy wartości nie może mieć konstruktora domyślnego w [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="06383-188">Value types can't have a default constructor in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="06383-189">(C# i Visual Basic uniemożliwiają domyślnych konstruktorów w typach wartości.</span><span class="sxs-lookup"><span data-stu-id="06383-189">(C# and Visual Basic prohibit default constructors on value types.</span></span> <span data-ttu-id="06383-190">Jednak można je utworzyć w IL.)</span><span class="sxs-lookup"><span data-stu-id="06383-190">However, these can be created in IL.)</span></span>  
  
 <span data-ttu-id="06383-191">**Tablice**</span><span class="sxs-lookup"><span data-stu-id="06383-191">**Arrays**</span></span>  
  
-   <span data-ttu-id="06383-192">Tablice z dolną granicą inną niż zero nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="06383-192">Arrays with a lower bound other than zero aren't supported.</span></span> <span data-ttu-id="06383-193">Zazwyczaj te tablice są tworzone przez wywołanie metody <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="06383-193">Typically, these arrays are created by calling the <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> overload.</span></span>  
  
-   <span data-ttu-id="06383-194">Dynamiczne tworzenie tablic wielowymiarowych nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="06383-194">Dynamic creation of multidimensional arrays isn't supported.</span></span> <span data-ttu-id="06383-195">Takie tablice są zwykle tworzone przez wywołanie metody przeciążenia <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> metodę, która obejmuje `lengths` parametru lub przez wywołanie metody <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> — metoda.</span><span class="sxs-lookup"><span data-stu-id="06383-195">Such arrays are typically created by calling an overload of the <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> method that includes a `lengths` parameter, or by calling the <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="06383-196">Tablice wielowymiarowe, które mają co najmniej czterema wymiarami nie są obsługiwane; oznacza to, że ich <xref:System.Array.Rank%2A?displayProperty=nameWithType> wartość właściwości jest 4 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="06383-196">Multidimensional arrays that have four or more dimensions aren't supported; that is, their <xref:System.Array.Rank%2A?displayProperty=nameWithType> property value is four or greater.</span></span> <span data-ttu-id="06383-197">Użyj [Tablice nieregularne](~/docs/csharp/programming-guide/arrays/jagged-arrays.md) (tablicy tablic) zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="06383-197">Use [jagged arrays](~/docs/csharp/programming-guide/arrays/jagged-arrays.md) (an array of arrays) instead.</span></span> <span data-ttu-id="06383-198">Na przykład `array[x,y,z]` jest nieprawidłowa, ale `array[x][y][z]` nie jest.</span><span class="sxs-lookup"><span data-stu-id="06383-198">For example, `array[x,y,z]` is invalid, but `array[x][y][z]` isn't.</span></span>  
  
-   <span data-ttu-id="06383-199">Wariancja dla tablic wielowymiarowych nie jest obsługiwane i powoduje, że <xref:System.InvalidCastException> wyjątek w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="06383-199">Variance for multidimensional arrays isn't supported and causes an <xref:System.InvalidCastException> exception at run time.</span></span>  
  
 <span data-ttu-id="06383-200">**Typy ogólne**</span><span class="sxs-lookup"><span data-stu-id="06383-200">**Generics**</span></span>  
  
-   <span data-ttu-id="06383-201">Błąd kompilatora powoduje nieskończone rozwijanie typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="06383-201">Infinite generic type expansion results in a compiler error.</span></span> <span data-ttu-id="06383-202">Na przykład ten kod nie powiedzie się do kompilacji:</span><span class="sxs-lookup"><span data-stu-id="06383-202">For example, this code fails to compile:</span></span>  
  
     [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]  
  
 <span data-ttu-id="06383-203">**Wskaźniki**</span><span class="sxs-lookup"><span data-stu-id="06383-203">**Pointers**</span></span>  
  
-   <span data-ttu-id="06383-204">Tablice wskaźniki nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="06383-204">Arrays of pointers aren't supported.</span></span>  
  
-   <span data-ttu-id="06383-205">Za pomocą odbicia nie można pobrać lub ustawić pole wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="06383-205">You can't use reflection to get or set a pointer field.</span></span>  
  
 <span data-ttu-id="06383-206">**Serializacja**</span><span class="sxs-lookup"><span data-stu-id="06383-206">**Serialization**</span></span>  
  
 <span data-ttu-id="06383-207"><xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> Atrybut nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="06383-207">The <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> attribute isn't supported.</span></span> <span data-ttu-id="06383-208">Użyj <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> zamiast tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="06383-208">Use the <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> attribute instead.</span></span>  
  
 <span data-ttu-id="06383-209">**Zasoby**</span><span class="sxs-lookup"><span data-stu-id="06383-209">**Resources**</span></span>  
  
 <span data-ttu-id="06383-210">Użycie zlokalizowane zasoby z <xref:System.Diagnostics.Tracing.EventSource> klasy nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="06383-210">The use of localized resources with the <xref:System.Diagnostics.Tracing.EventSource> class isn't supported.</span></span> <span data-ttu-id="06383-211"><xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> Właściwości nie definiuje zlokalizowanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="06383-211">The <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> property doesn't define localized resources.</span></span>  
  
 <span data-ttu-id="06383-212">**Delegaci**</span><span class="sxs-lookup"><span data-stu-id="06383-212">**Delegates**</span></span>  
  
 <span data-ttu-id="06383-213">`Delegate.BeginInvoke`i `Delegate.EndInvoke` nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="06383-213">`Delegate.BeginInvoke` and `Delegate.EndInvoke` aren't supported.</span></span>  
  
 <span data-ttu-id="06383-214">**Async**</span><span class="sxs-lookup"><span data-stu-id="06383-214">**Async**</span></span>  
  
 <span data-ttu-id="06383-215">Wątkowość logikę przeciążenia IAsync zadania nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="06383-215">Threading logic in overloads of Task IAsync isn't supported.</span></span>  
  
 <span data-ttu-id="06383-216">**Różne interfejsy API**</span><span class="sxs-lookup"><span data-stu-id="06383-216">**Miscellaneous APIs**</span></span>  
  
-   <span data-ttu-id="06383-217"><xref:System.Reflection.TypeInfo.GUID%2A?displayProperty=nameWithType> Zgłasza właściwości <xref:System.PlatformNotSupportedException> wyjątek Jeśli <xref:System.Runtime.InteropServices.GuidAttribute> atrybut nie jest stosowany do typu.</span><span class="sxs-lookup"><span data-stu-id="06383-217">The <xref:System.Reflection.TypeInfo.GUID%2A?displayProperty=nameWithType> property throws a <xref:System.PlatformNotSupportedException> exception if a <xref:System.Runtime.InteropServices.GuidAttribute> attribute isn't applied to the type.</span></span> <span data-ttu-id="06383-218">Identyfikator GUID jest używany głównie do obsługi modelu COM.</span><span class="sxs-lookup"><span data-stu-id="06383-218">The GUID is used primarily for COM support.</span></span>  
  
-   <span data-ttu-id="06383-219"><xref:System.DateTime.Parse%2A?displayProperty=nameWithType> Metody poprawnie analizuje ciągi zawierające krótkiej daty w [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="06383-219">The <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> method correctly parses strings that contain short dates in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="06383-220">Jednak nie go zachować zgodność z zmiany daty i czasu przetwarzania opisane w artykułach bazy wiedzy Microsoft Knowledge Base [KB2803771](http://support.microsoft.com/kb/2803771) i [KB2803755](http://support.microsoft.com/kb/2803755).</span><span class="sxs-lookup"><span data-stu-id="06383-220">However, it doesn't maintain compatibility with the changes in date and time parsing described in the Microsoft Knowledge Base articles [KB2803771](http://support.microsoft.com/kb/2803771) and [KB2803755](http://support.microsoft.com/kb/2803755).</span></span>  
  
-   <span data-ttu-id="06383-221"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType>`("E")` poprawnie jest zaokrąglana w [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="06383-221"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` is correctly rounded in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="06383-222">W niektórych wersjach środowiska CLR zostały obcięte ciąg wyniku zamiast zaokrąglona.</span><span class="sxs-lookup"><span data-stu-id="06383-222">In some versions of the CLR, the result string is truncated instead of rounded.</span></span>  
  
<a name="HttpClient"></a>   
### <a name="httpclient-differences"></a><span data-ttu-id="06383-223">Różnice HttpClient</span><span class="sxs-lookup"><span data-stu-id="06383-223">HttpClient differences</span></span>  
 <span data-ttu-id="06383-224">W [!INCLUDE[net_native](../../../includes/net-native-md.md)], <xref:System.Net.Http.HttpClientHandler> klasy wewnętrznie używa WinINet (za pośrednictwem [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) klasy) zamiast <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klasy używane standardowe .NET dla aplikacji ze Sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="06383-224">In [!INCLUDE[net_native](../../../includes/net-native-md.md)], the <xref:System.Net.Http.HttpClientHandler> class internally uses WinINet (through the [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) class) instead of the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes used in the standard .NET for Windows Store apps.</span></span>  <span data-ttu-id="06383-225">WinINet nie obsługuje wszystkie opcje konfiguracji <xref:System.Net.Http.HttpClientHandler> obsługuje klasy.</span><span class="sxs-lookup"><span data-stu-id="06383-225">WinINet doesn't support all the configuration options that the <xref:System.Net.Http.HttpClientHandler> class supports.</span></span>  <span data-ttu-id="06383-226">W efekcie:</span><span class="sxs-lookup"><span data-stu-id="06383-226">As a result:</span></span>  
  
-   <span data-ttu-id="06383-227">Niektóre właściwości możliwości na <xref:System.Net.Http.HttpClientHandler> zwracać `false` na [!INCLUDE[net_native](../../../includes/net-native-md.md)], podczas gdy zwracają `true` standardowe .NET dla aplikacji ze Sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="06383-227">Some of the capability properties on <xref:System.Net.Http.HttpClientHandler> return `false` on [!INCLUDE[net_native](../../../includes/net-native-md.md)], whereas they return `true` in the standard .NET for Windows Store apps.</span></span>  
  
-   <span data-ttu-id="06383-228">Niektóre właściwości konfiguracji `get` akcesorów zawsze zwraca wartość stałą na [!INCLUDE[net_native](../../../includes/net-native-md.md)] która jest inna niż domyślna wartość można skonfigurować w aplikacjach .NET dla Sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="06383-228">Some of the configuration property `get` accessors always return a fixed value on [!INCLUDE[net_native](../../../includes/net-native-md.md)] that is different than the default configurable value in .NET for Windows Store apps.</span></span>  
  
 <span data-ttu-id="06383-229">Niektóre dodatkowe różnicach są przedstawione w poniższych podsekcjach.</span><span class="sxs-lookup"><span data-stu-id="06383-229">Some additional behavior differences are covered in the following subsections.</span></span>  
  
 <span data-ttu-id="06383-230">**Serwer proxy**</span><span class="sxs-lookup"><span data-stu-id="06383-230">**Proxy**</span></span>  
  
 <span data-ttu-id="06383-231">[HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) klasa nie obsługuje konfigurowania lub zastępowania serwera proxy na podstawie danego żądania.</span><span class="sxs-lookup"><span data-stu-id="06383-231">The [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) class doesn’t support configuring or overriding the proxy on a per-request basis.</span></span>  <span data-ttu-id="06383-232">Oznacza to, że wszystkie żądania na [!INCLUDE[net_native](../../../includes/net-native-md.md)] za pomocą serwera proxy skonfigurowanego systemu lub żadnego serwera proxy, w zależności od wartości <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="06383-232">This means that all requests on [!INCLUDE[net_native](../../../includes/net-native-md.md)] use the system-configured proxy server or no proxy server, depending on the value of the <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="06383-233">.NET dla aplikacji ze Sklepu Windows, serwer proxy jest zdefiniowany przez <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="06383-233">In .NET for Windows Store apps, the proxy server is defined by the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="06383-234">Na [!INCLUDE[net_native](../../../includes/net-native-md.md)], ustawienie <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> wartość inną niż `null` zgłasza <xref:System.PlatformNotSupportedException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="06383-234">On [!INCLUDE[net_native](../../../includes/net-native-md.md)], setting the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> to a value other than `null` throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="06383-235"><xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> Zwraca `false` na [!INCLUDE[net_native](../../../includes/net-native-md.md)], podczas gdy zwraca `true` standardowe .NET Framework dla aplikacji ze Sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="06383-235">The <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> property returns `false` on [!INCLUDE[net_native](../../../includes/net-native-md.md)], whereas it returns `true` in the standard .NET Framework for Windows Store apps.</span></span>  
  
 <span data-ttu-id="06383-236">**Automatyczne przekierowanie**</span><span class="sxs-lookup"><span data-stu-id="06383-236">**Automatic redirection**</span></span>  
  
 <span data-ttu-id="06383-237">[HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) klasy nie zezwala na maksymalną liczbę przekierowań automatycznych do skonfigurowania.</span><span class="sxs-lookup"><span data-stu-id="06383-237">The [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) class doesn't allow the maximum number of automatic redirections to be configured.</span></span>  <span data-ttu-id="06383-238">Wartość <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> właściwości wynosi 50 domyślnie standardowa .NET dla aplikacji ze Sklepu Windows i może być modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="06383-238">The value of the <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> property is 50 by default in the standard .NET for Windows Store apps and can be modified.</span></span> <span data-ttu-id="06383-239">Na [!INCLUDE[net_native](../../../includes/net-native-md.md)], wartość tej właściwości jest 10 i w trakcie modyfikowania go zgłasza <xref:System.PlatformNotSupportedException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="06383-239">On [!INCLUDE[net_native](../../../includes/net-native-md.md)], the value of this property is 10, and trying to modify it throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="06383-240"><xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> Zwraca `false` na [!INCLUDE[net_native](../../../includes/net-native-md.md)], podczas gdy zwraca `true` w aplikacjach .NET dla Sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="06383-240">The <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> property returns `false` on [!INCLUDE[net_native](../../../includes/net-native-md.md)], whereas it returns `true` in .NET for Windows Store apps.</span></span>  
  
 <span data-ttu-id="06383-241">**Automatycznej dekompresji**</span><span class="sxs-lookup"><span data-stu-id="06383-241">**Automatic decompression**</span></span>  
  
 <span data-ttu-id="06383-242">.NET dla Sklepu Windows apps umożliwia ustawienie <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> właściwości <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, oba <xref:System.Net.DecompressionMethods.Deflate> i <xref:System.Net.DecompressionMethods.GZip>, lub <xref:System.Net.DecompressionMethods.None>.</span><span class="sxs-lookup"><span data-stu-id="06383-242">.NET for Windows Store apps allows you to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> property to <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  [!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="06383-243">obsługuje tylko <xref:System.Net.DecompressionMethods.Deflate> razem z <xref:System.Net.DecompressionMethods.GZip>, lub <xref:System.Net.DecompressionMethods.None>.</span><span class="sxs-lookup"><span data-stu-id="06383-243"> only supports <xref:System.Net.DecompressionMethods.Deflate> together with <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="06383-244">Ustawiany <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> właściwości albo <xref:System.Net.DecompressionMethods.Deflate> lub <xref:System.Net.DecompressionMethods.GZip> samodzielnie dyskretnie ustawia ją na obu <xref:System.Net.DecompressionMethods.Deflate> i <xref:System.Net.DecompressionMethods.GZip>.</span><span class="sxs-lookup"><span data-stu-id="06383-244">Trying to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> property to either <xref:System.Net.DecompressionMethods.Deflate> or <xref:System.Net.DecompressionMethods.GZip> alone silently sets it to both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>.</span></span>  
  
 <span data-ttu-id="06383-245">**Plik cookie**</span><span class="sxs-lookup"><span data-stu-id="06383-245">**Cookies**</span></span>  
  
 <span data-ttu-id="06383-246">Obsługa plików cookie jest wykonywane jednocześnie przez <xref:System.Net.Http.HttpClient> i WinINet.</span><span class="sxs-lookup"><span data-stu-id="06383-246">Cookie handling is performed simultaneously by <xref:System.Net.Http.HttpClient> and WinINet.</span></span>  <span data-ttu-id="06383-247">Pliki cookie z <xref:System.Net.CookieContainer> są łączone z plików cookie w pamięci podręcznej plików cookie WinINet.</span><span class="sxs-lookup"><span data-stu-id="06383-247">Cookies from the <xref:System.Net.CookieContainer> are combined with cookies in the WinINet cookie cache.</span></span>  <span data-ttu-id="06383-248">Usuwanie pliku cookie z <xref:System.Net.CookieContainer> uniemożliwia <xref:System.Net.Http.HttpClient> wysyłania plików cookie, ale jeśli plik cookie został już odebrany przez WinINet i pliki cookie nie zostały usunięte przez użytkownika, WinINet wysyła go.</span><span class="sxs-lookup"><span data-stu-id="06383-248">Removing a cookie from <xref:System.Net.CookieContainer> prevents <xref:System.Net.Http.HttpClient> from sending the cookie, but if the cookie was already seen by WinINet, and cookies weren't deleted by the user, WinINet sends it.</span></span>  <span data-ttu-id="06383-249">Nie można programistycznie usunąć plik cookie z WinINet przy użyciu <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>, lub <xref:System.Net.CookieContainer> interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="06383-249">It isn't possible to programmatically remove a cookie from WinINet by using the <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>, or <xref:System.Net.CookieContainer> API.</span></span>  <span data-ttu-id="06383-250">Ustawienie <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> właściwości `false` powoduje, że tylko <xref:System.Net.Http.HttpClient> Aby zatrzymać wysyłanie plików cookie. WinINet nadal mogą obejmować jego plików cookie w żądaniu.</span><span class="sxs-lookup"><span data-stu-id="06383-250">Setting the <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> property to `false` causes only <xref:System.Net.Http.HttpClient> to stop sending cookies; WinINet might still include its cookies in the request.</span></span>  
  
 <span data-ttu-id="06383-251">**Poświadczenia**</span><span class="sxs-lookup"><span data-stu-id="06383-251">**Credentials**</span></span>  
  
 <span data-ttu-id="06383-252">.NET dla aplikacji ze Sklepu Windows <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> i <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> właściwości działają niezależnie.</span><span class="sxs-lookup"><span data-stu-id="06383-252">In .NET for Windows Store apps, the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> properties work independently.</span></span>  <span data-ttu-id="06383-253">Ponadto <xref:System.Net.Http.HttpClientHandler.Credentials%2A> właściwość akceptuje dowolny obiekt, który implementuje <xref:System.Net.ICredentials> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="06383-253">Additionally, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property accepts any object that implements the <xref:System.Net.ICredentials> interface.</span></span>  <span data-ttu-id="06383-254">W [!INCLUDE[net_native](../../../includes/net-native-md.md)], ustawienie <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> właściwości `true` powoduje, że <xref:System.Net.Http.HttpClientHandler.Credentials%2A> właściwość, aby stać się `null`.</span><span class="sxs-lookup"><span data-stu-id="06383-254">In [!INCLUDE[net_native](../../../includes/net-native-md.md)], setting the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> property to `true` causes the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property to become `null`.</span></span>  <span data-ttu-id="06383-255">Ponadto <xref:System.Net.Http.HttpClientHandler.Credentials%2A> właściwość można ustawić tylko z `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>, lub obiekt typu <xref:System.Net.NetworkCredential>.</span><span class="sxs-lookup"><span data-stu-id="06383-255">In addition, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property can be set only to `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>, or an object of type <xref:System.Net.NetworkCredential>.</span></span>  <span data-ttu-id="06383-256">Przypisywanie innych <xref:System.Net.ICredentials> obiektu, jest najbardziej popularnym którego <xref:System.Net.CredentialCache>, do <xref:System.Net.Http.HttpClientHandler.Credentials%2A> zgłasza właściwości <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="06383-256">Assigning any other <xref:System.Net.ICredentials> object, the most popular of which is <xref:System.Net.CredentialCache>, to the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property throws a <xref:System.PlatformNotSupportedException>.</span></span>  
  
 <span data-ttu-id="06383-257">**Inne funkcje nieobsługiwane lub unconfigurable**</span><span class="sxs-lookup"><span data-stu-id="06383-257">**Other unsupported or unconfigurable features**</span></span>  
  
 <span data-ttu-id="06383-258">W [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="06383-258">In [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span></span>  
  
-   <span data-ttu-id="06383-259">Wartość <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> właściwość jest zawsze <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span><span class="sxs-lookup"><span data-stu-id="06383-259">The value of the <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> property is always <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span></span>  <span data-ttu-id="06383-260">.NET dla aplikacji ze Sklepu Windows, wartość domyślna to <xref:System.Net.Http.ClientCertificateOption.Manual>.</span><span class="sxs-lookup"><span data-stu-id="06383-260">In .NET for Windows Store apps, the default is <xref:System.Net.Http.ClientCertificateOption.Manual>.</span></span>  
  
-   <span data-ttu-id="06383-261"><xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> Właściwości nie można skonfigurować.</span><span class="sxs-lookup"><span data-stu-id="06383-261">The <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> property isn't configurable.</span></span>  
  
-   <span data-ttu-id="06383-262"><xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> Właściwość jest zawsze `true`.</span><span class="sxs-lookup"><span data-stu-id="06383-262">The <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> property is always `true`.</span></span>  <span data-ttu-id="06383-263">.NET dla aplikacji ze Sklepu Windows, wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="06383-263">In .NET for Windows Store apps, the default is `false`.</span></span>  
  
-   <span data-ttu-id="06383-264">`SetCookie2` Nagłówka w odpowiedzi jest ignorowana jako przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="06383-264">The `SetCookie2` header in responses is ignored as obsolete.</span></span>  
  
<a name="Interop"></a>   
### <a name="interop-differences"></a><span data-ttu-id="06383-265">Różnice międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="06383-265">Interop differences</span></span>  
 <span data-ttu-id="06383-266">**Przestarzałe interfejsy API**</span><span class="sxs-lookup"><span data-stu-id="06383-266">**Deprecated APIs**</span></span>  
  
 <span data-ttu-id="06383-267">Kilka interfejsów API, rzadko używane na współdziałanie z kodem zarządzanym są przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="06383-267">A number of infrequently used APIs for interoperability with managed code have been deprecated.</span></span> <span data-ttu-id="06383-268">W przypadku użycia z [!INCLUDE[net_native](../../../includes/net-native-md.md)], te interfejsy API może zgłaszać <xref:System.NotImplementedException> lub <xref:System.PlatformNotSupportedException> wyjątku lub spowodować błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="06383-268">When used with [!INCLUDE[net_native](../../../includes/net-native-md.md)], these APIs may throw a <xref:System.NotImplementedException> or <xref:System.PlatformNotSupportedException> exception, or result in a compiler error.</span></span> <span data-ttu-id="06383-269">.NET dla aplikacji ze Sklepu Windows te interfejsy API są oznaczone jako przestarzałe, mimo że je wywołuje generuje ostrzeżenie kompilatora, a nie wystąpi błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="06383-269">In .NET for Windows Store apps, these APIs are marked as obsolete, although calling them generates a compiler warning rather than a compiler error.</span></span>  
  
 <span data-ttu-id="06383-270">Przestarzałe interfejsy API dla `VARIANT` organizowanie:</span><span class="sxs-lookup"><span data-stu-id="06383-270">Deprecated APIs for `VARIANT` marshaling:</span></span>  
  
||  
|-|  
|<xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.VarEnum?displayProperty=nameWithType>|  
  
 <span data-ttu-id="06383-271"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType>jest obsługiwana, ale zgłasza wyjątek w niektórych scenariuszach, na przykład gdy jest używana z [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) lub byref VARIANT.</span><span class="sxs-lookup"><span data-stu-id="06383-271"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> is supported, but it throws an exception in some scenarios, such as when it is used with [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) or byref variants.</span></span>  
  
 <span data-ttu-id="06383-272">Przestarzałe interfejsy API dla [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) obsługuje:</span><span class="sxs-lookup"><span data-stu-id="06383-272">Deprecated APIs for [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) support:</span></span>  
  
|<span data-ttu-id="06383-273">Typ</span><span class="sxs-lookup"><span data-stu-id="06383-273">Type</span></span>|<span data-ttu-id="06383-274">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="06383-274">Member</span></span>|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch>|  
|<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual>|  
|<xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>|<span data-ttu-id="06383-275">Atrybut nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="06383-275">Attribute isn't supported</span></span>|  
  
 <span data-ttu-id="06383-276">Przestarzałe interfejsy API dla zdarzeń COM klasycznego:</span><span class="sxs-lookup"><span data-stu-id="06383-276">Deprecated APIs for classic COM events:</span></span>  
  
||  
|-|  
|<xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>|  
  
 <span data-ttu-id="06383-277">Przestarzałe interfejsy API w <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interfejsu, który nie jest obsługiwany w [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="06383-277">Deprecated APIs in the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface, which isn't supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span></span>  
  
|<span data-ttu-id="06383-278">Typ</span><span class="sxs-lookup"><span data-stu-id="06383-278">Type</span></span>|<span data-ttu-id="06383-279">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="06383-279">Member</span></span>|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType>|<span data-ttu-id="06383-280">Wszystkie elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="06383-280">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType>|<span data-ttu-id="06383-281">Wszystkie elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="06383-281">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType>|<span data-ttu-id="06383-282">Wszystkie elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="06383-282">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=nameWithType>|  
  
 <span data-ttu-id="06383-283">Inne nieobsługiwane funkcje międzyoperacyjnego:</span><span class="sxs-lookup"><span data-stu-id="06383-283">Other unsupported interop features:</span></span>  
  
|<span data-ttu-id="06383-284">Typ</span><span class="sxs-lookup"><span data-stu-id="06383-284">Type</span></span>|<span data-ttu-id="06383-285">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="06383-285">Member</span></span>|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType>|<span data-ttu-id="06383-286">Wszystkie elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="06383-286">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType>|<span data-ttu-id="06383-287">Wszystkie elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="06383-287">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.Currency>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.AsAny>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler>|  
  
 <span data-ttu-id="06383-288">Rzadko używane kierowanie interfejsów API:</span><span class="sxs-lookup"><span data-stu-id="06383-288">Rarely used marshalling APIs:</span></span>  
  
|<span data-ttu-id="06383-289">Typ</span><span class="sxs-lookup"><span data-stu-id="06383-289">Type</span></span>|<span data-ttu-id="06383-290">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="06383-290">Member</span></span>|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadByte%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadInt16%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadInt32%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadInt64%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadIntPtr%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteByte%28System.Object%2CSystem.Int32%2CSystem.Byte%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteInt16%28System.Object%2CSystem.Int32%2CSystem.Int16%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteInt32%28System.Object%2CSystem.Int32%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteInt64%28System.Object%2CSystem.Int32%2CSystem.Int64%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteIntPtr%28System.Object%2CSystem.Int32%2CSystem.IntPtr%29>|  
  
 <span data-ttu-id="06383-291">**Wywołanie platformy i zgodność międzyoperacyjnego modelu COM**</span><span class="sxs-lookup"><span data-stu-id="06383-291">**Platform invoke and COM interop compatibility**</span></span>  
  
 <span data-ttu-id="06383-292">Wywołanie platformy większości i scenariusze międzyoperacyjnego COM nadal są obsługiwane w [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="06383-292">Most platform invoke and COM interop scenarios are still supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="06383-293">W szczególności wszystkie współdziałanie z środowiska wykonawczego systemu Windows (WinRT) interfejsów API i organizowanie wszystkie wymagane przez środowisko wykonawcze systemu Windows jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="06383-293">In particular, all interoperability with Windows Runtime (WinRT) APIs and all marshaling required for the Windows Runtime is supported.</span></span> <span data-ttu-id="06383-294">Obejmuje to przekazywanie obsługę:</span><span class="sxs-lookup"><span data-stu-id="06383-294">This includes marshaling support for:</span></span>  
  
-   <span data-ttu-id="06383-295">Tablice (w tym <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span><span class="sxs-lookup"><span data-stu-id="06383-295">Arrays (including <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span></span>  
  
-   `BStr`  
  
-   <span data-ttu-id="06383-296">Delegaty</span><span class="sxs-lookup"><span data-stu-id="06383-296">Delegates</span></span>  
  
-   <span data-ttu-id="06383-297">Ciągi (Unicode, Ansi i HSTRING)</span><span class="sxs-lookup"><span data-stu-id="06383-297">Strings (Unicode, Ansi, and HSTRING)</span></span>  
  
-   <span data-ttu-id="06383-298">Struktury (`byref` i `byval`)</span><span class="sxs-lookup"><span data-stu-id="06383-298">Structs (`byref` and `byval`)</span></span>  
  
-   <span data-ttu-id="06383-299">Unie</span><span class="sxs-lookup"><span data-stu-id="06383-299">Unions</span></span>  
  
-   <span data-ttu-id="06383-300">Uchwyty Win32</span><span class="sxs-lookup"><span data-stu-id="06383-300">Win32 handles</span></span>  
  
-   <span data-ttu-id="06383-301">Wszystkie konstrukcje WinRT</span><span class="sxs-lookup"><span data-stu-id="06383-301">All WinRT constructs</span></span>  
  
-   <span data-ttu-id="06383-302">Obsługa częściowej organizowanie typów variant.</span><span class="sxs-lookup"><span data-stu-id="06383-302">Partial support for marshaling variant types.</span></span> <span data-ttu-id="06383-303">Obsługiwane są:</span><span class="sxs-lookup"><span data-stu-id="06383-303">The following are supported:</span></span>  
  
    -   <xref:System.Boolean>  
  
    -   <xref:System.Byte>  
  
    -   <xref:System.Decimal>  
  
    -   <xref:System.Double>  
  
    -   <xref:System.Int16>  
  
    -   <xref:System.Int32>  
  
    -   <xref:System.Int64>  
  
    -   <xref:System.SByte>  
  
    -   <xref:System.Single>  
  
    -   <xref:System.UInt16>  
  
    -   <xref:System.UInt32>  
  
    -   <xref:System.UInt64>  
  
    -   `BStr`  
  
    -   [<span data-ttu-id="06383-304">IUnknown</span><span class="sxs-lookup"><span data-stu-id="06383-304">IUnknown</span></span>](http://msdn.microsoft.com/library/windows/desktop/ms680509.aspx)  
  
 <span data-ttu-id="06383-305">Jednak [!INCLUDE[net_native](../../../includes/net-native-md.md)] nie obsługują następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="06383-305">However, [!INCLUDE[net_native](../../../includes/net-native-md.md)] doesn't support the following:</span></span>  
  
-   <span data-ttu-id="06383-306">Przy użyciu klasycznego zdarzeń COM</span><span class="sxs-lookup"><span data-stu-id="06383-306">Using classic COM events</span></span>  
  
-   <span data-ttu-id="06383-307">Implementowanie <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interfejs typu zarządzanego</span><span class="sxs-lookup"><span data-stu-id="06383-307">Implementing the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface on a managed type</span></span>  
  
-   <span data-ttu-id="06383-308">Implementowanie [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) interfejsu na typ zarządzany za pośrednictwem <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="06383-308">Implementing the [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) interface on a managed type through the <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> attribute.</span></span> <span data-ttu-id="06383-309">Jednak należy pamiętać, że nie można wywołać obiektów COM za pomocą `IDispatch`, i nie można zaimplementować zarządzane obiektu `IDispatch`.</span><span class="sxs-lookup"><span data-stu-id="06383-309">However, note that you can't call COM objects through `IDispatch`, and your managed object can't implement `IDispatch`.</span></span>  
  
 <span data-ttu-id="06383-310">Za pomocą odbicia do wywołania platformy wywołania metody nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="06383-310">Using reflection to invoke a platform invoke method isn't supported.</span></span> <span data-ttu-id="06383-311">To ograniczenie można obejść przez zawijanie wywołania metody w innej metody i zamiast tego wywołać otoka za pomocą odbicia.</span><span class="sxs-lookup"><span data-stu-id="06383-311">You can work around this limitation by wrapping the method call in another method and using reflection to call the wrapper instead.</span></span>  
  
<a name="APIs"></a>   
### <a name="other-differences-from-net-apis-for-windows-store-apps"></a><span data-ttu-id="06383-312">Inne różnice z interfejsów API platformy .NET dla Sklepu Windows apps</span><span class="sxs-lookup"><span data-stu-id="06383-312">Other differences from .NET APIs for Windows Store apps</span></span>  
 <span data-ttu-id="06383-313">Ta sekcja zawiera informacje o pozostałych interfejsów API, które nie są obsługiwane w [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="06383-313">This section lists the remaining APIs that aren't supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="06383-314">Największy zbiór nieobsługiwany interfejsy API są Windows Communication Foundation (WCF) interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="06383-314">The largest set of the unsupported APIs are Windows Communication Foundation (WCF) APIs.</span></span>  
  
 <span data-ttu-id="06383-315">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span><span class="sxs-lookup"><span data-stu-id="06383-315">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span></span>  
  
 <span data-ttu-id="06383-316">Typy w <xref:System.ComponentModel.DataAnnotations> i <xref:System.ComponentModel.DataAnnotations.Schema> przestrzeni nazw nie są obsługiwane w [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="06383-316">The types in the <xref:System.ComponentModel.DataAnnotations> and <xref:System.ComponentModel.DataAnnotations.Schema> namespaces aren't supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="06383-317">Obejmują one następujące typy, które znajdują się w aplikacji .NET dla Sklepu Windows dla systemu Windows 8:</span><span class="sxs-lookup"><span data-stu-id="06383-317">These include the following types that are present in the .NET for Windows Store apps for Windows 8:</span></span>  
  
||  
|-|  
|<xref:System.ComponentModel.DataAnnotations.AssociationAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ConcurrencyCheckAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.CustomValidationAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DataType?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DataTypeAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayColumnAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayFormatAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.EditableAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.EnumDataTypeAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.FilterUIHintAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.KeyAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.RangeAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.RegularExpressionAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.RequiredAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.StringLengthAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.TimestampAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.UIHintAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationContext?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationResult?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.Validator?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedOption?displayProperty=nameWithType>|  
  
 <span data-ttu-id="06383-318">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="06383-318">**Visual Basic**</span></span>  
  
 <span data-ttu-id="06383-319">Visual Basic nie jest obecnie obsługiwany w [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="06383-319">Visual Basic isn't currently supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="06383-320">Następujące typy w <xref:Microsoft.VisualBasic> i <xref:Microsoft.VisualBasic.CompilerServices> przestrzeni nazw nie są dostępne w [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="06383-320">The following types in the <xref:Microsoft.VisualBasic> and <xref:Microsoft.VisualBasic.CompilerServices> namespaces aren't available in [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span></span>  
  
||  
|-|  
|<xref:Microsoft.VisualBasic.CallType?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.Constants?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Conversions?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.IncompleteInitialization?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl.ForLoopControl?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Operators?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.OptionCompareAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.OptionTextAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ProjectData?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.StandardModuleAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.StaticLocalInitFlag?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Utils?displayProperty=nameWithType>|  
  
 <span data-ttu-id="06383-321">**Kontekście odbicia (przestrzeń nazw System.Reflection.Context)**</span><span class="sxs-lookup"><span data-stu-id="06383-321">**Reflection Context (System.Reflection.Context namespace)**</span></span>  
  
 <span data-ttu-id="06383-322"><xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> Klasy nie jest obsługiwany w [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="06383-322">The <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> class isn't supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
 <span data-ttu-id="06383-323">**RTC (System.Net.Http.Rtc)**</span><span class="sxs-lookup"><span data-stu-id="06383-323">**RTC (System.Net.Http.Rtc)**</span></span>  
  
 <span data-ttu-id="06383-324"><xref:System.Net.Http.RtcRequestFactory?displayProperty=nameWithType> Klasy nie jest obsługiwany w [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="06383-324">The <xref:System.Net.Http.RtcRequestFactory?displayProperty=nameWithType> class isn't supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
 <span data-ttu-id="06383-325">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span><span class="sxs-lookup"><span data-stu-id="06383-325">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span></span>  
  
 <span data-ttu-id="06383-326">Typy w [przestrzeni nazw System.ServiceModel.*](http://msdn.microsoft.com/library/gg145010.aspx) nie są obsługiwane w [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="06383-326">The types in the [System.ServiceModel.* namespaces](http://msdn.microsoft.com/library/gg145010.aspx) aren't supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="06383-327">Te zawiera następujące typy:</span><span class="sxs-lookup"><span data-stu-id="06383-327">These includes the following types:</span></span>  
  
||  
|-|  
|<xref:System.ServiceModel.ActionNotSupportedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpMessageCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpSecurityMode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.BeginOperationDelegate?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.ChannelBase%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.EndOperationDelegate?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.InvokeAsyncCompletedEventArgs?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationState?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DataContractFormatAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DnsEndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointAddress?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointAddressBuilder?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EnvelopeVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ExceptionDetail?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultCode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultReason?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultReasonText?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.HttpBindingBase?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.HttpClientCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.HttpTransportSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IDefaultCommunicationTimeouts?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IExtension%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IExtensionCollection%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.InvalidMessageContractException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageBodyMemberAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageContractMemberAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageHeader%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageHeaderException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageSecurityOverTcp?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageSecurityVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetHttpBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetHttpMessageEncoding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetTcpSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationContext?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationContextScope?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationFormatStyle?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ProtocolException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.QuotaExceededException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServerTooBusyException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServiceActivationException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServiceKnownTypeAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.SpnEndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.TcpClientCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.TcpTransportSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.TransferMode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.UnknownMessageReceivedEventArgs?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.UpnEndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.AddressHeader?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.AddressHeaderCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.AddressingVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ChannelManagerBase?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ChannelParameterCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.CommunicationObject?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.FaultConverter?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpRequestMessageProperty?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpResponseMessageProperty?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpsTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IChannelFactory?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IChannelFactory%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IDuplexChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IDuplexSession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IDuplexSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IHttpCookieContainerManager?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IInputChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IInputSession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IInputSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IMessageProperty?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IOutputChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IOutputSession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IOutputSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IRequestSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.LocalClientSecuritySettings?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageBuffer?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageEncoder?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageEncoderFactory?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageHeader?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageHeaderInfo?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageHeaders?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageProperties?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageState?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.RequestContext?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.SecurityHeaderLayout?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TcpConnectionPoolSettings?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TransportSecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.WebSocketTransportSettings?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.WebSocketTransportUsage?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.ClientCredentials?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.FaultDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.FaultDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageBodyDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageDirection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageHeaderDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageHeaderDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePartDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePartDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePropertyDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePropertyDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.OperationDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.OperationDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.ClientOperation?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.ClientRuntime?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.DispatchOperation?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.DispatchRuntime?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.EndpointDispatcher?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IClientOperationSelector?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.BasicSecurityProfileVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.HttpDigestClientCredential?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecureConversationVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecurityAccessDeniedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecurityPolicyVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecurityVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.TrustVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.UserNamePasswordClientCredential?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.WindowsClientCredential?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.UserNameSecurityTokenParameters?displayProperty=nameWithType>|  
  
### <a name="differences-in-serializers"></a><span data-ttu-id="06383-328">Różnice w serializatorów</span><span class="sxs-lookup"><span data-stu-id="06383-328">Differences in serializers</span></span>  
 <span data-ttu-id="06383-329">Następujące różnice dotyczą serializacji i deserializacji z <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, i <xref:System.Xml.Serialization.XmlSerializer> klasy:</span><span class="sxs-lookup"><span data-stu-id="06383-329">The following differences concern serialization and deserialization with the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes:</span></span>  
  
-   <span data-ttu-id="06383-330">W [!INCLUDE[net_native](../../../includes/net-native-md.md)], <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nie można serializować lub deserializować klasy pochodnej, która ma element członkowski klasy podstawowej, której typ nie jest typu serializacji głównego.</span><span class="sxs-lookup"><span data-stu-id="06383-330">In [!INCLUDE[net_native](../../../includes/net-native-md.md)], <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize or deserialize a derived class that has a base class member whose type isn't a root serialization type.</span></span> <span data-ttu-id="06383-331">Na przykład w poniższym kodzie próby serializacji lub deserializacji `Y` powoduje wystąpienie błędu:</span><span class="sxs-lookup"><span data-stu-id="06383-331">For example, in the following code, trying to serialize or deserialize `Y` results in an error:</span></span>  
  
     [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]  
  
     <span data-ttu-id="06383-332">Typ `InnerType` nie jest znana do serializatora, ponieważ elementy członkowskie klasy podstawowej nie przechodzić podczas serializacji.</span><span class="sxs-lookup"><span data-stu-id="06383-332">Type `InnerType` isn't known to the serializer, because the members of the base class aren't traversed during serialization.</span></span>  
  
-   <span data-ttu-id="06383-333"><xref:System.Runtime.Serialization.DataContractSerializer>i <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nie można serializować klasy lub struktury, która implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="06383-333"><xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize a class or structure that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="06383-334">Na przykład następujące typy nie do serializacji lub deserializacji:</span><span class="sxs-lookup"><span data-stu-id="06383-334">For example, the following types fail to serialize or deserialize:</span></span>  
  
  
  
-   <span data-ttu-id="06383-335"><xref:System.Xml.Serialization.XmlSerializer>nie powiedzie się do serializacji następującą wartość obiektu, ponieważ nie wie, dokładne typ obiektu do serializacji:</span><span class="sxs-lookup"><span data-stu-id="06383-335"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize the following object value, because it doesn't know the exact type of the object to be serialized:</span></span>  
  
  
  
-   <span data-ttu-id="06383-336"><xref:System.Xml.Serialization.XmlSerializer>nie powiedzie się do serializacji lub deserializacji w przypadku typu serializacji obiektu <xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="06383-336"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize or deserialize if the type of the serialized object is <xref:System.Xml.XmlQualifiedName>.</span></span>  
  
-   <span data-ttu-id="06383-337">Wszystkie serializatorów (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, i <xref:System.Xml.Serialization.XmlSerializer>) nie można wygenerować kodu serializacji dla typu <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> lub typu, który zawiera <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="06383-337">All serializers (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer>) fail to generate serialization code for type <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> or for a type that contains <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="06383-338">Zamiast niej wyświetlane błędy w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="06383-338">They display build-time errors instead.</span></span>  
  
-   <span data-ttu-id="06383-339">Następujące konstruktory serializacji typów nie są gwarancji działać zgodnie z oczekiwaniami:</span><span class="sxs-lookup"><span data-stu-id="06383-339">The following constructors of the serialization types aren't guaranteed to work as expected:</span></span>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.DataContractSerializerSettings%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Xml.XmlDictionaryString%2CSystem.Xml.XmlDictionaryString%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.Json.DataContractJsonSerializerSettings%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.String%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlRootAttribute%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%2CSystem.Type%5B%5D%2CSystem.Xml.Serialization.XmlRootAttribute%2CSystem.String%29?displayProperty=nameWithType>  
  
-   <span data-ttu-id="06383-340"><xref:System.Xml.Serialization.XmlSerializer>Nie można wygenerować kodu dla typu, który ma metodę z dowolnej z następujących atrybutów:</span><span class="sxs-lookup"><span data-stu-id="06383-340"><xref:System.Xml.Serialization.XmlSerializer> fails to generate code for a type that has methods attributed with any of the following attributes:</span></span>  
  
    -   <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
-   <span data-ttu-id="06383-341"><xref:System.Xml.Serialization.XmlSerializer>nie przestrzegać <xref:System.Xml.Serialization.IXmlSerializable> interfejsu niestandardowej serializacji.</span><span class="sxs-lookup"><span data-stu-id="06383-341"><xref:System.Xml.Serialization.XmlSerializer> doesn't honor the <xref:System.Xml.Serialization.IXmlSerializable> custom serialization interface.</span></span> <span data-ttu-id="06383-342">Jeśli masz klasy, który implementuje ten interfejs <xref:System.Xml.Serialization.XmlSerializer> uwzględnia typ zwykły stary typ obiektu (POCO) CLR i serializuje tylko właściwości publiczne.</span><span class="sxs-lookup"><span data-stu-id="06383-342">If you have a class that implements this interface, <xref:System.Xml.Serialization.XmlSerializer> considers the type a plain old CLR object (POCO) type and serializes only its public properties.</span></span>  
  
-   <span data-ttu-id="06383-343">Serializacja zwykły <xref:System.Exception> obiektu, na przykład następujące polecenie, nie działają prawidłowo w przypadku <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:</span><span class="sxs-lookup"><span data-stu-id="06383-343">Serializing a plain <xref:System.Exception> object, such as the following, doesn't work well with <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:</span></span>  
  
  
  
<a name="VS"></a>   
## <a name="visual-studio-differences"></a><span data-ttu-id="06383-344">Różnice w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="06383-344">Visual Studio differences</span></span>  
 <span data-ttu-id="06383-345">**Wyjątki i debugowania**</span><span class="sxs-lookup"><span data-stu-id="06383-345">**Exceptions and debugging**</span></span>  
  
 <span data-ttu-id="06383-346">Jeśli używasz aplikacji skompilowanych za pomocą [!INCLUDE[net_native](../../../includes/net-native-md.md)] w debugerze, pierwszej szansy wyjątki są włączone dla następujących typów wyjątków:</span><span class="sxs-lookup"><span data-stu-id="06383-346">When you're running apps compiled by using [!INCLUDE[net_native](../../../includes/net-native-md.md)] in the debugger, first-chance exceptions are enabled for the following exception types:</span></span>  
  
-   <xref:System.MemberAccessException>  
  
-   <xref:System.TypeAccessException>  
  
 <span data-ttu-id="06383-347">**Tworzenie aplikacji**</span><span class="sxs-lookup"><span data-stu-id="06383-347">**Building apps**</span></span>  
  
 <span data-ttu-id="06383-348">Użyj x86 kompilacji narzędzi używanych domyślnie w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="06383-348">Use the x86 build tools that are used by default by Visual Studio.</span></span> <span data-ttu-id="06383-349">Nie zaleca się za pomocą narzędzia AMD64 MSBuild, które znajdują się w C:\Program Files (x86)\MSBuild\12.0\bin\amd64; to może spowodować problemy kompilacji.</span><span class="sxs-lookup"><span data-stu-id="06383-349">We don't recommend using the AMD64 MSBuild tools, which are found in C:\Program Files (x86)\MSBuild\12.0\bin\amd64; these may create build problems.</span></span>  
  
 <span data-ttu-id="06383-350">**Profilery**</span><span class="sxs-lookup"><span data-stu-id="06383-350">**Profilers**</span></span>  
  
-   <span data-ttu-id="06383-351">Profiler procesora CPU w usłudze Visual Studio i języka XAML pamięci profilera nie wyświetlaj Just My-kodu poprawnie.</span><span class="sxs-lookup"><span data-stu-id="06383-351">The Visual Studio CPU Profiler and XAML Memory Profiler don't display Just-My-Code correctly.</span></span>  
  
-   <span data-ttu-id="06383-352">Profiler pamięci XAML nie wyświetlać dokładnie danych sterty zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="06383-352">The XAML Memory Profiler doesn't accurately display managed heap data.</span></span>  
  
-   <span data-ttu-id="06383-353">Profiler procesora CPU nie poprawnie zidentyfikować moduły i wyświetla prefiksem nazwy funkcji.</span><span class="sxs-lookup"><span data-stu-id="06383-353">The CPU Profiler doesn't correctly identify modules, and displays prefixed function names.</span></span>  
  
 <span data-ttu-id="06383-354">**Projektów Biblioteka testów jednostkowych**</span><span class="sxs-lookup"><span data-stu-id="06383-354">**Unit Test Library projects**</span></span>  
  
 <span data-ttu-id="06383-355">Włączanie [!INCLUDE[net_native](../../../includes/net-native-md.md)] na Biblioteka testów jednostkowych w Sklepie Windows aplikacji projektu nie jest obsługiwane i powoduje, że nie można utworzyć projektu.</span><span class="sxs-lookup"><span data-stu-id="06383-355">Enabling [!INCLUDE[net_native](../../../includes/net-native-md.md)] on a Unit Test Library for a Windows Store apps project isn't supported and causes the project to fail to build.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06383-356">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="06383-356">See Also</span></span>  
 [<span data-ttu-id="06383-357">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="06383-357">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [<span data-ttu-id="06383-358">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="06383-358">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="06383-359">Omówienie aplikacji .NET dla Sklepu Windows</span><span class="sxs-lookup"><span data-stu-id="06383-359">.NET For Windows Store apps overview</span></span>](http://msdn.microsoft.com/library/windows/apps/br230302.aspx)  
 [<span data-ttu-id="06383-360">Obsługa programu .NET Framework dla aplikacji ze Sklepu Windows i środowiska wykonawczego systemu Windows</span><span class="sxs-lookup"><span data-stu-id="06383-360">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)

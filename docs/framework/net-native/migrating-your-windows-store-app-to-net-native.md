---
title: Migrowanie aplikacji ze Sklepu Windows do architektury .NET Native
ms.date: 03/30/2017
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1d14e4ad45a4d5805187b993f2fc622a16dac09
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59163140"
---
# <a name="migrating-your-windows-store-app-to-net-native"></a><span data-ttu-id="ebf6a-102">Migrowanie aplikacji ze Sklepu Windows do architektury .NET Native</span><span class="sxs-lookup"><span data-stu-id="ebf6a-102">Migrating Your Windows Store App to .NET Native</span></span>
<span data-ttu-id="ebf6a-103">.NET native udostępnia statyczny kompilacji aplikacji Windows Store lub na komputerze dewelopera.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-103">.NET Native provides static compilation of apps in the Windows Store or on the developer’s computer.</span></span> <span data-ttu-id="ebf6a-104">To różni się od kompilacji dynamicznej wykonywane dla aplikacji Windows Store przez kompilator just-in-time (JIT) lub [Native Image Generator (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) na urządzeniu.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-104">This differs from the dynamic compilation performed for Windows Store apps by the just-in-time (JIT) compiler or the [Native Image Generator (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) on the device.</span></span> <span data-ttu-id="ebf6a-105">Mimo różnic, .NET Native próbuje zachować zgodność z [.NET for Windows Store apps](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29).</span><span class="sxs-lookup"><span data-stu-id="ebf6a-105">Despite the differences, .NET Native tries to maintain compatibility with the [.NET for Windows Store apps](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29).</span></span> <span data-ttu-id="ebf6a-106">W większości przypadków rzeczy, które działają w aplikacjach .NET for Windows Store również działać z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-106">For the most part, things that work on the .NET for Windows Store apps also work with .NET Native.</span></span>  <span data-ttu-id="ebf6a-107">Jednak w niektórych przypadkach mogą wystąpić zmiany zachowania.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-107">However, in some cases, you may encounter behavioral changes.</span></span> <span data-ttu-id="ebf6a-108">W tym dokumencie omówiono te różnice między standardowe aplikacje .NET for Windows Store i platforma .NET Native w następujących obszarach:</span><span class="sxs-lookup"><span data-stu-id="ebf6a-108">This document discusses these differences between the standard .NET for Windows Store apps and .NET Native in the following areas:</span></span>  
  
-   [<span data-ttu-id="ebf6a-109">Różnice ogólne w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="ebf6a-109">General runtime differences</span></span>](#Runtime)  
  
-   [<span data-ttu-id="ebf6a-110">Różnice programowania dynamicznego</span><span class="sxs-lookup"><span data-stu-id="ebf6a-110">Dynamic programming differences</span></span>](#Dynamic)  
  
-   [<span data-ttu-id="ebf6a-111">Inne różnice dotyczące odbicia</span><span class="sxs-lookup"><span data-stu-id="ebf6a-111">Other reflection-related differences</span></span>](#Reflection)  
  
-   [<span data-ttu-id="ebf6a-112">Nieobsługiwane scenariusze oraz interfejsów API</span><span class="sxs-lookup"><span data-stu-id="ebf6a-112">Unsupported scenarios and APIs</span></span>](#Unsupported)  
  
-   [<span data-ttu-id="ebf6a-113">Visual Studio differences</span><span class="sxs-lookup"><span data-stu-id="ebf6a-113">Visual Studio differences</span></span>](#VS)  
  
<a name="Runtime"></a>   
## <a name="general-runtime-differences"></a><span data-ttu-id="ebf6a-114">Różnice ogólne w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="ebf6a-114">General runtime differences</span></span>  
  
-   <span data-ttu-id="ebf6a-115">Wyjątki, takich jak <xref:System.TypeLoadException>, które są zgłaszane przez kompilator JIT gdy aplikacja jest uruchamiana na wspólnej aparatu plików wykonywalnych języka (wspólnego CLR) zazwyczaj powoduje błędy kompilacji podczas przetwarzania przez .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-115">Exceptions, such as <xref:System.TypeLoadException>, that are thrown by the JIT compiler when an app runs on the common language runtime (CLR) generally result in compile-time errors when processed by .NET Native.</span></span>  
  
-   <span data-ttu-id="ebf6a-116">Nie wywołuj <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> metody z wątku interfejsu użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-116">Don't call the <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method from an app's UI thread.</span></span> <span data-ttu-id="ebf6a-117">Może to spowodować zakleszczenie .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-117">This can result in a deadlock on .NET Native.</span></span>  
  
-   <span data-ttu-id="ebf6a-118">Nie należy polegać na określanie kolejności wywołania konstruktora klasy statycznej.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-118">Don't rely on static class constructor invocation ordering.</span></span> <span data-ttu-id="ebf6a-119">W .NET Native kolejności wywołania różni się od kolejności dla standardowego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-119">In .NET Native, the invocation order is different from the order on the standard runtime.</span></span> <span data-ttu-id="ebf6a-120">(Nawet w przypadku standardowego środowiska uruchomieniowego, nie należy traktować kolejności wykonywania konstruktorów w klasie statycznej.)</span><span class="sxs-lookup"><span data-stu-id="ebf6a-120">(Even with the standard runtime, you shouldn't rely on the order of execution of static class constructors.)</span></span>  
  
-   <span data-ttu-id="ebf6a-121">Odtwarzanie w pętli nieskończonej bez nawiązywania połączenia (na przykład `while(true);`) dotyczące dowolnego wątku, mogą powodować jej zatrzymania.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-121">Infinite looping without making a call (for example, `while(true);`) on any thread may bring the app to a halt.</span></span> <span data-ttu-id="ebf6a-122">Podobnie czeka dużych lub nieskończonej może zwrócić jej zatrzymania.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-122">Similarly, large or infinite waits may bring the app to a halt.</span></span>  
  
-   <span data-ttu-id="ebf6a-123">Niektóre ogólne inicjowanie cykle nie zgłaszają wyjątki w .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-123">Certain generic initialization cycles don't throw exceptions in .NET Native.</span></span> <span data-ttu-id="ebf6a-124">Na przykład, poniższy kod zgłasza <xref:System.TypeLoadException> wyjątku dla standardowego środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-124">For example, the following code throws a <xref:System.TypeLoadException> exception on the standard CLR.</span></span> <span data-ttu-id="ebf6a-125">W .NET Native nie.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-125">In .NET Native, it doesn't.</span></span>  
  
     [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]  
  
-   <span data-ttu-id="ebf6a-126">W niektórych przypadkach program .NET Native zapewnia różne implementacje biblioteki klas .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-126">In some cases, .NET Native provides different implementations of .NET Framework class libraries.</span></span> <span data-ttu-id="ebf6a-127">Obiekt zwrócony z metody zawsze wdroży elementy członkowskie typu zwracanego.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-127">An object returned from a method will always implement the members of the returned type.</span></span> <span data-ttu-id="ebf6a-128">Jednak ponieważ jego implementacja zapasowy jest inny, nie może być można rzutować do tego samego zestawu typów, jak można wykonać następujące akcje na innych platformach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-128">However, since its backing implementation is different, you may not be able to cast it to the same set of types as you could on other .NET Framework platforms.</span></span> <span data-ttu-id="ebf6a-129">Na przykład w niektórych przypadkach nie można rzutować <xref:System.Collections.Generic.IEnumerable%601> obiektu interfejsu zwracane przez metody takie jak <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> lub <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> do `T[]`.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-129">For example, in some cases, you may not be able to cast the <xref:System.Collections.Generic.IEnumerable%601> interface object returned by methods such as <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> or <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> to `T[]`.</span></span>  
  
-   <span data-ttu-id="ebf6a-130">Pamięci podręcznej WinInet nie jest domyślnie włączona, przy użyciu platformy .NET dla Windows Store apps, ale nie znajduje się na .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-130">The WinInet cache isn't enabled by default on .NET for Windows Store apps, but it is on .NET Native.</span></span> <span data-ttu-id="ebf6a-131">Zwiększa wydajność, ale ma skutki zestawu pracy.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-131">This improves performance but has working set implications.</span></span> <span data-ttu-id="ebf6a-132">Dla deweloperów jest wymagana żadna akcja.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-132">No developer action is necessary.</span></span>  
  
<a name="Dynamic"></a>   
## <a name="dynamic-programming-differences"></a><span data-ttu-id="ebf6a-133">Różnice programowania dynamicznego</span><span class="sxs-lookup"><span data-stu-id="ebf6a-133">Dynamic programming differences</span></span>  
 <span data-ttu-id="ebf6a-134">.NET native statycznie łączy w kodzie z programu .NET Framework, aby kod aplikacji — lokalny, aby osiągnąć najwyższą wydajność.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-134">.NET Native statically links in code from the .NET Framework to make the code app-local for maximum performance.</span></span> <span data-ttu-id="ebf6a-135">Rozmiary binarnego musi jednak pozostaną małe, więc całego środowiska .NET Framework nie można przełączyć.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-135">However, binary sizes have to remain small, so the entire .NET Framework can't be brought in.</span></span> <span data-ttu-id="ebf6a-136">.NET Native kompilator rozpoznaje tego ograniczenia przy użyciu reduktor zależności, które powoduje usunięcie odwołań do nieużywanych kodu.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-136">The .NET Native compiler resolves this limitation by using a dependency reducer that removes references to unused code.</span></span> <span data-ttu-id="ebf6a-137">Jednak .NET Native może nie obsługiwać lub generować niektóre informacje o typie i kodu, gdy te informacje nie można wywnioskować statycznie w czasie kompilacji, ale zamiast tego jest pobierany dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-137">However, .NET Native might not maintain or generate some type information and code when that information can't be inferred statically at compile time, but instead is retrieved dynamically at runtime.</span></span>  
  
 <span data-ttu-id="ebf6a-138">.NET native Włącz odbicia i programowanie dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-138">.NET Native does enable reflection and dynamic programming.</span></span> <span data-ttu-id="ebf6a-139">Jednak nie wszystkie typy mogą być oznaczane w celu odbicia, ponieważ dzięki temu upewnisz się rozmiar wygenerowanego kodu zbyt duży (przede wszystkim dlatego rozważania na temat publicznych interfejsów API w programie .NET Framework jest obsługiwany).</span><span class="sxs-lookup"><span data-stu-id="ebf6a-139">However, not all types can be marked for reflection, because this would make the generated code size too large (especially because reflecting on public APIs in the .NET Framework is supported).</span></span> <span data-ttu-id="ebf6a-140">Kompilator platformy .NET Native sprawia, że opcje inteligentne, o których typy powinien obsługiwać odbicia i przechowuje metadane i generuje kod tylko dla tych typów.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-140">The .NET Native compiler makes smart choices about which types should support reflection, and it keeps the metadata and generates code only for those types.</span></span>  
  
 <span data-ttu-id="ebf6a-141">Na przykład powiązanie danych wymaga aplikację, aby można było do mapowania nazw właściwości funkcji.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-141">For example, data binding requires an app to be able to map property names to functions.</span></span> <span data-ttu-id="ebf6a-142">W aplikacjach .NET for Windows Store środowisko uruchomieniowe języka wspólnego automatycznie używa odbicia do zapewnienia tej funkcji typami zarządzanymi i publicznie dostępnych typach natywnych.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-142">In .NET for Windows Store apps, the common language runtime automatically uses reflection to provide this capability for managed types and publicly available native types.</span></span> <span data-ttu-id="ebf6a-143">W .NET Native kompilator automatycznie zawiera metadanych dla typów, dla których wiązanie danych.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-143">In .NET Native, the compiler automatically includes metadata for types to which you bind data.</span></span>  
  
 <span data-ttu-id="ebf6a-144">.NET Native kompilator może również obsługiwać powszechnie używane typy rodzajowe taką jak <xref:System.Collections.Generic.List%601> i <xref:System.Collections.Generic.Dictionary%602>, które działają bez żadnych wskazówek dotyczących serwerów lub dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-144">The .NET Native compiler can also handle commonly used generic types such as <xref:System.Collections.Generic.List%601> and <xref:System.Collections.Generic.Dictionary%602>, which work without requiring any hints or directives.</span></span> <span data-ttu-id="ebf6a-145">[Dynamiczne](~/docs/csharp/language-reference/keywords/dynamic.md) — słowo kluczowe jest również obsługiwane w ramach określonych ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-145">The [dynamic](~/docs/csharp/language-reference/keywords/dynamic.md) keyword is also supported within certain limits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ebf6a-146">Należy dokładnie przetestuj wszystkie ścieżki kodu dynamicznej podczas przenoszenia aplikacji do platformy .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-146">You should test all dynamic code paths thoroughly when porting your app to .NET Native.</span></span>  
  
 <span data-ttu-id="ebf6a-147">Domyślna konfiguracja dla platformy .NET Native są wystarczające dla większości deweloperów, ale niektórzy deweloperzy chcieć szczegółowe dostosować swoje konfiguracje za pomocą dyrektywy środowiska uruchomieniowego (. rd.xml) pliku.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-147">The default configuration for .NET Native is sufficient for most developers, but some developers might want to fine- tune their configurations by using a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="ebf6a-148">Ponadto w niektórych przypadkach kompilator platformy .NET Native jest nie można ustalić metadanych, które muszą być dostępne dla odbicia i opiera się na wskazówek, szczególnie w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="ebf6a-148">In addition, in some cases, the .NET Native compiler is unable to determine which metadata must be available for reflection and relies on hints, particularly in the following cases:</span></span>  
  
-   <span data-ttu-id="ebf6a-149">Niektóre konstrukcji, takich jak <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> i <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> nie może być określana statycznie.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-149">Some constructs like <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> and <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> can't be determined statically.</span></span>  
  
-   <span data-ttu-id="ebf6a-150">Ponieważ kompilator nie może określić wystąpień, typ ogólny, który ma być zastanowić się nad musi być określone przez dyrektywy środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-150">Because the compiler can't determine the instantiations, a generic type that you want to reflect on has to be specified by runtime directives.</span></span> <span data-ttu-id="ebf6a-151">Nie jest to po prostu, ponieważ cały kod musi być uwzględniony, ale ponieważ odbicie w typach ogólnych może tworzyć nieskończoną cyklu (na przykład podczas wywoływania metody ogólnej dla typu ogólnego).</span><span class="sxs-lookup"><span data-stu-id="ebf6a-151">This isn't just because all code must be included, but because reflection on generic types can form an infinite cycle (for example, when a generic method is invoked on a generic type).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ebf6a-152">Dyrektywy środowiska uruchomieniowego są zdefiniowane w dyrektywy środowiska uruchomieniowego (. rd.xml) pliku.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-152">Runtime directives are defined in a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="ebf6a-153">Aby uzyskać ogólne informacje dotyczące korzystania z tego pliku, zobacz [wprowadzenie](../../../docs/framework/net-native/getting-started-with-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="ebf6a-153">For general information about using this file, see [Getting Started](../../../docs/framework/net-native/getting-started-with-net-native.md).</span></span> <span data-ttu-id="ebf6a-154">Aby uzyskać informacji dotyczących dyrektyw środowiska uruchomieniowego, zobacz [dyrektywy środowiska uruchomieniowego (rd.xml) odwołanie do pliku konfiguracji](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="ebf6a-154">For information about the runtime directives, see [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
 <span data-ttu-id="ebf6a-155">.NET native obejmuje również narzędzia pomagające deweloperów określania typów poza na wybranie domyślnego zestawu powinna obsługiwać odbicia profilowania.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-155">.NET Native also includes profiling tools that help the developer determine which types outside the default set should support reflection.</span></span>  
  
<a name="Reflection"></a>   
## <a name="other-reflection-related-differences"></a><span data-ttu-id="ebf6a-156">Inne różnice dotyczące odbicia</span><span class="sxs-lookup"><span data-stu-id="ebf6a-156">Other reflection-related differences</span></span>  
 <span data-ttu-id="ebf6a-157">Istnieje szereg innych poszczególnych dotyczące odbicia różnice w zachowaniu między aplikacjami .NET for Windows Store i platformy .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-157">There are a number of other individual reflection-related differences in behavior between the .NET for Windows Store apps and .NET Native.</span></span>  
  
 <span data-ttu-id="ebf6a-158">W architektura .NET Native:</span><span class="sxs-lookup"><span data-stu-id="ebf6a-158">In .NET Native:</span></span>  
  
-   <span data-ttu-id="ebf6a-159">Prywatne odbicia przez typy i elementy członkowskie w bibliotece klas programu .NET Framework nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-159">Private reflection over types and members in the .NET Framework class library is not supported.</span></span> <span data-ttu-id="ebf6a-160">Można jednak odzwierciedlają, za pośrednictwem własnych prywatnych typów i członków, a także typy i członków w bibliotek innych firm.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-160">You can, however, reflect over your own private types and members, as well as types and members in third-party libraries.</span></span>  
  
-   <span data-ttu-id="ebf6a-161"><xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> Niepoprawnie zwraca wartość właściwości `false` dla <xref:System.Reflection.ParameterInfo> obiekt, który reprezentuje wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-161">The <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> property correctly returns `false` for a <xref:System.Reflection.ParameterInfo> object that represents a return value.</span></span> <span data-ttu-id="ebf6a-162">W aplikacjach .NET for Windows Store, zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-162">In the .NET for Windows Store apps, it returns `true`.</span></span> <span data-ttu-id="ebf6a-163">Języka pośredniego (IL) nie obsługuje tej bezpośrednio i interpretacji pozostanie ustawiony na język.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-163">Intermediate language (IL) doesn’t support this directly, and interpretation is left to the language.</span></span>  
  
-   <span data-ttu-id="ebf6a-164">Publiczne elementy członkowskie na <xref:System.RuntimeFieldHandle> i <xref:System.RuntimeMethodHandle> struktury nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-164">Public members on the <xref:System.RuntimeFieldHandle> and <xref:System.RuntimeMethodHandle> structures aren't supported.</span></span> <span data-ttu-id="ebf6a-165">Te typy są obsługiwane tylko dla programu LINQ, drzew wyrażeń i inicjowania tablicy statycznej.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-165">These types are supported only for LINQ, expression trees, and static array initialization.</span></span>  
  
-   <span data-ttu-id="ebf6a-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> i <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> Uwzględnij ukryte elementy członkowskie w klasach bazowych i dlatego może być przeciążona bez jawne przesłonięcia.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> and <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> include hidden members in base classes and thus may be overridden without explicit overrides.</span></span> <span data-ttu-id="ebf6a-167">Dotyczy to również innych [RuntimeReflectionExtensions.GetRuntime\*](xref:System.Reflection.RuntimeReflectionExtensions) metody.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-167">This is also true of other [RuntimeReflectionExtensions.GetRuntime\*](xref:System.Reflection.RuntimeReflectionExtensions) methods.</span></span>  
  
-   <span data-ttu-id="ebf6a-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> i <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> nie zakończyć się niepowodzeniem podczas próby utworzenia niektóre połączenia (na przykład tablica zkratka).</span><span class="sxs-lookup"><span data-stu-id="ebf6a-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> don't fail when you try to create certain combinations (for example, an array of byrefs).</span></span>  
  
-   <span data-ttu-id="ebf6a-169">Nie można używać odbicia do wywołania elementów członkowskich, które mają parametry wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-169">You can't use reflection to invoke members that have pointer parameters.</span></span>  
  
-   <span data-ttu-id="ebf6a-170">Za pomocą odbicia nie można pobrać lub ustawić pole wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-170">You can't use reflection to get or set a pointer field.</span></span>  
  
-   <span data-ttu-id="ebf6a-171">Gdy liczba argumentów jest nieprawidłowa, a typ jednego z argumentów jest niepoprawny, zgłasza .NET Native <xref:System.ArgumentException> zamiast <xref:System.Reflection.TargetParameterCountException>.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-171">When the argument count is wrong and the type of one of the arguments is incorrect, .NET Native throws an <xref:System.ArgumentException> instead of a <xref:System.Reflection.TargetParameterCountException>.</span></span>  
  
-   <span data-ttu-id="ebf6a-172">Serializacja binarna wyjątków ogólnie nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-172">Binary serialization of exceptions is generally not supported.</span></span> <span data-ttu-id="ebf6a-173">W rezultacie nie można serializować obiekty mogą być dodawane do <xref:System.Exception.Data%2A?displayProperty=nameWithType> słownika.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-173">As a result, non-serializable objects can be added to the <xref:System.Exception.Data%2A?displayProperty=nameWithType> dictionary.</span></span>  
  
<a name="Unsupported"></a>   
## <a name="unsupported-scenarios-and-apis"></a><span data-ttu-id="ebf6a-174">Nieobsługiwane scenariusze oraz interfejsów API</span><span class="sxs-lookup"><span data-stu-id="ebf6a-174">Unsupported scenarios and APIs</span></span>  
 <span data-ttu-id="ebf6a-175">W poniższych sekcjach wymieniono nieobsługiwane scenariusze oraz interfejsów API ogólne ustawienia projektowania, współdziałanie i technologii, takich jak HTTPClient i Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="ebf6a-175">The following sections list unsupported scenarios and APIs for general development, interop, and technologies such as HTTPClient and Windows Communication Foundation (WCF):</span></span>  
  
-   [<span data-ttu-id="ebf6a-176">Ogólne ustawienia projektowania</span><span class="sxs-lookup"><span data-stu-id="ebf6a-176">General development</span></span>](#General)  
  
-   [<span data-ttu-id="ebf6a-177">HttpClient</span><span class="sxs-lookup"><span data-stu-id="ebf6a-177">HttpClient</span></span>](#HttpClient)  
  
-   [<span data-ttu-id="ebf6a-178">Interop</span><span class="sxs-lookup"><span data-stu-id="ebf6a-178">Interop</span></span>](#Interop)  
  
-   [<span data-ttu-id="ebf6a-179">Nieobsługiwana interfejsów API</span><span class="sxs-lookup"><span data-stu-id="ebf6a-179">Unsupported APIs</span></span>](#APIs)  
  
<a name="General"></a>   
### <a name="general-development-differences"></a><span data-ttu-id="ebf6a-180">Ogólne ustawienia projektowania różnice</span><span class="sxs-lookup"><span data-stu-id="ebf6a-180">General development differences</span></span>  
 <span data-ttu-id="ebf6a-181">**Typy wartości**</span><span class="sxs-lookup"><span data-stu-id="ebf6a-181">**Value types**</span></span>  
  
-   <span data-ttu-id="ebf6a-182">Jeśli zastąpisz <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> i <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> metody dla typu wartości Nie wywołuj implementacji klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-182">If you override the <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> and <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> methods for a value type, don't call the base class implementations.</span></span> <span data-ttu-id="ebf6a-183">W aplikacjach .NET for Windows Store te metody działają na podstawie odbicia.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-183">In .NET for Windows Store apps, these methods rely on reflection.</span></span> <span data-ttu-id="ebf6a-184">W czasie kompilacji platformy .NET Native generuje implementację, które nie działają na podstawie odbicia środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-184">At compile time, .NET Native generates an implementation that doesn't rely on runtime reflection.</span></span> <span data-ttu-id="ebf6a-185">Oznacza to, że jeśli nie zastąpisz te dwie metody, będą one działać zgodnie z oczekiwaniami, ponieważ .NET Native generuje implementacji w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-185">This means that if you don't override these two methods, they will work as expected, because .NET Native generates the implementation at compile time.</span></span> <span data-ttu-id="ebf6a-186">Jednak zastąpienie tych metod, ale wywołanie do implementacji klasy podstawowej powoduje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-186">However, overriding these methods but calling the base class implementation results in an exception.</span></span>  
  
-   <span data-ttu-id="ebf6a-187">Typy wartości jest większa niż jeden megabajt nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-187">Value types larger than one megabyte aren't supported.</span></span>  
  
-   <span data-ttu-id="ebf6a-188">Typy wartości nie może mieć domyślnego konstruktora w .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-188">Value types can't have a default constructor in .NET Native.</span></span> <span data-ttu-id="ebf6a-189">(C# i Visual Basic ze Stanów Zjednoczonych zabraniają konstruktory domyślne dla typów wartości.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-189">(C# and Visual Basic prohibit default constructors on value types.</span></span> <span data-ttu-id="ebf6a-190">Jednak można je utworzyć w IL.)</span><span class="sxs-lookup"><span data-stu-id="ebf6a-190">However, these can be created in IL.)</span></span>  
  
 <span data-ttu-id="ebf6a-191">**Tablice**</span><span class="sxs-lookup"><span data-stu-id="ebf6a-191">**Arrays**</span></span>  
  
-   <span data-ttu-id="ebf6a-192">Tablice za pomocą dolnej granicy różną od zera nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-192">Arrays with a lower bound other than zero aren't supported.</span></span> <span data-ttu-id="ebf6a-193">Zazwyczaj te tablice są tworzone przez wywołanie <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-193">Typically, these arrays are created by calling the <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> overload.</span></span>  
  
-   <span data-ttu-id="ebf6a-194">Dynamiczne tworzenie tablic wielowymiarowych nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-194">Dynamic creation of multidimensional arrays isn't supported.</span></span> <span data-ttu-id="ebf6a-195">Takie tablice są zwykle tworzone przez wywołanie przeciążenia <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> metodę, która obejmuje `lengths` parametr, lub przez wywołanie <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-195">Such arrays are typically created by calling an overload of the <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> method that includes a `lengths` parameter, or by calling the <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="ebf6a-196">Tablice wielowymiarowe, które mają co najmniej czterech wymiarów nie są obsługiwane; oznacza to, że ich <xref:System.Array.Rank%2A?displayProperty=nameWithType> wartość właściwości jest 4 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-196">Multidimensional arrays that have four or more dimensions aren't supported; that is, their <xref:System.Array.Rank%2A?displayProperty=nameWithType> property value is four or greater.</span></span> <span data-ttu-id="ebf6a-197">Użyj [nierówne tablic](~/docs/csharp/programming-guide/arrays/jagged-arrays.md) (tablicy tablic) zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-197">Use [jagged arrays](~/docs/csharp/programming-guide/arrays/jagged-arrays.md) (an array of arrays) instead.</span></span> <span data-ttu-id="ebf6a-198">Na przykład `array[x,y,z]` jest nieprawidłowy, ale `array[x][y][z]` nie jest.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-198">For example, `array[x,y,z]` is invalid, but `array[x][y][z]` isn't.</span></span>  
  
-   <span data-ttu-id="ebf6a-199">Wariancja dla tablic wielowymiarowych nie jest obsługiwane i powoduje, że <xref:System.InvalidCastException> wyjątek w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-199">Variance for multidimensional arrays isn't supported and causes an <xref:System.InvalidCastException> exception at run time.</span></span>  
  
 <span data-ttu-id="ebf6a-200">**Typy ogólne**</span><span class="sxs-lookup"><span data-stu-id="ebf6a-200">**Generics**</span></span>  
  
-   <span data-ttu-id="ebf6a-201">Rozszerzenia typu ogólnego nieskończonej powoduje błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-201">Infinite generic type expansion results in a compiler error.</span></span> <span data-ttu-id="ebf6a-202">Na przykład ten kod nie zostanie skompilowany:</span><span class="sxs-lookup"><span data-stu-id="ebf6a-202">For example, this code fails to compile:</span></span>  
  
     [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]  
  
 <span data-ttu-id="ebf6a-203">**Wskaźniki**</span><span class="sxs-lookup"><span data-stu-id="ebf6a-203">**Pointers**</span></span>  
  
-   <span data-ttu-id="ebf6a-204">Tablice wskaźników typu nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-204">Arrays of pointers aren't supported.</span></span>  
  
-   <span data-ttu-id="ebf6a-205">Za pomocą odbicia nie można pobrać lub ustawić pole wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-205">You can't use reflection to get or set a pointer field.</span></span>  
  
 <span data-ttu-id="ebf6a-206">**Serializacja**</span><span class="sxs-lookup"><span data-stu-id="ebf6a-206">**Serialization**</span></span>  
  
 <span data-ttu-id="ebf6a-207"><xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> Atrybut nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-207">The <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> attribute isn't supported.</span></span> <span data-ttu-id="ebf6a-208">Użyj <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> zamiast tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-208">Use the <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> attribute instead.</span></span>  
  
 <span data-ttu-id="ebf6a-209">**Zasoby**</span><span class="sxs-lookup"><span data-stu-id="ebf6a-209">**Resources**</span></span>  
  
 <span data-ttu-id="ebf6a-210">Użycie zlokalizowanych zasobów za pomocą <xref:System.Diagnostics.Tracing.EventSource> klasy nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-210">The use of localized resources with the <xref:System.Diagnostics.Tracing.EventSource> class isn't supported.</span></span> <span data-ttu-id="ebf6a-211"><xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> Właściwości nie definiuje zlokalizowane zasoby.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-211">The <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> property doesn't define localized resources.</span></span>  
  
 <span data-ttu-id="ebf6a-212">**Delegaty**</span><span class="sxs-lookup"><span data-stu-id="ebf6a-212">**Delegates**</span></span>  
  
 <span data-ttu-id="ebf6a-213">`Delegate.BeginInvoke` i `Delegate.EndInvoke` nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-213">`Delegate.BeginInvoke` and `Delegate.EndInvoke` aren't supported.</span></span>  
  
 <span data-ttu-id="ebf6a-214">**Różne interfejsy API**</span><span class="sxs-lookup"><span data-stu-id="ebf6a-214">**Miscellaneous APIs**</span></span>  
  
-   <span data-ttu-id="ebf6a-215">[TypeInfo.GUID](xref:System.Type.GUID) zgłasza właściwości <xref:System.PlatformNotSupportedException> wyjątek Jeśli <xref:System.Runtime.InteropServices.GuidAttribute> atrybut nie jest stosowany do typu.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-215">The [TypeInfo.GUID](xref:System.Type.GUID) property throws a <xref:System.PlatformNotSupportedException> exception if a <xref:System.Runtime.InteropServices.GuidAttribute> attribute isn't applied to the type.</span></span> <span data-ttu-id="ebf6a-216">Identyfikator GUID jest używany głównie do obsługi COM.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-216">The GUID is used primarily for COM support.</span></span>  
  
-   <span data-ttu-id="ebf6a-217"><xref:System.DateTime.Parse%2A?displayProperty=nameWithType> Metoda poprawnie analizuje ciągów, które zawierają daty krótkie w .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-217">The <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> method correctly parses strings that contain short dates in .NET Native.</span></span> <span data-ttu-id="ebf6a-218">Jednak go nie zachować zgodność z zmiany daty i czasu podczas analizowania opisane w artykułach bazy wiedzy Microsoft Knowledge Base [KB2803771](https://support.microsoft.com/kb/2803771) i [KB2803755](https://support.microsoft.com/kb/2803755).</span><span class="sxs-lookup"><span data-stu-id="ebf6a-218">However, it doesn't maintain compatibility with the changes in date and time parsing described in the Microsoft Knowledge Base articles [KB2803771](https://support.microsoft.com/kb/2803771) and [KB2803755](https://support.microsoft.com/kb/2803755).</span></span>  
  
-   <span data-ttu-id="ebf6a-219"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` poprawnie jest zaokrąglana w .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-219"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` is correctly rounded in .NET Native.</span></span> <span data-ttu-id="ebf6a-220">W niektórych wersjach środowiska CLR zostały obcięte wynikowego ciągu zamiast zaokrąglane.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-220">In some versions of the CLR, the result string is truncated instead of rounded.</span></span>  
  
<a name="HttpClient"></a>   
### <a name="httpclient-differences"></a><span data-ttu-id="ebf6a-221">Różnice HttpClient</span><span class="sxs-lookup"><span data-stu-id="ebf6a-221">HttpClient differences</span></span>  
 <span data-ttu-id="ebf6a-222">W .NET Native <xref:System.Net.Http.HttpClientHandler> klasa używa wewnętrznie WinINet (za pośrednictwem <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> klasy) zamiast <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klasy używane w standardowe aplikacje .NET for Windows Store.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-222">In .NET Native, the <xref:System.Net.Http.HttpClientHandler> class internally uses WinINet (through the <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class) instead of the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes used in the standard .NET for Windows Store apps.</span></span>  <span data-ttu-id="ebf6a-223">WinINet nie obsługuje wszystkich opcji konfiguracji, który <xref:System.Net.Http.HttpClientHandler> klasy obsługuje.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-223">WinINet doesn't support all the configuration options that the <xref:System.Net.Http.HttpClientHandler> class supports.</span></span>  <span data-ttu-id="ebf6a-224">W efekcie:</span><span class="sxs-lookup"><span data-stu-id="ebf6a-224">As a result:</span></span>  
  
-   <span data-ttu-id="ebf6a-225">Niektóre właściwości możliwości na <xref:System.Net.Http.HttpClientHandler> zwracają `false` na platformy .NET Native, natomiast zwracają `true` w standardowe aplikacje .NET for Windows Store.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-225">Some of the capability properties on <xref:System.Net.Http.HttpClientHandler> return `false` on .NET Native, whereas they return `true` in the standard .NET for Windows Store apps.</span></span>  
  
-   <span data-ttu-id="ebf6a-226">Niektóre właściwości konfiguracji `get` metod dostępu zawsze zwraca wartość stałą na .NET Native, która jest inna niż domyślna wartość można konfigurować w aplikacjach .NET for Windows Store.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-226">Some of the configuration property `get` accessors always return a fixed value on .NET Native that is different than the default configurable value in .NET for Windows Store apps.</span></span>  
  
 <span data-ttu-id="ebf6a-227">Niektóre dodatkowe różnicami znajdują się w następujących podsekcjach.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-227">Some additional behavior differences are covered in the following subsections.</span></span>  
  
 <span data-ttu-id="ebf6a-228">**Proxy**</span><span class="sxs-lookup"><span data-stu-id="ebf6a-228">**Proxy**</span></span>  
  
 <span data-ttu-id="ebf6a-229"><xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> Klasa nie obsługuje konfigurowania lub zastępowania serwera proxy na podstawie danego żądania.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-229">The <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class doesn’t support configuring or overriding the proxy on a per-request basis.</span></span>  <span data-ttu-id="ebf6a-230">Oznacza to, że wszystkie żądania na .NET Native przy użyciu serwera proxy system skonfigurowany lub żaden serwer proxy, w zależności od wartości <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-230">This means that all requests on .NET Native use the system-configured proxy server or no proxy server, depending on the value of the <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="ebf6a-231">W aplikacjach .NET for Windows Store, serwer proxy jest definiowany przez <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-231">In .NET for Windows Store apps, the proxy server is defined by the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="ebf6a-232">W .NET Native, ustawienie <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> wartość inną niż `null` zgłasza <xref:System.PlatformNotSupportedException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-232">On .NET Native, setting the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> to a value other than `null` throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="ebf6a-233"><xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> Właściwość zwraca `false` na platformy .NET Native, natomiast funkcja zwraca `true` w standardowe aplikacje programu .NET Framework dla Windows Store.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-233">The <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> property returns `false` on .NET Native, whereas it returns `true` in the standard .NET Framework for Windows Store apps.</span></span>  
  
 <span data-ttu-id="ebf6a-234">**Automatyczne przekierowania**</span><span class="sxs-lookup"><span data-stu-id="ebf6a-234">**Automatic redirection**</span></span>  
  
 <span data-ttu-id="ebf6a-235"><xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> Klasy nie zezwala na maksymalną liczbę przekierowań automatycznych do skonfigurowania.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-235">The <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class doesn't allow the maximum number of automatic redirections to be configured.</span></span>  <span data-ttu-id="ebf6a-236">Wartość <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> właściwości wynosi 50, domyślnie w standardowe aplikacje .NET for Windows Store i może być modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-236">The value of the <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> property is 50 by default in the standard .NET for Windows Store apps and can be modified.</span></span> <span data-ttu-id="ebf6a-237">Na platformy .NET Native, wartość tej właściwości jest 10 i zmodyfikuj go zgłasza wyjątek w trakcie <xref:System.PlatformNotSupportedException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-237">On .NET Native, the value of this property is 10, and trying to modify it throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="ebf6a-238"><xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> Właściwość zwraca `false` na platformy .NET Native, natomiast funkcja zwraca `true` w aplikacjach .NET for Windows Store.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-238">The <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> property returns `false` on .NET Native, whereas it returns `true` in .NET for Windows Store apps.</span></span>  
  
 <span data-ttu-id="ebf6a-239">**Dekompresja automatyczna jest**</span><span class="sxs-lookup"><span data-stu-id="ebf6a-239">**Automatic decompression**</span></span>  
  
 <span data-ttu-id="ebf6a-240">.NET for Windows Store apps pozwala na ustawienie <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> właściwości <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, zarówno <xref:System.Net.DecompressionMethods.Deflate> i <xref:System.Net.DecompressionMethods.GZip>, lub <xref:System.Net.DecompressionMethods.None>.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-240">.NET for Windows Store apps allows you to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> property to <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="ebf6a-241">.NET native obsługuje tylko <xref:System.Net.DecompressionMethods.Deflate> wraz z <xref:System.Net.DecompressionMethods.GZip>, lub <xref:System.Net.DecompressionMethods.None>.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-241">.NET Native only supports <xref:System.Net.DecompressionMethods.Deflate> together with <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="ebf6a-242">Ustawiany <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> właściwości albo <xref:System.Net.DecompressionMethods.Deflate> lub <xref:System.Net.DecompressionMethods.GZip> samodzielnie dyskretnie ustawia ją na wartość oba <xref:System.Net.DecompressionMethods.Deflate> i <xref:System.Net.DecompressionMethods.GZip>.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-242">Trying to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> property to either <xref:System.Net.DecompressionMethods.Deflate> or <xref:System.Net.DecompressionMethods.GZip> alone silently sets it to both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>.</span></span>  
  
 <span data-ttu-id="ebf6a-243">**Plik cookie**</span><span class="sxs-lookup"><span data-stu-id="ebf6a-243">**Cookies**</span></span>  
  
 <span data-ttu-id="ebf6a-244">Obsługa pliku cookie jest wykonywane jednocześnie przez <xref:System.Net.Http.HttpClient> i WinINet.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-244">Cookie handling is performed simultaneously by <xref:System.Net.Http.HttpClient> and WinINet.</span></span>  <span data-ttu-id="ebf6a-245">Pliki cookie z <xref:System.Net.CookieContainer> są łączone za pomocą plików cookie w pamięci podręcznej plików cookie WinINet.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-245">Cookies from the <xref:System.Net.CookieContainer> are combined with cookies in the WinINet cookie cache.</span></span>  <span data-ttu-id="ebf6a-246">Usuwanie pliku cookie z <xref:System.Net.CookieContainer> zapobiega <xref:System.Net.Http.HttpClient> wysyłanie plików cookie, ale jeśli plik cookie został już widzianych przez WinINet i pliki cookie nie zostały usunięte przez użytkownika, WinINet wysyła je.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-246">Removing a cookie from <xref:System.Net.CookieContainer> prevents <xref:System.Net.Http.HttpClient> from sending the cookie, but if the cookie was already seen by WinINet, and cookies weren't deleted by the user, WinINet sends it.</span></span>  <span data-ttu-id="ebf6a-247">Nie będzie już możliwe programowo usunąć plik cookie z WinINet przy użyciu <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>, lub <xref:System.Net.CookieContainer> interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-247">It isn't possible to programmatically remove a cookie from WinINet by using the <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>, or <xref:System.Net.CookieContainer> API.</span></span>  <span data-ttu-id="ebf6a-248">Ustawienie <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> właściwości `false` powoduje, że tylko <xref:System.Net.Http.HttpClient> Aby zatrzymać wysyłanie plików cookie. WinINet nadal mogą obejmować jego plików cookie w żądaniu.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-248">Setting the <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> property to `false` causes only <xref:System.Net.Http.HttpClient> to stop sending cookies; WinINet might still include its cookies in the request.</span></span>  
  
 <span data-ttu-id="ebf6a-249">**Poświadczenia**</span><span class="sxs-lookup"><span data-stu-id="ebf6a-249">**Credentials**</span></span>  
  
 <span data-ttu-id="ebf6a-250">W aplikacjach .NET for Windows Store <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> i <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> właściwości działać niezależnie.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-250">In .NET for Windows Store apps, the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> properties work independently.</span></span>  <span data-ttu-id="ebf6a-251">Ponadto <xref:System.Net.Http.HttpClientHandler.Credentials%2A> właściwość akceptuje dowolny obiekt, który implementuje <xref:System.Net.ICredentials> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-251">Additionally, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property accepts any object that implements the <xref:System.Net.ICredentials> interface.</span></span>  <span data-ttu-id="ebf6a-252">W .NET Native, ustawienie <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> właściwości `true` powoduje, że <xref:System.Net.Http.HttpClientHandler.Credentials%2A> właściwości `null`.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-252">In .NET Native, setting the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> property to `true` causes the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property to become `null`.</span></span>  <span data-ttu-id="ebf6a-253">Ponadto <xref:System.Net.Http.HttpClientHandler.Credentials%2A> właściwość można ustawić tylko do `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>, lub obiekt typu <xref:System.Net.NetworkCredential>.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-253">In addition, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property can be set only to `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>, or an object of type <xref:System.Net.NetworkCredential>.</span></span>  <span data-ttu-id="ebf6a-254">Przypisywanie inne <xref:System.Net.ICredentials> obiektu, najpopularniejsze z nich jest <xref:System.Net.CredentialCache>, <xref:System.Net.Http.HttpClientHandler.Credentials%2A> zgłasza właściwości <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-254">Assigning any other <xref:System.Net.ICredentials> object, the most popular of which is <xref:System.Net.CredentialCache>, to the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property throws a <xref:System.PlatformNotSupportedException>.</span></span>  
  
 <span data-ttu-id="ebf6a-255">**Inne funkcje nieobsługiwane lub unconfigurable**</span><span class="sxs-lookup"><span data-stu-id="ebf6a-255">**Other unsupported or unconfigurable features**</span></span>  
  
 <span data-ttu-id="ebf6a-256">W architektura .NET Native:</span><span class="sxs-lookup"><span data-stu-id="ebf6a-256">In .NET Native:</span></span>  
  
-   <span data-ttu-id="ebf6a-257">Wartość <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> właściwość jest zawsze <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-257">The value of the <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> property is always <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span></span>  <span data-ttu-id="ebf6a-258">W aplikacjach .NET for Windows Store, wartość domyślna to <xref:System.Net.Http.ClientCertificateOption.Manual>.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-258">In .NET for Windows Store apps, the default is <xref:System.Net.Http.ClientCertificateOption.Manual>.</span></span>  
  
-   <span data-ttu-id="ebf6a-259"><xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> Właściwość nie jest konfigurowalne.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-259">The <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> property isn't configurable.</span></span>  
  
-   <span data-ttu-id="ebf6a-260"><xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> Właściwość jest zawsze `true`.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-260">The <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> property is always `true`.</span></span>  <span data-ttu-id="ebf6a-261">W aplikacjach .NET for Windows Store, wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-261">In .NET for Windows Store apps, the default is `false`.</span></span>  
  
-   <span data-ttu-id="ebf6a-262">`SetCookie2` Nagłówka w odpowiedzi jest ignorowana jako przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-262">The `SetCookie2` header in responses is ignored as obsolete.</span></span>  
  
<a name="Interop"></a>   
### <a name="interop-differences"></a><span data-ttu-id="ebf6a-263">Różnice międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="ebf6a-263">Interop differences</span></span>  
 <span data-ttu-id="ebf6a-264">**Przestarzałe interfejsy API**</span><span class="sxs-lookup"><span data-stu-id="ebf6a-264">**Deprecated APIs**</span></span>  
  
 <span data-ttu-id="ebf6a-265">Liczba rzadko używanych interfejsów API na potrzeby współdziałania z kodem zarządzanym są przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-265">A number of infrequently used APIs for interoperability with managed code have been deprecated.</span></span> <span data-ttu-id="ebf6a-266">W przypadku użycia z architekturą .NET Native, te interfejsy API może zgłaszać <xref:System.NotImplementedException> lub <xref:System.PlatformNotSupportedException> wyjątku lub wynik błędu kompilatora.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-266">When used with .NET Native, these APIs may throw a <xref:System.NotImplementedException> or <xref:System.PlatformNotSupportedException> exception, or result in a compiler error.</span></span> <span data-ttu-id="ebf6a-267">W aplikacjach .NET for Windows Store tych interfejsów API są oznaczone jako przestarzałe, mimo, że wywołanie ich generuje ostrzeżenie kompilatora, a nie błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-267">In .NET for Windows Store apps, these APIs are marked as obsolete, although calling them generates a compiler warning rather than a compiler error.</span></span>  
  
 <span data-ttu-id="ebf6a-268">Przestarzałe interfejsy API dla `VARIANT` marshaling obejmują:</span><span class="sxs-lookup"><span data-stu-id="ebf6a-268">Deprecated APIs for `VARIANT` marshaling include:</span></span>  

- <xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>  
- <xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>  
- <xref:System.Runtime.InteropServices.VarEnum?displayProperty=nameWithType>
  
 <span data-ttu-id="ebf6a-269"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> jest obsługiwany, ale zgłasza wyjątek, w niektórych scenariuszach, na przykład gdy jest używany z [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) lub wariantów byref.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-269"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> is supported, but it throws an exception in some scenarios, such as when it is used with [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) or byref variants.</span></span>  
  
 <span data-ttu-id="ebf6a-270">Przestarzałe interfejsy API dla [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) pomocy technicznej obejmują:</span><span class="sxs-lookup"><span data-stu-id="ebf6a-270">Deprecated APIs for [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) support include:</span></span>  
  
- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual?displayProperty=fullName> 
- <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>  

<span data-ttu-id="ebf6a-271">Przestarzałe interfejsy API dla zdarzeń COM klasycznego obejmują:</span><span class="sxs-lookup"><span data-stu-id="ebf6a-271">Deprecated APIs for classic COM events include:</span></span>

- <xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>
  
<span data-ttu-id="ebf6a-272">Przestarzałe interfejsy API w <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interfejsu, który nie jest obsługiwany w .NET Native, obejmują:</span><span class="sxs-lookup"><span data-stu-id="ebf6a-272">Deprecated APIs in the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface, which isn't supported in .NET Native, include:</span></span>  
  
- <span data-ttu-id="ebf6a-273"><xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> (wszystkie elementy członkowskie)</span><span class="sxs-lookup"><span data-stu-id="ebf6a-273"><xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> (all members)</span></span>  
- <span data-ttu-id="ebf6a-274"><xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType> (wszystkie elementy członkowskie)</span><span class="sxs-lookup"><span data-stu-id="ebf6a-274"><xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType> (all members)</span></span>  
- <span data-ttu-id="ebf6a-275"><xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType> (wszystkie elementy członkowskie)</span><span class="sxs-lookup"><span data-stu-id="ebf6a-275"><xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType> (all members)</span></span>  
- <xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=fullName>  
  
<span data-ttu-id="ebf6a-276">Inne nieobsługiwane funkcje międzyoperacyjności:</span><span class="sxs-lookup"><span data-stu-id="ebf6a-276">Other unsupported interop features include:</span></span>  
  
- <span data-ttu-id="ebf6a-277"><xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType> (wszystkie elementy członkowskie)</span><span class="sxs-lookup"><span data-stu-id="ebf6a-277"><xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType> (all members)</span></span>  
- <span data-ttu-id="ebf6a-278"><xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType> (wszystkie elementy członkowskie)</span><span class="sxs-lookup"><span data-stu-id="ebf6a-278"><xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType> (all members)</span></span>  
- <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.UnmanagedType.AsAny?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler?displayProperty=fullName>  
  
 <span data-ttu-id="ebf6a-279">Rzadko używane kierujące interfejsów API:</span><span class="sxs-lookup"><span data-stu-id="ebf6a-279">Rarely used marshalling APIs:</span></span>  
  
- <xref:System.Runtime.InteropServices.Marshal.ReadByte%28System.Object%2CSystem.Int32%29?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.Marshal.ReadInt16%28System.Object%2CSystem.Int32%29?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.Marshal.ReadInt32%28System.Object%2CSystem.Int32%29?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.Marshal.ReadInt64%28System.Object%2CSystem.Int32%29?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.Marshal.ReadIntPtr%28System.Object%2CSystem.Int32%29?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.Marshal.WriteByte%28System.Object%2CSystem.Int32%2CSystem.Byte%29?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.Marshal.WriteInt16%28System.Object%2CSystem.Int32%2CSystem.Int16%29?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.Marshal.WriteInt32%28System.Object%2CSystem.Int32%2CSystem.Int32%29?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.Marshal.WriteInt64%28System.Object%2CSystem.Int32%2CSystem.Int64%29?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.Marshal.WriteIntPtr%28System.Object%2CSystem.Int32%2CSystem.IntPtr%29?displayProperty=fullName>  
  
 <span data-ttu-id="ebf6a-280">**Wywołanie platformy i zgodność międzyoperacyjnego modelu COM**</span><span class="sxs-lookup"><span data-stu-id="ebf6a-280">**Platform invoke and COM interop compatibility**</span></span>  
  
 <span data-ttu-id="ebf6a-281">Wywołanie platformy większości i scenariuszy międzyoperacyjnego modelu COM są nadal obsługiwane w .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-281">Most platform invoke and COM interop scenarios are still supported in .NET Native.</span></span> <span data-ttu-id="ebf6a-282">W szczególności wszystkich współdziałania z programem obsługi Windows (WinRT) interfejsów API i kierowanie wszystkich wymaganych dla środowiska uruchomieniowego Windows jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-282">In particular, all interoperability with Windows Runtime (WinRT) APIs and all marshaling required for the Windows Runtime is supported.</span></span> <span data-ttu-id="ebf6a-283">Obejmuje to organizowanie obsługę:</span><span class="sxs-lookup"><span data-stu-id="ebf6a-283">This includes marshaling support for:</span></span>  
  
-   <span data-ttu-id="ebf6a-284">Tablice (w tym <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span><span class="sxs-lookup"><span data-stu-id="ebf6a-284">Arrays (including <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span></span>  
  
-   `BStr`  
  
-   <span data-ttu-id="ebf6a-285">Delegaty</span><span class="sxs-lookup"><span data-stu-id="ebf6a-285">Delegates</span></span>  
  
-   <span data-ttu-id="ebf6a-286">Ciągi (Unicode, Ansi i HSTRING)</span><span class="sxs-lookup"><span data-stu-id="ebf6a-286">Strings (Unicode, Ansi, and HSTRING)</span></span>  
  
-   <span data-ttu-id="ebf6a-287">Struktury (`byref` i `byval`)</span><span class="sxs-lookup"><span data-stu-id="ebf6a-287">Structs (`byref` and `byval`)</span></span>  
  
-   <span data-ttu-id="ebf6a-288">Unie</span><span class="sxs-lookup"><span data-stu-id="ebf6a-288">Unions</span></span>  
  
-   <span data-ttu-id="ebf6a-289">Uchwyty Win32</span><span class="sxs-lookup"><span data-stu-id="ebf6a-289">Win32 handles</span></span>  
  
-   <span data-ttu-id="ebf6a-290">Wszystkie konstrukcje WinRT</span><span class="sxs-lookup"><span data-stu-id="ebf6a-290">All WinRT constructs</span></span>  
  
-   <span data-ttu-id="ebf6a-291">Częściowa Obsługa marshaling typów variant.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-291">Partial support for marshaling variant types.</span></span> <span data-ttu-id="ebf6a-292">Obsługiwane są następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="ebf6a-292">The following are supported:</span></span>  
  
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
  
    -   [<span data-ttu-id="ebf6a-293">IUnknown</span><span class="sxs-lookup"><span data-stu-id="ebf6a-293">IUnknown</span></span>](/windows/desktop/api/unknwn/nn-unknwn-iunknown)  
  
 <span data-ttu-id="ebf6a-294">Jednak .NET Native nie obsługuje następujących działań:</span><span class="sxs-lookup"><span data-stu-id="ebf6a-294">However, .NET Native doesn't support the following:</span></span>  
  
-   <span data-ttu-id="ebf6a-295">Za pomocą klasycznego zdarzenia COM</span><span class="sxs-lookup"><span data-stu-id="ebf6a-295">Using classic COM events</span></span>  
  
-   <span data-ttu-id="ebf6a-296">Implementowanie <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interfejsu na typ zarządzany</span><span class="sxs-lookup"><span data-stu-id="ebf6a-296">Implementing the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface on a managed type</span></span>  
  
-   <span data-ttu-id="ebf6a-297">Implementowanie [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) interfejsu na typ zarządzany za pomocą <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-297">Implementing the [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) interface on a managed type through the <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> attribute.</span></span> <span data-ttu-id="ebf6a-298">Należy jednak zauważyć, że nie można wywołać obiektów COM za pomocą `IDispatch`, i nie może implementować zarządzany obiekt `IDispatch`.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-298">However, note that you can't call COM objects through `IDispatch`, and your managed object can't implement `IDispatch`.</span></span>  
  
 <span data-ttu-id="ebf6a-299">Przy użyciu odbicia do wywołania platformy wywołania metody nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-299">Using reflection to invoke a platform invoke method isn't supported.</span></span> <span data-ttu-id="ebf6a-300">To ograniczenie można obejść, zawijanie wywołania metody w innej metody i przy użyciu odbicia, aby zamiast tego wywołania otoki.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-300">You can work around this limitation by wrapping the method call in another method and using reflection to call the wrapper instead.</span></span>  
  
<a name="APIs"></a>   
### <a name="other-differences-from-net-apis-for-windows-store-apps"></a><span data-ttu-id="ebf6a-301">Inne różnice z interfejsów API platformy .NET dla Windows Store apps</span><span class="sxs-lookup"><span data-stu-id="ebf6a-301">Other differences from .NET APIs for Windows Store apps</span></span>  
 <span data-ttu-id="ebf6a-302">W tej sekcji przedstawiono pozostałych interfejsów API, które nie są obsługiwane przez .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-302">This section lists the remaining APIs that aren't supported in .NET Native.</span></span> <span data-ttu-id="ebf6a-303">Największy zestaw nieobsługiwany interfejsów API jest Windows Communication Foundation (WCF) interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-303">The largest set of the unsupported APIs are Windows Communication Foundation (WCF) APIs.</span></span>  
  
 <span data-ttu-id="ebf6a-304">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span><span class="sxs-lookup"><span data-stu-id="ebf6a-304">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span></span>  
  
 <span data-ttu-id="ebf6a-305">Typy w <xref:System.ComponentModel.DataAnnotations> i <xref:System.ComponentModel.DataAnnotations.Schema> przestrzeni nazw nie są obsługiwane przez .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-305">The types in the <xref:System.ComponentModel.DataAnnotations> and <xref:System.ComponentModel.DataAnnotations.Schema> namespaces aren't supported in .NET Native.</span></span> <span data-ttu-id="ebf6a-306">Obejmują one następujące typy, które znajdują się w aplikacjach .NET for Windows Store dla systemu Windows 8:</span><span class="sxs-lookup"><span data-stu-id="ebf6a-306">These include the following types that are present in .NET for Windows Store apps for Windows 8:</span></span>  
  
- <xref:System.ComponentModel.DataAnnotations.AssociationAttribute?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.ConcurrencyCheckAttribute?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.CustomValidationAttribute?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.DataType?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DataTypeAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayColumnAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayFormatAttribute>
- <xref:System.ComponentModel.DataAnnotations.EditableAttribute>  
- <xref:System.ComponentModel.DataAnnotations.EnumDataTypeAttribute>  
- <xref:System.ComponentModel.DataAnnotations.FilterUIHintAttribute?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.KeyAttribute?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.RangeAttribute?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.RegularExpressionAttribute?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.RequiredAttribute?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.StringLengthAttribute?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.TimestampAttribute?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.UIHintAttribute?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.ValidationContext?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.ValidationResult?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.Validator?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedAttribute?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedOption?displayProperty=nameWithType>  
  
 <span data-ttu-id="ebf6a-307">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="ebf6a-307">**Visual Basic**</span></span>  
  
 <span data-ttu-id="ebf6a-308">Visual Basic nie jest obecnie obsługiwane w .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-308">Visual Basic isn't currently supported in .NET Native.</span></span> <span data-ttu-id="ebf6a-309">Następujące typy w <xref:Microsoft.VisualBasic> i <xref:Microsoft.VisualBasic.CompilerServices> przestrzenie nazw są niedostępne w przypadku platformy .NET Native:</span><span class="sxs-lookup"><span data-stu-id="ebf6a-309">The following types in the <xref:Microsoft.VisualBasic> and <xref:Microsoft.VisualBasic.CompilerServices> namespaces aren't available in .NET Native:</span></span>  

- <xref:Microsoft.VisualBasic.CallType?displayProperty=nameWithType>  
- <xref:Microsoft.VisualBasic.Constants?displayProperty=nameWithType>  
- <xref:Microsoft.VisualBasic.HideModuleNameAttribute?displayProperty=nameWithType>  
- <xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType>  
- <xref:Microsoft.VisualBasic.CompilerServices.Conversions?displayProperty=nameWithType>  
- <xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute?displayProperty=nameWithType>  
- <xref:Microsoft.VisualBasic.CompilerServices.IncompleteInitialization?displayProperty=nameWithType>  
- <xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=nameWithType>  
- <xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl?displayProperty=nameWithType>  
- <xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl.ForLoopControl?displayProperty=nameWithType>  
- <xref:Microsoft.VisualBasic.CompilerServices.Operators?displayProperty=nameWithType>  
- <xref:Microsoft.VisualBasic.CompilerServices.OptionCompareAttribute?displayProperty=nameWithType>  
- <xref:Microsoft.VisualBasic.CompilerServices.OptionTextAttribute?displayProperty=nameWithType>  
- <xref:Microsoft.VisualBasic.CompilerServices.ProjectData?displayProperty=nameWithType>  
- <xref:Microsoft.VisualBasic.CompilerServices.StandardModuleAttribute?displayProperty=nameWithType>  
- <xref:Microsoft.VisualBasic.CompilerServices.StaticLocalInitFlag?displayProperty=nameWithType>  
- <xref:Microsoft.VisualBasic.CompilerServices.Utils?displayProperty=nameWithType>  
  
 <span data-ttu-id="ebf6a-310">**Kontekstu odbicia (przestrzeń nazw System.Reflection.Context)**</span><span class="sxs-lookup"><span data-stu-id="ebf6a-310">**Reflection Context (System.Reflection.Context namespace)**</span></span>  
  
 <span data-ttu-id="ebf6a-311"><xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> Klasy nie jest obsługiwany w .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-311">The <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> class isn't supported in .NET Native.</span></span>  
  
 <span data-ttu-id="ebf6a-312">**RTC (System.Net.Http.Rtc)**</span><span class="sxs-lookup"><span data-stu-id="ebf6a-312">**RTC (System.Net.Http.Rtc)**</span></span>  
  
 <span data-ttu-id="ebf6a-313">`System.Net.Http.RtcRequestFactory` Klasy nie jest obsługiwany w .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-313">The `System.Net.Http.RtcRequestFactory` class isn't supported in .NET Native.</span></span>  
  
 <span data-ttu-id="ebf6a-314">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span><span class="sxs-lookup"><span data-stu-id="ebf6a-314">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span></span>  
  
 <span data-ttu-id="ebf6a-315">Typy w [przestrzenie nazw System.ServiceModel.\*](xref:System.ServiceModel) nie są obsługiwane przez .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-315">The types in the [System.ServiceModel.\* namespaces](xref:System.ServiceModel) aren't supported in .NET Native.</span></span> <span data-ttu-id="ebf6a-316">Te zawiera następujące typy:</span><span class="sxs-lookup"><span data-stu-id="ebf6a-316">These includes the following types:</span></span>  
  
- <xref:System.ServiceModel.ActionNotSupportedException?displayProperty=nameWithType>  
- <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>  
- <xref:System.ServiceModel.BasicHttpMessageCredentialType?displayProperty=nameWithType>  
- <xref:System.ServiceModel.BasicHttpSecurity?displayProperty=nameWithType>  
- <xref:System.ServiceModel.BasicHttpSecurityMode?displayProperty=nameWithType>  
- <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType>  
- <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>  
- <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>  
- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>  
- <xref:System.ServiceModel.ClientBase%601.BeginOperationDelegate?displayProperty=nameWithType>  
- <xref:System.ServiceModel.ClientBase%601.ChannelBase%601?displayProperty=nameWithType>  
- <xref:System.ServiceModel.ClientBase%601.EndOperationDelegate?displayProperty=nameWithType>  
- <xref:System.ServiceModel.ClientBase%601.InvokeAsyncCompletedEventArgs?displayProperty=nameWithType>  
- <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>  
- <xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>  
- <xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>  
- <xref:System.ServiceModel.CommunicationState?displayProperty=nameWithType>  
- <xref:System.ServiceModel.DataContractFormatAttribute?displayProperty=nameWithType>  
- <xref:System.ServiceModel.DnsEndpointIdentity?displayProperty=nameWithType>  
- <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType>  
- <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType>  
- <xref:System.ServiceModel.EndpointAddress?displayProperty=nameWithType>  
- <xref:System.ServiceModel.EndpointAddressBuilder?displayProperty=nameWithType>  
- <xref:System.ServiceModel.EndpointIdentity?displayProperty=nameWithType>  
- <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType>  
- <xref:System.ServiceModel.EnvelopeVersion?displayProperty=nameWithType>  
- <xref:System.ServiceModel.ExceptionDetail?displayProperty=nameWithType>  
- <xref:System.ServiceModel.FaultCode?displayProperty=nameWithType>  
- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>  
- <xref:System.ServiceModel.FaultException?displayProperty=nameWithType>  
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>  
- <xref:System.ServiceModel.FaultReason?displayProperty=nameWithType>  
- <xref:System.ServiceModel.FaultReasonText?displayProperty=nameWithType>  
- <xref:System.ServiceModel.HttpBindingBase?displayProperty=nameWithType>  
- <xref:System.ServiceModel.HttpClientCredentialType?displayProperty=nameWithType>  
- <xref:System.ServiceModel.HttpTransportSecurity?displayProperty=nameWithType>  
- <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>  
- <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType>  
- <xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType>  
- <xref:System.ServiceModel.IDefaultCommunicationTimeouts?displayProperty=nameWithType>  
- <xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType>  
- <xref:System.ServiceModel.IExtension%601?displayProperty=nameWithType>  
- <xref:System.ServiceModel.IExtensionCollection%601?displayProperty=nameWithType>  
- <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType>  
- <xref:System.ServiceModel.InvalidMessageContractException?displayProperty=nameWithType>  
- <xref:System.ServiceModel.MessageBodyMemberAttribute?displayProperty=nameWithType>  
- <xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType>  
- <xref:System.ServiceModel.MessageContractMemberAttribute?displayProperty=nameWithType>  
- <xref:System.ServiceModel.MessageCredentialType?displayProperty=nameWithType>  
- <xref:System.ServiceModel.MessageHeader%601?displayProperty=nameWithType>  
- <xref:System.ServiceModel.MessageHeaderException?displayProperty=nameWithType>  
- <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>  
- <xref:System.ServiceModel.MessageSecurityOverTcp?displayProperty=nameWithType>  
- <xref:System.ServiceModel.MessageSecurityVersion?displayProperty=nameWithType>  
- <xref:System.ServiceModel.NetHttpBinding?displayProperty=nameWithType>  
- <xref:System.ServiceModel.NetHttpMessageEncoding?displayProperty=nameWithType>  
- <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType>  
- <xref:System.ServiceModel.NetTcpSecurity?displayProperty=nameWithType>  
- <xref:System.ServiceModel.OperationContext?displayProperty=nameWithType>  
- <xref:System.ServiceModel.OperationContextScope?displayProperty=nameWithType>  
- <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType>  
- <xref:System.ServiceModel.OperationFormatStyle?displayProperty=nameWithType>  
- <xref:System.ServiceModel.ProtocolException?displayProperty=nameWithType>  
- <xref:System.ServiceModel.QuotaExceededException?displayProperty=nameWithType>  
- <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>  
- <xref:System.ServiceModel.ServerTooBusyException?displayProperty=nameWithType>  
- <xref:System.ServiceModel.ServiceActivationException?displayProperty=nameWithType>  
- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>  
- <xref:System.ServiceModel.ServiceKnownTypeAttribute?displayProperty=nameWithType>  
- <xref:System.ServiceModel.SpnEndpointIdentity?displayProperty=nameWithType>  
- <xref:System.ServiceModel.TcpClientCredentialType?displayProperty=nameWithType>  
- <xref:System.ServiceModel.TcpTransportSecurity?displayProperty=nameWithType>  
- <xref:System.ServiceModel.TransferMode?displayProperty=nameWithType>  
- <xref:System.ServiceModel.UnknownMessageReceivedEventArgs?displayProperty=nameWithType>  
- <xref:System.ServiceModel.UpnEndpointIdentity?displayProperty=nameWithType>  
- <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.AddressHeader?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.AddressHeaderCollection?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.AddressingVersion?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.ChannelManagerBase?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.ChannelParameterCollection?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.CommunicationObject?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.FaultConverter?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.HttpRequestMessageProperty?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.HttpResponseMessageProperty?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.IChannel?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.IChannelFactory?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.IChannelFactory%601?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.IDuplexChannel?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.IDuplexSession?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.IDuplexSessionChannel?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.IHttpCookieContainerManager?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.IInputChannel?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.IInputSession?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.IInputSessionChannel?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.IMessageProperty?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.IOutputChannel?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.IOutputSession?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.IOutputSessionChannel?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.IRequestSessionChannel?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.MessageBuffer?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.MessageEncoder?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.MessageEncoderFactory?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.MessageHeader?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.MessageHeaderInfo?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.MessageHeaders?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.MessageProperties?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.MessageState?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.RequestContext?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.SecurityHeaderLayout?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.TransportBindingElement?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.WebSocketTransportSettings?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.WebSocketTransportUsage?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.ClientCredentials?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.FaultDescription?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.FaultDescriptionCollection?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.MessageBodyDescription?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.MessageDescription?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.MessageDescriptionCollection?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.MessageDirection?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.MessageHeaderDescription?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.MessageHeaderDescriptionCollection?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.MessagePartDescription?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.MessagePartDescriptionCollection?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.MessagePropertyDescription?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.MessagePropertyDescriptionCollection?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.OperationDescription?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.OperationDescriptionCollection?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Dispatcher.ClientOperation?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Dispatcher.DispatchOperation?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Dispatcher.DispatchRuntime?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Dispatcher.EndpointDispatcher?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Dispatcher.IClientOperationSelector?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Security.BasicSecurityProfileVersion?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Security.HttpDigestClientCredential?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Security.SecureConversationVersion?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Security.SecurityAccessDeniedException?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Security.SecurityPolicyVersion?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Security.SecurityVersion?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Security.TrustVersion?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Security.WindowsClientCredential?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Security.Tokens.UserNameSecurityTokenParameters?displayProperty=nameWithType>  
  
### <a name="differences-in-serializers"></a><span data-ttu-id="ebf6a-317">Różnice serializatorów</span><span class="sxs-lookup"><span data-stu-id="ebf6a-317">Differences in serializers</span></span>  
 <span data-ttu-id="ebf6a-318">Następujące różnice dotyczą serializacji i deserializacji za pomocą <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, i <xref:System.Xml.Serialization.XmlSerializer> klasy:</span><span class="sxs-lookup"><span data-stu-id="ebf6a-318">The following differences concern serialization and deserialization with the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes:</span></span>  
  
-   <span data-ttu-id="ebf6a-319">W .NET Native <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> zakończyć się niepowodzeniem do serializacji lub deserializacji klasy pochodnej, która ma składową klasy bazowej, w której typ nie jest głównego typu serializacji.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-319">In .NET Native, <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize or deserialize a derived class that has a base class member whose type isn't a root serialization type.</span></span> <span data-ttu-id="ebf6a-320">Na przykład w poniższym kodzie próby serializacji lub deserializacji `Y` powoduje błąd:</span><span class="sxs-lookup"><span data-stu-id="ebf6a-320">For example, in the following code, trying to serialize or deserialize `Y` results in an error:</span></span>  
  
     [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]  
  
     <span data-ttu-id="ebf6a-321">Typ `InnerType` nie jest znana, serializator, ponieważ elementy członkowskie klasy bazowej nie są przesunięta podczas serializacji.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-321">Type `InnerType` isn't known to the serializer, because the members of the base class aren't traversed during serialization.</span></span>  
  
-   <span data-ttu-id="ebf6a-322"><xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nie można serializować klasy lub struktury, która implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-322"><xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize a class or structure that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="ebf6a-323">Na przykład do serializacji lub deserializacji zakończona niepowodzeniem następujących typów:</span><span class="sxs-lookup"><span data-stu-id="ebf6a-323">For example, the following types fail to serialize or deserialize:</span></span>  

-   <span data-ttu-id="ebf6a-324"><xref:System.Xml.Serialization.XmlSerializer> nie może serializować następującą wartość obiektu, ponieważ nie wie, dokładna typ obiektu do zserializowania:</span><span class="sxs-lookup"><span data-stu-id="ebf6a-324"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize the following object value, because it doesn't know the exact type of the object to be serialized:</span></span>  

-   <span data-ttu-id="ebf6a-325"><xref:System.Xml.Serialization.XmlSerializer> kończy się niepowodzeniem do serializacji lub deserializacji, jeśli typ Zserializowany obiekt <xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-325"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize or deserialize if the type of the serialized object is <xref:System.Xml.XmlQualifiedName>.</span></span>  
  
-   <span data-ttu-id="ebf6a-326">Wszystkie serializatory (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, i <xref:System.Xml.Serialization.XmlSerializer>) nie można wygenerować kodu serializacji dla typu <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> lub typu, który zawiera <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-326">All serializers (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer>) fail to generate serialization code for type <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> or for a type that contains <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="ebf6a-327">Zamiast tego są wyświetlane błędy czasu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-327">They display build-time errors instead.</span></span>  
  
-   <span data-ttu-id="ebf6a-328">Następujące konstruktory serializacji typów nie są gwarantowane zgodnie z oczekiwaniami:</span><span class="sxs-lookup"><span data-stu-id="ebf6a-328">The following constructors of the serialization types aren't guaranteed to work as expected:</span></span>  
  
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
  
-   <span data-ttu-id="ebf6a-329"><xref:System.Xml.Serialization.XmlSerializer> Nie można wygenerować kodu dla typu, który posiada metody opartego na atrybutach z dowolnymi z następujących atrybutów:</span><span class="sxs-lookup"><span data-stu-id="ebf6a-329"><xref:System.Xml.Serialization.XmlSerializer> fails to generate code for a type that has methods attributed with any of the following attributes:</span></span>  
  
    -   <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
-   <span data-ttu-id="ebf6a-330"><xref:System.Xml.Serialization.XmlSerializer> nie uznaje <xref:System.Xml.Serialization.IXmlSerializable> interfejsu niestandardowej serializacji.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-330"><xref:System.Xml.Serialization.XmlSerializer> doesn't honor the <xref:System.Xml.Serialization.IXmlSerializable> custom serialization interface.</span></span> <span data-ttu-id="ebf6a-331">Jeśli masz klasę, która implementuje ten interfejs <xref:System.Xml.Serialization.XmlSerializer> uwzględnia typu plain stary typ obiektu (POCO) środowiska CLR i serializuje tylko właściwości publiczne.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-331">If you have a class that implements this interface, <xref:System.Xml.Serialization.XmlSerializer> considers the type a plain old CLR object (POCO) type and serializes only its public properties.</span></span>  
  
-   <span data-ttu-id="ebf6a-332">Serializacja zwykły <xref:System.Exception> obiektu nie działa dobrze z <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-332">Serializing a plain <xref:System.Exception> object doesn't work well with <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

<a name="VS"></a>   
## <a name="visual-studio-differences"></a><span data-ttu-id="ebf6a-333">Różnice w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ebf6a-333">Visual Studio differences</span></span>  
 <span data-ttu-id="ebf6a-334">**Wyjątki i debugowanie**</span><span class="sxs-lookup"><span data-stu-id="ebf6a-334">**Exceptions and debugging**</span></span>  
  
 <span data-ttu-id="ebf6a-335">Jeśli korzystasz z aplikacji, skompilowane przy użyciu platformy .NET Native debugera, wyjątki pierwszej szansy są włączone dla następujących typów wyjątków:</span><span class="sxs-lookup"><span data-stu-id="ebf6a-335">When you're running apps compiled by using .NET Native in the debugger, first-chance exceptions are enabled for the following exception types:</span></span>  
  
-   <xref:System.MemberAccessException>  
  
-   <xref:System.TypeAccessException>  
  
 <span data-ttu-id="ebf6a-336">**Tworzenie aplikacji**</span><span class="sxs-lookup"><span data-stu-id="ebf6a-336">**Building apps**</span></span>  
  
 <span data-ttu-id="ebf6a-337">Użyj x86 kompilacji narzędzia, które są stosowane domyślnie przez program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-337">Use the x86 build tools that are used by default by Visual Studio.</span></span> <span data-ttu-id="ebf6a-338">Nie zaleca się za pomocą narzędzia AMD64 MSBuild, które znajdują się w folderze C:\Program Files (x86)\MSBuild\12.0\bin\amd64; mogą one tworzyć problemów związanych z kompilacją.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-338">We don't recommend using the AMD64 MSBuild tools, which are found in C:\Program Files (x86)\MSBuild\12.0\bin\amd64; these may create build problems.</span></span>  
  
 <span data-ttu-id="ebf6a-339">**Profilers**</span><span class="sxs-lookup"><span data-stu-id="ebf6a-339">**Profilers**</span></span>  
  
-   <span data-ttu-id="ebf6a-340">Profiler procesora CPU w usłudze Visual Studio i Profiler pamięci XAML nie Just My-kodu są poprawnie wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-340">The Visual Studio CPU Profiler and XAML Memory Profiler don't display Just-My-Code correctly.</span></span>  
  
-   <span data-ttu-id="ebf6a-341">Profiler pamięci XAML nie są wyświetlane dokładne dane sterty zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-341">The XAML Memory Profiler doesn't accurately display managed heap data.</span></span>  
  
-   <span data-ttu-id="ebf6a-342">Profiler procesora CPU nie poprawnie zidentyfikować modułów i wyświetla prefiks nazwy funkcji.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-342">The CPU Profiler doesn't correctly identify modules, and displays prefixed function names.</span></span>  
  
 <span data-ttu-id="ebf6a-343">**Projekty Biblioteka testów jednostkowych**</span><span class="sxs-lookup"><span data-stu-id="ebf6a-343">**Unit Test Library projects**</span></span>  
  
 <span data-ttu-id="ebf6a-344">Włączenie .NET Native na Biblioteka testów jednostkowych dla projektu aplikacji Windows Store nie jest obsługiwane i powoduje, że projekt, aby kompilacja się nie powieść.</span><span class="sxs-lookup"><span data-stu-id="ebf6a-344">Enabling .NET Native on a Unit Test Library for a Windows Store apps project isn't supported and causes the project to fail to build.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebf6a-345">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ebf6a-345">See also</span></span>

- [<span data-ttu-id="ebf6a-346">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="ebf6a-346">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)
- [<span data-ttu-id="ebf6a-347">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="ebf6a-347">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="ebf6a-348">Omówienie aplikacji .NET dla Windows Store</span><span class="sxs-lookup"><span data-stu-id="ebf6a-348">.NET For Windows Store apps overview</span></span>](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29)
- [<span data-ttu-id="ebf6a-349">Obsługa programu .NET Framework dla aplikacji ze Sklepu Windows i środowiska wykonawczego systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ebf6a-349">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)

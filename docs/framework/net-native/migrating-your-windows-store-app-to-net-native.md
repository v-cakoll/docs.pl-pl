---
title: Migrowanie aplikacji ze Sklepu Windows do architektury .NET Native
ms.date: 03/30/2017
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fdff7aa92e4c1c357c83b625a6daadbf0a8d556b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049517"
---
# <a name="migrating-your-windows-store-app-to-net-native"></a><span data-ttu-id="28a5c-102">Migrowanie aplikacji ze Sklepu Windows do architektury .NET Native</span><span class="sxs-lookup"><span data-stu-id="28a5c-102">Migrating Your Windows Store App to .NET Native</span></span>

<span data-ttu-id="28a5c-103">.NET Native zapewnia statyczną kompilację aplikacji w Sklepie Windows lub na komputerze dewelopera.</span><span class="sxs-lookup"><span data-stu-id="28a5c-103">.NET Native provides static compilation of apps in the Windows Store or on the developer’s computer.</span></span> <span data-ttu-id="28a5c-104">Różni się to od kompilacji dynamicznej wykonywanej dla aplikacji ze sklepu Windows przez kompilator just-in-Time (JIT) lub [natywny Generator obrazu (Ngen. exe)](../tools/ngen-exe-native-image-generator.md) na urządzeniu.</span><span class="sxs-lookup"><span data-stu-id="28a5c-104">This differs from the dynamic compilation performed for Windows Store apps by the just-in-time (JIT) compiler or the [Native Image Generator (Ngen.exe)](../tools/ngen-exe-native-image-generator.md) on the device.</span></span> <span data-ttu-id="28a5c-105">Pomimo różnic, .NET Native próbuje zachować zgodność z platformą [.NET dla aplikacji ze sklepu Windows](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29).</span><span class="sxs-lookup"><span data-stu-id="28a5c-105">Despite the differences, .NET Native tries to maintain compatibility with the [.NET for Windows Store apps](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29).</span></span> <span data-ttu-id="28a5c-106">W większości przypadków elementy, które działają na platformie .NET dla aplikacji ze sklepu Windows, działają również z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="28a5c-106">For the most part, things that work on the .NET for Windows Store apps also work with .NET Native.</span></span>  <span data-ttu-id="28a5c-107">Jednak w niektórych przypadkach mogą wystąpić zmiany behawioralne.</span><span class="sxs-lookup"><span data-stu-id="28a5c-107">However, in some cases, you may encounter behavioral changes.</span></span> <span data-ttu-id="28a5c-108">W tym dokumencie omówiono różnice między standardową platformą .NET dla aplikacji ze sklepu Windows i .NET Native w następujących obszarach:</span><span class="sxs-lookup"><span data-stu-id="28a5c-108">This document discusses these differences between the standard .NET for Windows Store apps and .NET Native in the following areas:</span></span>

- [<span data-ttu-id="28a5c-109">Ogólne różnice w środowisku uruchomieniowym</span><span class="sxs-lookup"><span data-stu-id="28a5c-109">General runtime differences</span></span>](#Runtime)

- [<span data-ttu-id="28a5c-110">Różnice w programowaniu dynamicznym</span><span class="sxs-lookup"><span data-stu-id="28a5c-110">Dynamic programming differences</span></span>](#Dynamic)

- [<span data-ttu-id="28a5c-111">Inne różnice dotyczące odbicia</span><span class="sxs-lookup"><span data-stu-id="28a5c-111">Other reflection-related differences</span></span>](#Reflection)

- [<span data-ttu-id="28a5c-112">Nieobsługiwane scenariusze i interfejsy API</span><span class="sxs-lookup"><span data-stu-id="28a5c-112">Unsupported scenarios and APIs</span></span>](#Unsupported)

- [<span data-ttu-id="28a5c-113">Różnice w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="28a5c-113">Visual Studio differences</span></span>](#VS)

<a name="Runtime"></a>

## <a name="general-runtime-differences"></a><span data-ttu-id="28a5c-114">Ogólne różnice w środowisku uruchomieniowym</span><span class="sxs-lookup"><span data-stu-id="28a5c-114">General runtime differences</span></span>

- <span data-ttu-id="28a5c-115">Wyjątki, takie jak <xref:System.TypeLoadException>, które są generowane przez kompilator JIT, gdy aplikacja działa w środowisku uruchomieniowym języka wspólnego (CLR) zwykle powoduje błędy w czasie kompilacji w przypadku przetworzenia przez .NET Native.</span><span class="sxs-lookup"><span data-stu-id="28a5c-115">Exceptions, such as <xref:System.TypeLoadException>, that are thrown by the JIT compiler when an app runs on the common language runtime (CLR) generally result in compile-time errors when processed by .NET Native.</span></span>

- <span data-ttu-id="28a5c-116">Nie wywołuj <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> metody z wątku interfejsu użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="28a5c-116">Don't call the <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method from an app's UI thread.</span></span> <span data-ttu-id="28a5c-117">Może to spowodować zakleszczenie .NET Native.</span><span class="sxs-lookup"><span data-stu-id="28a5c-117">This can result in a deadlock on .NET Native.</span></span>

- <span data-ttu-id="28a5c-118">Nie należy polegać na kolejności wywołania konstruktora klasy statycznej.</span><span class="sxs-lookup"><span data-stu-id="28a5c-118">Don't rely on static class constructor invocation ordering.</span></span> <span data-ttu-id="28a5c-119">W .NET Native kolejność wywoływania różni się od kolejności w standardowym środowisku uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="28a5c-119">In .NET Native, the invocation order is different from the order on the standard runtime.</span></span> <span data-ttu-id="28a5c-120">(Nawet w przypadku standardowego środowiska uruchomieniowego nie należy polegać na kolejności wykonywania konstruktorów klas statycznych).</span><span class="sxs-lookup"><span data-stu-id="28a5c-120">(Even with the standard runtime, you shouldn't rely on the order of execution of static class constructors.)</span></span>

- <span data-ttu-id="28a5c-121">Nieskończona pętla bez wykonywania wywołania (na przykład `while(true);`) w dowolnym wątku może spowodować zatrzymanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="28a5c-121">Infinite looping without making a call (for example, `while(true);`) on any thread may bring the app to a halt.</span></span> <span data-ttu-id="28a5c-122">Podobnie duże lub nieskończone oczekiwania mogą spowodować zatrzymanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="28a5c-122">Similarly, large or infinite waits may bring the app to a halt.</span></span>

- <span data-ttu-id="28a5c-123">Niektóre ogólne cykle inicjowania nie generują wyjątków w .NET Native.</span><span class="sxs-lookup"><span data-stu-id="28a5c-123">Certain generic initialization cycles don't throw exceptions in .NET Native.</span></span> <span data-ttu-id="28a5c-124">Na przykład poniższy kod zgłasza <xref:System.TypeLoadException> wyjątek dla standardowego środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="28a5c-124">For example, the following code throws a <xref:System.TypeLoadException> exception on the standard CLR.</span></span> <span data-ttu-id="28a5c-125">W .NET Native nie jest.</span><span class="sxs-lookup"><span data-stu-id="28a5c-125">In .NET Native, it doesn't.</span></span>

  [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]

- <span data-ttu-id="28a5c-126">W niektórych przypadkach .NET Native oferuje różne implementacje bibliotek klasy .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="28a5c-126">In some cases, .NET Native provides different implementations of .NET Framework class libraries.</span></span> <span data-ttu-id="28a5c-127">Obiekt zwrócony z metody zawsze implementuje elementy członkowskie zwracanego typu.</span><span class="sxs-lookup"><span data-stu-id="28a5c-127">An object returned from a method will always implement the members of the returned type.</span></span> <span data-ttu-id="28a5c-128">Jednak ze względu na to, że jego implementacja zapasowa jest inna, można nie być w stanie rzutować go na ten sam zestaw typów, co w przypadku innych platform .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="28a5c-128">However, since its backing implementation is different, you may not be able to cast it to the same set of types as you could on other .NET Framework platforms.</span></span> <span data-ttu-id="28a5c-129">Na przykład w niektórych przypadkach może nie <xref:System.Collections.Generic.IEnumerable%601> być możliwe rzutowanie obiektu interfejsu zwróconego przez metody takie jak <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> lub <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> do `T[]`.</span><span class="sxs-lookup"><span data-stu-id="28a5c-129">For example, in some cases, you may not be able to cast the <xref:System.Collections.Generic.IEnumerable%601> interface object returned by methods such as <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> or <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> to `T[]`.</span></span>

- <span data-ttu-id="28a5c-130">Pamięć podręczna usługi WinInet nie jest domyślnie włączona w programie .NET dla aplikacji ze sklepu Windows, ale jest włączona .NET Native.</span><span class="sxs-lookup"><span data-stu-id="28a5c-130">The WinInet cache isn't enabled by default on .NET for Windows Store apps, but it is on .NET Native.</span></span> <span data-ttu-id="28a5c-131">Poprawia to wydajność, ale ma implikacje dla zestawu roboczego.</span><span class="sxs-lookup"><span data-stu-id="28a5c-131">This improves performance but has working set implications.</span></span> <span data-ttu-id="28a5c-132">Nie jest wymagana żadna akcja dewelopera.</span><span class="sxs-lookup"><span data-stu-id="28a5c-132">No developer action is necessary.</span></span>

<a name="Dynamic"></a>

## <a name="dynamic-programming-differences"></a><span data-ttu-id="28a5c-133">Różnice w programowaniu dynamicznym</span><span class="sxs-lookup"><span data-stu-id="28a5c-133">Dynamic programming differences</span></span>

<span data-ttu-id="28a5c-134">.NET Native statycznie linki w kodzie z .NET Framework, aby udostępnić kod aplikacji w celu uzyskania maksymalnej wydajności.</span><span class="sxs-lookup"><span data-stu-id="28a5c-134">.NET Native statically links in code from the .NET Framework to make the code app-local for maximum performance.</span></span> <span data-ttu-id="28a5c-135">Jednak rozmiary binarne muszą pozostać małe, więc nie można wykonać całego .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="28a5c-135">However, binary sizes have to remain small, so the entire .NET Framework can't be brought in.</span></span> <span data-ttu-id="28a5c-136">Kompilator .NET Native rozwiązuje to ograniczenie przy użyciu funkcji zmniejszającej zależność, która usuwa odwołania do nieużywanego kodu.</span><span class="sxs-lookup"><span data-stu-id="28a5c-136">The .NET Native compiler resolves this limitation by using a dependency reducer that removes references to unused code.</span></span> <span data-ttu-id="28a5c-137">Jednak .NET Native mogą nie obsługiwać ani generować informacji o typie i kodzie, gdy te informacje nie mogą zostać wywnioskowane statycznie w czasie kompilacji, ale zamiast tego są pobierane dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="28a5c-137">However, .NET Native might not maintain or generate some type information and code when that information can't be inferred statically at compile time, but instead is retrieved dynamically at runtime.</span></span>

<span data-ttu-id="28a5c-138">.NET Native umożliwia programowanie odbicia i dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="28a5c-138">.NET Native does enable reflection and dynamic programming.</span></span> <span data-ttu-id="28a5c-139">Jednak nie wszystkie typy mogą być oznaczone do odbicia, ponieważ spowodowałoby to, że rozmiar wygenerowanego kodu jest zbyt duży (szczególnie ze względu na to, że jest obsługiwane odbicie w publicznych interfejsach API w .NET Framework).</span><span class="sxs-lookup"><span data-stu-id="28a5c-139">However, not all types can be marked for reflection, because this would make the generated code size too large (especially because reflecting on public APIs in the .NET Framework is supported).</span></span> <span data-ttu-id="28a5c-140">Kompilator .NET Native umożliwia inteligentne wybór typów, które powinny obsługiwać odbicie, i utrzymuje metadane i generuje kod tylko dla tych typów.</span><span class="sxs-lookup"><span data-stu-id="28a5c-140">The .NET Native compiler makes smart choices about which types should support reflection, and it keeps the metadata and generates code only for those types.</span></span>

<span data-ttu-id="28a5c-141">Na przykład powiązanie danych wymaga, aby aplikacja mogła mapować nazwy właściwości do funkcji.</span><span class="sxs-lookup"><span data-stu-id="28a5c-141">For example, data binding requires an app to be able to map property names to functions.</span></span> <span data-ttu-id="28a5c-142">W programie .NET dla aplikacji do sklepu Windows środowisko uruchomieniowe języka wspólnego automatycznie używa odbicia w celu zapewnienia tej możliwości dla typów zarządzanych i publicznie dostępnych typów natywnych.</span><span class="sxs-lookup"><span data-stu-id="28a5c-142">In .NET for Windows Store apps, the common language runtime automatically uses reflection to provide this capability for managed types and publicly available native types.</span></span> <span data-ttu-id="28a5c-143">W .NET Native kompilator automatycznie zawiera metadane dla typów, do których są powiązane dane.</span><span class="sxs-lookup"><span data-stu-id="28a5c-143">In .NET Native, the compiler automatically includes metadata for types to which you bind data.</span></span>

<span data-ttu-id="28a5c-144">Kompilator .NET Native może również obsługiwać powszechnie używane typy ogólne, takie jak <xref:System.Collections.Generic.List%601> i <xref:System.Collections.Generic.Dictionary%602>, które działają bez konieczności stosowania jakichkolwiek wskazówek lub dyrektyw.</span><span class="sxs-lookup"><span data-stu-id="28a5c-144">The .NET Native compiler can also handle commonly used generic types such as <xref:System.Collections.Generic.List%601> and <xref:System.Collections.Generic.Dictionary%602>, which work without requiring any hints or directives.</span></span> <span data-ttu-id="28a5c-145">[Dynamiczne](../../csharp/language-reference/keywords/dynamic.md) słowo kluczowe jest również obsługiwane w ramach pewnych limitów.</span><span class="sxs-lookup"><span data-stu-id="28a5c-145">The [dynamic](../../csharp/language-reference/keywords/dynamic.md) keyword is also supported within certain limits.</span></span>

> [!NOTE]
> <span data-ttu-id="28a5c-146">Należy dokładnie przetestować wszystkie dynamiczne ścieżki kodu podczas przenoszenia aplikacji do .NET Native.</span><span class="sxs-lookup"><span data-stu-id="28a5c-146">You should test all dynamic code paths thoroughly when porting your app to .NET Native.</span></span>

<span data-ttu-id="28a5c-147">Domyślna konfiguracja .NET Native jest wystarczająca dla większości deweloperów, ale niektórzy deweloperzy mogą chcieć dostosować konfiguracje przy użyciu pliku dyrektywy środowiska uruchomieniowego (. Rd. xml).</span><span class="sxs-lookup"><span data-stu-id="28a5c-147">The default configuration for .NET Native is sufficient for most developers, but some developers might want to fine- tune their configurations by using a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="28a5c-148">Ponadto w niektórych przypadkach kompilator .NET Native nie jest w stanie określić, które metadane muszą być dostępne do odbicia, i opierają się na wskazówkach, szczególnie w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="28a5c-148">In addition, in some cases, the .NET Native compiler is unable to determine which metadata must be available for reflection and relies on hints, particularly in the following cases:</span></span>

- <span data-ttu-id="28a5c-149">Niektóre konstrukcje takie <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> jak <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> i nie mogą być określane statycznie.</span><span class="sxs-lookup"><span data-stu-id="28a5c-149">Some constructs like <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> and <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> can't be determined statically.</span></span>

- <span data-ttu-id="28a5c-150">Ponieważ kompilator nie może określić wystąpień, typ ogólny, który ma być uwzględniany, musi być określony przez dyrektywy środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="28a5c-150">Because the compiler can't determine the instantiations, a generic type that you want to reflect on has to be specified by runtime directives.</span></span> <span data-ttu-id="28a5c-151">To nie tylko dlatego, że cały kod musi być uwzględniony, ale odbicie na typach ogólnych może tworzyć nieskończony cykl (na przykład gdy metoda ogólna jest wywoływana w typie ogólnym).</span><span class="sxs-lookup"><span data-stu-id="28a5c-151">This isn't just because all code must be included, but because reflection on generic types can form an infinite cycle (for example, when a generic method is invoked on a generic type).</span></span>

> [!NOTE]
> <span data-ttu-id="28a5c-152">Dyrektywy środowiska uruchomieniowego są zdefiniowane w pliku dyrektywy środowiska uruchomieniowego (. Rd. xml).</span><span class="sxs-lookup"><span data-stu-id="28a5c-152">Runtime directives are defined in a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="28a5c-153">Aby uzyskać ogólne informacje na temat korzystania z tego pliku, zobacz [wprowadzenie](getting-started-with-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="28a5c-153">For general information about using this file, see [Getting Started](getting-started-with-net-native.md).</span></span> <span data-ttu-id="28a5c-154">Aby uzyskać informacje o dyrektywach środowiska uruchomieniowego, zobacz [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (RD. xml)](runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="28a5c-154">For information about the runtime directives, see [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span></span>

<span data-ttu-id="28a5c-155">.NET Native również zawiera narzędzia profilowania, które ułatwiają deweloperom określenie, które typy poza domyślnym zestawem powinny obsługiwać odbicie.</span><span class="sxs-lookup"><span data-stu-id="28a5c-155">.NET Native also includes profiling tools that help the developer determine which types outside the default set should support reflection.</span></span>

<a name="Reflection"></a>

## <a name="other-reflection-related-differences"></a><span data-ttu-id="28a5c-156">Inne różnice dotyczące odbicia</span><span class="sxs-lookup"><span data-stu-id="28a5c-156">Other reflection-related differences</span></span>

<span data-ttu-id="28a5c-157">Istnieje wiele innych różnic dotyczących zachowań między platformą .NET dla aplikacji do sklepu Windows i .NET Native.</span><span class="sxs-lookup"><span data-stu-id="28a5c-157">There are a number of other individual reflection-related differences in behavior between the .NET for Windows Store apps and .NET Native.</span></span>

<span data-ttu-id="28a5c-158">W .NET Native:</span><span class="sxs-lookup"><span data-stu-id="28a5c-158">In .NET Native:</span></span>

- <span data-ttu-id="28a5c-159">Prywatne odbicie typów i elementów członkowskich w bibliotece klas .NET Framework nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="28a5c-159">Private reflection over types and members in the .NET Framework class library is not supported.</span></span> <span data-ttu-id="28a5c-160">Można jednak odzwierciedlić własne typy prywatne i członków, a także typy i elementy członkowskie w bibliotekach innych firm.</span><span class="sxs-lookup"><span data-stu-id="28a5c-160">You can, however, reflect over your own private types and members, as well as types and members in third-party libraries.</span></span>

- <span data-ttu-id="28a5c-161">Właściwość prawidłowo zwraca `false` dla<xref:System.Reflection.ParameterInfo> obiektu, który reprezentuje wartość zwracaną. <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="28a5c-161">The <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> property correctly returns `false` for a <xref:System.Reflection.ParameterInfo> object that represents a return value.</span></span> <span data-ttu-id="28a5c-162">W programie .NET dla aplikacji ze sklepu Windows funkcja zwraca `true`wartość.</span><span class="sxs-lookup"><span data-stu-id="28a5c-162">In the .NET for Windows Store apps, it returns `true`.</span></span> <span data-ttu-id="28a5c-163">Język pośredni (IL) nie obsługuje tego bezpośrednio, a interpretacja pozostała do języka.</span><span class="sxs-lookup"><span data-stu-id="28a5c-163">Intermediate language (IL) doesn’t support this directly, and interpretation is left to the language.</span></span>

- <span data-ttu-id="28a5c-164">Publiczne składowe w <xref:System.RuntimeFieldHandle> strukturach i <xref:System.RuntimeMethodHandle> nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="28a5c-164">Public members on the <xref:System.RuntimeFieldHandle> and <xref:System.RuntimeMethodHandle> structures aren't supported.</span></span> <span data-ttu-id="28a5c-165">Te typy są obsługiwane tylko dla LINQ, drzew wyrażeń i inicjalizacji tablicy statycznej.</span><span class="sxs-lookup"><span data-stu-id="28a5c-165">These types are supported only for LINQ, expression trees, and static array initialization.</span></span>

- <span data-ttu-id="28a5c-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType>i <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> Uwzględnij ukryte składowe w klasach bazowych, więc mogą zostać zastąpione bez jawnych zastąpień.</span><span class="sxs-lookup"><span data-stu-id="28a5c-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> and <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> include hidden members in base classes and thus may be overridden without explicit overrides.</span></span> <span data-ttu-id="28a5c-167">Jest to również prawdziwe w przypadku innych metod [RuntimeReflectionExtensions. GetRuntime \*](xref:System.Reflection.RuntimeReflectionExtensions) .</span><span class="sxs-lookup"><span data-stu-id="28a5c-167">This is also true of other [RuntimeReflectionExtensions.GetRuntime\*](xref:System.Reflection.RuntimeReflectionExtensions) methods.</span></span>

- <span data-ttu-id="28a5c-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType>i <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> nie kończy się niepowodzeniem podczas próby utworzenia niektórych kombinacji (na przykład tablicy ByRef).</span><span class="sxs-lookup"><span data-stu-id="28a5c-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> don't fail when you try to create certain combinations (for example, an array of byrefs).</span></span>

- <span data-ttu-id="28a5c-169">Nie można używać odbicia do wywoływania elementów członkowskich, które mają parametry wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="28a5c-169">You can't use reflection to invoke members that have pointer parameters.</span></span>

- <span data-ttu-id="28a5c-170">Nie można użyć odbicia w celu pobrania lub ustawienia pola wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="28a5c-170">You can't use reflection to get or set a pointer field.</span></span>

- <span data-ttu-id="28a5c-171">Gdy liczba argumentów jest nieprawidłowa i typ jednego z argumentów jest niepoprawny, .NET Native zgłasza <xref:System.ArgumentException> zamiast elementu. <xref:System.Reflection.TargetParameterCountException></span><span class="sxs-lookup"><span data-stu-id="28a5c-171">When the argument count is wrong and the type of one of the arguments is incorrect, .NET Native throws an <xref:System.ArgumentException> instead of a <xref:System.Reflection.TargetParameterCountException>.</span></span>

- <span data-ttu-id="28a5c-172">Serializacja binarna wyjątków zazwyczaj nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="28a5c-172">Binary serialization of exceptions is generally not supported.</span></span> <span data-ttu-id="28a5c-173">W związku z tym <xref:System.Exception.Data%2A?displayProperty=nameWithType> obiekty, które nie są możliwe do serializacji, można dodać do słownika.</span><span class="sxs-lookup"><span data-stu-id="28a5c-173">As a result, non-serializable objects can be added to the <xref:System.Exception.Data%2A?displayProperty=nameWithType> dictionary.</span></span>

<a name="Unsupported"></a>

## <a name="unsupported-scenarios-and-apis"></a><span data-ttu-id="28a5c-174">Nieobsługiwane scenariusze i interfejsy API</span><span class="sxs-lookup"><span data-stu-id="28a5c-174">Unsupported scenarios and APIs</span></span>

<span data-ttu-id="28a5c-175">W poniższych sekcjach zamieszczono listę nieobsługiwanych scenariuszy i interfejsów API na potrzeby ogólnego programowania, międzyoperacyjności i technologii, takich jak HTTPClient i Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="28a5c-175">The following sections list unsupported scenarios and APIs for general development, interop, and technologies such as HTTPClient and Windows Communication Foundation (WCF):</span></span>

- [<span data-ttu-id="28a5c-176">Opracowywanie ogólne</span><span class="sxs-lookup"><span data-stu-id="28a5c-176">General development</span></span>](#General)

- [<span data-ttu-id="28a5c-177">HttpClient</span><span class="sxs-lookup"><span data-stu-id="28a5c-177">HttpClient</span></span>](#HttpClient)

- [<span data-ttu-id="28a5c-178">Interop</span><span class="sxs-lookup"><span data-stu-id="28a5c-178">Interop</span></span>](#Interop)

- [<span data-ttu-id="28a5c-179">Nieobsługiwane interfejsy API</span><span class="sxs-lookup"><span data-stu-id="28a5c-179">Unsupported APIs</span></span>](#APIs)

<a name="General"></a>

### <a name="general-development-differences"></a><span data-ttu-id="28a5c-180">Ogólne różnice w programowaniu</span><span class="sxs-lookup"><span data-stu-id="28a5c-180">General development differences</span></span>

<span data-ttu-id="28a5c-181">**Typy wartości**</span><span class="sxs-lookup"><span data-stu-id="28a5c-181">**Value types**</span></span>

- <span data-ttu-id="28a5c-182">W przypadku zastąpienia <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> metod i <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> dla typu wartości nie należy wywoływać implementacji klas podstawowych.</span><span class="sxs-lookup"><span data-stu-id="28a5c-182">If you override the <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> and <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> methods for a value type, don't call the base class implementations.</span></span> <span data-ttu-id="28a5c-183">W programie .NET dla aplikacji do sklepu Windows te metody polegają na odbiciu.</span><span class="sxs-lookup"><span data-stu-id="28a5c-183">In .NET for Windows Store apps, these methods rely on reflection.</span></span> <span data-ttu-id="28a5c-184">W czasie kompilacji .NET Native generuje implementację, która nie polega na odbiciu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="28a5c-184">At compile time, .NET Native generates an implementation that doesn't rely on runtime reflection.</span></span> <span data-ttu-id="28a5c-185">Oznacza to, że jeśli nie zastąpisz tych dwóch metod, będą one działały zgodnie z oczekiwaniami, ponieważ .NET Native generuje implementację w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="28a5c-185">This means that if you don't override these two methods, they will work as expected, because .NET Native generates the implementation at compile time.</span></span> <span data-ttu-id="28a5c-186">Jednak zastąpienie tych metod, ale wywołanie implementacji klasy bazowej powoduje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="28a5c-186">However, overriding these methods but calling the base class implementation results in an exception.</span></span>

- <span data-ttu-id="28a5c-187">Typy wartości większe niż jeden megabajt nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="28a5c-187">Value types larger than one megabyte aren't supported.</span></span>

- <span data-ttu-id="28a5c-188">Typy wartości nie mogą mieć konstruktora bez parametrów w .NET Native.</span><span class="sxs-lookup"><span data-stu-id="28a5c-188">Value types can't have a parameterless constructor in .NET Native.</span></span> <span data-ttu-id="28a5c-189">(C# i Visual Basic zabraniać konstruktorów bez parametrów w typach wartości.</span><span class="sxs-lookup"><span data-stu-id="28a5c-189">(C# and Visual Basic prohibit parameterless constructors on value types.</span></span> <span data-ttu-id="28a5c-190">Można je jednak utworzyć w języku IL.)</span><span class="sxs-lookup"><span data-stu-id="28a5c-190">However, these can be created in IL.)</span></span>

<span data-ttu-id="28a5c-191">**Tablice**</span><span class="sxs-lookup"><span data-stu-id="28a5c-191">**Arrays**</span></span>

- <span data-ttu-id="28a5c-192">Tablice z dolną granicą inną niż zero nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="28a5c-192">Arrays with a lower bound other than zero aren't supported.</span></span> <span data-ttu-id="28a5c-193">Zwykle te tablice są tworzone przez wywołanie <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="28a5c-193">Typically, these arrays are created by calling the <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> overload.</span></span>

- <span data-ttu-id="28a5c-194">Dynamiczne tworzenie tablic wielowymiarowych nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="28a5c-194">Dynamic creation of multidimensional arrays isn't supported.</span></span> <span data-ttu-id="28a5c-195">Takie tablice są zwykle tworzone przez wywołanie przeciążenia <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> metody zawierającej `lengths` parametr lub przez wywołanie <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="28a5c-195">Such arrays are typically created by calling an overload of the <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> method that includes a `lengths` parameter, or by calling the <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="28a5c-196">Tablice wielowymiarowe, które mają co najmniej cztery wymiary, nie są obsługiwane. oznacza to, że <xref:System.Array.Rank%2A?displayProperty=nameWithType> ich wartość właściwości jest równa co najmniej cztery.</span><span class="sxs-lookup"><span data-stu-id="28a5c-196">Multidimensional arrays that have four or more dimensions aren't supported; that is, their <xref:System.Array.Rank%2A?displayProperty=nameWithType> property value is four or greater.</span></span> <span data-ttu-id="28a5c-197">Zamiast tego używaj [tablic nieregularnych](../../csharp/programming-guide/arrays/jagged-arrays.md) (tablicowych tablic).</span><span class="sxs-lookup"><span data-stu-id="28a5c-197">Use [jagged arrays](../../csharp/programming-guide/arrays/jagged-arrays.md) (an array of arrays) instead.</span></span> <span data-ttu-id="28a5c-198">Na przykład `array[x,y,z]` jest nieprawidłowa, ale `array[x][y][z]` nie jest.</span><span class="sxs-lookup"><span data-stu-id="28a5c-198">For example, `array[x,y,z]` is invalid, but `array[x][y][z]` isn't.</span></span>

- <span data-ttu-id="28a5c-199">WARIANCJA dla tablic wielowymiarowych nie jest obsługiwana i <xref:System.InvalidCastException> powoduje wyjątek w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="28a5c-199">Variance for multidimensional arrays isn't supported and causes an <xref:System.InvalidCastException> exception at run time.</span></span>

<span data-ttu-id="28a5c-200">**Typy ogólne**</span><span class="sxs-lookup"><span data-stu-id="28a5c-200">**Generics**</span></span>

- <span data-ttu-id="28a5c-201">Nieskończone rozwijanie typów ogólnych powoduje błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="28a5c-201">Infinite generic type expansion results in a compiler error.</span></span> <span data-ttu-id="28a5c-202">Na przykład następujący kod nie zostanie skompilowany:</span><span class="sxs-lookup"><span data-stu-id="28a5c-202">For example, this code fails to compile:</span></span>

  [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]

<span data-ttu-id="28a5c-203">**Wskaźniki**</span><span class="sxs-lookup"><span data-stu-id="28a5c-203">**Pointers**</span></span>

- <span data-ttu-id="28a5c-204">Tablice wskaźników nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="28a5c-204">Arrays of pointers aren't supported.</span></span>

- <span data-ttu-id="28a5c-205">Nie można użyć odbicia w celu pobrania lub ustawienia pola wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="28a5c-205">You can't use reflection to get or set a pointer field.</span></span>

<span data-ttu-id="28a5c-206">**Serializacja**</span><span class="sxs-lookup"><span data-stu-id="28a5c-206">**Serialization**</span></span>

<span data-ttu-id="28a5c-207">Ten <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> atrybut nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="28a5c-207">The <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> attribute isn't supported.</span></span> <span data-ttu-id="28a5c-208">Zamiast tego użyj atrybutu. <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29></span><span class="sxs-lookup"><span data-stu-id="28a5c-208">Use the <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> attribute instead.</span></span>

<span data-ttu-id="28a5c-209">**Zasoby**</span><span class="sxs-lookup"><span data-stu-id="28a5c-209">**Resources**</span></span>

<span data-ttu-id="28a5c-210">Użycie zlokalizowanych zasobów z <xref:System.Diagnostics.Tracing.EventSource> klasą nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="28a5c-210">The use of localized resources with the <xref:System.Diagnostics.Tracing.EventSource> class isn't supported.</span></span> <span data-ttu-id="28a5c-211"><xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> Właściwość nie definiuje zlokalizowanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="28a5c-211">The <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> property doesn't define localized resources.</span></span>

<span data-ttu-id="28a5c-212">**Delegaty**</span><span class="sxs-lookup"><span data-stu-id="28a5c-212">**Delegates**</span></span>

<span data-ttu-id="28a5c-213">`Delegate.BeginInvoke`i `Delegate.EndInvoke` nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="28a5c-213">`Delegate.BeginInvoke` and `Delegate.EndInvoke` aren't supported.</span></span>

<span data-ttu-id="28a5c-214">**Różne interfejsy API**</span><span class="sxs-lookup"><span data-stu-id="28a5c-214">**Miscellaneous APIs**</span></span>

- <span data-ttu-id="28a5c-215">Właściwośćname [. GUID](xref:System.Type.GUID) zgłasza wyjątek, <xref:System.PlatformNotSupportedException> Jeśli <xref:System.Runtime.InteropServices.GuidAttribute> atrybut nie jest stosowany do typu.</span><span class="sxs-lookup"><span data-stu-id="28a5c-215">The [TypeInfo.GUID](xref:System.Type.GUID) property throws a <xref:System.PlatformNotSupportedException> exception if a <xref:System.Runtime.InteropServices.GuidAttribute> attribute isn't applied to the type.</span></span> <span data-ttu-id="28a5c-216">Identyfikator GUID jest używany głównie do obsługi modelu COM.</span><span class="sxs-lookup"><span data-stu-id="28a5c-216">The GUID is used primarily for COM support.</span></span>

- <span data-ttu-id="28a5c-217"><xref:System.DateTime.Parse%2A?displayProperty=nameWithType> Metoda prawidłowo analizuje ciągi zawierające daty krótkie w .NET Native.</span><span class="sxs-lookup"><span data-stu-id="28a5c-217">The <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> method correctly parses strings that contain short dates in .NET Native.</span></span> <span data-ttu-id="28a5c-218">Jednak nie zachowuje zgodności z zmianami dotyczącymi analizy daty i godziny opisanej w artykułach bazy wiedzy Microsoft [KB2803771](https://support.microsoft.com/kb/2803771) i [KB2803755](https://support.microsoft.com/kb/2803755).</span><span class="sxs-lookup"><span data-stu-id="28a5c-218">However, it doesn't maintain compatibility with the changes in date and time parsing described in the Microsoft Knowledge Base articles [KB2803771](https://support.microsoft.com/kb/2803771) and [KB2803755](https://support.microsoft.com/kb/2803755).</span></span>

- <span data-ttu-id="28a5c-219"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType>`("E")` jest poprawnie zaokrąglona w .NET Native.</span><span class="sxs-lookup"><span data-stu-id="28a5c-219"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` is correctly rounded in .NET Native.</span></span> <span data-ttu-id="28a5c-220">W niektórych wersjach środowiska CLR ciąg wynikowy jest obcinany zamiast zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="28a5c-220">In some versions of the CLR, the result string is truncated instead of rounded.</span></span>

<a name="HttpClient"></a>

### <a name="httpclient-differences"></a><span data-ttu-id="28a5c-221">Różnice HttpClient</span><span class="sxs-lookup"><span data-stu-id="28a5c-221">HttpClient differences</span></span>

<span data-ttu-id="28a5c-222">W .NET Native <xref:System.Net.Http.HttpClientHandler> Klasa wewnętrznie używa interfejsu WinINet ( <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> za pośrednictwem <xref:System.Net.WebRequest> klasy) zamiast klas i <xref:System.Net.WebResponse> używanych w standardowym środowisku .NET dla aplikacji do sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="28a5c-222">In .NET Native, the <xref:System.Net.Http.HttpClientHandler> class internally uses WinINet (through the <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class) instead of the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes used in the standard .NET for Windows Store apps.</span></span>  <span data-ttu-id="28a5c-223">Usługa WinInet nie obsługuje wszystkich opcji <xref:System.Net.Http.HttpClientHandler> konfiguracji obsługiwanych przez klasę.</span><span class="sxs-lookup"><span data-stu-id="28a5c-223">WinINet doesn't support all the configuration options that the <xref:System.Net.Http.HttpClientHandler> class supports.</span></span>  <span data-ttu-id="28a5c-224">W efekcie:</span><span class="sxs-lookup"><span data-stu-id="28a5c-224">As a result:</span></span>

- <span data-ttu-id="28a5c-225">Niektóre właściwości możliwości w <xref:System.Net.Http.HttpClientHandler> przypadku powrotu `false` do .NET Native, które zwracają `true` w standardowej technologii .NET dla aplikacji ze sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="28a5c-225">Some of the capability properties on <xref:System.Net.Http.HttpClientHandler> return `false` on .NET Native, whereas they return `true` in the standard .NET for Windows Store apps.</span></span>

- <span data-ttu-id="28a5c-226">Niektóre metody dostępu do właściwości `get` konfiguracji zawsze zwracają stałą wartość .NET Native, która różni się od domyślnej konfigurowalnej wartości w programie .NET dla aplikacji ze sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="28a5c-226">Some of the configuration property `get` accessors always return a fixed value on .NET Native that is different than the default configurable value in .NET for Windows Store apps.</span></span>

<span data-ttu-id="28a5c-227">Niektóre dodatkowe różnice w zachowaniu zostały omówione w poniższych podsekcjach.</span><span class="sxs-lookup"><span data-stu-id="28a5c-227">Some additional behavior differences are covered in the following subsections.</span></span>

<span data-ttu-id="28a5c-228">**Proxy**</span><span class="sxs-lookup"><span data-stu-id="28a5c-228">**Proxy**</span></span>

<span data-ttu-id="28a5c-229"><xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> Klasa nie obsługuje konfigurowania lub zastępowania serwera proxy dla poszczególnych żądań.</span><span class="sxs-lookup"><span data-stu-id="28a5c-229">The <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class doesn’t support configuring or overriding the proxy on a per-request basis.</span></span>  <span data-ttu-id="28a5c-230">Oznacza to, że wszystkie żądania dotyczące .NET Native korzystają z serwera proxy skonfigurowany systemowo lub bez serwera proxy, w zależności od wartości <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="28a5c-230">This means that all requests on .NET Native use the system-configured proxy server or no proxy server, depending on the value of the <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="28a5c-231">W programie .NET dla aplikacji do sklepu Windows serwer proxy jest zdefiniowany przez <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> właściwość.</span><span class="sxs-lookup"><span data-stu-id="28a5c-231">In .NET for Windows Store apps, the proxy server is defined by the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="28a5c-232">Na .NET Native ustawienie <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> wartości innej niż `null` zgłasza <xref:System.PlatformNotSupportedException> wyjątek.</span><span class="sxs-lookup"><span data-stu-id="28a5c-232">On .NET Native, setting the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> to a value other than `null` throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="28a5c-233">Właściwość zwraca wartość `false` w .NET Native, podczas gdy zwraca `true` w standardowym .NET Framework dla aplikacji ze sklepu Windows. <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="28a5c-233">The <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> property returns `false` on .NET Native, whereas it returns `true` in the standard .NET Framework for Windows Store apps.</span></span>

<span data-ttu-id="28a5c-234">**Automatyczne przekierowanie**</span><span class="sxs-lookup"><span data-stu-id="28a5c-234">**Automatic redirection**</span></span>

<span data-ttu-id="28a5c-235"><xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> Klasa nie zezwala na skonfigurowanie maksymalnej liczby przekierowań automatycznych.</span><span class="sxs-lookup"><span data-stu-id="28a5c-235">The <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class doesn't allow the maximum number of automatic redirections to be configured.</span></span>  <span data-ttu-id="28a5c-236">Wartość <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> właściwości jest 50 domyślnie w standardowym środowisku .NET dla aplikacji ze sklepu Windows i można ją modyfikować.</span><span class="sxs-lookup"><span data-stu-id="28a5c-236">The value of the <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> property is 50 by default in the standard .NET for Windows Store apps and can be modified.</span></span> <span data-ttu-id="28a5c-237">Na .NET Native wartość tej właściwości wynosi 10 i próba zmodyfikowania <xref:System.PlatformNotSupportedException> spowoduje zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="28a5c-237">On .NET Native, the value of this property is 10, and trying to modify it throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="28a5c-238">Właściwość zwraca wartość `false` w .NET Native, podczas gdy zwraca `true` w programie .NET dla aplikacji ze sklepu Windows. <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="28a5c-238">The <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> property returns `false` on .NET Native, whereas it returns `true` in .NET for Windows Store apps.</span></span>

<span data-ttu-id="28a5c-239">**Automatyczna dekompresja**</span><span class="sxs-lookup"><span data-stu-id="28a5c-239">**Automatic decompression**</span></span>

<span data-ttu-id="28a5c-240">Platforma .NET dla aplikacji do <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> sklepu Windows umożliwia ustawienie właściwości na <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, zarówno <xref:System.Net.DecompressionMethods.Deflate> , jak <xref:System.Net.DecompressionMethods.GZip>i. <xref:System.Net.DecompressionMethods.None></span><span class="sxs-lookup"><span data-stu-id="28a5c-240">.NET for Windows Store apps allows you to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> property to <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="28a5c-241">.NET Native obsługuje <xref:System.Net.DecompressionMethods.Deflate> tylko razem z <xref:System.Net.DecompressionMethods.GZip>, lub <xref:System.Net.DecompressionMethods.None>.</span><span class="sxs-lookup"><span data-stu-id="28a5c-241">.NET Native only supports <xref:System.Net.DecompressionMethods.Deflate> together with <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="28a5c-242">Podjęto próbę <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> ustawienia właściwości <xref:System.Net.DecompressionMethods.Deflate> w trybie <xref:System.Net.DecompressionMethods.GZip> dyskretnym lub autonomicznie ustawia ją <xref:System.Net.DecompressionMethods.Deflate> jednocześnie <xref:System.Net.DecompressionMethods.GZip>na i.</span><span class="sxs-lookup"><span data-stu-id="28a5c-242">Trying to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> property to either <xref:System.Net.DecompressionMethods.Deflate> or <xref:System.Net.DecompressionMethods.GZip> alone silently sets it to both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>.</span></span>

<span data-ttu-id="28a5c-243">**Plik cookie**</span><span class="sxs-lookup"><span data-stu-id="28a5c-243">**Cookies**</span></span>

<span data-ttu-id="28a5c-244">Obsługa plików cookie jest wykonywana jednocześnie <xref:System.Net.Http.HttpClient> przez program i WinInet.</span><span class="sxs-lookup"><span data-stu-id="28a5c-244">Cookie handling is performed simultaneously by <xref:System.Net.Http.HttpClient> and WinINet.</span></span>  <span data-ttu-id="28a5c-245">Pliki cookie z <xref:System.Net.CookieContainer> programu są łączone z plikami cookie w pamięci podręcznej plików cookie WinInet.</span><span class="sxs-lookup"><span data-stu-id="28a5c-245">Cookies from the <xref:System.Net.CookieContainer> are combined with cookies in the WinINet cookie cache.</span></span>  <span data-ttu-id="28a5c-246">Usunięcie pliku cookie z <xref:System.Net.CookieContainer> uniemożliwia <xref:System.Net.Http.HttpClient> wysyłanie plików cookie, ale jeśli plik cookie był już widziany przez program WinInet, a pliki cookie nie zostały usunięte przez użytkownika, program WinInet wysyła go.</span><span class="sxs-lookup"><span data-stu-id="28a5c-246">Removing a cookie from <xref:System.Net.CookieContainer> prevents <xref:System.Net.Http.HttpClient> from sending the cookie, but if the cookie was already seen by WinINet, and cookies weren't deleted by the user, WinINet sends it.</span></span>  <span data-ttu-id="28a5c-247">Nie można programowo usunąć pliku cookie z usługi WinInet przy użyciu <xref:System.Net.Http.HttpClient>interfejsu API, <xref:System.Net.Http.HttpClientHandler>lub. <xref:System.Net.CookieContainer></span><span class="sxs-lookup"><span data-stu-id="28a5c-247">It isn't possible to programmatically remove a cookie from WinINet by using the <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>, or <xref:System.Net.CookieContainer> API.</span></span>  <span data-ttu-id="28a5c-248">Ustawienie właściwości na `false` przyczyny powoduje <xref:System.Net.Http.HttpClient> zatrzymanie wysyłania plików cookie; <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> Usługa WinINet może nadal zawierać swoje pliki cookie w żądaniu.</span><span class="sxs-lookup"><span data-stu-id="28a5c-248">Setting the <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> property to `false` causes only <xref:System.Net.Http.HttpClient> to stop sending cookies; WinINet might still include its cookies in the request.</span></span>

<span data-ttu-id="28a5c-249">**Uwierzytelniające**</span><span class="sxs-lookup"><span data-stu-id="28a5c-249">**Credentials**</span></span>

<span data-ttu-id="28a5c-250">W programie .NET dla aplikacji ze <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> sklepu Windows właściwości i <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> działają niezależnie.</span><span class="sxs-lookup"><span data-stu-id="28a5c-250">In .NET for Windows Store apps, the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> properties work independently.</span></span>  <span data-ttu-id="28a5c-251">Ponadto Właściwość akceptuje każdy obiekt, który <xref:System.Net.ICredentials> implementuje interfejs. <xref:System.Net.Http.HttpClientHandler.Credentials%2A></span><span class="sxs-lookup"><span data-stu-id="28a5c-251">Additionally, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property accepts any object that implements the <xref:System.Net.ICredentials> interface.</span></span>  <span data-ttu-id="28a5c-252">W <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> .NET Native ustawienie `true` właściwości powoduje,<xref:System.Net.Http.HttpClientHandler.Credentials%2A> że właściwość zostanie ustawiona. `null`</span><span class="sxs-lookup"><span data-stu-id="28a5c-252">In .NET Native, setting the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> property to `true` causes the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property to become `null`.</span></span>  <span data-ttu-id="28a5c-253">Ponadto <xref:System.Net.Http.HttpClientHandler.Credentials%2A> Właściwość można ustawić tylko dla `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>lub obiekt typu <xref:System.Net.NetworkCredential>.</span><span class="sxs-lookup"><span data-stu-id="28a5c-253">In addition, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property can be set only to `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>, or an object of type <xref:System.Net.NetworkCredential>.</span></span>  <span data-ttu-id="28a5c-254">Przypisując <xref:System.Net.ICredentials> każdy inny obiekt, najpopularniejszy jest <xref:System.Net.CredentialCache>, <xref:System.PlatformNotSupportedException>do <xref:System.Net.Http.HttpClientHandler.Credentials%2A> właściwości zgłasza.</span><span class="sxs-lookup"><span data-stu-id="28a5c-254">Assigning any other <xref:System.Net.ICredentials> object, the most popular of which is <xref:System.Net.CredentialCache>, to the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property throws a <xref:System.PlatformNotSupportedException>.</span></span>

<span data-ttu-id="28a5c-255">**Inne nieobsługiwane lub niekonfigurowalne funkcje**</span><span class="sxs-lookup"><span data-stu-id="28a5c-255">**Other unsupported or unconfigurable features**</span></span>

<span data-ttu-id="28a5c-256">W .NET Native:</span><span class="sxs-lookup"><span data-stu-id="28a5c-256">In .NET Native:</span></span>

- <span data-ttu-id="28a5c-257">Wartość <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> właściwości jest zawsze <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span><span class="sxs-lookup"><span data-stu-id="28a5c-257">The value of the <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> property is always <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span></span>  <span data-ttu-id="28a5c-258">W programie .NET dla aplikacji do sklepu Windows wartość domyślna <xref:System.Net.Http.ClientCertificateOption.Manual>to.</span><span class="sxs-lookup"><span data-stu-id="28a5c-258">In .NET for Windows Store apps, the default is <xref:System.Net.Http.ClientCertificateOption.Manual>.</span></span>

- <span data-ttu-id="28a5c-259">Nie można skonfigurować właściwości. <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="28a5c-259">The <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> property isn't configurable.</span></span>

- <span data-ttu-id="28a5c-260">Właściwość jest zawsze `true`. <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="28a5c-260">The <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> property is always `true`.</span></span>  <span data-ttu-id="28a5c-261">W programie .NET dla aplikacji do sklepu Windows wartość domyślna `false`to.</span><span class="sxs-lookup"><span data-stu-id="28a5c-261">In .NET for Windows Store apps, the default is `false`.</span></span>

- <span data-ttu-id="28a5c-262">`SetCookie2` Nagłówek w odpowiedzi jest ignorowany jako przestarzały.</span><span class="sxs-lookup"><span data-stu-id="28a5c-262">The `SetCookie2` header in responses is ignored as obsolete.</span></span>

<a name="Interop"></a>
### <a name="interop-differences"></a><span data-ttu-id="28a5c-263">Różnice międzyoperacyjnych</span><span class="sxs-lookup"><span data-stu-id="28a5c-263">Interop differences</span></span>
 <span data-ttu-id="28a5c-264">**Przestarzałe interfejsy API**</span><span class="sxs-lookup"><span data-stu-id="28a5c-264">**Deprecated APIs**</span></span>

 <span data-ttu-id="28a5c-265">Wiele rzadko używanych interfejsów API do współdziałania z kodem zarządzanym jest przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="28a5c-265">A number of infrequently used APIs for interoperability with managed code have been deprecated.</span></span> <span data-ttu-id="28a5c-266">W przypadku użycia z .NET Native te interfejsy API mogą zgłosić <xref:System.NotImplementedException> wyjątek <xref:System.PlatformNotSupportedException> lub lub spowodować błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="28a5c-266">When used with .NET Native, these APIs may throw a <xref:System.NotImplementedException> or <xref:System.PlatformNotSupportedException> exception, or result in a compiler error.</span></span> <span data-ttu-id="28a5c-267">W programie .NET dla aplikacji ze sklepu Windows te interfejsy API są oznaczane jako przestarzałe, chociaż wywołanie ich powoduje wygenerowanie ostrzeżenia kompilatora, a nie błędu kompilatora.</span><span class="sxs-lookup"><span data-stu-id="28a5c-267">In .NET for Windows Store apps, these APIs are marked as obsolete, although calling them generates a compiler warning rather than a compiler error.</span></span>

 <span data-ttu-id="28a5c-268">Przestarzałe interfejsy API `VARIANT` do organizowania obejmują:</span><span class="sxs-lookup"><span data-stu-id="28a5c-268">Deprecated APIs for `VARIANT` marshaling include:</span></span>

- <xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VarEnum?displayProperty=nameWithType>

 <span data-ttu-id="28a5c-269"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType>jest obsługiwane, ale zgłasza wyjątek w niektórych scenariuszach, na przykład gdy jest używany z wariantami [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) lub ByRef.</span><span class="sxs-lookup"><span data-stu-id="28a5c-269"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> is supported, but it throws an exception in some scenarios, such as when it is used with [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) or byref variants.</span></span>

 <span data-ttu-id="28a5c-270">Przestarzałe interfejsy API obsługi [interfejsu IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) obejmują:</span><span class="sxs-lookup"><span data-stu-id="28a5c-270">Deprecated APIs for [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) support include:</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>

<span data-ttu-id="28a5c-271">Przestarzałe interfejsy API dla klasycznych zdarzeń COM obejmują:</span><span class="sxs-lookup"><span data-stu-id="28a5c-271">Deprecated APIs for classic COM events include:</span></span>

- <xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>

<span data-ttu-id="28a5c-272">Przestarzałe interfejsy API w <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interfejsie, które nie są obsługiwane w .NET Native, obejmują:</span><span class="sxs-lookup"><span data-stu-id="28a5c-272">Deprecated APIs in the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface, which isn't supported in .NET Native, include:</span></span>

- <span data-ttu-id="28a5c-273"><xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType>(wszystkie elementy członkowskie)</span><span class="sxs-lookup"><span data-stu-id="28a5c-273"><xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> (all members)</span></span>
- <span data-ttu-id="28a5c-274"><xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType>(wszystkie elementy członkowskie)</span><span class="sxs-lookup"><span data-stu-id="28a5c-274"><xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType> (all members)</span></span>
- <span data-ttu-id="28a5c-275"><xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType>(wszystkie elementy członkowskie)</span><span class="sxs-lookup"><span data-stu-id="28a5c-275"><xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType> (all members)</span></span>
- <xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=fullName>

<span data-ttu-id="28a5c-276">Inne Nieobsługiwane funkcje międzyoperacyjności obejmują:</span><span class="sxs-lookup"><span data-stu-id="28a5c-276">Other unsupported interop features include:</span></span>

- <span data-ttu-id="28a5c-277"><xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType>(wszystkie elementy członkowskie)</span><span class="sxs-lookup"><span data-stu-id="28a5c-277"><xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType> (all members)</span></span>
- <span data-ttu-id="28a5c-278"><xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType>(wszystkie elementy członkowskie)</span><span class="sxs-lookup"><span data-stu-id="28a5c-278"><xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType> (all members)</span></span>
- <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AsAny?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler?displayProperty=fullName>

 <span data-ttu-id="28a5c-279">Rzadko używane kierowanie interfejsów API:</span><span class="sxs-lookup"><span data-stu-id="28a5c-279">Rarely used marshaling APIs:</span></span>

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

 <span data-ttu-id="28a5c-280">**Wywołanie platformy i zgodność z modelem COM**</span><span class="sxs-lookup"><span data-stu-id="28a5c-280">**Platform invoke and COM interop compatibility**</span></span>

 <span data-ttu-id="28a5c-281">Większość scenariuszy wywołania i międzyoperacyjności platformy COM jest nadal obsługiwana w .NET Native.</span><span class="sxs-lookup"><span data-stu-id="28a5c-281">Most platform invoke and COM interop scenarios are still supported in .NET Native.</span></span> <span data-ttu-id="28a5c-282">W szczególności obsługiwane są wszystkie współdziałanie z interfejsami API środowisko wykonawcze systemu Windows (WinRT) i wszystkie elementy Marshaling wymagane dla środowisko wykonawcze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="28a5c-282">In particular, all interoperability with Windows Runtime (WinRT) APIs and all marshaling required for the Windows Runtime is supported.</span></span> <span data-ttu-id="28a5c-283">Obejmuje to kierowanie wsparcie dla:</span><span class="sxs-lookup"><span data-stu-id="28a5c-283">This includes marshaling support for:</span></span>

- <span data-ttu-id="28a5c-284">Tablice (w <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>tym)</span><span class="sxs-lookup"><span data-stu-id="28a5c-284">Arrays (including <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span></span>

- `BStr`

- <span data-ttu-id="28a5c-285">Delegaty</span><span class="sxs-lookup"><span data-stu-id="28a5c-285">Delegates</span></span>

- <span data-ttu-id="28a5c-286">Ciągi (Unicode, ANSI i HSTRING)</span><span class="sxs-lookup"><span data-stu-id="28a5c-286">Strings (Unicode, Ansi, and HSTRING)</span></span>

- <span data-ttu-id="28a5c-287">Struktury (`byref` i `byval`)</span><span class="sxs-lookup"><span data-stu-id="28a5c-287">Structs (`byref` and `byval`)</span></span>

- <span data-ttu-id="28a5c-288">Unie</span><span class="sxs-lookup"><span data-stu-id="28a5c-288">Unions</span></span>

- <span data-ttu-id="28a5c-289">Uchwyty Win32</span><span class="sxs-lookup"><span data-stu-id="28a5c-289">Win32 handles</span></span>

- <span data-ttu-id="28a5c-290">Wszystkie konstrukcje WinRT</span><span class="sxs-lookup"><span data-stu-id="28a5c-290">All WinRT constructs</span></span>

- <span data-ttu-id="28a5c-291">Częściowa obsługa organizowania typów wariantów.</span><span class="sxs-lookup"><span data-stu-id="28a5c-291">Partial support for marshaling variant types.</span></span> <span data-ttu-id="28a5c-292">Obsługiwane są następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="28a5c-292">The following are supported:</span></span>

  - <xref:System.Boolean>

  - <xref:System.Byte>

  - <xref:System.Decimal>

  - <xref:System.Double>

  - <xref:System.Int16>

  - <xref:System.Int32>

  - <xref:System.Int64>

  - <xref:System.SByte>

  - <xref:System.Single>

  - <xref:System.UInt16>

  - <xref:System.UInt32>

  - <xref:System.UInt64>

  - `BStr`

  - [<span data-ttu-id="28a5c-293">IUnknown</span><span class="sxs-lookup"><span data-stu-id="28a5c-293">IUnknown</span></span>](/windows/desktop/api/unknwn/nn-unknwn-iunknown)

<span data-ttu-id="28a5c-294">Jednak .NET Native nie obsługuje następujących funkcji:</span><span class="sxs-lookup"><span data-stu-id="28a5c-294">However, .NET Native doesn't support the following:</span></span>

- <span data-ttu-id="28a5c-295">Używanie klasycznych zdarzeń COM</span><span class="sxs-lookup"><span data-stu-id="28a5c-295">Using classic COM events</span></span>

- <span data-ttu-id="28a5c-296">Implementowanie <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interfejsu w typie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="28a5c-296">Implementing the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface on a managed type</span></span>

- <span data-ttu-id="28a5c-297">Implementowanie interfejsu [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) w typie zarządzanym za pomocą <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="28a5c-297">Implementing the [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) interface on a managed type through the <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> attribute.</span></span> <span data-ttu-id="28a5c-298">Należy jednak pamiętać, że nie można wywoływać obiektów `IDispatch`com za poorednictwem, a obiekt zarządzany `IDispatch`nie może implementować.</span><span class="sxs-lookup"><span data-stu-id="28a5c-298">However, note that you can't call COM objects through `IDispatch`, and your managed object can't implement `IDispatch`.</span></span>

<span data-ttu-id="28a5c-299">Używanie odbicia do wywołania metody Invoke platformy nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="28a5c-299">Using reflection to invoke a platform invoke method isn't supported.</span></span> <span data-ttu-id="28a5c-300">To ograniczenie można obejść przez zapakowanie wywołania metody w innej metodzie i użycie odbicia w celu wywołania otoki.</span><span class="sxs-lookup"><span data-stu-id="28a5c-300">You can work around this limitation by wrapping the method call in another method and using reflection to call the wrapper instead.</span></span>

<a name="APIs"></a>

### <a name="other-differences-from-net-apis-for-windows-store-apps"></a><span data-ttu-id="28a5c-301">Inne różnice dotyczące interfejsów API platformy .NET dla aplikacji ze sklepu Windows</span><span class="sxs-lookup"><span data-stu-id="28a5c-301">Other differences from .NET APIs for Windows Store apps</span></span>

<span data-ttu-id="28a5c-302">Ta sekcja zawiera listę pozostałych interfejsów API, które nie są obsługiwane w programie .NET Native.</span><span class="sxs-lookup"><span data-stu-id="28a5c-302">This section lists the remaining APIs that aren't supported in .NET Native.</span></span> <span data-ttu-id="28a5c-303">Największym zestawem nieobsługiwanych interfejsów API są Windows Communication Foundation (WCF) interfejsy API.</span><span class="sxs-lookup"><span data-stu-id="28a5c-303">The largest set of the unsupported APIs are Windows Communication Foundation (WCF) APIs.</span></span>

<span data-ttu-id="28a5c-304">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span><span class="sxs-lookup"><span data-stu-id="28a5c-304">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span></span>

<span data-ttu-id="28a5c-305">Typy w <xref:System.ComponentModel.DataAnnotations> przestrzeniach nazw <xref:System.ComponentModel.DataAnnotations.Schema> i nie są obsługiwane w .NET Native.</span><span class="sxs-lookup"><span data-stu-id="28a5c-305">The types in the <xref:System.ComponentModel.DataAnnotations> and <xref:System.ComponentModel.DataAnnotations.Schema> namespaces aren't supported in .NET Native.</span></span> <span data-ttu-id="28a5c-306">Należą do nich następujące typy, które są obecne w programie .NET dla aplikacji ze sklepu Windows dla systemu Windows 8:</span><span class="sxs-lookup"><span data-stu-id="28a5c-306">These include the following types that are present in .NET for Windows Store apps for Windows 8:</span></span>

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

 <span data-ttu-id="28a5c-307">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="28a5c-307">**Visual Basic**</span></span>

<span data-ttu-id="28a5c-308">Visual Basic nie jest obecnie obsługiwana w .NET Native.</span><span class="sxs-lookup"><span data-stu-id="28a5c-308">Visual Basic isn't currently supported in .NET Native.</span></span> <span data-ttu-id="28a5c-309">Następujące typy w <xref:Microsoft.VisualBasic> przestrzeniach nazw <xref:Microsoft.VisualBasic.CompilerServices> i nie są dostępne w .NET Native:</span><span class="sxs-lookup"><span data-stu-id="28a5c-309">The following types in the <xref:Microsoft.VisualBasic> and <xref:Microsoft.VisualBasic.CompilerServices> namespaces aren't available in .NET Native:</span></span>

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

<span data-ttu-id="28a5c-310">**Kontekst odbicia (przestrzeń nazw System. odbicie. Context)**</span><span class="sxs-lookup"><span data-stu-id="28a5c-310">**Reflection Context (System.Reflection.Context namespace)**</span></span>

<span data-ttu-id="28a5c-311"><xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> Klasa nie jest obsługiwana w .NET Native.</span><span class="sxs-lookup"><span data-stu-id="28a5c-311">The <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> class isn't supported in .NET Native.</span></span>

<span data-ttu-id="28a5c-312">**RTC (System.Net.Http.Rtc)**</span><span class="sxs-lookup"><span data-stu-id="28a5c-312">**RTC (System.Net.Http.Rtc)**</span></span>

<span data-ttu-id="28a5c-313">`System.Net.Http.RtcRequestFactory` Klasa nie jest obsługiwana w .NET Native.</span><span class="sxs-lookup"><span data-stu-id="28a5c-313">The `System.Net.Http.RtcRequestFactory` class isn't supported in .NET Native.</span></span>

<span data-ttu-id="28a5c-314">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span><span class="sxs-lookup"><span data-stu-id="28a5c-314">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span></span>

<span data-ttu-id="28a5c-315">Typy w przestrzeniach [nazw System. ServiceModel. \*](xref:System.ServiceModel) nie są obsługiwane w .NET Native.</span><span class="sxs-lookup"><span data-stu-id="28a5c-315">The types in the [System.ServiceModel.\* namespaces](xref:System.ServiceModel) aren't supported in .NET Native.</span></span> <span data-ttu-id="28a5c-316">Należą do nich następujące typy:</span><span class="sxs-lookup"><span data-stu-id="28a5c-316">These includes the following types:</span></span>

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

### <a name="differences-in-serializers"></a><span data-ttu-id="28a5c-317">Różnice w serializatorach</span><span class="sxs-lookup"><span data-stu-id="28a5c-317">Differences in serializers</span></span>

<span data-ttu-id="28a5c-318">Poniższe różnice dotyczą serializacji i deserializacji z <xref:System.Runtime.Serialization.DataContractSerializer>klasami, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>i: <xref:System.Xml.Serialization.XmlSerializer></span><span class="sxs-lookup"><span data-stu-id="28a5c-318">The following differences concern serialization and deserialization with the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes:</span></span>

- <span data-ttu-id="28a5c-319">W .NET Native <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nie można serializować lub deserializować klasy pochodnej, która ma składową klasy bazowej, której typ nie jest typem serializacji głównej.</span><span class="sxs-lookup"><span data-stu-id="28a5c-319">In .NET Native, <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize or deserialize a derived class that has a base class member whose type isn't a root serialization type.</span></span> <span data-ttu-id="28a5c-320">Na przykład w poniższym kodzie próba serializacji lub deserializacji `Y` powoduje błąd:</span><span class="sxs-lookup"><span data-stu-id="28a5c-320">For example, in the following code, trying to serialize or deserialize `Y` results in an error:</span></span>

  [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]

  <span data-ttu-id="28a5c-321">Typ `InnerType` nie jest znany jako Serializator, ponieważ elementy członkowskie klasy bazowej nie są przenoszone podczas serializacji.</span><span class="sxs-lookup"><span data-stu-id="28a5c-321">Type `InnerType` isn't known to the serializer, because the members of the base class aren't traversed during serialization.</span></span>

- <span data-ttu-id="28a5c-322"><xref:System.Runtime.Serialization.DataContractSerializer>i <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nie można serializować klasy lub struktury <xref:System.Collections.Generic.IEnumerable%601> implementującej interfejs.</span><span class="sxs-lookup"><span data-stu-id="28a5c-322"><xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize a class or structure that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="28a5c-323">Na przykład następujące typy nie mogą serializować lub deserializować:</span><span class="sxs-lookup"><span data-stu-id="28a5c-323">For example, the following types fail to serialize or deserialize:</span></span>

- <span data-ttu-id="28a5c-324"><xref:System.Xml.Serialization.XmlSerializer>Serializacja następującej wartości obiektu nie powiodła się, ponieważ nie jest ona poznania dokładnego typu obiektu do serializacji:</span><span class="sxs-lookup"><span data-stu-id="28a5c-324"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize the following object value, because it doesn't know the exact type of the object to be serialized:</span></span>

- <span data-ttu-id="28a5c-325"><xref:System.Xml.Serialization.XmlSerializer>nie można serializować lub deserializować, jeśli typ serializowanego obiektu to <xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="28a5c-325"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize or deserialize if the type of the serialized object is <xref:System.Xml.XmlQualifiedName>.</span></span>

- <span data-ttu-id="28a5c-326">Wszystkie serializatory (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>i <xref:System.Xml.Serialization.XmlSerializer>) nie generują kodu serializacji dla typu <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> lub dla typu, który zawiera <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="28a5c-326">All serializers (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer>) fail to generate serialization code for type <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> or for a type that contains <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="28a5c-327">Wyświetlają one błędy czasu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="28a5c-327">They display build-time errors instead.</span></span>

- <span data-ttu-id="28a5c-328">Następujące konstruktory typów serializacji nie gwarantują działania zgodnie z oczekiwaniami:</span><span class="sxs-lookup"><span data-stu-id="28a5c-328">The following constructors of the serialization types aren't guaranteed to work as expected:</span></span>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.DataContractSerializerSettings%29?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Xml.XmlDictionaryString%2CSystem.Xml.XmlDictionaryString%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.Json.DataContractJsonSerializerSettings%29?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.String%29?displayProperty=nameWithType>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%29?displayProperty=nameWithType>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlRootAttribute%29?displayProperty=nameWithType>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%2CSystem.Type%5B%5D%2CSystem.Xml.Serialization.XmlRootAttribute%2CSystem.String%29?displayProperty=nameWithType>

- <span data-ttu-id="28a5c-329"><xref:System.Xml.Serialization.XmlSerializer>nie można wygenerować kodu dla typu, który ma metody przypisane do żadnego z następujących atrybutów:</span><span class="sxs-lookup"><span data-stu-id="28a5c-329"><xref:System.Xml.Serialization.XmlSerializer> fails to generate code for a type that has methods attributed with any of the following attributes:</span></span>

  - <xref:System.Runtime.Serialization.OnSerializingAttribute>

  - <xref:System.Runtime.Serialization.OnSerializedAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializingAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializedAttribute>

- <span data-ttu-id="28a5c-330"><xref:System.Xml.Serialization.XmlSerializer>nie honoruje <xref:System.Xml.Serialization.IXmlSerializable> niestandardowego interfejsu serializacji.</span><span class="sxs-lookup"><span data-stu-id="28a5c-330"><xref:System.Xml.Serialization.XmlSerializer> doesn't honor the <xref:System.Xml.Serialization.IXmlSerializable> custom serialization interface.</span></span> <span data-ttu-id="28a5c-331">Jeśli masz klasę, która implementuje ten interfejs, <xref:System.Xml.Serialization.XmlSerializer> traktuje typ zwykłego starego obiektu CLR (POCO) i serializować tylko jego właściwości publiczne.</span><span class="sxs-lookup"><span data-stu-id="28a5c-331">If you have a class that implements this interface, <xref:System.Xml.Serialization.XmlSerializer> considers the type a plain old CLR object (POCO) type and serializes only its public properties.</span></span>

- <span data-ttu-id="28a5c-332">Serializacja zwykłego <xref:System.Exception> obiektu nie działa dobrze z <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="28a5c-332">Serializing a plain <xref:System.Exception> object doesn't work well with <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

<a name="VS"></a>

## <a name="visual-studio-differences"></a><span data-ttu-id="28a5c-333">Różnice w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="28a5c-333">Visual Studio differences</span></span>

<span data-ttu-id="28a5c-334">**Wyjątki i debugowanie**</span><span class="sxs-lookup"><span data-stu-id="28a5c-334">**Exceptions and debugging**</span></span>

<span data-ttu-id="28a5c-335">Gdy uruchamiasz Aplikacje skompilowane przy użyciu .NET Native w debugerze, wyjątki pierwszej szansy są włączone dla następujących typów wyjątków:</span><span class="sxs-lookup"><span data-stu-id="28a5c-335">When you're running apps compiled by using .NET Native in the debugger, first-chance exceptions are enabled for the following exception types:</span></span>

- <xref:System.MemberAccessException>

- <xref:System.TypeAccessException>

<span data-ttu-id="28a5c-336">**Tworzenie aplikacji**</span><span class="sxs-lookup"><span data-stu-id="28a5c-336">**Building apps**</span></span>

<span data-ttu-id="28a5c-337">Użyj narzędzi kompilacji x86, które są używane domyślnie przez program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="28a5c-337">Use the x86 build tools that are used by default by Visual Studio.</span></span> <span data-ttu-id="28a5c-338">Nie zalecamy korzystania z narzędzi MSBuild AMD64, które znajdują się w folderze C:\Program Files (x86) \MSBuild\12.0\bin\amd64; może to spowodować problemy z kompilacją.</span><span class="sxs-lookup"><span data-stu-id="28a5c-338">We don't recommend using the AMD64 MSBuild tools, which are found in C:\Program Files (x86)\MSBuild\12.0\bin\amd64; these may create build problems.</span></span>

<span data-ttu-id="28a5c-339">**Profilery**</span><span class="sxs-lookup"><span data-stu-id="28a5c-339">**Profilers**</span></span>

- <span data-ttu-id="28a5c-340">Profiler procesora CPU programu Visual Studio i Profiler pamięci XAML nie wyświetlają poprawnie kodu "tylko mój kod".</span><span class="sxs-lookup"><span data-stu-id="28a5c-340">The Visual Studio CPU Profiler and XAML Memory Profiler don't display Just-My-Code correctly.</span></span>

- <span data-ttu-id="28a5c-341">Profiler pamięci XAML nie wyświetla prawidłowo danych sterty zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="28a5c-341">The XAML Memory Profiler doesn't accurately display managed heap data.</span></span>

- <span data-ttu-id="28a5c-342">Program profilujący procesora nie zidentyfikuje prawidłowo modułów i wyświetla nazwy funkcji poprzedzone prefiksem.</span><span class="sxs-lookup"><span data-stu-id="28a5c-342">The CPU Profiler doesn't correctly identify modules, and displays prefixed function names.</span></span>

<span data-ttu-id="28a5c-343">**Projekty biblioteki testów jednostkowych**</span><span class="sxs-lookup"><span data-stu-id="28a5c-343">**Unit Test Library projects**</span></span>

<span data-ttu-id="28a5c-344">Włączanie .NET Native w bibliotece testów jednostkowych dla projektu aplikacji ze sklepu Windows nie jest obsługiwane i powoduje, że kompilacja nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="28a5c-344">Enabling .NET Native on a Unit Test Library for a Windows Store apps project isn't supported and causes the project to fail to build.</span></span>

## <a name="see-also"></a><span data-ttu-id="28a5c-345">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="28a5c-345">See also</span></span>

- [<span data-ttu-id="28a5c-346">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="28a5c-346">Getting Started</span></span>](getting-started-with-net-native.md)
- [<span data-ttu-id="28a5c-347">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="28a5c-347">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="28a5c-348">Omówienie programu .NET dla aplikacji do sklepu Windows</span><span class="sxs-lookup"><span data-stu-id="28a5c-348">.NET For Windows Store apps overview</span></span>](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29)
- [<span data-ttu-id="28a5c-349">Obsługa programu .NET Framework dla aplikacji ze Sklepu Windows i środowiska wykonawczego systemu Windows</span><span class="sxs-lookup"><span data-stu-id="28a5c-349">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)

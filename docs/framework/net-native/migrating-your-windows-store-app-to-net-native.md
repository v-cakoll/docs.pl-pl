---
title: Migrowanie aplikacji ze Sklepu Windows do architektury .NET Native
ms.date: 03/30/2017
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
ms.openlocfilehash: 36f9ac4647b349ff379869f3415a5fb9e55228e3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81241948"
---
# <a name="migrate-your-windows-store-app-to-net-native"></a><span data-ttu-id="c3714-102">Migrowanie aplikacji ze Sklepu Windows do macierzystej platformy .NET</span><span class="sxs-lookup"><span data-stu-id="c3714-102">Migrate Your Windows Store App to .NET Native</span></span>

<span data-ttu-id="c3714-103">Program .NET Native zapewnia statyczną kompilację aplikacji w Sklepie Windows lub na komputerze dewelopera.</span><span class="sxs-lookup"><span data-stu-id="c3714-103">.NET Native provides static compilation of apps in the Windows Store or on the developer’s computer.</span></span> <span data-ttu-id="c3714-104">Różni się to od kompilacji dynamicznej wykonywanej dla aplikacji ze Sklepu Windows przez kompilator just-in-time (JIT) lub [natywny generator obrazów (Ngen.exe)](../tools/ngen-exe-native-image-generator.md) na urządzeniu.</span><span class="sxs-lookup"><span data-stu-id="c3714-104">This differs from the dynamic compilation performed for Windows Store apps by the just-in-time (JIT) compiler or the [Native Image Generator (Ngen.exe)](../tools/ngen-exe-native-image-generator.md) on the device.</span></span> <span data-ttu-id="c3714-105">Pomimo różnic program .NET Native próbuje zachować zgodność z [aplikacjami ze Sklepu Windows .NET dla aplikacji ze Sklepu Windows](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29).</span><span class="sxs-lookup"><span data-stu-id="c3714-105">Despite the differences, .NET Native tries to maintain compatibility with the [.NET for Windows Store apps](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29).</span></span> <span data-ttu-id="c3714-106">W przeważającej części działa również z aplikacjami .NET dla Sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="c3714-106">For the most part, things that work on the .NET for Windows Store apps also work with .NET Native.</span></span>  <span data-ttu-id="c3714-107">Jednak w niektórych przypadkach mogą wystąpić zmiany w zachowaniu.</span><span class="sxs-lookup"><span data-stu-id="c3714-107">However, in some cases, you may encounter behavioral changes.</span></span> <span data-ttu-id="c3714-108">W tym dokumencie omówiono te różnice między standardową platformą .NET dla aplikacji ze Sklepu Windows a platformą .NET Native w następujących obszarach:</span><span class="sxs-lookup"><span data-stu-id="c3714-108">This document discusses these differences between the standard .NET for Windows Store apps and .NET Native in the following areas:</span></span>

- [<span data-ttu-id="c3714-109">Ogólne różnice czasu wykonywania</span><span class="sxs-lookup"><span data-stu-id="c3714-109">General runtime differences</span></span>](#Runtime)

- [<span data-ttu-id="c3714-110">Dynamiczne różnice w programowaniu</span><span class="sxs-lookup"><span data-stu-id="c3714-110">Dynamic programming differences</span></span>](#Dynamic)

- [<span data-ttu-id="c3714-111">Inne różnice związane z refleksją</span><span class="sxs-lookup"><span data-stu-id="c3714-111">Other reflection-related differences</span></span>](#Reflection)

- [<span data-ttu-id="c3714-112">Nieobsługiwały się scenariusze i interfejsy API</span><span class="sxs-lookup"><span data-stu-id="c3714-112">Unsupported scenarios and APIs</span></span>](#Unsupported)

- [<span data-ttu-id="c3714-113">Różnice w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c3714-113">Visual Studio differences</span></span>](#VS)

<a name="Runtime"></a>

## <a name="general-runtime-differences"></a><span data-ttu-id="c3714-114">Ogólne różnice czasu wykonywania</span><span class="sxs-lookup"><span data-stu-id="c3714-114">General runtime differences</span></span>

- <span data-ttu-id="c3714-115">Wyjątki, takie <xref:System.TypeLoadException>jak , które są generowane przez kompilator JIT, gdy aplikacja jest uruchamiana w środowisku uruchomieniowym języka wspólnego (CLR) zazwyczaj powoduje błędy w czasie kompilacji podczas przetwarzania przez .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c3714-115">Exceptions, such as <xref:System.TypeLoadException>, that are thrown by the JIT compiler when an app runs on the common language runtime (CLR) generally result in compile-time errors when processed by .NET Native.</span></span>

- <span data-ttu-id="c3714-116">Nie wywoływaj <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> metody z wątku interfejsu użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c3714-116">Don't call the <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method from an app's UI thread.</span></span> <span data-ttu-id="c3714-117">Może to spowodować zakleszczenie na natywnym .NET.</span><span class="sxs-lookup"><span data-stu-id="c3714-117">This can result in a deadlock on .NET Native.</span></span>

- <span data-ttu-id="c3714-118">Nie polegaj na kolejności wywoływania konstruktora klasy statycznej.</span><span class="sxs-lookup"><span data-stu-id="c3714-118">Don't rely on static class constructor invocation ordering.</span></span> <span data-ttu-id="c3714-119">W programie .NET Native kolejność wywołania różni się od kolejności w standardowym czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c3714-119">In .NET Native, the invocation order is different from the order on the standard runtime.</span></span> <span data-ttu-id="c3714-120">(Nawet w przypadku standardowego środowiska uruchomieniowego nie należy polegać na kolejności wykonywania konstruktorów klas statycznych).</span><span class="sxs-lookup"><span data-stu-id="c3714-120">(Even with the standard runtime, you shouldn't rely on the order of execution of static class constructors.)</span></span>

- <span data-ttu-id="c3714-121">Nieskończone zapętlanie bez wywoływania (na `while(true);`przykład) w dowolnym wątku może doprowadzić aplikację do zatrzymania.</span><span class="sxs-lookup"><span data-stu-id="c3714-121">Infinite looping without making a call (for example, `while(true);`) on any thread may bring the app to a halt.</span></span> <span data-ttu-id="c3714-122">Podobnie duże lub nieskończone oczekiwania mogą doprowadzić aplikację do zatrzymania.</span><span class="sxs-lookup"><span data-stu-id="c3714-122">Similarly, large or infinite waits may bring the app to a halt.</span></span>

- <span data-ttu-id="c3714-123">Niektóre ogólne cykle inicjowania nie zgłaszają wyjątków w .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c3714-123">Certain generic initialization cycles don't throw exceptions in .NET Native.</span></span> <span data-ttu-id="c3714-124">Na przykład następujący kod zgłasza <xref:System.TypeLoadException> wyjątek w standardowym programie CLR.</span><span class="sxs-lookup"><span data-stu-id="c3714-124">For example, the following code throws a <xref:System.TypeLoadException> exception on the standard CLR.</span></span> <span data-ttu-id="c3714-125">W .NET Native, nie.</span><span class="sxs-lookup"><span data-stu-id="c3714-125">In .NET Native, it doesn't.</span></span>

  [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]

- <span data-ttu-id="c3714-126">W niektórych przypadkach .NET Native udostępnia różne implementacje bibliotek klas programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c3714-126">In some cases, .NET Native provides different implementations of .NET Framework class libraries.</span></span> <span data-ttu-id="c3714-127">Obiekt zwrócony z metody zawsze zaimplementuje elementy członkowskie zwracanego typu.</span><span class="sxs-lookup"><span data-stu-id="c3714-127">An object returned from a method will always implement the members of the returned type.</span></span> <span data-ttu-id="c3714-128">Jednak ponieważ jego implementacji kopii zapasowej jest inna, może nie być w stanie oddać go do tego samego zestawu typów, jak można na innych platformach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c3714-128">However, since its backing implementation is different, you may not be able to cast it to the same set of types as you could on other .NET Framework platforms.</span></span> <span data-ttu-id="c3714-129">Na przykład w niektórych przypadkach może nie <xref:System.Collections.Generic.IEnumerable%601> być możliwe rzutowania <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> obiektu <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> `T[]`interfejsu zwróconego metodami, takimi jak lub do .</span><span class="sxs-lookup"><span data-stu-id="c3714-129">For example, in some cases, you may not be able to cast the <xref:System.Collections.Generic.IEnumerable%601> interface object returned by methods such as <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> or <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> to `T[]`.</span></span>

- <span data-ttu-id="c3714-130">Pamięć podręczna WinInet nie jest domyślnie włączona w aplikacjiach ze Sklepu Windows .NET, ale jest na natywna .NET.</span><span class="sxs-lookup"><span data-stu-id="c3714-130">The WinInet cache isn't enabled by default on .NET for Windows Store apps, but it is on .NET Native.</span></span> <span data-ttu-id="c3714-131">Zwiększa to wydajność, ale ma wpływ na zestaw roboczy.</span><span class="sxs-lookup"><span data-stu-id="c3714-131">This improves performance but has working set implications.</span></span> <span data-ttu-id="c3714-132">Nie jest konieczne żadne działanie dewelopera.</span><span class="sxs-lookup"><span data-stu-id="c3714-132">No developer action is necessary.</span></span>

<a name="Dynamic"></a>

## <a name="dynamic-programming-differences"></a><span data-ttu-id="c3714-133">Dynamiczne różnice w programowaniu</span><span class="sxs-lookup"><span data-stu-id="c3714-133">Dynamic programming differences</span></span>

<span data-ttu-id="c3714-134">.NET Natywne statycznie łącza w kodzie z .NET Framework, aby kod app-local dla maksymalnej wydajności.</span><span class="sxs-lookup"><span data-stu-id="c3714-134">.NET Native statically links in code from the .NET Framework to make the code app-local for maximum performance.</span></span> <span data-ttu-id="c3714-135">Jednak rozmiary binarne muszą pozostać małe, więc nie można wniesieć całego programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c3714-135">However, binary sizes have to remain small, so the entire .NET Framework can't be brought in.</span></span> <span data-ttu-id="c3714-136">Kompilator natywny platformy .NET rozwiązuje to ograniczenie przy użyciu reduktora zależności, który usuwa odwołania do nieużytego kodu.</span><span class="sxs-lookup"><span data-stu-id="c3714-136">The .NET Native compiler resolves this limitation by using a dependency reducer that removes references to unused code.</span></span> <span data-ttu-id="c3714-137">Jednak .NET Native może nie obsługiwać lub generować niektóre informacje o typie i kod, gdy informacje te nie można wywnioskować statycznie w czasie kompilacji, ale zamiast tego jest pobierana dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c3714-137">However, .NET Native might not maintain or generate some type information and code when that information can't be inferred statically at compile time, but instead is retrieved dynamically at runtime.</span></span>

<span data-ttu-id="c3714-138">Program .NET Native umożliwia odbicie i dynamiczne programowanie.</span><span class="sxs-lookup"><span data-stu-id="c3714-138">.NET Native does enable reflection and dynamic programming.</span></span> <span data-ttu-id="c3714-139">Jednak nie wszystkie typy mogą być oznaczone do odbicia, ponieważ spowodowałoby to rozmiar wygenerowanego kodu zbyt duży (zwłaszcza, że odbijanie się na publicznych interfejsów API w programie .NET Framework jest obsługiwane).</span><span class="sxs-lookup"><span data-stu-id="c3714-139">However, not all types can be marked for reflection, because this would make the generated code size too large (especially because reflecting on public APIs in the .NET Framework is supported).</span></span> <span data-ttu-id="c3714-140">Kompilator natywny platformy .NET dokonuje inteligentnych wyborów dotyczących typów, które powinny obsługiwać odbicie, a także przechowuje metadane i generuje kod tylko dla tych typów.</span><span class="sxs-lookup"><span data-stu-id="c3714-140">The .NET Native compiler makes smart choices about which types should support reflection, and it keeps the metadata and generates code only for those types.</span></span>

<span data-ttu-id="c3714-141">Na przykład powiązanie danych wymaga aplikacji, aby móc mapować nazwy właściwości do funkcji.</span><span class="sxs-lookup"><span data-stu-id="c3714-141">For example, data binding requires an app to be able to map property names to functions.</span></span> <span data-ttu-id="c3714-142">W aplikacjach .NET dla Sklepu Windows środowisko wykonawcze języka wspólnego automatycznie używa odbicia, aby zapewnić tę możliwość dla typów zarządzanych i publicznie dostępnych typów natywnych.</span><span class="sxs-lookup"><span data-stu-id="c3714-142">In .NET for Windows Store apps, the common language runtime automatically uses reflection to provide this capability for managed types and publicly available native types.</span></span> <span data-ttu-id="c3714-143">W programie .NET Native kompilator automatycznie zawiera metadane dla typów, z którymi wiążą się dane.</span><span class="sxs-lookup"><span data-stu-id="c3714-143">In .NET Native, the compiler automatically includes metadata for types to which you bind data.</span></span>

<span data-ttu-id="c3714-144">Kompilator natywny platformy .NET może również <xref:System.Collections.Generic.List%601> obsługiwać powszechnie używane typy ogólne, takie jak i <xref:System.Collections.Generic.Dictionary%602>, które działają bez konieczności żadnych wskazówek lub dyrektyw.</span><span class="sxs-lookup"><span data-stu-id="c3714-144">The .NET Native compiler can also handle commonly used generic types such as <xref:System.Collections.Generic.List%601> and <xref:System.Collections.Generic.Dictionary%602>, which work without requiring any hints or directives.</span></span> <span data-ttu-id="c3714-145">[Dynamiczne](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) słowo kluczowe jest również obsługiwane w określonych granicach.</span><span class="sxs-lookup"><span data-stu-id="c3714-145">The [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) keyword is also supported within certain limits.</span></span>

> [!NOTE]
> <span data-ttu-id="c3714-146">Należy dokładnie przetestować wszystkie ścieżki kodu dynamicznego podczas przenoszenia aplikacji do platformy .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c3714-146">You should test all dynamic code paths thoroughly when porting your app to .NET Native.</span></span>

<span data-ttu-id="c3714-147">Domyślna konfiguracja dla platformy .NET Native jest wystarczająca dla większości deweloperów, ale niektórzy deweloperzy mogą chcieć dostosować swoje konfiguracje przy użyciu pliku dyrektyw środowiska uruchomieniowego (.rd.xml).</span><span class="sxs-lookup"><span data-stu-id="c3714-147">The default configuration for .NET Native is sufficient for most developers, but some developers might want to fine- tune their configurations by using a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="c3714-148">Ponadto w niektórych przypadkach kompilator natywny platformy .NET nie może określić, które metadane muszą być dostępne do odbicia i opiera się na wskazówkach, szczególnie w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="c3714-148">In addition, in some cases, the .NET Native compiler is unable to determine which metadata must be available for reflection and relies on hints, particularly in the following cases:</span></span>

- <span data-ttu-id="c3714-149">Niektóre konstrukcje <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> lubią i nie mogą być ustalone statycznie.</span><span class="sxs-lookup"><span data-stu-id="c3714-149">Some constructs like <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> and <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> can't be determined statically.</span></span>

- <span data-ttu-id="c3714-150">Ponieważ kompilator nie może określić wystąpienia, typ ogólny, który chcesz odzwierciedlić, musi być określony przez dyrektywy środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="c3714-150">Because the compiler can't determine the instantiations, a generic type that you want to reflect on has to be specified by runtime directives.</span></span> <span data-ttu-id="c3714-151">Nie jest to tylko dlatego, że cały kod musi być uwzględniony, ale ponieważ odbicie typów ogólnych może tworzyć nieskończony cykl (na przykład, gdy metoda rodzajowa jest wywoływana na typ ogólny).</span><span class="sxs-lookup"><span data-stu-id="c3714-151">This isn't just because all code must be included, but because reflection on generic types can form an infinite cycle (for example, when a generic method is invoked on a generic type).</span></span>

> [!NOTE]
> <span data-ttu-id="c3714-152">Dyrektywy środowiska uruchomieniowego są zdefiniowane w pliku dyrektyw środowiska uruchomieniowego (.rd.xml).</span><span class="sxs-lookup"><span data-stu-id="c3714-152">Runtime directives are defined in a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="c3714-153">Aby uzyskać ogólne informacje dotyczące korzystania z tego pliku, zobacz [Wprowadzenie](getting-started-with-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="c3714-153">For general information about using this file, see [Getting Started](getting-started-with-net-native.md).</span></span> <span data-ttu-id="c3714-154">Aby uzyskać informacje na temat dyrektyw środowiska wykonawczego, zobacz [Odwołanie do plików konfiguracyjnych dyrektyw środowiska wykonawczego (rd.xml).](runtime-directives-rd-xml-configuration-file-reference.md)</span><span class="sxs-lookup"><span data-stu-id="c3714-154">For information about the runtime directives, see [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span></span>

<span data-ttu-id="c3714-155">Program .NET Native zawiera również narzędzia profilowania, które pomagają deweloperowi określić, które typy poza zestawem domyślnym powinny obsługiwać odbicie.</span><span class="sxs-lookup"><span data-stu-id="c3714-155">.NET Native also includes profiling tools that help the developer determine which types outside the default set should support reflection.</span></span>

<a name="Reflection"></a>

## <a name="other-reflection-related-differences"></a><span data-ttu-id="c3714-156">Inne różnice związane z refleksją</span><span class="sxs-lookup"><span data-stu-id="c3714-156">Other reflection-related differences</span></span>

<span data-ttu-id="c3714-157">Istnieje wiele innych indywidualnych różnic związanych z odbiciem w zachowaniu między aplikacjami .NET dla Sklepu Windows a programem .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c3714-157">There are a number of other individual reflection-related differences in behavior between the .NET for Windows Store apps and .NET Native.</span></span>

<span data-ttu-id="c3714-158">W .NET native:</span><span class="sxs-lookup"><span data-stu-id="c3714-158">In .NET Native:</span></span>

- <span data-ttu-id="c3714-159">Prywatne odbicie nad typami i członkami w bibliotece klas .NET Framework nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="c3714-159">Private reflection over types and members in the .NET Framework class library is not supported.</span></span> <span data-ttu-id="c3714-160">Można jednak odzwierciedlać własne typy prywatne i członków, a także typy i elementy członkowskie w bibliotekach innych firm.</span><span class="sxs-lookup"><span data-stu-id="c3714-160">You can, however, reflect over your own private types and members, as well as types and members in third-party libraries.</span></span>

- <span data-ttu-id="c3714-161">Właściwość <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> poprawnie `false` zwraca <xref:System.Reflection.ParameterInfo> dla obiektu, który reprezentuje wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="c3714-161">The <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> property correctly returns `false` for a <xref:System.Reflection.ParameterInfo> object that represents a return value.</span></span> <span data-ttu-id="c3714-162">W aplikacjiach .NET dla Sklepu `true`Windows zwraca program .</span><span class="sxs-lookup"><span data-stu-id="c3714-162">In the .NET for Windows Store apps, it returns `true`.</span></span> <span data-ttu-id="c3714-163">Język pośredni (IL) nie obsługuje tego bezpośrednio, a interpretacja jest pozostawiona w języku.</span><span class="sxs-lookup"><span data-stu-id="c3714-163">Intermediate language (IL) doesn’t support this directly, and interpretation is left to the language.</span></span>

- <span data-ttu-id="c3714-164">Członkowie publiczni <xref:System.RuntimeFieldHandle> <xref:System.RuntimeMethodHandle> na i struktur nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="c3714-164">Public members on the <xref:System.RuntimeFieldHandle> and <xref:System.RuntimeMethodHandle> structures aren't supported.</span></span> <span data-ttu-id="c3714-165">Te typy są obsługiwane tylko dla LINQ, drzewa wyrażeń i inicjowania tablic statycznych.</span><span class="sxs-lookup"><span data-stu-id="c3714-165">These types are supported only for LINQ, expression trees, and static array initialization.</span></span>

- <span data-ttu-id="c3714-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType>i <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> dołączyć ukryte elementy członkowskie w klasach podstawowych i w związku z tym mogą być zastąpione bez jawnych zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="c3714-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> and <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> include hidden members in base classes and thus may be overridden without explicit overrides.</span></span> <span data-ttu-id="c3714-167">Dotyczy to również innych metod [RuntimeReflectionExtensions.GetRuntime\*.](xref:System.Reflection.RuntimeReflectionExtensions)</span><span class="sxs-lookup"><span data-stu-id="c3714-167">This is also true of other [RuntimeReflectionExtensions.GetRuntime\*](xref:System.Reflection.RuntimeReflectionExtensions) methods.</span></span>

- <span data-ttu-id="c3714-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType>i <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> nie zawiedziej podczas próby utworzenia pewnych kombinacji (na przykład tablicy byrefs).</span><span class="sxs-lookup"><span data-stu-id="c3714-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> don't fail when you try to create certain combinations (for example, an array of byrefs).</span></span>

- <span data-ttu-id="c3714-169">Nie można użyć odbicia do wywoływania elementów członkowskich, które mają parametry wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="c3714-169">You can't use reflection to invoke members that have pointer parameters.</span></span>

- <span data-ttu-id="c3714-170">Odbicie nie można używać do uzyskania lub ustawionego pola wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="c3714-170">You can't use reflection to get or set a pointer field.</span></span>

- <span data-ttu-id="c3714-171">Gdy liczba argumentów jest nieprawidłowa, a typ jednego z argumentów <xref:System.ArgumentException> jest niepoprawny, .NET Native zgłasza zamiast <xref:System.Reflection.TargetParameterCountException>.</span><span class="sxs-lookup"><span data-stu-id="c3714-171">When the argument count is wrong and the type of one of the arguments is incorrect, .NET Native throws an <xref:System.ArgumentException> instead of a <xref:System.Reflection.TargetParameterCountException>.</span></span>

- <span data-ttu-id="c3714-172">Serializacja binarna wyjątków zazwyczaj nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="c3714-172">Binary serialization of exceptions is generally not supported.</span></span> <span data-ttu-id="c3714-173">W rezultacie obiekty nieserwialne mogą być <xref:System.Exception.Data%2A?displayProperty=nameWithType> dodawane do słownika.</span><span class="sxs-lookup"><span data-stu-id="c3714-173">As a result, non-serializable objects can be added to the <xref:System.Exception.Data%2A?displayProperty=nameWithType> dictionary.</span></span>

<a name="Unsupported"></a>

## <a name="unsupported-scenarios-and-apis"></a><span data-ttu-id="c3714-174">Nieobsługiwały się scenariusze i interfejsy API</span><span class="sxs-lookup"><span data-stu-id="c3714-174">Unsupported scenarios and APIs</span></span>

<span data-ttu-id="c3714-175">W poniższych sekcjach lista nieobsługiwane scenariusze i interfejsy API dla ogólnego rozwoju, interop i technologii, takich jak HTTPClient i Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="c3714-175">The following sections list unsupported scenarios and APIs for general development, interop, and technologies such as HTTPClient and Windows Communication Foundation (WCF):</span></span>

- [<span data-ttu-id="c3714-176">Ogólny rozwój</span><span class="sxs-lookup"><span data-stu-id="c3714-176">General development</span></span>](#General)

- [<span data-ttu-id="c3714-177">Funkcja HttpClient</span><span class="sxs-lookup"><span data-stu-id="c3714-177">HttpClient</span></span>](#HttpClient)

- [<span data-ttu-id="c3714-178">Interop</span><span class="sxs-lookup"><span data-stu-id="c3714-178">Interop</span></span>](#Interop)

- [<span data-ttu-id="c3714-179">Nieobsługiwały interfejsy API</span><span class="sxs-lookup"><span data-stu-id="c3714-179">Unsupported APIs</span></span>](#APIs)

<a name="General"></a>

### <a name="general-development-differences"></a><span data-ttu-id="c3714-180">Ogólne różnice rozwojowe</span><span class="sxs-lookup"><span data-stu-id="c3714-180">General development differences</span></span>

<span data-ttu-id="c3714-181">**Typy wartości**</span><span class="sxs-lookup"><span data-stu-id="c3714-181">**Value types**</span></span>

- <span data-ttu-id="c3714-182">Jeśli zastąpisz <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> i <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> metody dla typu wartości, nie należy wywoływać implementacji klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="c3714-182">If you override the <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> and <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> methods for a value type, don't call the base class implementations.</span></span> <span data-ttu-id="c3714-183">W aplikacji .NET dla Sklepu Windows te metody opierają się na odbiciu.</span><span class="sxs-lookup"><span data-stu-id="c3714-183">In .NET for Windows Store apps, these methods rely on reflection.</span></span> <span data-ttu-id="c3714-184">W czasie kompilacji .NET Native generuje implementację, która nie opiera się na odbicie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="c3714-184">At compile time, .NET Native generates an implementation that doesn't rely on runtime reflection.</span></span> <span data-ttu-id="c3714-185">Oznacza to, że jeśli nie zastąpisz tych dwóch metod, będą działać zgodnie z oczekiwaniami, ponieważ .NET Native generuje implementację w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c3714-185">This means that if you don't override these two methods, they will work as expected, because .NET Native generates the implementation at compile time.</span></span> <span data-ttu-id="c3714-186">Jednak zastąpienie tych metod, ale wywołanie implementacji klasy podstawowej powoduje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c3714-186">However, overriding these methods but calling the base class implementation results in an exception.</span></span>

- <span data-ttu-id="c3714-187">Typy wartości większe niż jeden megabajt nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="c3714-187">Value types larger than one megabyte aren't supported.</span></span>

- <span data-ttu-id="c3714-188">Typy wartości nie mogą mieć konstruktora bez parametrów w .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c3714-188">Value types can't have a parameterless constructor in .NET Native.</span></span> <span data-ttu-id="c3714-189">(C# i Visual Basic zabraniają konstruktorów bez parametrów na typach wartości.</span><span class="sxs-lookup"><span data-stu-id="c3714-189">(C# and Visual Basic prohibit parameterless constructors on value types.</span></span> <span data-ttu-id="c3714-190">Można je jednak utworzyć w IL.)</span><span class="sxs-lookup"><span data-stu-id="c3714-190">However, these can be created in IL.)</span></span>

<span data-ttu-id="c3714-191">**Tablice**</span><span class="sxs-lookup"><span data-stu-id="c3714-191">**Arrays**</span></span>

- <span data-ttu-id="c3714-192">Tablice z dolną granicą inną niż zero nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="c3714-192">Arrays with a lower bound other than zero aren't supported.</span></span> <span data-ttu-id="c3714-193">Zazwyczaj te tablice są tworzone <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> przez wywołanie przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="c3714-193">Typically, these arrays are created by calling the <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> overload.</span></span>

- <span data-ttu-id="c3714-194">Dynamiczne tworzenie tablic wielowymiarowych nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="c3714-194">Dynamic creation of multidimensional arrays isn't supported.</span></span> <span data-ttu-id="c3714-195">Takie tablice są zazwyczaj tworzone przez wywołanie przeciążenia <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> metody, która zawiera `lengths` parametr lub wywołując <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="c3714-195">Such arrays are typically created by calling an overload of the <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> method that includes a `lengths` parameter, or by calling the <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="c3714-196">Tablice wielowymiarowe, które mają cztery lub więcej wymiarów, nie są obsługiwane; oznacza to, <xref:System.Array.Rank%2A?displayProperty=nameWithType> że ich wartość nieruchomości wynosi cztery lub więcej.</span><span class="sxs-lookup"><span data-stu-id="c3714-196">Multidimensional arrays that have four or more dimensions aren't supported; that is, their <xref:System.Array.Rank%2A?displayProperty=nameWithType> property value is four or greater.</span></span> <span data-ttu-id="c3714-197">Zamiast tego należy użyć [tablic postrzępionych](../../csharp/programming-guide/arrays/jagged-arrays.md) (tablicy tablic).</span><span class="sxs-lookup"><span data-stu-id="c3714-197">Use [jagged arrays](../../csharp/programming-guide/arrays/jagged-arrays.md) (an array of arrays) instead.</span></span> <span data-ttu-id="c3714-198">Na przykład `array[x,y,z]` jest nieprawidłowy, ale `array[x][y][z]` nie jest.</span><span class="sxs-lookup"><span data-stu-id="c3714-198">For example, `array[x,y,z]` is invalid, but `array[x][y][z]` isn't.</span></span>

- <span data-ttu-id="c3714-199">Odchylenie dla tablic wielowymiarowych nie jest <xref:System.InvalidCastException> obsługiwane i powoduje wyjątek w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c3714-199">Variance for multidimensional arrays isn't supported and causes an <xref:System.InvalidCastException> exception at run time.</span></span>

<span data-ttu-id="c3714-200">**Typy ogólne**</span><span class="sxs-lookup"><span data-stu-id="c3714-200">**Generics**</span></span>

- <span data-ttu-id="c3714-201">Nieskończone rozszerzenie typu ogólnego powoduje błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="c3714-201">Infinite generic type expansion results in a compiler error.</span></span> <span data-ttu-id="c3714-202">Na przykład ten kod nie można skompilować:</span><span class="sxs-lookup"><span data-stu-id="c3714-202">For example, this code fails to compile:</span></span>

  [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]

<span data-ttu-id="c3714-203">**Wskaźniki**</span><span class="sxs-lookup"><span data-stu-id="c3714-203">**Pointers**</span></span>

- <span data-ttu-id="c3714-204">Tablice wskaźników nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="c3714-204">Arrays of pointers aren't supported.</span></span>

- <span data-ttu-id="c3714-205">Odbicie nie można używać do uzyskania lub ustawionego pola wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="c3714-205">You can't use reflection to get or set a pointer field.</span></span>

<span data-ttu-id="c3714-206">**Serializacja**</span><span class="sxs-lookup"><span data-stu-id="c3714-206">**Serialization**</span></span>

<span data-ttu-id="c3714-207">Atrybut <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="c3714-207">The <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> attribute isn't supported.</span></span> <span data-ttu-id="c3714-208">Zamiast <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> tego użyj atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c3714-208">Use the <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> attribute instead.</span></span>

<span data-ttu-id="c3714-209">**Zasoby**</span><span class="sxs-lookup"><span data-stu-id="c3714-209">**Resources**</span></span>

<span data-ttu-id="c3714-210">Użycie zlokalizowanych zasobów z <xref:System.Diagnostics.Tracing.EventSource> klasą nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="c3714-210">The use of localized resources with the <xref:System.Diagnostics.Tracing.EventSource> class isn't supported.</span></span> <span data-ttu-id="c3714-211">Właściwość <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> nie definiuje zlokalizowanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="c3714-211">The <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> property doesn't define localized resources.</span></span>

<span data-ttu-id="c3714-212">**Delegaty**</span><span class="sxs-lookup"><span data-stu-id="c3714-212">**Delegates**</span></span>

<span data-ttu-id="c3714-213">`Delegate.BeginInvoke`i `Delegate.EndInvoke` nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="c3714-213">`Delegate.BeginInvoke` and `Delegate.EndInvoke` aren't supported.</span></span>

<span data-ttu-id="c3714-214">**Różne interfejsy API**</span><span class="sxs-lookup"><span data-stu-id="c3714-214">**Miscellaneous APIs**</span></span>

- <span data-ttu-id="c3714-215">[Właściwość TypeInfo.GUID](xref:System.Type.GUID) zgłasza <xref:System.PlatformNotSupportedException> wyjątek, jeśli <xref:System.Runtime.InteropServices.GuidAttribute> atrybut nie jest stosowany do typu.</span><span class="sxs-lookup"><span data-stu-id="c3714-215">The [TypeInfo.GUID](xref:System.Type.GUID) property throws a <xref:System.PlatformNotSupportedException> exception if a <xref:System.Runtime.InteropServices.GuidAttribute> attribute isn't applied to the type.</span></span> <span data-ttu-id="c3714-216">Identyfikator GUID jest używany głównie do obsługi COM.</span><span class="sxs-lookup"><span data-stu-id="c3714-216">The GUID is used primarily for COM support.</span></span>

- <span data-ttu-id="c3714-217">Metoda <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> poprawnie analizuje ciągi, które zawierają krótkie daty w .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c3714-217">The <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> method correctly parses strings that contain short dates in .NET Native.</span></span> <span data-ttu-id="c3714-218">Nie utrzymuje jednak zgodności ze zmianami w analizowaniu daty i godziny opisanymi w artykułach bazy wiedzy Microsoft Knowledge Base [KB2803771](https://support.microsoft.com/kb/2803771) i [KB2803755](https://support.microsoft.com/kb/2803755).</span><span class="sxs-lookup"><span data-stu-id="c3714-218">However, it doesn't maintain compatibility with the changes in date and time parsing described in the Microsoft Knowledge Base articles [KB2803771](https://support.microsoft.com/kb/2803771) and [KB2803755](https://support.microsoft.com/kb/2803755).</span></span>

- <span data-ttu-id="c3714-219"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType>`("E")` jest poprawnie zaokrąglona w pliku .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c3714-219"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` is correctly rounded in .NET Native.</span></span> <span data-ttu-id="c3714-220">W niektórych wersjach CLR ciąg wynik jest obcinany zamiast zaokrąglone.</span><span class="sxs-lookup"><span data-stu-id="c3714-220">In some versions of the CLR, the result string is truncated instead of rounded.</span></span>

<a name="HttpClient"></a>

### <a name="httpclient-differences"></a><span data-ttu-id="c3714-221">Różnice w clientie http</span><span class="sxs-lookup"><span data-stu-id="c3714-221">HttpClient differences</span></span>

<span data-ttu-id="c3714-222">W programie .NET <xref:System.Net.Http.HttpClientHandler> Native klasa wewnętrznie używa usługi <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> WinINet (za <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> pośrednictwem klasy) zamiast klas i używanych w standardowej sieci .NET dla aplikacji ze Sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="c3714-222">In .NET Native, the <xref:System.Net.Http.HttpClientHandler> class internally uses WinINet (through the <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class) instead of the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes used in the standard .NET for Windows Store apps.</span></span>  <span data-ttu-id="c3714-223">WinINet nie obsługuje wszystkich opcji konfiguracji, które obsługuje <xref:System.Net.Http.HttpClientHandler> klasa.</span><span class="sxs-lookup"><span data-stu-id="c3714-223">WinINet doesn't support all the configuration options that the <xref:System.Net.Http.HttpClientHandler> class supports.</span></span>  <span data-ttu-id="c3714-224">W efekcie:</span><span class="sxs-lookup"><span data-stu-id="c3714-224">As a result:</span></span>

- <span data-ttu-id="c3714-225">Niektóre właściwości możliwości w <xref:System.Net.Http.HttpClientHandler> przypadku `false` zwrotu na natywnych `true` platformy .NET, podczas gdy zwracają one w standardowej sieci .NET dla aplikacji ze Sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="c3714-225">Some of the capability properties on <xref:System.Net.Http.HttpClientHandler> return `false` on .NET Native, whereas they return `true` in the standard .NET for Windows Store apps.</span></span>

- <span data-ttu-id="c3714-226">Niektóre akcesory właściwości `get` konfiguracji zawsze zwracają stałą wartość na natywną platformy .NET, która różni się od domyślnej wartości konfigurowalnej w programie .NET dla aplikacji ze Sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="c3714-226">Some of the configuration property `get` accessors always return a fixed value on .NET Native that is different than the default configurable value in .NET for Windows Store apps.</span></span>

<span data-ttu-id="c3714-227">Niektóre dodatkowe różnice w zachowaniu są omówione w następujących podsekcjach.</span><span class="sxs-lookup"><span data-stu-id="c3714-227">Some additional behavior differences are covered in the following subsections.</span></span>

<span data-ttu-id="c3714-228">**Proxy**</span><span class="sxs-lookup"><span data-stu-id="c3714-228">**Proxy**</span></span>

<span data-ttu-id="c3714-229">Klasa <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> nie obsługuje konfigurowania lub zastępowania serwera proxy na podstawie żądania.</span><span class="sxs-lookup"><span data-stu-id="c3714-229">The <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class doesn’t support configuring or overriding the proxy on a per-request basis.</span></span>  <span data-ttu-id="c3714-230">Oznacza to, że wszystkie żądania na natywne platformy .NET używają serwera proxy <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> skonfigurowanego przez system lub nie ma serwera proxy, w zależności od wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="c3714-230">This means that all requests on .NET Native use the system-configured proxy server or no proxy server, depending on the value of the <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="c3714-231">W aplikacji .NET dla Sklepu Windows serwer <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> proxy jest definiowany przez właściwość.</span><span class="sxs-lookup"><span data-stu-id="c3714-231">In .NET for Windows Store apps, the proxy server is defined by the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="c3714-232">W programie .NET <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> Native ustawienie wartości `null` innej <xref:System.PlatformNotSupportedException> niż zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c3714-232">On .NET Native, setting the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> to a value other than `null` throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="c3714-233">Właściwość <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> `false` zwraca na poziomie natywnym `true` platformy .NET, podczas gdy zwraca w standardowym programie .NET Framework dla aplikacji ze Sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="c3714-233">The <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> property returns `false` on .NET Native, whereas it returns `true` in the standard .NET Framework for Windows Store apps.</span></span>

<span data-ttu-id="c3714-234">**Automatyczne przekierowanie**</span><span class="sxs-lookup"><span data-stu-id="c3714-234">**Automatic redirection**</span></span>

<span data-ttu-id="c3714-235">Klasa <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> nie zezwala na skonfigurowanie maksymalnej liczby automatycznych przekierowań.</span><span class="sxs-lookup"><span data-stu-id="c3714-235">The <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class doesn't allow the maximum number of automatic redirections to be configured.</span></span>  <span data-ttu-id="c3714-236">Wartość <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> właściwości jest domyślnie 50 w standardzie .NET dla aplikacji ze Sklepu Windows i mogą być modyfikowane.</span><span class="sxs-lookup"><span data-stu-id="c3714-236">The value of the <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> property is 50 by default in the standard .NET for Windows Store apps and can be modified.</span></span> <span data-ttu-id="c3714-237">W programie .NET Native wartość tej właściwości wynosi 10, a <xref:System.PlatformNotSupportedException> próba zmodyfikowania zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c3714-237">On .NET Native, the value of this property is 10, and trying to modify it throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="c3714-238">Właściwość <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> `false` zwraca na natywną `true` platformę .NET, podczas gdy zwraca w programie .NET dla aplikacji ze Sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="c3714-238">The <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> property returns `false` on .NET Native, whereas it returns `true` in .NET for Windows Store apps.</span></span>

<span data-ttu-id="c3714-239">**Automatyczna dekompresja**</span><span class="sxs-lookup"><span data-stu-id="c3714-239">**Automatic decompression**</span></span>

<span data-ttu-id="c3714-240">.NET dla aplikacji ze Sklepu <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> Windows <xref:System.Net.DecompressionMethods.Deflate>umożliwia <xref:System.Net.DecompressionMethods.GZip>ustawienie <xref:System.Net.DecompressionMethods.Deflate> <xref:System.Net.DecompressionMethods.GZip>właściwości <xref:System.Net.DecompressionMethods.None>na , , i , lub .</span><span class="sxs-lookup"><span data-stu-id="c3714-240">.NET for Windows Store apps allows you to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> property to <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="c3714-241">Program .NET <xref:System.Net.DecompressionMethods.Deflate> Native <xref:System.Net.DecompressionMethods.GZip>obsługuje <xref:System.Net.DecompressionMethods.None>tylko razem z programem , lub .</span><span class="sxs-lookup"><span data-stu-id="c3714-241">.NET Native only supports <xref:System.Net.DecompressionMethods.Deflate> together with <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="c3714-242">Próba ustawienie <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> właściwości na <xref:System.Net.DecompressionMethods.Deflate> jedną <xref:System.Net.DecompressionMethods.GZip> lub samotnie po <xref:System.Net.DecompressionMethods.Deflate> <xref:System.Net.DecompressionMethods.GZip>cichu ustawia ją na obie i .</span><span class="sxs-lookup"><span data-stu-id="c3714-242">Trying to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> property to either <xref:System.Net.DecompressionMethods.Deflate> or <xref:System.Net.DecompressionMethods.GZip> alone silently sets it to both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>.</span></span>

<span data-ttu-id="c3714-243">**Plik cookie**</span><span class="sxs-lookup"><span data-stu-id="c3714-243">**Cookies**</span></span>

<span data-ttu-id="c3714-244">Obsługa plików cookie jest <xref:System.Net.Http.HttpClient> wykonywana jednocześnie przez i WinINet.</span><span class="sxs-lookup"><span data-stu-id="c3714-244">Cookie handling is performed simultaneously by <xref:System.Net.Http.HttpClient> and WinINet.</span></span>  <span data-ttu-id="c3714-245">Pliki cookie <xref:System.Net.CookieContainer> są łączone z plikami cookie w pamięci podręcznej plików cookie WinINet.</span><span class="sxs-lookup"><span data-stu-id="c3714-245">Cookies from the <xref:System.Net.CookieContainer> are combined with cookies in the WinINet cookie cache.</span></span>  <span data-ttu-id="c3714-246">Usunięcie pliku cookie <xref:System.Net.CookieContainer> uniemożliwia <xref:System.Net.Http.HttpClient> wysyłanie pliku cookie, ale jeśli plik cookie był już widoczny przez WinINet, a pliki cookie nie zostały usunięte przez użytkownika, WinINet wysyła go.</span><span class="sxs-lookup"><span data-stu-id="c3714-246">Removing a cookie from <xref:System.Net.CookieContainer> prevents <xref:System.Net.Http.HttpClient> from sending the cookie, but if the cookie was already seen by WinINet, and cookies weren't deleted by the user, WinINet sends it.</span></span>  <span data-ttu-id="c3714-247">Nie można programowo usunąć pliku cookie z usługi WinINet <xref:System.Net.Http.HttpClientHandler>za <xref:System.Net.CookieContainer> pomocą interfejsu <xref:System.Net.Http.HttpClient>API .</span><span class="sxs-lookup"><span data-stu-id="c3714-247">It isn't possible to programmatically remove a cookie from WinINet by using the <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>, or <xref:System.Net.CookieContainer> API.</span></span>  <span data-ttu-id="c3714-248">Ustawienie <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> właściwości `false` na <xref:System.Net.Http.HttpClient> powoduje, że tylko przestać wysyłać pliki cookie; WinINet może nadal zawierać swoje pliki cookie w żądaniu.</span><span class="sxs-lookup"><span data-stu-id="c3714-248">Setting the <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> property to `false` causes only <xref:System.Net.Http.HttpClient> to stop sending cookies; WinINet might still include its cookies in the request.</span></span>

<span data-ttu-id="c3714-249">**Poświadczenia**</span><span class="sxs-lookup"><span data-stu-id="c3714-249">**Credentials**</span></span>

<span data-ttu-id="c3714-250">W aplikacjach .NET dla <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> Sklepu Windows i właściwości działają niezależnie.</span><span class="sxs-lookup"><span data-stu-id="c3714-250">In .NET for Windows Store apps, the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> properties work independently.</span></span>  <span data-ttu-id="c3714-251">Ponadto <xref:System.Net.Http.HttpClientHandler.Credentials%2A> właściwość akceptuje dowolny obiekt, który <xref:System.Net.ICredentials> implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="c3714-251">Additionally, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property accepts any object that implements the <xref:System.Net.ICredentials> interface.</span></span>  <span data-ttu-id="c3714-252">W .NET Native <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> ustawienie `true` właściwości <xref:System.Net.Http.HttpClientHandler.Credentials%2A> powoduje, `null`że właściwość staje się .</span><span class="sxs-lookup"><span data-stu-id="c3714-252">In .NET Native, setting the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> property to `true` causes the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property to become `null`.</span></span>  <span data-ttu-id="c3714-253">Ponadto <xref:System.Net.Http.HttpClientHandler.Credentials%2A> właściwość można ustawić tylko `null` <xref:System.Net.CredentialCache.DefaultCredentials%2A>na , lub <xref:System.Net.NetworkCredential>obiekt typu .</span><span class="sxs-lookup"><span data-stu-id="c3714-253">In addition, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property can be set only to `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>, or an object of type <xref:System.Net.NetworkCredential>.</span></span>  <span data-ttu-id="c3714-254">Przypisywanie innego <xref:System.Net.ICredentials> obiektu, z których <xref:System.Net.CredentialCache>najbardziej popularne <xref:System.Net.Http.HttpClientHandler.Credentials%2A> jest , <xref:System.PlatformNotSupportedException>do właściwości rzuca .</span><span class="sxs-lookup"><span data-stu-id="c3714-254">Assigning any other <xref:System.Net.ICredentials> object, the most popular of which is <xref:System.Net.CredentialCache>, to the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property throws a <xref:System.PlatformNotSupportedException>.</span></span>

<span data-ttu-id="c3714-255">**Inne nieobsługiwanych lub niekonfigurowalnych funkcji**</span><span class="sxs-lookup"><span data-stu-id="c3714-255">**Other unsupported or unconfigurable features**</span></span>

<span data-ttu-id="c3714-256">W .NET native:</span><span class="sxs-lookup"><span data-stu-id="c3714-256">In .NET Native:</span></span>

- <span data-ttu-id="c3714-257">Wartość <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> właściwości jest zawsze <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span><span class="sxs-lookup"><span data-stu-id="c3714-257">The value of the <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> property is always <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span></span>  <span data-ttu-id="c3714-258">W programie .NET dla aplikacji <xref:System.Net.Http.ClientCertificateOption.Manual>ze Sklepu Windows wartość domyślna to .</span><span class="sxs-lookup"><span data-stu-id="c3714-258">In .NET for Windows Store apps, the default is <xref:System.Net.Http.ClientCertificateOption.Manual>.</span></span>

- <span data-ttu-id="c3714-259">Właściwość <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> nie jest konfigurowalna.</span><span class="sxs-lookup"><span data-stu-id="c3714-259">The <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> property isn't configurable.</span></span>

- <span data-ttu-id="c3714-260">Obiekt <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> jest `true`zawsze.</span><span class="sxs-lookup"><span data-stu-id="c3714-260">The <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> property is always `true`.</span></span>  <span data-ttu-id="c3714-261">W programie .NET dla aplikacji `false`ze Sklepu Windows wartość domyślna to .</span><span class="sxs-lookup"><span data-stu-id="c3714-261">In .NET for Windows Store apps, the default is `false`.</span></span>

- <span data-ttu-id="c3714-262">Nagłówek `SetCookie2` w odpowiedziach jest ignorowany jako przestarzały.</span><span class="sxs-lookup"><span data-stu-id="c3714-262">The `SetCookie2` header in responses is ignored as obsolete.</span></span>

<a name="Interop"></a>
### <a name="interop-differences"></a><span data-ttu-id="c3714-263">Różnice międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="c3714-263">Interop differences</span></span>
 <span data-ttu-id="c3714-264">**Przestarzałe interfejsy API**</span><span class="sxs-lookup"><span data-stu-id="c3714-264">**Deprecated APIs**</span></span>

 <span data-ttu-id="c3714-265">Liczba rzadko używanych interfejsów API dla współdziałania z kodem zarządzanym zostały przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="c3714-265">A number of infrequently used APIs for interoperability with managed code have been deprecated.</span></span> <span data-ttu-id="c3714-266">W przypadku użycia z .NET Native te <xref:System.NotImplementedException> <xref:System.PlatformNotSupportedException> interfejsy API mogą zgłaszać lub wyjątek lub spowodować błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="c3714-266">When used with .NET Native, these APIs may throw a <xref:System.NotImplementedException> or <xref:System.PlatformNotSupportedException> exception, or result in a compiler error.</span></span> <span data-ttu-id="c3714-267">W aplikacjach .NET dla Sklepu Windows te interfejsy API są oznaczone jako przestarzałe, chociaż wywołanie ich generuje ostrzeżenie kompilatora, a nie błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="c3714-267">In .NET for Windows Store apps, these APIs are marked as obsolete, although calling them generates a compiler warning rather than a compiler error.</span></span>

 <span data-ttu-id="c3714-268">Przestarzałe interfejsy `VARIANT` API do organizowania obejmują:</span><span class="sxs-lookup"><span data-stu-id="c3714-268">Deprecated APIs for `VARIANT` marshaling include:</span></span>

- <xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VarEnum?displayProperty=nameWithType>

 <span data-ttu-id="c3714-269"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType>jest obsługiwany, ale zgłasza wyjątek w niektórych scenariuszach, takich jak gdy jest używany z [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) lub byref wariantów.</span><span class="sxs-lookup"><span data-stu-id="c3714-269"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> is supported, but it throws an exception in some scenarios, such as when it is used with [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) or byref variants.</span></span>

 <span data-ttu-id="c3714-270">Przestarzałe interfejsy API dla obsługi [funkcji IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) obejmują:</span><span class="sxs-lookup"><span data-stu-id="c3714-270">Deprecated APIs for [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) support include:</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>

<span data-ttu-id="c3714-271">Przestarzałe interfejsy API dla klasycznych zdarzeń COM obejmują:</span><span class="sxs-lookup"><span data-stu-id="c3714-271">Deprecated APIs for classic COM events include:</span></span>

- <xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>

<span data-ttu-id="c3714-272">Przestarzałe interfejsy <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> API w interfejsie, który nie jest obsługiwany w .NET Native, obejmują:</span><span class="sxs-lookup"><span data-stu-id="c3714-272">Deprecated APIs in the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface, which isn't supported in .NET Native, include:</span></span>

- <span data-ttu-id="c3714-273"><xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType>(wszyscy członkowie)</span><span class="sxs-lookup"><span data-stu-id="c3714-273"><xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> (all members)</span></span>
- <span data-ttu-id="c3714-274"><xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType>(wszyscy członkowie)</span><span class="sxs-lookup"><span data-stu-id="c3714-274"><xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType> (all members)</span></span>
- <span data-ttu-id="c3714-275"><xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType>(wszyscy członkowie)</span><span class="sxs-lookup"><span data-stu-id="c3714-275"><xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType> (all members)</span></span>
- <xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=fullName>

<span data-ttu-id="c3714-276">Inne nieobsługiwały funkcje interop obejmują:</span><span class="sxs-lookup"><span data-stu-id="c3714-276">Other unsupported interop features include:</span></span>

- <span data-ttu-id="c3714-277"><xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType>(wszyscy członkowie)</span><span class="sxs-lookup"><span data-stu-id="c3714-277"><xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType> (all members)</span></span>
- <span data-ttu-id="c3714-278"><xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType>(wszyscy członkowie)</span><span class="sxs-lookup"><span data-stu-id="c3714-278"><xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType> (all members)</span></span>
- <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AsAny?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler?displayProperty=fullName>

 <span data-ttu-id="c3714-279">Rzadko używane kierowanie interfejsów API:</span><span class="sxs-lookup"><span data-stu-id="c3714-279">Rarely used marshaling APIs:</span></span>

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

 <span data-ttu-id="c3714-280">**Platforma wywołać i com międzyop zgodności**</span><span class="sxs-lookup"><span data-stu-id="c3714-280">**Platform invoke and COM interop compatibility**</span></span>

 <span data-ttu-id="c3714-281">Większość scenariuszy interop platformy wywołać i COM są nadal obsługiwane w .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c3714-281">Most platform invoke and COM interop scenarios are still supported in .NET Native.</span></span> <span data-ttu-id="c3714-282">W szczególności wszystkie współdziałanie z interfejsami API środowiska wykonawczego systemu Windows (WinRT) i wszystkie kierowanie wymagane dla środowiska wykonawczego systemu Windows jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="c3714-282">In particular, all interoperability with Windows Runtime (WinRT) APIs and all marshaling required for the Windows Runtime is supported.</span></span> <span data-ttu-id="c3714-283">Obejmuje to kierowanie wsparcie dla:</span><span class="sxs-lookup"><span data-stu-id="c3714-283">This includes marshaling support for:</span></span>

- <span data-ttu-id="c3714-284">Tablice (w tym) <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="c3714-284">Arrays (including <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span></span>

- `BStr`

- <span data-ttu-id="c3714-285">Delegaty</span><span class="sxs-lookup"><span data-stu-id="c3714-285">Delegates</span></span>

- <span data-ttu-id="c3714-286">Ciągi (Unicode, Ansi i HSTRING)</span><span class="sxs-lookup"><span data-stu-id="c3714-286">Strings (Unicode, Ansi, and HSTRING)</span></span>

- <span data-ttu-id="c3714-287">Struktury (`byref` i `byval`)</span><span class="sxs-lookup"><span data-stu-id="c3714-287">Structs (`byref` and `byval`)</span></span>

- <span data-ttu-id="c3714-288">Unie</span><span class="sxs-lookup"><span data-stu-id="c3714-288">Unions</span></span>

- <span data-ttu-id="c3714-289">Uchwyty Win32</span><span class="sxs-lookup"><span data-stu-id="c3714-289">Win32 handles</span></span>

- <span data-ttu-id="c3714-290">Wszystkie konstrukcje WinRT</span><span class="sxs-lookup"><span data-stu-id="c3714-290">All WinRT constructs</span></span>

- <span data-ttu-id="c3714-291">Częściowa obsługa typów wariantów organizowania.</span><span class="sxs-lookup"><span data-stu-id="c3714-291">Partial support for marshaling variant types.</span></span> <span data-ttu-id="c3714-292">Obsługiwane są następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="c3714-292">The following are supported:</span></span>

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

  - [<span data-ttu-id="c3714-293">IUnknown</span><span class="sxs-lookup"><span data-stu-id="c3714-293">IUnknown</span></span>](/windows/desktop/api/unknwn/nn-unknwn-iunknown)

<span data-ttu-id="c3714-294">Jednak .NET Native nie obsługuje następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="c3714-294">However, .NET Native doesn't support the following:</span></span>

- <span data-ttu-id="c3714-295">Korzystanie z klasycznych zdarzeń COM</span><span class="sxs-lookup"><span data-stu-id="c3714-295">Using classic COM events</span></span>

- <span data-ttu-id="c3714-296">Implementowanie <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interfejsu w typie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="c3714-296">Implementing the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface on a managed type</span></span>

- <span data-ttu-id="c3714-297">Implementowanie interfejsu [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) na typ <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> zarządzany za pomocą atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c3714-297">Implementing the [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) interface on a managed type through the <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> attribute.</span></span> <span data-ttu-id="c3714-298">Należy jednak pamiętać, że nie można `IDispatch`wywołać obiektów COM za `IDispatch`pośrednictwem obiektu, a obiekt zarządzany nie może zaimplementować .</span><span class="sxs-lookup"><span data-stu-id="c3714-298">However, note that you can't call COM objects through `IDispatch`, and your managed object can't implement `IDispatch`.</span></span>

<span data-ttu-id="c3714-299">Za pomocą odbicia do wywołania platformy wywołać metodę nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="c3714-299">Using reflection to invoke a platform invoke method isn't supported.</span></span> <span data-ttu-id="c3714-300">Można obejść to ograniczenie, zawijając wywołanie metody w innej metodzie i za pomocą odbicia, aby zamiast tego wywołać otokę.</span><span class="sxs-lookup"><span data-stu-id="c3714-300">You can work around this limitation by wrapping the method call in another method and using reflection to call the wrapper instead.</span></span>

<a name="APIs"></a>

### <a name="other-differences-from-net-apis-for-windows-store-apps"></a><span data-ttu-id="c3714-301">Inne różnice w porównaniu z interfejsami API platformy .NET dla aplikacji ze Sklepu Windows</span><span class="sxs-lookup"><span data-stu-id="c3714-301">Other differences from .NET APIs for Windows Store apps</span></span>

<span data-ttu-id="c3714-302">W tej sekcji wymieniono pozostałe interfejsy API, które nie są obsługiwane w programie .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c3714-302">This section lists the remaining APIs that aren't supported in .NET Native.</span></span> <span data-ttu-id="c3714-303">Największy zestaw nieobsługiwał interfejsów API są interfejsy API programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c3714-303">The largest set of the unsupported APIs are Windows Communication Foundation (WCF) APIs.</span></span>

<span data-ttu-id="c3714-304">**Usługi DataAnnotations (System.ComponentModel.DataAnnotations)**</span><span class="sxs-lookup"><span data-stu-id="c3714-304">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span></span>

<span data-ttu-id="c3714-305">Typy w <xref:System.ComponentModel.DataAnnotations> <xref:System.ComponentModel.DataAnnotations.Schema> i przestrzenie nazw nie są obsługiwane w .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c3714-305">The types in the <xref:System.ComponentModel.DataAnnotations> and <xref:System.ComponentModel.DataAnnotations.Schema> namespaces aren't supported in .NET Native.</span></span> <span data-ttu-id="c3714-306">Należą do nich następujące typy, które są obecne w aplikacjach ze Sklepu Windows dla systemu Windows dla systemu Windows 8:</span><span class="sxs-lookup"><span data-stu-id="c3714-306">These include the following types that are present in .NET for Windows Store apps for Windows 8:</span></span>

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

 <span data-ttu-id="c3714-307">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="c3714-307">**Visual Basic**</span></span>

<span data-ttu-id="c3714-308">Visual Basic nie jest obecnie obsługiwany w programie .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c3714-308">Visual Basic isn't currently supported in .NET Native.</span></span> <span data-ttu-id="c3714-309">Następujące typy <xref:Microsoft.VisualBasic> w <xref:Microsoft.VisualBasic.CompilerServices> obszarach i nazw nie są dostępne w obszarze natywnym platformy .NET:</span><span class="sxs-lookup"><span data-stu-id="c3714-309">The following types in the <xref:Microsoft.VisualBasic> and <xref:Microsoft.VisualBasic.CompilerServices> namespaces aren't available in .NET Native:</span></span>

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

<span data-ttu-id="c3714-310">**Kontekst odbicia (obszar nazw System.Reflection.Context)**</span><span class="sxs-lookup"><span data-stu-id="c3714-310">**Reflection Context (System.Reflection.Context namespace)**</span></span>

<span data-ttu-id="c3714-311">Klasa <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> nie jest obsługiwana w .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c3714-311">The <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> class isn't supported in .NET Native.</span></span>

<span data-ttu-id="c3714-312">**RTC (System.Net.http.rtc)**</span><span class="sxs-lookup"><span data-stu-id="c3714-312">**RTC (System.Net.Http.Rtc)**</span></span>

<span data-ttu-id="c3714-313">Klasa `System.Net.Http.RtcRequestFactory` nie jest obsługiwana w .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c3714-313">The `System.Net.Http.RtcRequestFactory` class isn't supported in .NET Native.</span></span>

<span data-ttu-id="c3714-314">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span><span class="sxs-lookup"><span data-stu-id="c3714-314">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span></span>

<span data-ttu-id="c3714-315">Typy w [przestrzeniach nazw System.ServiceModel.\*](xref:System.ServiceModel) nie są obsługiwane w obszarze .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c3714-315">The types in the [System.ServiceModel.\* namespaces](xref:System.ServiceModel) aren't supported in .NET Native.</span></span> <span data-ttu-id="c3714-316">Obejmują one następujące typy:</span><span class="sxs-lookup"><span data-stu-id="c3714-316">These includes the following types:</span></span>

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

### <a name="differences-in-serializers"></a><span data-ttu-id="c3714-317">Różnice w serializatorach</span><span class="sxs-lookup"><span data-stu-id="c3714-317">Differences in serializers</span></span>

<span data-ttu-id="c3714-318">Następujące różnice dotyczą serializacji i deserializacji z <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>i <xref:System.Xml.Serialization.XmlSerializer> klasami:</span><span class="sxs-lookup"><span data-stu-id="c3714-318">The following differences concern serialization and deserialization with the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes:</span></span>

- <span data-ttu-id="c3714-319">W .NET <xref:System.Runtime.Serialization.DataContractSerializer> Native <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> i nie można serializować lub deserialize klasy pochodnej, która ma element członkowski klasy podstawowej, którego typ nie jest głównym typem serializacji.</span><span class="sxs-lookup"><span data-stu-id="c3714-319">In .NET Native, <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize or deserialize a derived class that has a base class member whose type isn't a root serialization type.</span></span> <span data-ttu-id="c3714-320">Na przykład w poniższym kodzie próba serializacji `Y` lub deserializacji powoduje błąd:</span><span class="sxs-lookup"><span data-stu-id="c3714-320">For example, in the following code, trying to serialize or deserialize `Y` results in an error:</span></span>

  [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]

  <span data-ttu-id="c3714-321">Typ `InnerType` nie jest znany serializatorowi, ponieważ członkowie klasy podstawowej nie są przemierzane podczas serializacji.</span><span class="sxs-lookup"><span data-stu-id="c3714-321">Type `InnerType` isn't known to the serializer, because the members of the base class aren't traversed during serialization.</span></span>

- <span data-ttu-id="c3714-322"><xref:System.Runtime.Serialization.DataContractSerializer>i <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nie można serializować klasy lub <xref:System.Collections.Generic.IEnumerable%601> struktury, która implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="c3714-322"><xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize a class or structure that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="c3714-323">Na przykład następujące typy nie można serializować lub deserialize:</span><span class="sxs-lookup"><span data-stu-id="c3714-323">For example, the following types fail to serialize or deserialize:</span></span>

- <span data-ttu-id="c3714-324"><xref:System.Xml.Serialization.XmlSerializer>nie można serializować następującą wartość obiektu, ponieważ nie zna dokładnego typu obiektu, który ma być serializowany:</span><span class="sxs-lookup"><span data-stu-id="c3714-324"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize the following object value, because it doesn't know the exact type of the object to be serialized:</span></span>

- <span data-ttu-id="c3714-325"><xref:System.Xml.Serialization.XmlSerializer>nie powiedzie się serializacji lub deserializacji, <xref:System.Xml.XmlQualifiedName>jeśli typem obiektu serializowanego jest .</span><span class="sxs-lookup"><span data-stu-id="c3714-325"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize or deserialize if the type of the serialized object is <xref:System.Xml.XmlQualifiedName>.</span></span>

- <span data-ttu-id="c3714-326">Wszystkie serializatory<xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>( <xref:System.Xml.Serialization.XmlSerializer>, , i ) nie <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> generują kodu serializacji dla typu lub typu, który zawiera <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="c3714-326">All serializers (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer>) fail to generate serialization code for type <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> or for a type that contains <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="c3714-327">Zamiast tego wyświetlają błędy czasu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c3714-327">They display build-time errors instead.</span></span>

- <span data-ttu-id="c3714-328">Następujące konstruktory typów serializacji nie są gwarantowane do pracy zgodnie z oczekiwaniami:</span><span class="sxs-lookup"><span data-stu-id="c3714-328">The following constructors of the serialization types aren't guaranteed to work as expected:</span></span>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.DataContractSerializerSettings%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Xml.XmlDictionaryString%2CSystem.Xml.XmlDictionaryString%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.Json.DataContractJsonSerializerSettings%29>

  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.String%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlRootAttribute%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%2CSystem.Type%5B%5D%2CSystem.Xml.Serialization.XmlRootAttribute%2CSystem.String%29>

- <span data-ttu-id="c3714-329"><xref:System.Xml.Serialization.XmlSerializer>nie można wygenerować kodu dla typu, który ma metody przypisane z dowolnym z następujących atrybutów:</span><span class="sxs-lookup"><span data-stu-id="c3714-329"><xref:System.Xml.Serialization.XmlSerializer> fails to generate code for a type that has methods attributed with any of the following attributes:</span></span>

  - <xref:System.Runtime.Serialization.OnSerializingAttribute>

  - <xref:System.Runtime.Serialization.OnSerializedAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializingAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializedAttribute>

- <span data-ttu-id="c3714-330"><xref:System.Xml.Serialization.XmlSerializer>nie honoruje <xref:System.Xml.Serialization.IXmlSerializable> niestandardowego interfejsu serializacji.</span><span class="sxs-lookup"><span data-stu-id="c3714-330"><xref:System.Xml.Serialization.XmlSerializer> doesn't honor the <xref:System.Xml.Serialization.IXmlSerializable> custom serialization interface.</span></span> <span data-ttu-id="c3714-331">Jeśli masz klasę, która implementuje <xref:System.Xml.Serialization.XmlSerializer> ten interfejs, uważa typ zwykły stary obiekt CLR (POCO) typu i serializuje tylko jego właściwości publicznych.</span><span class="sxs-lookup"><span data-stu-id="c3714-331">If you have a class that implements this interface, <xref:System.Xml.Serialization.XmlSerializer> considers the type a plain old CLR object (POCO) type and serializes only its public properties.</span></span>

- <span data-ttu-id="c3714-332">Serializacja zwykłego <xref:System.Exception> obiektu nie działa <xref:System.Runtime.Serialization.DataContractSerializer> dobrze <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>i .</span><span class="sxs-lookup"><span data-stu-id="c3714-332">Serializing a plain <xref:System.Exception> object doesn't work well with <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

<a name="VS"></a>

## <a name="visual-studio-differences"></a><span data-ttu-id="c3714-333">Różnice w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c3714-333">Visual Studio differences</span></span>

<span data-ttu-id="c3714-334">**Wyjątki i debugowanie**</span><span class="sxs-lookup"><span data-stu-id="c3714-334">**Exceptions and debugging**</span></span>

<span data-ttu-id="c3714-335">Podczas uruchamiania aplikacji skompilowanych przy użyciu platformy .NET Native w debugerze wyjątki pierwszej szansy są włączone dla następujących typów wyjątków:</span><span class="sxs-lookup"><span data-stu-id="c3714-335">When you're running apps compiled by using .NET Native in the debugger, first-chance exceptions are enabled for the following exception types:</span></span>

- <xref:System.MemberAccessException>

- <xref:System.TypeAccessException>

<span data-ttu-id="c3714-336">**Tworzenie aplikacji**</span><span class="sxs-lookup"><span data-stu-id="c3714-336">**Building apps**</span></span>

<span data-ttu-id="c3714-337">Użyj narzędzi kompilacji x86, które są domyślnie używane przez program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c3714-337">Use the x86 build tools that are used by default by Visual Studio.</span></span> <span data-ttu-id="c3714-338">Nie zalecamy używania narzędzi AMD64 MSBuild, które znajdują się w folderze C:\Program Files (x86)\MSBuild\12.0\bin\amd64; mogą one powodować problemy z kompilacją.</span><span class="sxs-lookup"><span data-stu-id="c3714-338">We don't recommend using the AMD64 MSBuild tools, which are found in C:\Program Files (x86)\MSBuild\12.0\bin\amd64; these may create build problems.</span></span>

<span data-ttu-id="c3714-339">**Profilowania**</span><span class="sxs-lookup"><span data-stu-id="c3714-339">**Profilers**</span></span>

- <span data-ttu-id="c3714-340">Profiler procesora CPU visual studio i profiler pamięci XAML nie są wyświetlane just-my-code poprawnie.</span><span class="sxs-lookup"><span data-stu-id="c3714-340">The Visual Studio CPU Profiler and XAML Memory Profiler don't display Just-My-Code correctly.</span></span>

- <span data-ttu-id="c3714-341">Profiler pamięci XAML nie dokładnie wyświetla dane zarządzanego sterty.</span><span class="sxs-lookup"><span data-stu-id="c3714-341">The XAML Memory Profiler doesn't accurately display managed heap data.</span></span>

- <span data-ttu-id="c3714-342">Profiler procesora CPU nie poprawnie zidentyfikować moduły i wyświetla nazwy funkcji z prefiksem.</span><span class="sxs-lookup"><span data-stu-id="c3714-342">The CPU Profiler doesn't correctly identify modules, and displays prefixed function names.</span></span>

<span data-ttu-id="c3714-343">**Projekty biblioteki testów jednostkowych**</span><span class="sxs-lookup"><span data-stu-id="c3714-343">**Unit Test Library projects**</span></span>

<span data-ttu-id="c3714-344">Włączenie programu .NET native w bibliotece testów jednostkowych dla projektu aplikacji ze Sklepu Windows nie jest obsługiwane i powoduje, że projekt nie może się zbudować.</span><span class="sxs-lookup"><span data-stu-id="c3714-344">Enabling .NET Native on a Unit Test Library for a Windows Store apps project isn't supported and causes the project to fail to build.</span></span>

## <a name="see-also"></a><span data-ttu-id="c3714-345">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c3714-345">See also</span></span>

- [<span data-ttu-id="c3714-346">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="c3714-346">Getting Started</span></span>](getting-started-with-net-native.md)
- [<span data-ttu-id="c3714-347">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="c3714-347">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="c3714-348">.NET Dla aplikacji ze Sklepu Windows — omówienie</span><span class="sxs-lookup"><span data-stu-id="c3714-348">.NET For Windows Store apps overview</span></span>](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29)
- [<span data-ttu-id="c3714-349">Obsługa programu .NET Framework dla aplikacji ze Sklepu Windows i środowiska wykonawczego systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c3714-349">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)

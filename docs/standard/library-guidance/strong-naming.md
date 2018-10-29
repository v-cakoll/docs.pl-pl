---
title: Silne nazewnictwo i bibliotek platformy .NET
description: Zalecenia dotyczące najlepszych rozwiązań dla silnego nazewnictwa bibliotek platformy .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/16/2018
ms.openlocfilehash: 6f5743c7a8c6fdbdcdcf3aa80d2f92f2e04621f2
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201455"
---
# <a name="strong-naming"></a><span data-ttu-id="5ca6a-103">Silne nazewnictwo</span><span class="sxs-lookup"><span data-stu-id="5ca6a-103">Strong naming</span></span>

<span data-ttu-id="5ca6a-104">Silne nazwy odwołuje się do podpisywania zestawu za pomocą klucza, tworzenie [zestawu z silną nazwą](../../framework/app-domains/strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="5ca6a-104">Strong naming refers to signing an assembly with a key, producing a [strong-named assembly](../../framework/app-domains/strong-named-assemblies.md).</span></span> <span data-ttu-id="5ca6a-105">W przypadku zestawu o silnej nazwie, tworzy unikatową tożsamość na podstawie numeru wersji nazwy i zestawu, a może pomóc zapobiec konfliktom zestawu.</span><span class="sxs-lookup"><span data-stu-id="5ca6a-105">When an assembly is strong-named, it creates a unique identity based on the name and assembly version number, and it can help prevent assembly conflicts.</span></span>

<span data-ttu-id="5ca6a-106">Wadą do silne nazwy jest .NET Framework na Windows umożliwia strict ładowania zestawów, gdy zestaw ma silną nazwę.</span><span class="sxs-lookup"><span data-stu-id="5ca6a-106">The downside to strong naming is that the .NET Framework on Windows enables strict loading of assemblies once an assembly is strong named.</span></span> <span data-ttu-id="5ca6a-107">Odwołanie do zestawu z silną nazwą musi dokładnie odpowiadać wersji odwołuje się zestaw wymuszanie deweloperom [Konfigurowanie przekierowania powiązań](../../framework/configure-apps/redirect-assembly-versions.md) korzystając z zestawu:</span><span class="sxs-lookup"><span data-stu-id="5ca6a-107">A strong-named assembly reference must exactly match the version referenced by an assembly, forcing developers to [configure binding redirects](../../framework/configure-apps/redirect-assembly-versions.md) when using the assembly:</span></span>

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
         <dependentAssembly>
            <assemblyIdentity name="myAssembly" publicKeyToken="32ab4ba45e0a69a1" culture="neutral" />
            <bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0"/>
         </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

<span data-ttu-id="5ca6a-108">W przypadku deweloperów platformy .NET narzekają — silne nazwy, co to są one zazwyczaj skarżących o jest strict ładowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="5ca6a-108">When .NET developers complain about strong naming, what they're usually complaining about is strict assembly loading.</span></span> <span data-ttu-id="5ca6a-109">Na szczęście tego problemu jest izolowane do programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5ca6a-109">Fortunately, this issue is isolated to the .NET Framework.</span></span> <span data-ttu-id="5ca6a-110">.NET core, Xamarin, platformy uniwersalnej systemu Windows i większości innych implementacji .NET nie mają ściśle z ładowaniem zestawu i usuwa głównego wadą — silne nazwy.</span><span class="sxs-lookup"><span data-stu-id="5ca6a-110">.NET Core, Xamarin, UWP, and most other .NET implementations don't have strict assembly loading and removes the main downside of strong naming.</span></span>

<span data-ttu-id="5ca6a-111">Ważnym aspektem — silne nazwy jest wirusowe: silna o nazwie zestawu mogą odwoływać się tylko inne silne nazwanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="5ca6a-111">One important aspect of strong naming is that it's viral: a strong named assembly can only reference other strong named assemblies.</span></span> <span data-ttu-id="5ca6a-112">Jeśli biblioteka nie jest silne o nazwie, zostały wykluczone deweloperzy, którzy tworzą aplikację lub bibliotekę, która potrzebuje — silne nazwy korzystanie z niego.</span><span class="sxs-lookup"><span data-stu-id="5ca6a-112">If your library isn't strong named, then you have excluded developers who are building an application or library that needs strong naming from using it.</span></span>

<span data-ttu-id="5ca6a-113">Zalety — silne nazwy to:</span><span class="sxs-lookup"><span data-stu-id="5ca6a-113">The benefits of strong naming are:</span></span>

1. <span data-ttu-id="5ca6a-114">Zestaw można odwołanie i używany przez inne zestawy o silnych nazwach.</span><span class="sxs-lookup"><span data-stu-id="5ca6a-114">The assembly can be referenced and used by other strong-named assemblies.</span></span>
2. <span data-ttu-id="5ca6a-115">Zestaw mogą być przechowywane w globalnej pamięci podręcznej zestawów (GAC).</span><span class="sxs-lookup"><span data-stu-id="5ca6a-115">The assembly can be stored in the Global Assembly Cache (GAC).</span></span>
3. <span data-ttu-id="5ca6a-116">Zestaw można załadować równolegle z innymi wersjami zestawu.</span><span class="sxs-lookup"><span data-stu-id="5ca6a-116">The assembly can be loaded side by side with other versions of the assembly.</span></span> <span data-ttu-id="5ca6a-117">Ładowanie zestawu Side-by-side często jest wymagane przez aplikacje za pomocą wtyczki architektury.</span><span class="sxs-lookup"><span data-stu-id="5ca6a-117">Side-by-side assembly loading is commonly required by applications with plug-in architectures.</span></span>

## <a name="create-strong-named-net-libraries"></a><span data-ttu-id="5ca6a-118">Utwórz silne o nazwie bibliotek platformy .NET</span><span class="sxs-lookup"><span data-stu-id="5ca6a-118">Create strong named .NET libraries</span></span>

<span data-ttu-id="5ca6a-119">Strong należy nadać nazwę bibliotek .NET typu open source.</span><span class="sxs-lookup"><span data-stu-id="5ca6a-119">You should strong name your open-source .NET libraries.</span></span> <span data-ttu-id="5ca6a-120">Silne nazewnictwo zestawu zapewnia większość użytkowników będzie można jej używać, i tylko z ładowaniem zestawu, ograniczeniami ma wpływ na .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5ca6a-120">Strong naming an assembly ensures the most people can use it, and strict assembly loading only affects the .NET Framework.</span></span>

> [!NOTE]
> <span data-ttu-id="5ca6a-121">Niniejsze wskazówki dotyczy publicznie rozpowszechniane bibliotek .NET, takich jak biblioteki .NET opublikowane w witrynie NuGet.org. Silne nazwy nie jest wymagane przez większość aplikacji .NET i nie należy wykonywać domyślnie.</span><span class="sxs-lookup"><span data-stu-id="5ca6a-121">This guidance is specific to publicly distributed .NET libraries, such as .NET libraries published on NuGet.org. Strong naming is not required by most .NET applications and should not be done by default.</span></span>

<span data-ttu-id="5ca6a-122">**ROZWAŻ ✔️** silnych nazw zestawów biblioteki.</span><span class="sxs-lookup"><span data-stu-id="5ca6a-122">**✔️ CONSIDER** strong naming your library's assemblies.</span></span>

<span data-ttu-id="5ca6a-123">**ROZWAŻ ✔️** Dodawanie silnych nazw klucz do systemu kontroli źródła.</span><span class="sxs-lookup"><span data-stu-id="5ca6a-123">**✔️ CONSIDER** adding the strong naming key to your source control system.</span></span>

> <span data-ttu-id="5ca6a-124">Publicznie dostępne klucz umożliwia deweloperom zmodyfikować i ponownie skompilować kod źródłowy biblioteki za pomocą tego samego klucza.</span><span class="sxs-lookup"><span data-stu-id="5ca6a-124">A publicly available key lets developers modify and recompile your library source code with the same key.</span></span>
> 
> <span data-ttu-id="5ca6a-125">Nie należy wprowadzeniu silnych nazw klucz publiczny, jeśli został on użyty w przeszłości do nadania uprawnienia specjalne w [scenariuszy częściowego zaufania](/dotnet/framework/misc/using-libraries-from-partially-trusted-code).</span><span class="sxs-lookup"><span data-stu-id="5ca6a-125">You shouldn't make the strong naming key public if it has been used in the past to give special permissions in [partial-trust scenarios](/dotnet/framework/misc/using-libraries-from-partially-trusted-code).</span></span> <span data-ttu-id="5ca6a-126">W przeciwnym razie może spowodować naruszenie istniejących środowisk.</span><span class="sxs-lookup"><span data-stu-id="5ca6a-126">Otherwise, you might compromise existing environments.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5ca6a-127">Gdy tożsamość wydawcy kodu, [Authenticode](/windows-hardware/drivers/install/authenticode) i [podpisywanie pakietów NuGet](/nuget/create-packages/sign-a-package) są zalecane.</span><span class="sxs-lookup"><span data-stu-id="5ca6a-127">When the identity of the publisher of the code is desired, [Authenticode](/windows-hardware/drivers/install/authenticode) and [NuGet Package Signing](/nuget/create-packages/sign-a-package) are recommended.</span></span> <span data-ttu-id="5ca6a-128">Zabezpieczeń dostępu kodu (CAS) nie powinien służyć jako ograniczenia zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5ca6a-128">Code Access Security (CAS) should not be used as a security mitigation.</span></span>

<span data-ttu-id="5ca6a-129">**ROZWAŻ ✔️** zwiększanie wersji zestawu na zmiany wersji jedyny duży, aby ułatwić użytkownikom zmniejszenie przekierowania powiązań i jak często są aktualizowane.</span><span class="sxs-lookup"><span data-stu-id="5ca6a-129">**✔️ CONSIDER** incrementing the assembly version on only major version changes to help users reduce binding redirects, and how often they're updated.</span></span>

> <span data-ttu-id="5ca6a-130">Przeczytaj więcej na temat [przechowywanie wersji i wersję zestawu](./versioning.md#assembly-version).</span><span class="sxs-lookup"><span data-stu-id="5ca6a-130">Read more about [versioning and the assembly version](./versioning.md#assembly-version).</span></span>

<span data-ttu-id="5ca6a-131">**❌ NIE** dodać, usunąć lub zmienić silnego klucza nazewnictwa.</span><span class="sxs-lookup"><span data-stu-id="5ca6a-131">**❌ DO NOT** add, remove, or change the strong naming key.</span></span>

> <span data-ttu-id="5ca6a-132">Modyfikowanie zestawu silnego nazewnictwa klucza tożsamości zestawu zmian i przerywa skompilowany kod, który korzysta z niego.</span><span class="sxs-lookup"><span data-stu-id="5ca6a-132">Modifying an assembly's strong naming key changes the assembly's identity and breaks compiled code that uses it.</span></span> <span data-ttu-id="5ca6a-133">Aby uzyskać więcej informacji, zobacz [binarne istotne zmiany w](./breaking-changes.md#binary-breaking-change).</span><span class="sxs-lookup"><span data-stu-id="5ca6a-133">For more information, see [binary breaking changes](./breaking-changes.md#binary-breaking-change).</span></span>

<span data-ttu-id="5ca6a-134">**❌ NIE** publikowanie o silnych nazwach i innych niż-o silnej nazwie wersji biblioteki.</span><span class="sxs-lookup"><span data-stu-id="5ca6a-134">**❌ DO NOT** publish strong-named and non-strong-named versions of your library.</span></span> <span data-ttu-id="5ca6a-135">Na przykład `Contoso.Api` i `Contoso.Api.StrongNamed`.</span><span class="sxs-lookup"><span data-stu-id="5ca6a-135">For example, `Contoso.Api` and `Contoso.Api.StrongNamed`.</span></span>

> <span data-ttu-id="5ca6a-136">Publikowanie oba pakiety rozwidlenia ekosystemu usługi dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="5ca6a-136">Publishing two packages forks your developer eco-system.</span></span> <span data-ttu-id="5ca6a-137">Ponadto jeśli aplikacji, kończy się w zależności od tego, oba pakiety Deweloper mogą wystąpić konflikty nazw typu.</span><span class="sxs-lookup"><span data-stu-id="5ca6a-137">Also, if an application ends up depending on both packages the developer can encounter type name conflicts.</span></span> <span data-ttu-id="5ca6a-138">Chodzi .NET jest są różnych typów w różnych zestawach.</span><span class="sxs-lookup"><span data-stu-id="5ca6a-138">As far as .NET is concerned they are different types in different assemblies.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="5ca6a-139">[Poprzednie](./cross-platform-targeting.md)
[dalej](./nuget.md)</span><span class="sxs-lookup"><span data-stu-id="5ca6a-139">[Previous](./cross-platform-targeting.md)
[Next](./nuget.md)</span></span>

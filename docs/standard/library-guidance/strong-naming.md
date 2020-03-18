---
title: Silne nazewnictwo i biblioteki .NET
description: Najlepsze zalecenia dotyczące silnego nazewnictwa bibliotek .NET.
ms.date: 10/16/2018
ms.openlocfilehash: db268093b07a2ece7cdb8329fd789b52da9c5c32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "76744538"
---
# <a name="strong-naming"></a><span data-ttu-id="5dfa9-103">Silne nazewnictwo</span><span class="sxs-lookup"><span data-stu-id="5dfa9-103">Strong naming</span></span>

<span data-ttu-id="5dfa9-104">Silne nazewnictwo odnosi się do podpisywania zestawu za pomocą klucza, tworząc [zestaw o silnej nazwie](../assembly/strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="5dfa9-104">Strong naming refers to signing an assembly with a key, producing a [strong-named assembly](../assembly/strong-named.md).</span></span> <span data-ttu-id="5dfa9-105">Gdy zestaw ma silną nazwę, tworzy unikatową tożsamość na podstawie numeru wersji nazwy i zestawu i może pomóc w zapobieganiu konfliktom zestawów.</span><span class="sxs-lookup"><span data-stu-id="5dfa9-105">When an assembly is strong-named, it creates a unique identity based on the name and assembly version number, and it can help prevent assembly conflicts.</span></span>

<span data-ttu-id="5dfa9-106">Wadą silnego nazewnictwa jest to, że .NET Framework w systemie Windows umożliwia ścisłe ładowanie zestawów, gdy zestaw jest silny.</span><span class="sxs-lookup"><span data-stu-id="5dfa9-106">The downside to strong naming is that the .NET Framework on Windows enables strict loading of assemblies once an assembly is strong named.</span></span> <span data-ttu-id="5dfa9-107">Odwołanie do zestawu o silnej nazwie musi dokładnie odpowiadać wersji, do której odwołuje się zestaw, zmuszając deweloperów do [konfigurowania przekierowań wiązania](../../framework/configure-apps/redirect-assembly-versions.md) podczas korzystania z zestawu:</span><span class="sxs-lookup"><span data-stu-id="5dfa9-107">A strong-named assembly reference must exactly match the version referenced by an assembly, forcing developers to [configure binding redirects](../../framework/configure-apps/redirect-assembly-versions.md) when using the assembly:</span></span>

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

<span data-ttu-id="5dfa9-108">Gdy deweloperzy .NET skarżą się na silne nazewnictwa, co oni zwykle narzekają jest ścisłe ładowanie zestawu.</span><span class="sxs-lookup"><span data-stu-id="5dfa9-108">When .NET developers complain about strong naming, what they're usually complaining about is strict assembly loading.</span></span> <span data-ttu-id="5dfa9-109">Na szczęście ten problem jest izolowany do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5dfa9-109">Fortunately, this issue is isolated to the .NET Framework.</span></span> <span data-ttu-id="5dfa9-110">.NET Core, Xamarin, UWP i większość innych implementacji .NET nie mają ścisłego ładowania zestawu i usuwa główną wadę silnego nazewnictwa.</span><span class="sxs-lookup"><span data-stu-id="5dfa9-110">.NET Core, Xamarin, UWP, and most other .NET implementations don't have strict assembly loading and removes the main downside of strong naming.</span></span>

<span data-ttu-id="5dfa9-111">Jednym z ważnych aspektów silnego nazewnictwa jest to, że jest wirusowy: silny nazwany zestaw może odwoływać się tylko do innych silnych zespołów o nazwie.</span><span class="sxs-lookup"><span data-stu-id="5dfa9-111">One important aspect of strong naming is that it's viral: a strong named assembly can only reference other strong named assemblies.</span></span> <span data-ttu-id="5dfa9-112">Jeśli biblioteka nie jest silna nazwa, a następnie zostały wykluczone deweloperzy, którzy budują aplikację lub bibliotekę, która wymaga silnego nazewnictwa z niego używać.</span><span class="sxs-lookup"><span data-stu-id="5dfa9-112">If your library isn't strong named, then you have excluded developers who are building an application or library that needs strong naming from using it.</span></span>

<span data-ttu-id="5dfa9-113">Korzyści z silnego nazewnictwa są:</span><span class="sxs-lookup"><span data-stu-id="5dfa9-113">The benefits of strong naming are:</span></span>

1. <span data-ttu-id="5dfa9-114">Do zestawu można odwoływać się i używać innych zestawów o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="5dfa9-114">The assembly can be referenced and used by other strong-named assemblies.</span></span>
2. <span data-ttu-id="5dfa9-115">Zestaw może być przechowywany w globalnej pamięci podręcznej zestawów (GAC).</span><span class="sxs-lookup"><span data-stu-id="5dfa9-115">The assembly can be stored in the Global Assembly Cache (GAC).</span></span>
3. <span data-ttu-id="5dfa9-116">Zespół może być ładowany obok siebie z innymi wersjami złożenia.</span><span class="sxs-lookup"><span data-stu-id="5dfa9-116">The assembly can be loaded side by side with other versions of the assembly.</span></span> <span data-ttu-id="5dfa9-117">Ładowanie zestawu side-by-side jest często wymagane przez aplikacje z architekturami dodatków plug-in.</span><span class="sxs-lookup"><span data-stu-id="5dfa9-117">Side-by-side assembly loading is commonly required by applications with plug-in architectures.</span></span>

## <a name="create-strong-named-net-libraries"></a><span data-ttu-id="5dfa9-118">Tworzenie silnych nazwanych bibliotek .NET</span><span class="sxs-lookup"><span data-stu-id="5dfa9-118">Create strong named .NET libraries</span></span>

<span data-ttu-id="5dfa9-119">Należy silnej nazwy bibliotek .NET typu open source.</span><span class="sxs-lookup"><span data-stu-id="5dfa9-119">You should strong name your open-source .NET libraries.</span></span> <span data-ttu-id="5dfa9-120">Silne nazewnictwo zestawu zapewnia, że większość osób może go używać, a ścisłe ładowanie zestawu dotyczy tylko .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5dfa9-120">Strong naming an assembly ensures the most people can use it, and strict assembly loading only affects the .NET Framework.</span></span>

> [!NOTE]
> <span data-ttu-id="5dfa9-121">Te wskazówki są specyficzne dla publicznie rozpowszechnianych bibliotek .NET, takich jak biblioteki .NET opublikowane w NuGet.org. Silne nazewnictwo nie jest wymagane przez większość aplikacji .NET i nie powinno być wykonywane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="5dfa9-121">This guidance is specific to publicly distributed .NET libraries, such as .NET libraries published on NuGet.org. Strong naming is not required by most .NET applications and should not be done by default.</span></span>

<span data-ttu-id="5dfa9-122">✔️ ROZWAŻ silne nazewnictwo zestawów biblioteki.</span><span class="sxs-lookup"><span data-stu-id="5dfa9-122">✔️ CONSIDER strong naming your library's assemblies.</span></span>

<span data-ttu-id="5dfa9-123">✔️ ROZWAŻ dodanie silnego klucza nazewnictwa do systemu kontroli źródła.</span><span class="sxs-lookup"><span data-stu-id="5dfa9-123">✔️ CONSIDER adding the strong naming key to your source control system.</span></span>

> <span data-ttu-id="5dfa9-124">Publicznie dostępny klucz umożliwia deweloperom modyfikowanie i ponowne kompilowanie kodu źródłowego biblioteki przy tym samym kluczu.</span><span class="sxs-lookup"><span data-stu-id="5dfa9-124">A publicly available key lets developers modify and recompile your library source code with the same key.</span></span>
>
> <span data-ttu-id="5dfa9-125">Nie należy upubliczniać silnego klucza nazewnictwa, jeśli był on używany w przeszłości do nadawania specjalnych uprawnień w [scenariuszach częściowego zaufania.](../../framework/misc/using-libraries-from-partially-trusted-code.md)</span><span class="sxs-lookup"><span data-stu-id="5dfa9-125">You shouldn't make the strong naming key public if it has been used in the past to give special permissions in [partial-trust scenarios](../../framework/misc/using-libraries-from-partially-trusted-code.md).</span></span> <span data-ttu-id="5dfa9-126">W przeciwnym razie może naruszyć istniejące środowiska.</span><span class="sxs-lookup"><span data-stu-id="5dfa9-126">Otherwise, you might compromise existing environments.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5dfa9-127">Gdy tożsamość wydawcy kodu jest zalecane [Authenticode](/windows-hardware/drivers/install/authenticode) i [NuGet Podpisywania pakietu](/nuget/create-packages/sign-a-package) są zalecane.</span><span class="sxs-lookup"><span data-stu-id="5dfa9-127">When the identity of the publisher of the code is desired, [Authenticode](/windows-hardware/drivers/install/authenticode) and [NuGet Package Signing](/nuget/create-packages/sign-a-package) are recommended.</span></span> <span data-ttu-id="5dfa9-128">Zabezpieczenia dostępu do kodu (CAS) nie powinny być używane jako środki zaradcze zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5dfa9-128">Code Access Security (CAS) should not be used as a security mitigation.</span></span>

<span data-ttu-id="5dfa9-129">✔️ ZAStanów się nad zwiększaniem wersji zestawu tylko na głównych zmianach wersji, aby pomóc użytkownikom zmniejszyć przekierowanie powiązania i jak często są one aktualizowane.</span><span class="sxs-lookup"><span data-stu-id="5dfa9-129">✔️ CONSIDER incrementing the assembly version on only major version changes to help users reduce binding redirects, and how often they're updated.</span></span>

> <span data-ttu-id="5dfa9-130">Przeczytaj więcej o [wersji i wersji zestawu](./versioning.md#assembly-version).</span><span class="sxs-lookup"><span data-stu-id="5dfa9-130">Read more about [versioning and the assembly version](./versioning.md#assembly-version).</span></span>

<span data-ttu-id="5dfa9-131">❌NIE dodawaj, NIE usuwaj ani nie zmieniaj silnego klucza nazewnictwa.</span><span class="sxs-lookup"><span data-stu-id="5dfa9-131">❌ DO NOT add, remove, or change the strong naming key.</span></span>

> <span data-ttu-id="5dfa9-132">Modyfikowanie silnego klucza nazewnictwa zestawu zmienia tożsamość zestawu i przerywa skompilowany kod, który go używa.</span><span class="sxs-lookup"><span data-stu-id="5dfa9-132">Modifying an assembly's strong naming key changes the assembly's identity and breaks compiled code that uses it.</span></span> <span data-ttu-id="5dfa9-133">Aby uzyskać więcej informacji, zobacz [zmiany łamania zasad binarnych](./breaking-changes.md#binary-breaking-change).</span><span class="sxs-lookup"><span data-stu-id="5dfa9-133">For more information, see [binary breaking changes](./breaking-changes.md#binary-breaking-change).</span></span>

<span data-ttu-id="5dfa9-134">❌NIE publikuj wersji biblioteki o silnej nazwie i nieo silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="5dfa9-134">❌ DO NOT publish strong-named and non-strong-named versions of your library.</span></span> <span data-ttu-id="5dfa9-135">Na przykład `Contoso.Api` `Contoso.Api.StrongNamed`i .</span><span class="sxs-lookup"><span data-stu-id="5dfa9-135">For example, `Contoso.Api` and `Contoso.Api.StrongNamed`.</span></span>

> <span data-ttu-id="5dfa9-136">Publikowanie dwóch pakietów rozwidliwek e-systemu deweloperskiego.</span><span class="sxs-lookup"><span data-stu-id="5dfa9-136">Publishing two packages forks your developer eco-system.</span></span> <span data-ttu-id="5dfa9-137">Ponadto jeśli aplikacja kończy się w zależności od obu pakietów deweloper może napotkać konflikty nazw typów.</span><span class="sxs-lookup"><span data-stu-id="5dfa9-137">Also, if an application ends up depending on both packages the developer can encounter type name conflicts.</span></span> <span data-ttu-id="5dfa9-138">Jeśli chodzi o .NET dotyczy są różne typy w różnych zestawach.</span><span class="sxs-lookup"><span data-stu-id="5dfa9-138">As far as .NET is concerned they are different types in different assemblies.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5dfa9-139">[Poprzedni](cross-platform-targeting.md)
>[następny](nuget.md)</span><span class="sxs-lookup"><span data-stu-id="5dfa9-139">[Previous](cross-platform-targeting.md)
[Next](nuget.md)</span></span>

---
title: Wskazówki dotyczące biblioteki .NET Open Source
description: Zalecenia dotyczące najlepszych rozwiązań dla deweloperów do tworzenia bibliotek platformy .NET o wysokiej jakości.
author: jamesnk
ms.author: mairaw
ms.date: 10/17/2018
ms.openlocfilehash: eff6c822757af6fb85622e88714accd40c32bcf5
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928963"
---
# <a name="open-source-library-guidance"></a><span data-ttu-id="e9fb8-103">Wskazówki dotyczące biblioteki typu open-source</span><span class="sxs-lookup"><span data-stu-id="e9fb8-103">Open-source library guidance</span></span>

<span data-ttu-id="e9fb8-104">Te wskazówki zawierają zalecenia dla deweloperów umożliwiające tworzenie bibliotek platformy .NET o wysokiej jakości.</span><span class="sxs-lookup"><span data-stu-id="e9fb8-104">This guidance provides recommendations for developers to create high-quality .NET libraries.</span></span> <span data-ttu-id="e9fb8-105">Ta dokumentacja koncentruje się na tym, *co* i *dlaczego* podczas kompilowania biblioteki .NET, a nie w *sposób*.</span><span class="sxs-lookup"><span data-stu-id="e9fb8-105">This documentation focuses on the *what* and the *why* when building a .NET library, not the *how*.</span></span>

<span data-ttu-id="e9fb8-106">Aspekty wysokiej jakości bibliotek .NET typu open source:</span><span class="sxs-lookup"><span data-stu-id="e9fb8-106">Aspects of high-quality open-source .NET libraries:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="e9fb8-107">**Włączne** — dobre biblioteki .NET dążą do obsługi wielu platform, języków programowania i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e9fb8-107">**Inclusive** - Good .NET libraries strive to support many platforms, programming languages, and applications.</span></span>
> * <span data-ttu-id="e9fb8-108">**Stabilne** i dobre biblioteki platformy .NET współdziałają w ekosystemie platformy .NET, działając w aplikacjach skompilowanych z wieloma bibliotekami.</span><span class="sxs-lookup"><span data-stu-id="e9fb8-108">**Stable** - Good .NET libraries coexist in the .NET ecosystem, running in applications built with many libraries.</span></span>
> * <span data-ttu-id="e9fb8-109">**Zaprojektowana do** rozdzielania bibliotek platformy .NET powinna być ulepszana i zwiększana wraz z upływem czasu obsługi istniejących użytkowników.</span><span class="sxs-lookup"><span data-stu-id="e9fb8-109">**Designed to evolve** - .NET libraries should improve and evolve over time, while supporting existing users.</span></span>
> * <span data-ttu-id="e9fb8-110">**Możliwością debugowania** — biblioteki platformy .NET powinny używać najnowszych narzędzi do tworzenia doskonałego środowiska debugowania dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="e9fb8-110">**Debuggable** - .NET libraries should use the latest tools to create a great debugging experience for users.</span></span>
> * <span data-ttu-id="e9fb8-111">Biblioteki **Zaufane** — .NET mają zaufanie deweloperów, publikując w NuGet przy użyciu najlepszych rozwiązań w zakresie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="e9fb8-111">**Trusted** - .NET libraries have developers' trust by publishing to NuGet using security best practices.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e9fb8-112">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="e9fb8-112">Get Started</span></span>](./get-started.md)

## <a name="types-of-recommendations"></a><span data-ttu-id="e9fb8-113">Typy zaleceń</span><span class="sxs-lookup"><span data-stu-id="e9fb8-113">Types of recommendations</span></span>

<span data-ttu-id="e9fb8-114">W każdym artykule przedstawiono cztery typy zaleceń: **Należy** **rozważyć**, **unikać**i **nie**.</span><span class="sxs-lookup"><span data-stu-id="e9fb8-114">Each article presents four types of recommendations: **Do**, **Consider**, **Avoid**, and **Do not**.</span></span> <span data-ttu-id="e9fb8-115">Typ zalecenia wskazuje, jak silnie należy postępować.</span><span class="sxs-lookup"><span data-stu-id="e9fb8-115">The type of recommendation indicates how strongly it should be followed.</span></span>

<span data-ttu-id="e9fb8-116">Prawie zawsze należy **przestrzegać zalecenia.**</span><span class="sxs-lookup"><span data-stu-id="e9fb8-116">You should almost always follow a **Do** recommendation.</span></span> <span data-ttu-id="e9fb8-117">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e9fb8-117">For example:</span></span>

<span data-ttu-id="e9fb8-118">**✔️** Przeprowadź dystrybucję biblioteki przy użyciu pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="e9fb8-118">**✔️ DO** distribute your library using a NuGet package.</span></span>

<span data-ttu-id="e9fb8-119">Z drugiej strony należy **wziąć pod uwagę** zalecenia, które powinny być przestrzegane, ale istnieją uzasadnione wyjątki wobec reguły i nie należy mieć żadnego nieprzestrzegania wskazówek:</span><span class="sxs-lookup"><span data-stu-id="e9fb8-119">On the other hand, **Consider** recommendations should generally be followed, but there are legitimate exceptions to the rule and you shouldn't feel bad about not following the guidance:</span></span>

<span data-ttu-id="e9fb8-120">**✔️ rozważyć** użycie programu [SemVer 2.0.0](https://semver.org/) w celu uzyskania wersji pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="e9fb8-120">**✔️ CONSIDER** using [SemVer 2.0.0](https://semver.org/) to version your NuGet package.</span></span>

<span data-ttu-id="e9fb8-121">**Należy unikać występowania** zaleceń, które zwykle nie są dobrym pomysłem, ale przerwanie reguły czasami ma sens:</span><span class="sxs-lookup"><span data-stu-id="e9fb8-121">**Avoid** recommendations mention things that are generally not a good idea, but breaking the rule sometimes makes sense:</span></span>

<span data-ttu-id="e9fb8-122">**❌ Unikać** Odwołania do pakietu NuGet, które wymagają dokładnej wersji.</span><span class="sxs-lookup"><span data-stu-id="e9fb8-122">**❌ AVOID** NuGet package references that demand an exact version.</span></span>

<span data-ttu-id="e9fb8-123">A wreszcie **nie są** zalecenia wskazują coś, co należy prawie nigdy nie robić:</span><span class="sxs-lookup"><span data-stu-id="e9fb8-123">And finally, **Do not** recommendations indicate something you should almost never do:</span></span>

<span data-ttu-id="e9fb8-124">**❌** Nie publikować wersji z silną nazwą i niesilną nazwą biblioteki.</span><span class="sxs-lookup"><span data-stu-id="e9fb8-124">**❌ DO NOT** publish strong-named and non-strong-named versions of your library.</span></span> <span data-ttu-id="e9fb8-125">Na przykład `Contoso.Api` i `Contoso.Api.StrongNamed`.</span><span class="sxs-lookup"><span data-stu-id="e9fb8-125">For example, `Contoso.Api` and `Contoso.Api.StrongNamed`.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="e9fb8-126">Next</span><span class="sxs-lookup"><span data-stu-id="e9fb8-126">Next</span></span>](get-started.md)

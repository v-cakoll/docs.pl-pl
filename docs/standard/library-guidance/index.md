---
title: Wskazówki dotyczące biblioteki .NET typu open source
description: Najlepsze zalecenia dla deweloperów do tworzenia bibliotek .NET wysokiej jakości.
ms.date: 10/17/2018
ms.openlocfilehash: 4c76dfae6ffc39df7f15381be64e33657067d79d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "76731422"
---
# <a name="open-source-library-guidance"></a><span data-ttu-id="f7be5-103">Wskazówki dotyczące biblioteki typu open-source</span><span class="sxs-lookup"><span data-stu-id="f7be5-103">Open-source library guidance</span></span>

<span data-ttu-id="f7be5-104">Te wskazówki zawierają zalecenia dla deweloperów do tworzenia wysokiej jakości bibliotek .NET.</span><span class="sxs-lookup"><span data-stu-id="f7be5-104">This guidance provides recommendations for developers to create high-quality .NET libraries.</span></span> <span data-ttu-id="f7be5-105">Ta dokumentacja koncentruje się na *co* i *dlaczego* podczas tworzenia biblioteki .NET, a nie *jak*.</span><span class="sxs-lookup"><span data-stu-id="f7be5-105">This documentation focuses on the *what* and the *why* when building a .NET library, not the *how*.</span></span>

<span data-ttu-id="f7be5-106">Aspekty wysokiej jakości bibliotek open source .NET:</span><span class="sxs-lookup"><span data-stu-id="f7be5-106">Aspects of high-quality open-source .NET libraries:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="f7be5-107">**Włącznie —** dobre biblioteki .NET starają się obsługiwać wiele platform, języków programowania i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f7be5-107">**Inclusive** - Good .NET libraries strive to support many platforms, programming languages, and applications.</span></span>
> * <span data-ttu-id="f7be5-108">**Stabilny** — dobre biblioteki .NET współistnieją w ekosystemie .NET, działające w aplikacjach zbudowanych z wielu bibliotek.</span><span class="sxs-lookup"><span data-stu-id="f7be5-108">**Stable** - Good .NET libraries coexist in the .NET ecosystem, running in applications built with many libraries.</span></span>
> * <span data-ttu-id="f7be5-109">**Zaprojektowany do ewolucji** — biblioteki .NET powinny udoskonalać i ewoluować wraz z urazem, jednocześnie obsługując istniejących użytkowników.</span><span class="sxs-lookup"><span data-stu-id="f7be5-109">**Designed to evolve** - .NET libraries should improve and evolve over time, while supporting existing users.</span></span>
> * <span data-ttu-id="f7be5-110">**Debugowanie** — biblioteki .NET powinny używać najnowszych narzędzi do tworzenia doskonałego środowiska debugowania dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="f7be5-110">**Debuggable** - .NET libraries should use the latest tools to create a great debugging experience for users.</span></span>
> * <span data-ttu-id="f7be5-111">**Zaufane** — biblioteki .NET mają zaufanie deweloperów, publikując w NuGet przy użyciu najlepszych rozwiązań w zakresie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="f7be5-111">**Trusted** - .NET libraries have developers' trust by publishing to NuGet using security best practices.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f7be5-112">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f7be5-112">Get Started</span></span>](./get-started.md)

## <a name="types-of-recommendations"></a><span data-ttu-id="f7be5-113">Rodzaje zaleceń</span><span class="sxs-lookup"><span data-stu-id="f7be5-113">Types of recommendations</span></span>

<span data-ttu-id="f7be5-114">Każdy artykuł przedstawia cztery rodzaje zaleceń: **Czy**, **Należy rozważyć**, **Unikać**, i **nie**.</span><span class="sxs-lookup"><span data-stu-id="f7be5-114">Each article presents four types of recommendations: **Do**, **Consider**, **Avoid**, and **Do not**.</span></span> <span data-ttu-id="f7be5-115">Typ zalecenia wskazuje, jak mocno należy go przestrzegać.</span><span class="sxs-lookup"><span data-stu-id="f7be5-115">The type of recommendation indicates how strongly it should be followed.</span></span>

<span data-ttu-id="f7be5-116">Prawie zawsze należy przestrzegać zalecenia **Do.**</span><span class="sxs-lookup"><span data-stu-id="f7be5-116">You should almost always follow a **Do** recommendation.</span></span> <span data-ttu-id="f7be5-117">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f7be5-117">For example:</span></span>

<span data-ttu-id="f7be5-118">✔️ dystrybuują biblioteki przy użyciu pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="f7be5-118">✔️ DO distribute your library using a NuGet package.</span></span>

<span data-ttu-id="f7be5-119">Z drugiej strony **należy wziąć pod uwagę** zalecenia powinny być ogólnie przestrzegane, ale istnieją uzasadnione wyjątki od reguły i nie należy czuć się źle o nie przestrzeganie wskazówek:</span><span class="sxs-lookup"><span data-stu-id="f7be5-119">On the other hand, **Consider** recommendations should generally be followed, but there are legitimate exceptions to the rule and you shouldn't feel bad about not following the guidance:</span></span>

<span data-ttu-id="f7be5-120">✔️ ZASTANÓW SIĘ przy użyciu [SemVer 2.0.0](https://semver.org/) do wersji pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="f7be5-120">✔️ CONSIDER using [SemVer 2.0.0](https://semver.org/) to version your NuGet package.</span></span>

<span data-ttu-id="f7be5-121">**Unikaj** zaleceń wspomnieć rzeczy, które na ogół nie są dobrym pomysłem, ale łamanie reguły czasami ma sens:</span><span class="sxs-lookup"><span data-stu-id="f7be5-121">**Avoid** recommendations mention things that are generally not a good idea, but breaking the rule sometimes makes sense:</span></span>

<span data-ttu-id="f7be5-122">❌UNIKAJ nuget odwołań do pakietu, które wymagają dokładnej wersji.</span><span class="sxs-lookup"><span data-stu-id="f7be5-122">❌ AVOID NuGet package references that demand an exact version.</span></span>

<span data-ttu-id="f7be5-123">I wreszcie, **Nie** zalecają wskazać coś, czego prawie nigdy nie należy robić:</span><span class="sxs-lookup"><span data-stu-id="f7be5-123">And finally, **Do not** recommendations indicate something you should almost never do:</span></span>

<span data-ttu-id="f7be5-124">❌NIE publikuj wersji biblioteki o silnej nazwie i nieo silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="f7be5-124">❌ DO NOT publish strong-named and non-strong-named versions of your library.</span></span> <span data-ttu-id="f7be5-125">Na przykład `Contoso.Api` `Contoso.Api.StrongNamed`i .</span><span class="sxs-lookup"><span data-stu-id="f7be5-125">For example, `Contoso.Api` and `Contoso.Api.StrongNamed`.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="f7be5-126">Dalej</span><span class="sxs-lookup"><span data-stu-id="f7be5-126">Next</span></span>](get-started.md)

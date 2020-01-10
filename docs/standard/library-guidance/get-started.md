---
title: Wprowadzenie do tworzenia bibliotek platformy .NET o wysokiej jakości
description: Wprowadzenie do tworzenia bibliotek platformy .NET.
ms.date: 10/02/2018
ms.openlocfilehash: 10576219d8470a171ad0f1f347196999b2a2ee03
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706494"
---
# <a name="get-started"></a><span data-ttu-id="3b55c-103">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="3b55c-103">Get started</span></span>

## <a name="cross-platform-targetingcross-platform-targetingmd"></a>[<span data-ttu-id="3b55c-104">Obsługiwane rozwiązania międzyplatformowe</span><span class="sxs-lookup"><span data-stu-id="3b55c-104">Cross-platform targeting</span></span>](./cross-platform-targeting.md)

<span data-ttu-id="3b55c-105">Jak używać .NET Standard i wielu elementów docelowych do tworzenia bibliotek dla wielu platform.</span><span class="sxs-lookup"><span data-stu-id="3b55c-105">How to use .NET Standard and multi-targeting to create cross-platform libraries.</span></span> <span data-ttu-id="3b55c-106">Platforma .NET działa w wielu miejscach, a dobra Biblioteka .NET powinna dążyć do obsługi tylu platform i deweloperów, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="3b55c-106">.NET runs in many places, and good .NET libraries should strive to support as many platforms and developers as possible.</span></span>

## <a name="strong-namingstrong-namingmd"></a>[<span data-ttu-id="3b55c-107">Silne nazewnictwo</span><span class="sxs-lookup"><span data-stu-id="3b55c-107">Strong naming</span></span>](./strong-naming.md)

<span data-ttu-id="3b55c-108">Poznaj silne nazewnictwo oraz zalety i wady.</span><span class="sxs-lookup"><span data-stu-id="3b55c-108">Learn about strong naming and its advantages and disadvantages.</span></span> <span data-ttu-id="3b55c-109">Silne nazewnictwo biblioteki platformy .NET pozwala większości deweloperów korzystać z niej i jest zalecanym najlepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="3b55c-109">Strong naming a .NET library allows the most developers to use it and is a recommended best practice.</span></span>

## <a name="nuget-and-open-source-librariesnugetmd"></a>[<span data-ttu-id="3b55c-110">Biblioteki NuGet i Open Source</span><span class="sxs-lookup"><span data-stu-id="3b55c-110">NuGet and open-source libraries</span></span>](./nuget.md)

<span data-ttu-id="3b55c-111">Najlepszym sposobem tworzenia pakietów NuGet dla bibliotek .NET Open Source, w tym zalecanych metadanych dla wszystkich pakietów opublikowanych publicznie w witrynie NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="3b55c-111">The best way to create NuGet packages for open-source .NET libraries, including recommended metadata for all packages published publicly on NuGet.org.</span></span>

### <a name="dependenciesdependenciesmd"></a>[<span data-ttu-id="3b55c-112">Zależności</span><span class="sxs-lookup"><span data-stu-id="3b55c-112">Dependencies</span></span>](./dependencies.md)

<span data-ttu-id="3b55c-113">Pakiet NuGet ułatwia korzystanie z istniejących pakietów podczas kompilowania biblioteki .NET.</span><span class="sxs-lookup"><span data-stu-id="3b55c-113">NuGet makes it easy to use existing packages when building a .NET library.</span></span> <span data-ttu-id="3b55c-114">Dowiedz się więcej o zależnościach programu NuGet "Typowe źródła tarcia i sposobach ich unikania".</span><span class="sxs-lookup"><span data-stu-id="3b55c-114">Learn about NuGet dependencies' common sources of friction and how to avoid them.</span></span>

### <a name="source-linksourcelinkmd"></a>[<span data-ttu-id="3b55c-115">Link do źródła</span><span class="sxs-lookup"><span data-stu-id="3b55c-115">Source Link</span></span>](./sourcelink.md)

<span data-ttu-id="3b55c-116">Link źródłowy to doskonałe narzędzie umożliwiające użytkownikom biblioteki .NET przechodzenie do kodu źródłowego podczas debugowania.</span><span class="sxs-lookup"><span data-stu-id="3b55c-116">Source Link is a great tool that allows users of your .NET library to step into its source code while debugging.</span></span> <span data-ttu-id="3b55c-117">Ten artykuł zawiera omówienie łącznego źródła i przyczyny jego użycia.</span><span class="sxs-lookup"><span data-stu-id="3b55c-117">This article is an overview of what Source Link is and why you should use it.</span></span>

### <a name="publishingpublish-nuget-packagemd"></a>[<span data-ttu-id="3b55c-118">Publikowanie</span><span class="sxs-lookup"><span data-stu-id="3b55c-118">Publishing</span></span>](./publish-nuget-package.md)

<span data-ttu-id="3b55c-119">Chociaż NuGet.org jest najczęściej znanym i używanym repozytorium, istnieje wiele miejsc do publikowania pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="3b55c-119">While NuGet.org is the most widely known and used repository, there are many places to publish NuGet packages.</span></span> <span data-ttu-id="3b55c-120">Poznaj różne dostępne repozytoria pakietów NuGet oraz najlepsze rozwiązania w zakresie zabezpieczeń dotyczące publikowania biblioteki .NET.</span><span class="sxs-lookup"><span data-stu-id="3b55c-120">Learn about the different NuGet package repositories available, and security best practices for publishing a .NET library.</span></span>

## <a name="versioningversioningmd"></a>[<span data-ttu-id="3b55c-121">Przechowywanie wersji</span><span class="sxs-lookup"><span data-stu-id="3b55c-121">Versioning</span></span>](./versioning.md)

<span data-ttu-id="3b55c-122">Dobre biblioteki .NET są rozwijane wraz z upływem czasu, dodawaniem funkcji, naprawianie usterek i Poprawianie wydajności w nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="3b55c-122">Good .NET libraries evolve over time, adding features, fixing bugs, and improving performance in later releases.</span></span> <span data-ttu-id="3b55c-123">Dowiedz się więcej o różnych numerach wersji i sposobach przekazywania istotnych zmian do deweloperów.</span><span class="sxs-lookup"><span data-stu-id="3b55c-123">Learn about the various version numbers and how to communicate breaking changes to developers.</span></span>

### <a name="breaking-changesbreaking-changesmd"></a>[<span data-ttu-id="3b55c-124">Zmiany powodujące niezgodność</span><span class="sxs-lookup"><span data-stu-id="3b55c-124">Breaking changes</span></span>](./breaking-changes.md)

<span data-ttu-id="3b55c-125">Ważne jest, aby w bibliotece .NET znaleźć równowagę między stabilnością dla istniejących użytkowników i innowacji w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="3b55c-125">It's important for a .NET library to find a balance between stability for existing users and innovation for the future.</span></span> <span data-ttu-id="3b55c-126">Poznaj różne rodzaje istotnych zmian i strategii dodawania nowych funkcji przy zachowaniu zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="3b55c-126">Learn about the different kinds of breaking changes and strategies for adding new features while maintaining backwards compatibility.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="3b55c-127">[Poprzedni](index.md)
>[Następny](cross-platform-targeting.md)</span><span class="sxs-lookup"><span data-stu-id="3b55c-127">[Previous](index.md)
[Next](cross-platform-targeting.md)</span></span>

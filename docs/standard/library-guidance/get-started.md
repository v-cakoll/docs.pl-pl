---
title: Wprowadzenie do tworzenia bibliotek .NET wysokiej jakości
description: Wprowadzenie do tworzenia bibliotek platformy .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 980f0edcee07688935f6d08f3ce1ed812159695e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65640741"
---
# <a name="get-started"></a><span data-ttu-id="e42f0-103">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="e42f0-103">Get started</span></span>

## <a name="cross-platform-targetingcross-platform-targetingmd"></a>[<span data-ttu-id="e42f0-104">Obsługiwane rozwiązania międzyplatformowe</span><span class="sxs-lookup"><span data-stu-id="e42f0-104">Cross-platform targeting</span></span>](./cross-platform-targeting.md)

<span data-ttu-id="e42f0-105">Jak używać .NET Standard i wielowersyjność kodu do tworzenia bibliotek dla wielu platform.</span><span class="sxs-lookup"><span data-stu-id="e42f0-105">How to use .NET Standard and multi-targeting to create cross-platform libraries.</span></span> <span data-ttu-id="e42f0-106">.NET, który jest uruchamiany w wielu miejscach i dobre bibliotek .NET należy dążyć do obsługuje dowolną liczbę platform i deweloperów jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="e42f0-106">.NET runs in many places, and good .NET libraries should strive to support as many platforms and developers as possible.</span></span>

## <a name="strong-namingstrong-namingmd"></a>[<span data-ttu-id="e42f0-107">Silne nazewnictwo</span><span class="sxs-lookup"><span data-stu-id="e42f0-107">Strong naming</span></span>](./strong-naming.md)

<span data-ttu-id="e42f0-108">Więcej informacji na temat silnych nazw i jego zalety i wady.</span><span class="sxs-lookup"><span data-stu-id="e42f0-108">Learn about strong naming and its advantages and disadvantages.</span></span> <span data-ttu-id="e42f0-109">Silne nazewnictwo biblioteki .NET programiści mogą wykorzystać z niego korzystać i jest zalecanym najlepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="e42f0-109">Strong naming a .NET library allows the most developers to use it and is a recommended best practice.</span></span>

## <a name="nuget-and-open-source-librariesnugetmd"></a>[<span data-ttu-id="e42f0-110">Biblioteki typu open source i NuGet</span><span class="sxs-lookup"><span data-stu-id="e42f0-110">NuGet and open-source libraries</span></span>](./nuget.md)

<span data-ttu-id="e42f0-111">Najlepszym sposobem tworzenia pakietów NuGet dla bibliotek .NET typu open source, takie jak metadane zalecana dla wszystkich pakietów publicznie opublikowane w witrynie NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="e42f0-111">The best way to create NuGet packages for open-source .NET libraries, including recommended metadata for all packages published publicly on NuGet.org.</span></span>

### <a name="dependenciesdependenciesmd"></a>[<span data-ttu-id="e42f0-112">Zależności</span><span class="sxs-lookup"><span data-stu-id="e42f0-112">Dependencies</span></span>](./dependencies.md)

<span data-ttu-id="e42f0-113">NuGet umożliwia łatwe w użyciu istniejących pakietów podczas tworzenia biblioteki .NET.</span><span class="sxs-lookup"><span data-stu-id="e42f0-113">NuGet makes it easy to use existing packages when building a .NET library.</span></span> <span data-ttu-id="e42f0-114">Więcej informacji na temat zależności NuGet wspólnych źródeł Ogranicz liczbę problemów i jak ich unikać.</span><span class="sxs-lookup"><span data-stu-id="e42f0-114">Learn about NuGet dependencies' common sources of friction and how to avoid them.</span></span>

### <a name="source-linksourcelinkmd"></a>[<span data-ttu-id="e42f0-115">Link do źródła</span><span class="sxs-lookup"><span data-stu-id="e42f0-115">Source Link</span></span>](./sourcelink.md)

<span data-ttu-id="e42f0-116">Link źródłowy jest doskonałym narzędziem, który umożliwia użytkownikom biblioteki .NET wkroczyć do jego kod źródłowy podczas debugowania.</span><span class="sxs-lookup"><span data-stu-id="e42f0-116">Source Link is a great tool that allows users of your .NET library to step into its source code while debugging.</span></span> <span data-ttu-id="e42f0-117">W tym artykule przedstawiono omówienie Link źródłowy jest i dlaczego należy z niej korzystać.</span><span class="sxs-lookup"><span data-stu-id="e42f0-117">This article is an overview of what Source Link is and why you should use it.</span></span>

### <a name="publishingpublish-nuget-packagemd"></a>[<span data-ttu-id="e42f0-118">Publikowanie</span><span class="sxs-lookup"><span data-stu-id="e42f0-118">Publishing</span></span>](./publish-nuget-package.md)

<span data-ttu-id="e42f0-119">NuGet.org najczęściej jest znany i używane repozytorium, są dużo miejsca do publikowania pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="e42f0-119">While NuGet.org is the most widely known and used repository, there are many places to publish NuGet packages.</span></span> <span data-ttu-id="e42f0-120">Informacje na temat różnych repozytoriach pakietów NuGet dostępne i najlepsze rozwiązania dotyczące publikowania biblioteki .NET.</span><span class="sxs-lookup"><span data-stu-id="e42f0-120">Learn about the different NuGet package repositories available, and security best practices for publishing a .NET library.</span></span>

## <a name="versioningversioningmd"></a>[<span data-ttu-id="e42f0-121">Przechowywanie wersji</span><span class="sxs-lookup"><span data-stu-id="e42f0-121">Versioning</span></span>](./versioning.md)

<span data-ttu-id="e42f0-122">Dobre bibliotek .NET z czasem ewoluować, dodawanie funkcji, naprawianie błędów i poprawę wydajności w nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="e42f0-122">Good .NET libraries evolve over time, adding features, fixing bugs, and improving performance in later releases.</span></span> <span data-ttu-id="e42f0-123">Więcej informacji na temat różnych numerów wersji oraz sposób komunikowania się zmian powodujących niezgodność dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="e42f0-123">Learn about the various version numbers and how to communicate breaking changes to developers.</span></span>

### <a name="breaking-changesbreaking-changesmd"></a>[<span data-ttu-id="e42f0-124">Zmiany powodujące niezgodność</span><span class="sxs-lookup"><span data-stu-id="e42f0-124">Breaking changes</span></span>](./breaking-changes.md)

<span data-ttu-id="e42f0-125">Jest ważne dla biblioteki .NET znaleźć równowagę między stabilności istniejących użytkowników i innowacji w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="e42f0-125">It's important for a .NET library to find a balance between stability for existing users and innovation for the future.</span></span> <span data-ttu-id="e42f0-126">Więcej informacji na temat różnych rodzajów przełomowe zmiany i strategie Dodawanie nowych funkcji, przy zachowaniu wstecznej zgodności.</span><span class="sxs-lookup"><span data-stu-id="e42f0-126">Learn about the different kinds of breaking changes and strategies for adding new features while maintaining backwards compatibility.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e42f0-127">[Poprzednie](index.md)
>[dalej](cross-platform-targeting.md)</span><span class="sxs-lookup"><span data-stu-id="e42f0-127">[Previous](index.md)
[Next](cross-platform-targeting.md)</span></span>

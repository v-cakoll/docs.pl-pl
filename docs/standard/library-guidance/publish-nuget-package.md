---
title: Publikowanie pakietu NuGet
description: Zalecenia dotyczące najlepszych rozwiązań do publikowania NuGet biblioteki .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: e0244d2a9d09382c289c74a45969bca0a1311445
ms.sourcegitcommit: b5cd9d5d3b75a5537fc9ad8a3f085f0bb1845ee0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2018
ms.locfileid: "50757312"
---
# <a name="publishing-a-nuget-package"></a><span data-ttu-id="a69bc-103">Publikowanie pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="a69bc-103">Publishing a NuGet package</span></span>

<span data-ttu-id="a69bc-104">Pakiety NuGet są publikowane i używane z repozytoriów pakietów.</span><span class="sxs-lookup"><span data-stu-id="a69bc-104">NuGet packages are published and consumed from package repositories.</span></span> <span data-ttu-id="a69bc-105">NuGet.org najczęściej jest znany i używane repozytorium, istnieje wiele miejsc, aby opublikować pakiety NuGet:</span><span class="sxs-lookup"><span data-stu-id="a69bc-105">While NuGet.org is the most widely known and used repository, there are many places to publish NuGet packages:</span></span>

* <span data-ttu-id="a69bc-106">**[NuGet.org](https://www.nuget.org/)**  głównej repozytorium online dla pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="a69bc-106">**[NuGet.org](https://www.nuget.org/)** is the primary online repository for NuGet packages.</span></span> <span data-ttu-id="a69bc-107">Wszystkie pakiety w witrynie NuGet.org są publicznie dostępne dla wszystkich użytkowników.</span><span class="sxs-lookup"><span data-stu-id="a69bc-107">All packages on NuGet.org are publicly available to everyone.</span></span> <span data-ttu-id="a69bc-108">Domyślnie program Visual Studio zawiera NuGet.org jako źródło pakietów i wielu deweloperów NuGet.org znajduje się tylko repozytorium pakietów, który będzie interakcji z.</span><span class="sxs-lookup"><span data-stu-id="a69bc-108">By default, Visual Studio has NuGet.org as a package source and for many developers NuGet.org is the only package repository they'll interact with.</span></span> <span data-ttu-id="a69bc-109">NuGet.org to najlepsze miejsce do publikowania stabilne pakiety i pakiety w wersji wstępnej, które ma być opinii społeczności.</span><span class="sxs-lookup"><span data-stu-id="a69bc-109">NuGet.org is the best place to publish stable packages and pre-release packages that you want community feedback on.</span></span>

* <span data-ttu-id="a69bc-110">**[MyGet](https://myget.org/)**  to usługa repozytorium, która obsługuje źródła danych pakiet niestandardowy w przypadku projektów typu open source.</span><span class="sxs-lookup"><span data-stu-id="a69bc-110">**[MyGet](https://myget.org/)** is a repository service that supports custom package feeds for open-source projects.</span></span> <span data-ttu-id="a69bc-111">MyGet publiczne źródło niestandardowe to idealne miejsce do publikowania utworzone przez usługę CI pakiety w wersji wstępnej.</span><span class="sxs-lookup"><span data-stu-id="a69bc-111">A MyGet public custom feed is an ideal place to publish pre-release packages created by your CI service.</span></span> <span data-ttu-id="a69bc-112">MyGet także kanały prywatne dostępnym w sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="a69bc-112">MyGet also provides private feeds commercially.</span></span>

* <span data-ttu-id="a69bc-113">A **[lokalne źródła danych](/nuget/hosting-packages/local-feeds)** umożliwia traktowanie folderem, takich jak repozytorium pakietów i sprawia, że `*.nupkg` pliki w folderze dostępne przez NuGet.</span><span class="sxs-lookup"><span data-stu-id="a69bc-113">A **[local feed](/nuget/hosting-packages/local-feeds)** allows you to treat a folder like a package repository and makes the `*.nupkg` files in the folder accessible by NuGet.</span></span> <span data-ttu-id="a69bc-114">Lokalne źródło danych jest przydatna przy testowaniu pakietu NuGet przed jego opublikowaniem NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="a69bc-114">A local feed is useful for testing a NuGet package before publishing it to NuGet.org.</span></span>

> [!NOTE]
> <span data-ttu-id="a69bc-115">NuGet.org [nie zezwala na pakiet do usunięcia](/nuget/policies/deleting-packages) po jego przekazaniu.</span><span class="sxs-lookup"><span data-stu-id="a69bc-115">NuGet.org [does not allow a package to be deleted](/nuget/policies/deleting-packages) once it is uploaded.</span></span> <span data-ttu-id="a69bc-116">Pakiet może być nieznajdujące się na liście, tak aby nie była widoczna publicznie w interfejsie użytkownika, ale `*.nupkg` nadal można pobrać podczas przywracania.</span><span class="sxs-lookup"><span data-stu-id="a69bc-116">A package can be unlisted so that it is not publicly visible in the UI but the `*.nupkg` can still be downloaded on restore.</span></span> <span data-ttu-id="a69bc-117">Ponadto nuget.org nie zezwala na wersje zduplikowanych pakietów.</span><span class="sxs-lookup"><span data-stu-id="a69bc-117">Also, nuget.org does not allow duplicate package versions.</span></span> <span data-ttu-id="a69bc-118">Aby poprawić pakietu NuGet z powodu błędu konieczne wyrejestrowanie pakietu niepoprawne, zwiększ numer wersji, a następnie opublikować nową wersję pakietu.</span><span class="sxs-lookup"><span data-stu-id="a69bc-118">To correct a NuGet package with an error you have to unlist the incorrect package, increment the version number and publish a new version of the package.</span></span>

<span data-ttu-id="a69bc-119">**CZY ✔️** [publikowania stabilne pakiety i pakiety w wersji wstępnej](/nuget/create-packages/publish-a-package) chcesz, aby opinia społeczności do NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="a69bc-119">**✔️ DO** [publish stable packages and pre-release packages](/nuget/create-packages/publish-a-package) you want community feedback on to NuGet.org.</span></span>

<span data-ttu-id="a69bc-120">**ROZWAŻ ✔️** publikowania pakiety w wersji wstępnej MyGet źródła danych z kompilacji ciągłej integracji.</span><span class="sxs-lookup"><span data-stu-id="a69bc-120">**✔️ CONSIDER** publishing pre-release packages to a MyGet feed from a continuous integration build.</span></span>

<span data-ttu-id="a69bc-121">**ROZWAŻ ✔️** testowania w środowisku deweloperskim za pomocą lokalnego źródła danych lub MyGet.</span><span class="sxs-lookup"><span data-stu-id="a69bc-121">**✔️ CONSIDER** testing packages in your development environment using a local feed or MyGet.</span></span> <span data-ttu-id="a69bc-122">Sprawdź działa pakiet, a następnie opublikuj go w witrynie NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="a69bc-122">Check the package works then publish it to NuGet.org.</span></span>

## <a name="nugetorg-security"></a><span data-ttu-id="a69bc-123">Zabezpieczenia NuGet.org</span><span class="sxs-lookup"><span data-stu-id="a69bc-123">NuGet.org security</span></span>

<span data-ttu-id="a69bc-124">Jest ważne, nieupoważnione osoby nie można uzyskać dostępu do konta NuGet i przekazać złośliwego wersję biblioteki.</span><span class="sxs-lookup"><span data-stu-id="a69bc-124">It's important that bad actors can't access your NuGet account and upload a malicious version of your library.</span></span> <span data-ttu-id="a69bc-125">NuGet.org oferuje two-Factor Authentication uwierzytelnianie i powiadomień e-mail po opublikowaniu pakietu.</span><span class="sxs-lookup"><span data-stu-id="a69bc-125">NuGet.org offers two-factor authentication and email notifications when a package is published.</span></span> <span data-ttu-id="a69bc-126">Włączyć te funkcje po zalogowaniu w witrynie NuGet.org **ustawienia konta** strony.</span><span class="sxs-lookup"><span data-stu-id="a69bc-126">Enable these features after logging into NuGet.org on the **Account settings** page.</span></span>

<span data-ttu-id="a69bc-127">![tekst alternatywny](./media/publish-nuget-package/nuget-2fa.png "zabezpieczenia konta NuGet")</span><span class="sxs-lookup"><span data-stu-id="a69bc-127">![alt text](./media/publish-nuget-package/nuget-2fa.png "NuGet Account Security")</span></span>

<span data-ttu-id="a69bc-128">**CZY ✔️** Użyj konta Microsoft do logowania się na NuGet.</span><span class="sxs-lookup"><span data-stu-id="a69bc-128">**✔️ DO** use a Microsoft account to sign in to NuGet.</span></span>

<span data-ttu-id="a69bc-129">**CZY ✔️** Włączanie uwierzytelniania dwuskładnikowego do uzyskiwania dostępu do NuGet.</span><span class="sxs-lookup"><span data-stu-id="a69bc-129">**✔️ DO** enable two-factor authentication for accessing NuGet.</span></span>

<span data-ttu-id="a69bc-130">**CZY ✔️** Włączanie powiadomień e-mail po opublikowaniu pakietu.</span><span class="sxs-lookup"><span data-stu-id="a69bc-130">**✔️ DO** enable email notification when a package is published.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="a69bc-131">[Poprzednie](./sourcelink.md)
[dalej](./versioning.md)</span><span class="sxs-lookup"><span data-stu-id="a69bc-131">[Previous](./sourcelink.md)
[Next](./versioning.md)</span></span>

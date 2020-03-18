---
title: Publikowanie pakietu NuGet
description: Najlepsze zalecenia dotyczące publikowania bibliotek .NET w nuget.
ms.date: 10/02/2018
ms.openlocfilehash: 089c660bc51252c6295858b1462ae59bde968564
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "76744552"
---
# <a name="publishing-a-nuget-package"></a><span data-ttu-id="debfc-103">Publikowanie pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="debfc-103">Publishing a NuGet package</span></span>

<span data-ttu-id="debfc-104">Pakiety NuGet są publikowane i używane z repozytoriów pakietów.</span><span class="sxs-lookup"><span data-stu-id="debfc-104">NuGet packages are published and consumed from package repositories.</span></span> <span data-ttu-id="debfc-105">Chociaż NuGet.org jest najbardziej znanym i używanym repozytorium, istnieje wiele miejsc do publikowania pakietów NuGet:</span><span class="sxs-lookup"><span data-stu-id="debfc-105">While NuGet.org is the most widely known and used repository, there are many places to publish NuGet packages:</span></span>

* <span data-ttu-id="debfc-106">**[NuGet.org](https://www.nuget.org/)** jest podstawowym repozytorium online dla pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="debfc-106">**[NuGet.org](https://www.nuget.org/)** is the primary online repository for NuGet packages.</span></span> <span data-ttu-id="debfc-107">Wszystkie pakiety na NuGet.org są publicznie dostępne dla wszystkich.</span><span class="sxs-lookup"><span data-stu-id="debfc-107">All packages on NuGet.org are publicly available to everyone.</span></span> <span data-ttu-id="debfc-108">Domyślnie program Visual Studio ma NuGet.org jako źródło pakietu, a dla wielu deweloperów NuGet.org jest jedynym repozytorium pakietów, z którymi będą współpracować.</span><span class="sxs-lookup"><span data-stu-id="debfc-108">By default, Visual Studio has NuGet.org as a package source and for many developers NuGet.org is the only package repository they'll interact with.</span></span> <span data-ttu-id="debfc-109">NuGet.org jest najlepszym miejscem do publikowania stabilnych pakietów i pakietów w wersji wstępnej, na których chcesz uzyskać opinię społeczności.</span><span class="sxs-lookup"><span data-stu-id="debfc-109">NuGet.org is the best place to publish stable packages and pre-release packages that you want community feedback on.</span></span>

* <span data-ttu-id="debfc-110">**[MyGet](https://myget.org/)** to usługa repozytorium, która obsługuje niestandardowe źródła danych pakietów dla projektów typu open source.</span><span class="sxs-lookup"><span data-stu-id="debfc-110">**[MyGet](https://myget.org/)** is a repository service that supports custom package feeds for open-source projects.</span></span> <span data-ttu-id="debfc-111">MyGet publicznego niestandardowego źródła danych jest idealnym miejscem do publikowania pakietów w wersji wstępnej utworzonych przez usługę ci.</span><span class="sxs-lookup"><span data-stu-id="debfc-111">A MyGet public custom feed is an ideal place to publish pre-release packages created by your CI service.</span></span> <span data-ttu-id="debfc-112">MyGet zapewnia również prywatne kanały handlowe.</span><span class="sxs-lookup"><span data-stu-id="debfc-112">MyGet also provides private feeds commercially.</span></span>

* <span data-ttu-id="debfc-113">**[Lokalny kanał informacyjny](/nuget/hosting-packages/local-feeds)** umożliwia traktowanie folderu jak repozytorium `*.nupkg` pakietów i sprawia, że pliki w folderze są dostępne przez NuGet.</span><span class="sxs-lookup"><span data-stu-id="debfc-113">A **[local feed](/nuget/hosting-packages/local-feeds)** allows you to treat a folder like a package repository and makes the `*.nupkg` files in the folder accessible by NuGet.</span></span> <span data-ttu-id="debfc-114">Lokalny kanał informacyjny jest przydatny do testowania pakietu NuGet przed opublikowaniem go do NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="debfc-114">A local feed is useful for testing a NuGet package before publishing it to NuGet.org.</span></span>

> [!NOTE]
> <span data-ttu-id="debfc-115">NuGet.org [nie zezwala na usunięcie pakietu](/nuget/policies/deleting-packages) po jego przesłaniu.</span><span class="sxs-lookup"><span data-stu-id="debfc-115">NuGet.org [does not allow a package to be deleted](/nuget/policies/deleting-packages) once it is uploaded.</span></span> <span data-ttu-id="debfc-116">Pakiet może być niepubliczny, dzięki czemu nie jest publicznie widoczny `*.nupkg` w ui, ale nadal można go pobrać przy przywracaniu.</span><span class="sxs-lookup"><span data-stu-id="debfc-116">A package can be unlisted so that it is not publicly visible in the UI but the `*.nupkg` can still be downloaded on restore.</span></span> <span data-ttu-id="debfc-117">Ponadto nuget.org nie zezwala na zduplikowane wersje pakietów.</span><span class="sxs-lookup"><span data-stu-id="debfc-117">Also, nuget.org does not allow duplicate package versions.</span></span> <span data-ttu-id="debfc-118">Aby poprawić pakiet NuGet z błędem, musisz odsunąć listę niepoprawnego pakietu, podwoż numer wersji i opublikować nową wersję pakietu.</span><span class="sxs-lookup"><span data-stu-id="debfc-118">To correct a NuGet package with an error you have to unlist the incorrect package, increment the version number and publish a new version of the package.</span></span>

<span data-ttu-id="debfc-119">✔️ [publikujstabilne pakiety i pakiety w wersji wstępnej,](/nuget/create-packages/publish-a-package) na których chcesz NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="debfc-119">✔️ DO [publish stable packages and pre-release packages](/nuget/create-packages/publish-a-package) you want community feedback on to NuGet.org.</span></span>

<span data-ttu-id="debfc-120">✔️ ROZWAŻ publikowanie pakietów w wersji wstępnej do kanału informacyjnego MyGet z kompilacji ciągłej integracji.</span><span class="sxs-lookup"><span data-stu-id="debfc-120">✔️ CONSIDER publishing pre-release packages to a MyGet feed from a continuous integration build.</span></span>

<span data-ttu-id="debfc-121">✔️ ROZWAŻ testowanie pakietów w środowisku programistycznym przy użyciu lokalnego źródła danych lub MyGet.</span><span class="sxs-lookup"><span data-stu-id="debfc-121">✔️ CONSIDER testing packages in your development environment using a local feed or MyGet.</span></span> <span data-ttu-id="debfc-122">Sprawdź, czy pakiet działa, a następnie opublikuj go w NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="debfc-122">Check the package works then publish it to NuGet.org.</span></span>

## <a name="nugetorg-security"></a><span data-ttu-id="debfc-123">NuGet.org bezpieczeństwo</span><span class="sxs-lookup"><span data-stu-id="debfc-123">NuGet.org security</span></span>

<span data-ttu-id="debfc-124">Ważne jest, aby złe podmioty nie mogły uzyskać dostępu do konta NuGet i przekazać złośliwą wersję biblioteki.</span><span class="sxs-lookup"><span data-stu-id="debfc-124">It's important that bad actors can't access your NuGet account and upload a malicious version of your library.</span></span> <span data-ttu-id="debfc-125">NuGet.org oferuje uwierzytelnianie dwuskładnikowe i powiadomienia e-mail po opublikowaniu pakietu.</span><span class="sxs-lookup"><span data-stu-id="debfc-125">NuGet.org offers two-factor authentication and email notifications when a package is published.</span></span> <span data-ttu-id="debfc-126">Włącz te funkcje po zalogowaniu się do NuGet.org na stronie **Ustawienia konta.**</span><span class="sxs-lookup"><span data-stu-id="debfc-126">Enable these features after logging into NuGet.org on the **Account settings** page.</span></span>

<span data-ttu-id="debfc-127">![tekst alternatywny](./media/publish-nuget-package/nuget-2fa.png "Zabezpieczenia konta NuGet")</span><span class="sxs-lookup"><span data-stu-id="debfc-127">![alt text](./media/publish-nuget-package/nuget-2fa.png "NuGet Account Security")</span></span>

<span data-ttu-id="debfc-128">✔️ do logowania się do NuGet za pomocą konta Microsoft.</span><span class="sxs-lookup"><span data-stu-id="debfc-128">✔️ DO use a Microsoft account to sign in to NuGet.</span></span>

<span data-ttu-id="debfc-129">✔️ do włączania uwierzytelniania dwuskładnikowego do uzyskiwania dostępu nuget.</span><span class="sxs-lookup"><span data-stu-id="debfc-129">✔️ DO enable two-factor authentication for accessing NuGet.</span></span>

<span data-ttu-id="debfc-130">✔️ włącz powiadomienia e-mail po opublikowaniu pakietu.</span><span class="sxs-lookup"><span data-stu-id="debfc-130">✔️ DO enable email notification when a package is published.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="debfc-131">[Poprzedni](sourcelink.md)
>[następny](versioning.md)</span><span class="sxs-lookup"><span data-stu-id="debfc-131">[Previous](sourcelink.md)
[Next](versioning.md)</span></span>

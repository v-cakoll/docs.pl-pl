---
title: Publikowanie pakietu NuGet
description: Zalecenia dotyczące najlepszych rozwiązań dotyczących publikowania bibliotek .NET w programie NuGet.
ms.date: 10/02/2018
ms.openlocfilehash: e567fe3f7e00bf322cdd50786e50128961107469
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706468"
---
# <a name="publishing-a-nuget-package"></a><span data-ttu-id="0d615-103">Publikowanie pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="0d615-103">Publishing a NuGet package</span></span>

<span data-ttu-id="0d615-104">Pakiety NuGet są publikowane i używane z repozytoriów pakietów.</span><span class="sxs-lookup"><span data-stu-id="0d615-104">NuGet packages are published and consumed from package repositories.</span></span> <span data-ttu-id="0d615-105">Chociaż NuGet.org jest najczęściej znanym i używanym repozytorium, istnieje wiele miejsc do publikowania pakietów NuGet:</span><span class="sxs-lookup"><span data-stu-id="0d615-105">While NuGet.org is the most widely known and used repository, there are many places to publish NuGet packages:</span></span>

* <span data-ttu-id="0d615-106">**[NuGet.org](https://www.nuget.org/)** to podstawowe repozytorium online dla pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="0d615-106">**[NuGet.org](https://www.nuget.org/)** is the primary online repository for NuGet packages.</span></span> <span data-ttu-id="0d615-107">Wszystkie pakiety na NuGet.org są publicznie dostępne dla wszystkich użytkowników.</span><span class="sxs-lookup"><span data-stu-id="0d615-107">All packages on NuGet.org are publicly available to everyone.</span></span> <span data-ttu-id="0d615-108">Domyślnie program Visual Studio ma NuGet.org jako źródło pakietu, a dla wielu deweloperów NuGet.org jest jedynym repozytorium pakietu, z którym będą korzystać.</span><span class="sxs-lookup"><span data-stu-id="0d615-108">By default, Visual Studio has NuGet.org as a package source and for many developers NuGet.org is the only package repository they'll interact with.</span></span> <span data-ttu-id="0d615-109">NuGet.org to najlepsze miejsce do publikowania stabilnych pakietów i pakietów w wersji wstępnej, na które chcesz uzyskać opinię społecznościową.</span><span class="sxs-lookup"><span data-stu-id="0d615-109">NuGet.org is the best place to publish stable packages and pre-release packages that you want community feedback on.</span></span>

* <span data-ttu-id="0d615-110">**[MyGet](https://myget.org/)** to usługa repozytorium, która obsługuje niestandardowe źródła pakietów dla projektów typu open source.</span><span class="sxs-lookup"><span data-stu-id="0d615-110">**[MyGet](https://myget.org/)** is a repository service that supports custom package feeds for open-source projects.</span></span> <span data-ttu-id="0d615-111">Publiczne niestandardowe źródło danych MyGet jest idealnym miejscem do publikowania pakietów w wersji wstępnej utworzonych przez usługę CI.</span><span class="sxs-lookup"><span data-stu-id="0d615-111">A MyGet public custom feed is an ideal place to publish pre-release packages created by your CI service.</span></span> <span data-ttu-id="0d615-112">MyGet również udostępnia prywatne źródła komercyjne.</span><span class="sxs-lookup"><span data-stu-id="0d615-112">MyGet also provides private feeds commercially.</span></span>

* <span data-ttu-id="0d615-113">**[Lokalne źródło danych](/nuget/hosting-packages/local-feeds)** umożliwia traktowanie folderu, takiego jak repozytorium pakietu, i udostępnia `*.nupkg` pliki w folderze dostępnym dla narzędzia NuGet.</span><span class="sxs-lookup"><span data-stu-id="0d615-113">A **[local feed](/nuget/hosting-packages/local-feeds)** allows you to treat a folder like a package repository and makes the `*.nupkg` files in the folder accessible by NuGet.</span></span> <span data-ttu-id="0d615-114">Lokalne źródło danych jest przydatne w przypadku testowania pakietu NuGet przed opublikowaniem go w usłudze NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="0d615-114">A local feed is useful for testing a NuGet package before publishing it to NuGet.org.</span></span>

> [!NOTE]
> <span data-ttu-id="0d615-115">NuGet.org nie [zezwala na usunięcie pakietu](/nuget/policies/deleting-packages) po jego przekazaniu.</span><span class="sxs-lookup"><span data-stu-id="0d615-115">NuGet.org [does not allow a package to be deleted](/nuget/policies/deleting-packages) once it is uploaded.</span></span> <span data-ttu-id="0d615-116">Pakiet może być wystawiony, aby nie był publicznie widoczny w interfejsie użytkownika, ale `*.nupkg` nadal można pobrać podczas przywracania.</span><span class="sxs-lookup"><span data-stu-id="0d615-116">A package can be unlisted so that it is not publicly visible in the UI but the `*.nupkg` can still be downloaded on restore.</span></span> <span data-ttu-id="0d615-117">Ponadto nuget.org nie zezwala na duplikowanie wersji pakietu.</span><span class="sxs-lookup"><span data-stu-id="0d615-117">Also, nuget.org does not allow duplicate package versions.</span></span> <span data-ttu-id="0d615-118">Aby poprawić pakiet NuGet z błędem należy usunąć listę niepoprawnego pakietu, zwiększyć numer wersji i opublikować nową wersję pakietu.</span><span class="sxs-lookup"><span data-stu-id="0d615-118">To correct a NuGet package with an error you have to unlist the incorrect package, increment the version number and publish a new version of the package.</span></span>

<span data-ttu-id="0d615-119">**✔️** [publikować pakiety stabilne i pakiety wersji wstępnej](/nuget/create-packages/publish-a-package) , na które chcesz, aby opinia społeczności była NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="0d615-119">**✔️ DO** [publish stable packages and pre-release packages](/nuget/create-packages/publish-a-package) you want community feedback on to NuGet.org.</span></span>

<span data-ttu-id="0d615-120">**✔️ rozważyć** opublikowanie pakietów w wersji wstępnej do źródła danych MyGet z kompilacji ciągłej integracji.</span><span class="sxs-lookup"><span data-stu-id="0d615-120">**✔️ CONSIDER** publishing pre-release packages to a MyGet feed from a continuous integration build.</span></span>

<span data-ttu-id="0d615-121">**✔️ rozważyć** testowanie pakietów w środowisku programistycznym przy użyciu lokalnego źródła danych lub MyGet.</span><span class="sxs-lookup"><span data-stu-id="0d615-121">**✔️ CONSIDER** testing packages in your development environment using a local feed or MyGet.</span></span> <span data-ttu-id="0d615-122">Sprawdź, czy pakiet działa, a następnie opublikuj go w NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="0d615-122">Check the package works then publish it to NuGet.org.</span></span>

## <a name="nugetorg-security"></a><span data-ttu-id="0d615-123">Zabezpieczenia NuGet.org</span><span class="sxs-lookup"><span data-stu-id="0d615-123">NuGet.org security</span></span>

<span data-ttu-id="0d615-124">Ważne jest, aby niektórym uczestnikom nie mógł uzyskać dostępu do konta NuGet i przekazać złośliwą wersję biblioteki.</span><span class="sxs-lookup"><span data-stu-id="0d615-124">It's important that bad actors can't access your NuGet account and upload a malicious version of your library.</span></span> <span data-ttu-id="0d615-125">NuGet.org oferuje uwierzytelnianie dwuskładnikowe i powiadomienia e-mail w przypadku opublikowania pakietu.</span><span class="sxs-lookup"><span data-stu-id="0d615-125">NuGet.org offers two-factor authentication and email notifications when a package is published.</span></span> <span data-ttu-id="0d615-126">Te funkcje należy włączyć po zalogowaniu się do NuGet.org na stronie **Ustawienia konta** .</span><span class="sxs-lookup"><span data-stu-id="0d615-126">Enable these features after logging into NuGet.org on the **Account settings** page.</span></span>

<span data-ttu-id="0d615-127">![tekst alternatywny](./media/publish-nuget-package/nuget-2fa.png "Zabezpieczenia konta NuGet")</span><span class="sxs-lookup"><span data-stu-id="0d615-127">![alt text](./media/publish-nuget-package/nuget-2fa.png "NuGet Account Security")</span></span>

<span data-ttu-id="0d615-128">**✔️** używać konto Microsoft do logowania się do narzędzia NuGet.</span><span class="sxs-lookup"><span data-stu-id="0d615-128">**✔️ DO** use a Microsoft account to sign in to NuGet.</span></span>

<span data-ttu-id="0d615-129">**✔️** włączyć uwierzytelnianie dwuskładnikowe w celu uzyskania dostępu do programu NuGet.</span><span class="sxs-lookup"><span data-stu-id="0d615-129">**✔️ DO** enable two-factor authentication for accessing NuGet.</span></span>

<span data-ttu-id="0d615-130">**✔️** włączyć powiadomienia e-mail po opublikowaniu pakietu.</span><span class="sxs-lookup"><span data-stu-id="0d615-130">**✔️ DO** enable email notification when a package is published.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0d615-131">[Poprzedni](sourcelink.md)
>[Następny](versioning.md)</span><span class="sxs-lookup"><span data-stu-id="0d615-131">[Previous](sourcelink.md)
[Next](versioning.md)</span></span>

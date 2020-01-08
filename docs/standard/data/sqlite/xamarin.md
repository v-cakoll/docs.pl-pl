---
title: Ograniczenia dotyczące platformy Xamarin
ms.date: 12/13/2019
description: W tym artykule opisano niektóre ograniczenia, które można napotkać podczas korzystania z platformy Xamarin.
ms.openlocfilehash: 192f25954726919dc66d706e755e0853404b4d85
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447168"
---
# <a name="xamarin-limitations"></a><span data-ttu-id="b44e5-103">Ograniczenia dotyczące platformy Xamarin</span><span class="sxs-lookup"><span data-stu-id="b44e5-103">Xamarin limitations</span></span>

<span data-ttu-id="b44e5-104">Elementy docelowe Microsoft. Data. sqlite .NET Standard 2,0 i są obsługiwane w środowisku Xamarin.</span><span class="sxs-lookup"><span data-stu-id="b44e5-104">Microsoft.Data.Sqlite targets .NET Standard 2.0 and is supported on Xamarin.</span></span> <span data-ttu-id="b44e5-105">W poniższej tabeli przedstawiono, które platformy domyślny pakiet SQLitePCLRaw zapewnia natywne pliki binarne oprogramowania SQLite dla programu.</span><span class="sxs-lookup"><span data-stu-id="b44e5-105">The following table shows which platforms the default SQLitePCLRaw bundle provides native SQLite binaries for.</span></span> <span data-ttu-id="b44e5-106">Zobacz [niestandardowe wersje oprogramowania SQLite](custom-versions.md) , aby uzyskać szczegółowe informacje na temat korzystania z innego pakietu lub udostępniania natywnych plików binarnych oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="b44e5-106">See [Custom SQLite versions](custom-versions.md) for details on using a different bundle or providing your own native SQLite binaries.</span></span>

| <span data-ttu-id="b44e5-107">Platforma</span><span class="sxs-lookup"><span data-stu-id="b44e5-107">Platform</span></span> | <span data-ttu-id="b44e5-108">Pliki binarne oprogramowania SQLite</span><span class="sxs-lookup"><span data-stu-id="b44e5-108">SQLite binaries</span></span> |
| --- | --- |
| <span data-ttu-id="b44e5-109">**Xamarin.Android**</span><span class="sxs-lookup"><span data-stu-id="b44e5-109">**Xamarin.Android**</span></span> | <span data-ttu-id="b44e5-110">—</span><span class="sxs-lookup"><span data-stu-id="b44e5-110">—</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm64-v8a` | <span data-ttu-id="b44e5-111">✔</span><span class="sxs-lookup"><span data-stu-id="b44e5-111">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`armeabi-v7a` | <span data-ttu-id="b44e5-112">✔</span><span class="sxs-lookup"><span data-stu-id="b44e5-112">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86` | <span data-ttu-id="b44e5-113">✔</span><span class="sxs-lookup"><span data-stu-id="b44e5-113">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86_64` | <span data-ttu-id="b44e5-114">✔</span><span class="sxs-lookup"><span data-stu-id="b44e5-114">✔</span></span> |
| <span data-ttu-id="b44e5-115">**Xamarin.iOS**</span><span class="sxs-lookup"><span data-stu-id="b44e5-115">**Xamarin.iOS**</span></span> | <span data-ttu-id="b44e5-116">✔</span><span class="sxs-lookup"><span data-stu-id="b44e5-116">✔</span></span> |
| <span data-ttu-id="b44e5-117">**Xamarin.Mac**</span><span class="sxs-lookup"><span data-stu-id="b44e5-117">**Xamarin.Mac**</span></span> | <span data-ttu-id="b44e5-118">✔</span><span class="sxs-lookup"><span data-stu-id="b44e5-118">✔</span></span> |
| <span data-ttu-id="b44e5-119">**Xamarin. systemu TVOS**</span><span class="sxs-lookup"><span data-stu-id="b44e5-119">**Xamarin.TVOS**</span></span> | <span data-ttu-id="b44e5-120">✔</span><span class="sxs-lookup"><span data-stu-id="b44e5-120">✔</span></span> |
| <span data-ttu-id="b44e5-121">**PLATFORMY UNIWERSALNEJ SYSTEMU WINDOWS**</span><span class="sxs-lookup"><span data-stu-id="b44e5-121">**UWP**</span></span> | <span data-ttu-id="b44e5-122">—</span><span class="sxs-lookup"><span data-stu-id="b44e5-122">—</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm` | <span data-ttu-id="b44e5-123">✔</span><span class="sxs-lookup"><span data-stu-id="b44e5-123">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm64` | <span data-ttu-id="b44e5-124">✔</span><span class="sxs-lookup"><span data-stu-id="b44e5-124">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`x64` | <span data-ttu-id="b44e5-125">✔</span><span class="sxs-lookup"><span data-stu-id="b44e5-125">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86` | <span data-ttu-id="b44e5-126">✔</span><span class="sxs-lookup"><span data-stu-id="b44e5-126">✔</span></span> |

## <a name="ios"></a><span data-ttu-id="b44e5-127">iOS</span><span class="sxs-lookup"><span data-stu-id="b44e5-127">iOS</span></span>

<span data-ttu-id="b44e5-128">Firma Microsoft. Data. sqlite próbuje automatycznie zainicjować zbiory SQLitePCLRaw.</span><span class="sxs-lookup"><span data-stu-id="b44e5-128">Microsoft.Data.Sqlite tries to automatically initialize SQLitePCLRaw bundles.</span></span> <span data-ttu-id="b44e5-129">Niestety, ze względu na ograniczenia w kompilacji z wyprzedzeniem (AOT) dla platformy Xamarin. iOS, próba nie powiedzie się i zostanie wyświetlony następujący błąd.</span><span class="sxs-lookup"><span data-stu-id="b44e5-129">Unfortunately, because of limitations in the ahead-of-time (AOT) compilation for Xamarin.iOS, the attempt fails and you get the following error.</span></span>

> <span data-ttu-id="b44e5-130">Musisz wywołać `SQLitePCL.raw.SetProvider()`.</span><span class="sxs-lookup"><span data-stu-id="b44e5-130">You need to call `SQLitePCL.raw.SetProvider()`.</span></span> <span data-ttu-id="b44e5-131">Jeśli korzystasz z pakietu pakietów, możesz to zrobić, wywołując `SQLitePCL.Batteries.Init()`.</span><span class="sxs-lookup"><span data-stu-id="b44e5-131">If you're using a bundle package, this is done by calling `SQLitePCL.Batteries.Init()`.</span></span>

<span data-ttu-id="b44e5-132">Aby zainicjować pakiet, Dodaj następujący wiersz kodu do aplikacji przed użyciem Microsoft. Data. sqlite.</span><span class="sxs-lookup"><span data-stu-id="b44e5-132">To initialize the bundle, add the following line of code to your app before using Microsoft.Data.Sqlite.</span></span>

```csharp
SQLitePCL.Batteries_V2.Init();
```

## <a name="see-also"></a><span data-ttu-id="b44e5-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b44e5-133">See also</span></span>

* [<span data-ttu-id="b44e5-134">Ograniczenia asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="b44e5-134">Async limitations</span></span>](async.md)
* [<span data-ttu-id="b44e5-135">Niestandardowe wersje programu SQLite</span><span class="sxs-lookup"><span data-stu-id="b44e5-135">Custom SQLite versions</span></span>](custom-versions.md)

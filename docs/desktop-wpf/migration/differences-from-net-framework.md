---
title: Różnice między programem .NET Framework a programem .NET Core
description: W tym artykule opisano różnice między implementacją programu .NET Framework programu Windows Presentation Foundation (WPF) i .NET Core WPF. Podczas migracji aplikacji należy wziąć pod uwagę te niezgodności.
author: thraka
ms.date: 09/21/2019
ms.author: adegeo
ms.openlocfilehash: 341e576f17c522fbcbb9c417176e9d4a13ab1b18
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82072208"
---
# <a name="differences-in-wpf"></a><span data-ttu-id="621fa-104">Różnice w WPF</span><span class="sxs-lookup"><span data-stu-id="621fa-104">Differences in WPF</span></span>

<span data-ttu-id="621fa-105">W tym artykule opisano różnice między programem Windows Presentation Foundation (WPF) w programie .NET Core i .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="621fa-105">This article describes the differences between Windows Presentation Foundation (WPF) on .NET Core and .NET Framework.</span></span> <span data-ttu-id="621fa-106">WPF WPF dla .NET Core jest [platformą open source](https://github.com/dotnet/wpf) rozwidlił z oryginalnego WPF dla .NET Framework kod źródłowy.</span><span class="sxs-lookup"><span data-stu-id="621fa-106">WPF for .NET Core is an [open-source framework](https://github.com/dotnet/wpf) forked from the original WPF for .NET Framework source code.</span></span>

<span data-ttu-id="621fa-107">Istnieje kilka funkcji programu .NET Framework, których program .NET Core nie obsługuje.</span><span class="sxs-lookup"><span data-stu-id="621fa-107">There are a few features of .NET Framework that .NET Core doesn't support.</span></span> <span data-ttu-id="621fa-108">Aby uzyskać więcej informacji na temat nieobsługiwałych technologii, zobacz [.NET Framework technologie niedostępne w programie .NET Core](../../core/porting/net-framework-tech-unavailable.md).</span><span class="sxs-lookup"><span data-stu-id="621fa-108">For more information on unsupported technologies, see [.NET Framework technologies unavailable on .NET Core](../../core/porting/net-framework-tech-unavailable.md).</span></span>

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sdk-style-projects"></a><span data-ttu-id="621fa-109">Projekty w stylu SDK</span><span class="sxs-lookup"><span data-stu-id="621fa-109">SDK-style projects</span></span>

<span data-ttu-id="621fa-110">Program .NET Core używa plików projektu w stylu SDK.</span><span class="sxs-lookup"><span data-stu-id="621fa-110">.NET Core uses SDK-style project files.</span></span> <span data-ttu-id="621fa-111">Te pliki projektu różnią się od tradycyjnych plików projektu .NET Framework zarządzanych przez program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="621fa-111">These project files are different from the traditional .NET Framework project files managed by Visual Studio.</span></span> <span data-ttu-id="621fa-112">Aby przeprowadzić migrację aplikacji .NET Framework WPF do platformy .NET Core, należy przekonwertować projekty.</span><span class="sxs-lookup"><span data-stu-id="621fa-112">To migrate your .NET Framework WPF apps to .NET Core, you must convert your projects.</span></span> <span data-ttu-id="621fa-113">Aby uzyskać więcej informacji, zobacz [Migrowanie aplikacji WPF do platformy .NET Core 3.0](convert-project-from-net-framework.md).</span><span class="sxs-lookup"><span data-stu-id="621fa-113">For more information, see [Migrate WPF apps to .NET Core 3.0](convert-project-from-net-framework.md).</span></span>

## <a name="nuget-package-references"></a><span data-ttu-id="621fa-114">Odwołania do pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="621fa-114">NuGet package references</span></span>

<span data-ttu-id="621fa-115">Jeśli aplikacja .NET Framework wyświetla jej zależności NuGet w pliku *packages.config,* należy przeprowadzić migrację do formatu: [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files)</span><span class="sxs-lookup"><span data-stu-id="621fa-115">If your .NET Framework app lists its NuGet dependencies in a *packages.config* file, migrate to the [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) format:</span></span>

1. <span data-ttu-id="621fa-116">W programie Visual Studio otwórz okienko **Eksploratora rozwiązań.**</span><span class="sxs-lookup"><span data-stu-id="621fa-116">In Visual Studio, open the **Solution Explorer** pane.</span></span>
1. <span data-ttu-id="621fa-117">W projekcie WPF kliknij prawym przyciskiem myszy **packages.config** > **Migrate packages.config to PackageReference**.</span><span class="sxs-lookup"><span data-stu-id="621fa-117">In your WPF project, right-click **packages.config** > **Migrate packages.config to PackageReference**.</span></span>

![Uaktualnianie do packageReference](media/differences-from-net-framework/package-reference-migration.png)

<span data-ttu-id="621fa-119">Pojawi się okno dialogowe pokazujące obliczone zależności NuGet najwyższego poziomu i pytanie, które inne pakiety NuGet powinny być promowane do najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="621fa-119">A dialog will appear showing calculated top-level NuGet dependencies and asking which other NuGet packages should be promoted to top level.</span></span> <span data-ttu-id="621fa-120">Wybierz **przycisk OK,** a plik *packages.config* `<PackageReference>` zostanie usunięty z projektu, a elementy zostaną dodane do pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="621fa-120">Select **OK** and the *packages.config* file will be removed from the project and `<PackageReference>` elements will be added to the project file.</span></span>

<span data-ttu-id="621fa-121">Gdy projekt używa, `<PackageReference>`pakiety nie są przechowywane lokalnie w folderze *Pakiety,* są przechowywane globalnie.</span><span class="sxs-lookup"><span data-stu-id="621fa-121">When your project uses `<PackageReference>`, packages aren't stored locally in a *Packages* folder, they're stored globally.</span></span> <span data-ttu-id="621fa-122">Otwórz plik projektu i `<Analyzer>` usuń wszystkie elementy, które odnoszą się do folderu *Packages.*</span><span class="sxs-lookup"><span data-stu-id="621fa-122">Open the project file and remove any `<Analyzer>` elements that referred to the *Packages* folder.</span></span> <span data-ttu-id="621fa-123">Analizatory te są automatycznie dołączone do odwołań do pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="621fa-123">These analyzers are automatically included with the NuGet package references.</span></span>

## <a name="code-access-security"></a><span data-ttu-id="621fa-124">Zabezpieczenia dostępu kodu</span><span class="sxs-lookup"><span data-stu-id="621fa-124">Code Access Security</span></span>

<span data-ttu-id="621fa-125">Zabezpieczenia dostępu do kodu (CAS) nie są obsługiwane przez program .NET Core ani WPF dla platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="621fa-125">Code Access Security (CAS) is not supported by .NET Core or WPF for .NET Core.</span></span> <span data-ttu-id="621fa-126">Wszystkie funkcje związane z CAS są traktowane przy założeniu pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="621fa-126">All CAS-related functionality is treated under the assumption of full-trust.</span></span> <span data-ttu-id="621fa-127">WPF WPF dla platformy .NET Core usuwa kod związany z CAS.</span><span class="sxs-lookup"><span data-stu-id="621fa-127">WPF for .NET Core removes CAS-related code.</span></span> <span data-ttu-id="621fa-128">Publicznej powierzchni interfejsu API tych typów nadal istnieje, aby upewnić się, że wywołania do tych typów zakończyć się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="621fa-128">The public API surface of these types still exists to ensure that calls into these types succeed.</span></span>

<span data-ttu-id="621fa-129">Publicznie zdefiniowane typy związane z CAS zostały przeniesione z zestawów WPF i do core .NET zestawy biblioteki.</span><span class="sxs-lookup"><span data-stu-id="621fa-129">Publicly defined CAS-related types were moved out of the WPF assemblies and into the Core .NET library assemblies.</span></span> <span data-ttu-id="621fa-130">Zestawy WPF mają zestaw przekazywania tekstu do nowej lokalizacji przeniesionych typów.</span><span class="sxs-lookup"><span data-stu-id="621fa-130">The WPF assemblies have type-forwarding set to the new location of the moved types.</span></span>

| <span data-ttu-id="621fa-131">Zespół źródłowy</span><span class="sxs-lookup"><span data-stu-id="621fa-131">Source assembly</span></span> | <span data-ttu-id="621fa-132">Zestaw docelowy</span><span class="sxs-lookup"><span data-stu-id="621fa-132">Target assembly</span></span> | <span data-ttu-id="621fa-133">Typ</span><span class="sxs-lookup"><span data-stu-id="621fa-133">Type</span></span>                |
| --------------- | --------------- | ------------------- |
| <span data-ttu-id="621fa-134">*Windowsbase.dll*</span><span class="sxs-lookup"><span data-stu-id="621fa-134">*WindowsBase.dll*</span></span> | <span data-ttu-id="621fa-135">*Plik System.Security.Permissions.dll*</span><span class="sxs-lookup"><span data-stu-id="621fa-135">*System.Security.Permissions.dll*</span></span> | <xref:System.Security.Permissions.MediaPermission> <br /> <xref:System.Security.Permissions.MediaPermissionAttribute> <br /> <xref:System.Security.Permissions.MediaPermissionAudio> <br /> <xref:System.Security.Permissions.MediaPermissionImage> <br /> <xref:System.Security.Permissions.MediaPermissionVideo> <br /> <xref:System.Security.Permissions.WebBrowserPermission> <br /> <xref:System.Security.Permissions.WebBrowserPermissionAttribute> <br /> <xref:System.Security.Permissions.WebBrowserPermissionLevel> |
| <span data-ttu-id="621fa-136">*Plik System.Xaml.dll*</span><span class="sxs-lookup"><span data-stu-id="621fa-136">*System.Xaml.dll*</span></span> | <span data-ttu-id="621fa-137">*Plik System.Security.Permissions.dll*</span><span class="sxs-lookup"><span data-stu-id="621fa-137">*System.Security.Permissions.dll*</span></span> | <xref:System.Xaml.Permissions.XamlLoadPermission> |
| <span data-ttu-id="621fa-138">*Plik System.Xaml.dll*</span><span class="sxs-lookup"><span data-stu-id="621fa-138">*System.Xaml.dll*</span></span> | <span data-ttu-id="621fa-139">*Plik System.Windows.Extension.dll*</span><span class="sxs-lookup"><span data-stu-id="621fa-139">*System.Windows.Extension.dll*</span></span>    | <xref:System.Xaml.Permissions.XamlAccessLevel><br/> |

> [!NOTE]
> <span data-ttu-id="621fa-140">Aby zminimalizować tarcie portów, funkcje przechowywania i pobierania informacji związanych z następującymi `XamlAccessLevel` właściwościami zostały zachowane w typie.</span><span class="sxs-lookup"><span data-stu-id="621fa-140">In order to minimize porting friction, the functionality for storing and retrieving information related to the following properties was retained in the `XamlAccessLevel` type.</span></span>
>
> - `PrivateAccessToTypeName`
> - `AssemblyNameString`

## <a name="next-steps"></a><span data-ttu-id="621fa-141">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="621fa-141">Next steps</span></span>

- [<span data-ttu-id="621fa-142">Dowiedz się, jak przenieść aplikację .NET Framework WPF do platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="621fa-142">Learn how to port a .NET Framework WPF app to .NET Core.</span></span>](convert-project-from-net-framework.md)

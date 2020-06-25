---
title: Różnice między .NET Framework i .NET Core
description: Opisuje różnice między implementacją .NET Framework Windows Presentation Foundation (WPF) i .NET Core WPF. Podczas migrowania aplikacji należy wziąć pod uwagę te niezgodności.
author: adegeo
ms.date: 09/21/2019
ms.author: adegeo
ms.openlocfilehash: 3bedc30046c36d4c5430feedf5854276ebaef8aa
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325691"
---
# <a name="differences-in-wpf"></a><span data-ttu-id="f01df-104">Różnice w WPF</span><span class="sxs-lookup"><span data-stu-id="f01df-104">Differences in WPF</span></span>

<span data-ttu-id="f01df-105">W tym artykule opisano różnice między Windows Presentation Foundation (WPF) na platformie .NET Core i .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f01df-105">This article describes the differences between Windows Presentation Foundation (WPF) on .NET Core and .NET Framework.</span></span> <span data-ttu-id="f01df-106">WPF for .NET Core to [Struktura "open source"](https://github.com/dotnet/wpf) powarta na podstawie oryginalnego programu WPF dla .NET Framework kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="f01df-106">WPF for .NET Core is an [open-source framework](https://github.com/dotnet/wpf) forked from the original WPF for .NET Framework source code.</span></span>

<span data-ttu-id="f01df-107">Istnieje kilka funkcji .NET Framework, które nie są obsługiwane przez platformę .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f01df-107">There are a few features of .NET Framework that .NET Core doesn't support.</span></span> <span data-ttu-id="f01df-108">Aby uzyskać więcej informacji na temat nieobsługiwanych technologii, zobacz [technologie .NET Framework niedostępne w programie .NET Core](../../core/porting/net-framework-tech-unavailable.md).</span><span class="sxs-lookup"><span data-stu-id="f01df-108">For more information on unsupported technologies, see [.NET Framework technologies unavailable on .NET Core](../../core/porting/net-framework-tech-unavailable.md).</span></span>

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sdk-style-projects"></a><span data-ttu-id="f01df-109">Projekty w stylu zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="f01df-109">SDK-style projects</span></span>

<span data-ttu-id="f01df-110">.NET Core używa plików projektu w stylu zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="f01df-110">.NET Core uses SDK-style project files.</span></span> <span data-ttu-id="f01df-111">Te pliki projektu różnią się od tradycyjnych plików projektu .NET Framework zarządzanych przez program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f01df-111">These project files are different from the traditional .NET Framework project files managed by Visual Studio.</span></span> <span data-ttu-id="f01df-112">Aby migrować .NET Framework aplikacje WPF do programu .NET Core, należy przekonwertować projekty.</span><span class="sxs-lookup"><span data-stu-id="f01df-112">To migrate your .NET Framework WPF apps to .NET Core, you must convert your projects.</span></span> <span data-ttu-id="f01df-113">Aby uzyskać więcej informacji, zobacz [Migrowanie aplikacji WPF do programu .NET Core 3,0](convert-project-from-net-framework.md).</span><span class="sxs-lookup"><span data-stu-id="f01df-113">For more information, see [Migrate WPF apps to .NET Core 3.0](convert-project-from-net-framework.md).</span></span>

## <a name="nuget-package-references"></a><span data-ttu-id="f01df-114">Odwołania do pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="f01df-114">NuGet package references</span></span>

<span data-ttu-id="f01df-115">Jeśli Twoja aplikacja .NET Framework wyświetli zależności NuGet w pliku *packages.config* , Przeprowadź migrację do [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) formatu:</span><span class="sxs-lookup"><span data-stu-id="f01df-115">If your .NET Framework app lists its NuGet dependencies in a *packages.config* file, migrate to the [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) format:</span></span>

1. <span data-ttu-id="f01df-116">W programie Visual Studio Otwórz okienko **Eksplorator rozwiązań** .</span><span class="sxs-lookup"><span data-stu-id="f01df-116">In Visual Studio, open the **Solution Explorer** pane.</span></span>
1. <span data-ttu-id="f01df-117">W projekcie WPF kliknij prawym przyciskiem myszy **packages.config**  >  **zmigrować packages.config do PackageReference**.</span><span class="sxs-lookup"><span data-stu-id="f01df-117">In your WPF project, right-click **packages.config** > **Migrate packages.config to PackageReference**.</span></span>

![Uaktualnianie do PackageReference](media/differences-from-net-framework/package-reference-migration.png)

<span data-ttu-id="f01df-119">Zostanie wyświetlone okno dialogowe przedstawiające obliczone zależności NuGet najwyższego poziomu i pytanie, które inne pakiety NuGet mają być podwyższenie poziomu.</span><span class="sxs-lookup"><span data-stu-id="f01df-119">A dialog will appear showing calculated top-level NuGet dependencies and asking which other NuGet packages should be promoted to top level.</span></span> <span data-ttu-id="f01df-120">Wybierz **przycisk OK** , a plik *packages.config* zostanie usunięty z projektu, a `<PackageReference>` elementy zostaną dodane do pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="f01df-120">Select **OK** and the *packages.config* file will be removed from the project and `<PackageReference>` elements will be added to the project file.</span></span>

<span data-ttu-id="f01df-121">Gdy Twój projekt `<PackageReference>` jest używany, pakiety nie są przechowywane lokalnie w folderze *Packages* , są przechowywane globalnie.</span><span class="sxs-lookup"><span data-stu-id="f01df-121">When your project uses `<PackageReference>`, packages aren't stored locally in a *Packages* folder, they're stored globally.</span></span> <span data-ttu-id="f01df-122">Otwórz plik projektu i Usuń wszystkie `<Analyzer>` elementy, które odwołują się do folderu *Packages* .</span><span class="sxs-lookup"><span data-stu-id="f01df-122">Open the project file and remove any `<Analyzer>` elements that referred to the *Packages* folder.</span></span> <span data-ttu-id="f01df-123">Te analizatory są automatycznie dołączane do odwołania do pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="f01df-123">These analyzers are automatically included with the NuGet package references.</span></span>

## <a name="code-access-security"></a><span data-ttu-id="f01df-124">Zabezpieczenia dostępu kodu</span><span class="sxs-lookup"><span data-stu-id="f01df-124">Code Access Security</span></span>

<span data-ttu-id="f01df-125">Zabezpieczenia dostępu kodu (CAS) nie są obsługiwane przez platformę .NET Core lub WPF dla platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f01df-125">Code Access Security (CAS) is not supported by .NET Core or WPF for .NET Core.</span></span> <span data-ttu-id="f01df-126">Wszystkie funkcje związane z urzędem certyfikacji są traktowane w ramach założeń pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="f01df-126">All CAS-related functionality is treated under the assumption of full-trust.</span></span> <span data-ttu-id="f01df-127">Program WPF for .NET Core usuwa kod związany z urzędem certyfikacji.</span><span class="sxs-lookup"><span data-stu-id="f01df-127">WPF for .NET Core removes CAS-related code.</span></span> <span data-ttu-id="f01df-128">Publiczna powierzchnia interfejsu API tych typów nadal istnieje, aby upewnić się, że wywołania do tych typów powiodło się.</span><span class="sxs-lookup"><span data-stu-id="f01df-128">The public API surface of these types still exists to ensure that calls into these types succeed.</span></span>

<span data-ttu-id="f01df-129">Publicznie zdefiniowane typy związane z urzędem certyfikacji zostały przeniesione z zestawów WPF i do zestawów podstawowych bibliotek platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="f01df-129">Publicly defined CAS-related types were moved out of the WPF assemblies and into the Core .NET library assemblies.</span></span> <span data-ttu-id="f01df-130">Zestawy WPF mają ustawioną funkcję przesyłania dalej typu na nową lokalizację przenoszonych typów.</span><span class="sxs-lookup"><span data-stu-id="f01df-130">The WPF assemblies have type-forwarding set to the new location of the moved types.</span></span>

| <span data-ttu-id="f01df-131">Zestaw źródłowy</span><span class="sxs-lookup"><span data-stu-id="f01df-131">Source assembly</span></span> | <span data-ttu-id="f01df-132">Zestaw docelowy</span><span class="sxs-lookup"><span data-stu-id="f01df-132">Target assembly</span></span> | <span data-ttu-id="f01df-133">Typ</span><span class="sxs-lookup"><span data-stu-id="f01df-133">Type</span></span>                |
| --------------- | --------------- | ------------------- |
| <span data-ttu-id="f01df-134">*WindowsBase.dll*</span><span class="sxs-lookup"><span data-stu-id="f01df-134">*WindowsBase.dll*</span></span> | <span data-ttu-id="f01df-135">*System.Security.Permissions.dll*</span><span class="sxs-lookup"><span data-stu-id="f01df-135">*System.Security.Permissions.dll*</span></span> | <xref:System.Security.Permissions.MediaPermission> <br /> <xref:System.Security.Permissions.MediaPermissionAttribute> <br /> <xref:System.Security.Permissions.MediaPermissionAudio> <br /> <xref:System.Security.Permissions.MediaPermissionImage> <br /> <xref:System.Security.Permissions.MediaPermissionVideo> <br /> <xref:System.Security.Permissions.WebBrowserPermission> <br /> <xref:System.Security.Permissions.WebBrowserPermissionAttribute> <br /> <xref:System.Security.Permissions.WebBrowserPermissionLevel> |
| <span data-ttu-id="f01df-136">*System.Xaml.dll*</span><span class="sxs-lookup"><span data-stu-id="f01df-136">*System.Xaml.dll*</span></span> | <span data-ttu-id="f01df-137">*System.Security.Permissions.dll*</span><span class="sxs-lookup"><span data-stu-id="f01df-137">*System.Security.Permissions.dll*</span></span> | <xref:System.Xaml.Permissions.XamlLoadPermission> |
| <span data-ttu-id="f01df-138">*System.Xaml.dll*</span><span class="sxs-lookup"><span data-stu-id="f01df-138">*System.Xaml.dll*</span></span> | <span data-ttu-id="f01df-139">*System.Windows.Extension.dll*</span><span class="sxs-lookup"><span data-stu-id="f01df-139">*System.Windows.Extension.dll*</span></span>    | <xref:System.Xaml.Permissions.XamlAccessLevel><br/> |

> [!NOTE]
> <span data-ttu-id="f01df-140">Aby zminimalizować tarcie do przenoszenia, funkcje przechowywania i pobierania informacji związanych z poniższymi właściwościami zostały zachowane w `XamlAccessLevel` typie.</span><span class="sxs-lookup"><span data-stu-id="f01df-140">In order to minimize porting friction, the functionality for storing and retrieving information related to the following properties was retained in the `XamlAccessLevel` type.</span></span>
>
> - `PrivateAccessToTypeName`
> - `AssemblyNameString`

## <a name="next-steps"></a><span data-ttu-id="f01df-141">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="f01df-141">Next steps</span></span>

- [<span data-ttu-id="f01df-142">Dowiedz się, jak portować .NET Framework aplikację WPF do programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f01df-142">Learn how to port a .NET Framework WPF app to .NET Core.</span></span>](convert-project-from-net-framework.md)

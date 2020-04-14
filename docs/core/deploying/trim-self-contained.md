---
title: Przycinanie samodzielnych aplikacji
description: Dowiedz się, jak przycinać samodzielne aplikacje, aby zmniejszyć ich rozmiar. .NET Core pakiety środowiska wykonawczego z aplikacją, która jest publikowana samodzielnie i zazwyczaj zawiera więcej środowiska wykonawczego, a następnie jest konieczne.
author: jamshedd
ms.author: jamshedd
ms.date: 04/03/2020
ms.openlocfilehash: bb8ac88c5e16b7fd20a7670e4ad76dbe4b44da1b
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242924"
---
# <a name="trim-self-contained-deployments-and-executables"></a><span data-ttu-id="0a5f5-104">Przycinanie samodzielnych wdrożeń i plików wykonywalnych</span><span class="sxs-lookup"><span data-stu-id="0a5f5-104">Trim self-contained deployments and executables</span></span>

<span data-ttu-id="0a5f5-105">Podczas publikowania aplikacji samodzielny, .NET Core środowiska uruchomieniowego jest powiązany z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="0a5f5-105">When publishing an application self-contained, the .NET Core runtime is bundled together with the application.</span></span> <span data-ttu-id="0a5f5-106">Ten pakiet dodaje znaczną ilość zawartości do spakowanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0a5f5-106">This bundling adds a significant amount of content to your packaged application.</span></span> <span data-ttu-id="0a5f5-107">Jeśli chodzi o wdrażanie aplikacji, rozmiar jest często ważnym czynnikiem.</span><span class="sxs-lookup"><span data-stu-id="0a5f5-107">When it comes to deploying your application, size is often an important factor.</span></span> <span data-ttu-id="0a5f5-108">Utrzymanie rozmiaru aplikacji pakietu tak małe, jak to możliwe jest zazwyczaj celem dla deweloperów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0a5f5-108">Keeping the size of the package application as small as possible is typically a goal for application developers.</span></span>

<span data-ttu-id="0a5f5-109">W zależności od złożoności aplikacji do uruchomienia aplikacji wymagany jest tylko podzbiór środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="0a5f5-109">Depending on the complexity of the application, only a subset of the runtime is required to run the application.</span></span> <span data-ttu-id="0a5f5-110">Te nieużywane części środowiska wykonawczego są niepotrzebne i mogą być przycinane z spakowanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0a5f5-110">These unused parts of the runtime are unnecessary and can be trimmed from the packaged application.</span></span>

<span data-ttu-id="0a5f5-111">Funkcja przycinania działa przez sprawdzenie plików binarnych aplikacji w celu odnajdywania i tworzenia wykresu wymaganych zestawów środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="0a5f5-111">The trimming feature works by examining the application binaries to discover and build a graph of the required runtime assemblies.</span></span> <span data-ttu-id="0a5f5-112">Pozostałe zestawy środowiska wykonawczego, do których nie istnieją odwołania, są wykluczone.</span><span class="sxs-lookup"><span data-stu-id="0a5f5-112">The remaining runtime assemblies that aren't referenced are excluded.</span></span>

> [!NOTE]
> <span data-ttu-id="0a5f5-113">Przycinanie jest funkcją eksperymentalną w .NET Core 3.1 i jest dostępne _tylko_ dla aplikacji, które są publikowane samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="0a5f5-113">Trimming is an experimental feature in .NET Core 3.1 and is _only_ available to applications that are published self-contained.</span></span>

## <a name="prevent-assemblies-from-being-trimmed"></a><span data-ttu-id="0a5f5-114">Zapobieganie przycinaniu zespołów</span><span class="sxs-lookup"><span data-stu-id="0a5f5-114">Prevent assemblies from being trimmed</span></span>

<span data-ttu-id="0a5f5-115">Istnieją scenariusze, w których funkcja przycinania nie będzie wykryć odwołań.</span><span class="sxs-lookup"><span data-stu-id="0a5f5-115">There are scenarios in which the trimming functionality will fail to detect references.</span></span> <span data-ttu-id="0a5f5-116">Na przykład gdy odbicie jest używany w zestawie środowiska wykonawczego, przez aplikację lub biblioteki, do którego odwołuje się aplikacja, zestaw nie jest bezpośrednio odwołuje.</span><span class="sxs-lookup"><span data-stu-id="0a5f5-116">For example, when reflection is used on a runtime assembly, either by your application or a library that is referenced by your application, the assembly isn't directly referenced.</span></span> <span data-ttu-id="0a5f5-117">Przycinanie nie jest świadomy tych pośrednich odwołań i wyklucza bibliotekę z opublikowanego folderu.</span><span class="sxs-lookup"><span data-stu-id="0a5f5-117">Trimming is unaware of these indirect references and would exclude the library from the published folder.</span></span>

<span data-ttu-id="0a5f5-118">Gdy kod pośrednio odwołuje się do złożenia za pomocą odbicia, można zapobiec `<TrimmerRootAssembly>` przycinaniu złożenia z ustawieniem.</span><span class="sxs-lookup"><span data-stu-id="0a5f5-118">When the code is indirectly referencing an assembly through reflection, you can prevent the assembly from being trimmed with the `<TrimmerRootAssembly>` setting.</span></span> <span data-ttu-id="0a5f5-119">W poniższym przykładzie pokazano, `System.Security` jak zapobiec przycinaniu zestawu o nazwie zestawu:</span><span class="sxs-lookup"><span data-stu-id="0a5f5-119">The following example shows how to prevent an assembly called `System.Security` assembly from being trimmed:</span></span>

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="trim-your-app---cli"></a><span data-ttu-id="0a5f5-120">Przycinanie aplikacji - CLI</span><span class="sxs-lookup"><span data-stu-id="0a5f5-120">Trim your app - CLI</span></span>

<span data-ttu-id="0a5f5-121">Przytnij aplikację za pomocą polecenia [publikowania dotnet.](../tools/dotnet-publish.md)</span><span class="sxs-lookup"><span data-stu-id="0a5f5-121">Trim your application using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="0a5f5-122">Podczas publikowania aplikacji ustaw następujące trzy ustawienia:</span><span class="sxs-lookup"><span data-stu-id="0a5f5-122">When you publish your app, set the following three settings:</span></span>

- <span data-ttu-id="0a5f5-123">Publikować jako samodzielne:`--self-contained true`</span><span class="sxs-lookup"><span data-stu-id="0a5f5-123">Publish as self-contained: `--self-contained true`</span></span>
- <span data-ttu-id="0a5f5-124">Wyłącz publikowanie pojedynczych plików:`-p:PublishSingleFile=false`</span><span class="sxs-lookup"><span data-stu-id="0a5f5-124">Disable single-file publishing: `-p:PublishSingleFile=false`</span></span>
- <span data-ttu-id="0a5f5-125">Włącz przycinanie:`p:PublishTrimmed=true`</span><span class="sxs-lookup"><span data-stu-id="0a5f5-125">Enable trimming: `p:PublishTrimmed=true`</span></span>

<span data-ttu-id="0a5f5-126">Poniższy przykład publikuje aplikację dla systemu Windows 10 jako samodzielną i przycina dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="0a5f5-126">The following example publishes an app for Windows 10 as self-contained and trims the output.</span></span>

```dotnetcli
dotnet publish -c Release -r win10-x64 --self-contained true -p:PublishSingleFile=false -p:PublishTrimmed=true
```

<span data-ttu-id="0a5f5-127">Aby uzyskać więcej informacji, zobacz [Publikowanie aplikacji .NET Core w pliku .NET Core CLI](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="0a5f5-127">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="trim-your-app---visual-studio"></a><span data-ttu-id="0a5f5-128">Przycinanie aplikacji — Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0a5f5-128">Trim your app - Visual Studio</span></span>

<span data-ttu-id="0a5f5-129">Visual Studio tworzy profile publikowania wielokrotnegoużytnia, które kontrolują sposób publikowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0a5f5-129">Visual Studio creates reusable publishing profiles that control how your application is published.</span></span>

01. <span data-ttu-id="0a5f5-130">W okienku **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt, który chcesz opublikować.</span><span class="sxs-lookup"><span data-stu-id="0a5f5-130">On the **Solution Explorer** pane, right-click on the project you want to publish.</span></span> <span data-ttu-id="0a5f5-131">Wybierz **pozycję Publikuj...**.</span><span class="sxs-lookup"><span data-stu-id="0a5f5-131">Select **Publish...**.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-solution-explorer.png" alt-text="Eksplorator rozwiązań z menu z zaznaczonym prawym przyciskiem myszy z zaznaczoną opcją Publikuj.":::

    <span data-ttu-id="0a5f5-133">Jeśli nie masz jeszcze profilu publikowania, postępuj zgodnie z instrukcjami, aby go utworzyć i wybrać typ docelowy **folderu.**</span><span class="sxs-lookup"><span data-stu-id="0a5f5-133">If you don't already have a publishing profile, follow the instructions to create one and choose the **Folder** target-type.</span></span>

01. <span data-ttu-id="0a5f5-134">Wybierz **pozycję Edytuj**.</span><span class="sxs-lookup"><span data-stu-id="0a5f5-134">Choose **Edit**.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-edit-settings.png" alt-text="Profil publikowania w programie Visual Studio za pomocą przycisku edycji.":::

01. <span data-ttu-id="0a5f5-136">W oknie dialogowym **Ustawienia profilu** ustaw następujące opcje:</span><span class="sxs-lookup"><span data-stu-id="0a5f5-136">In the **Profile settings** dialog, set the following options:</span></span>

    - <span data-ttu-id="0a5f5-137">Ustaw **tryb wdrażania** na **samodzielny**.</span><span class="sxs-lookup"><span data-stu-id="0a5f5-137">Set **Deployment mode** to **Self-contained**.</span></span>
    - <span data-ttu-id="0a5f5-138">Ustaw **docelowe środowisko uruchomieniowe** na platformie, na której chcesz opublikować.</span><span class="sxs-lookup"><span data-stu-id="0a5f5-138">Set **Target runtime** to the platform you want to publish to.</span></span>
    - <span data-ttu-id="0a5f5-139">Wybierz **pozycję Przytnij nieużywane złożenia (w podglądzie)**.</span><span class="sxs-lookup"><span data-stu-id="0a5f5-139">Select **Trim unused assemblies (in preview)**.</span></span>

    <span data-ttu-id="0a5f5-140">Wybierz **pozycję Zapisz,** aby zapisać ustawienia i powrócić do okna dialogowego **Publikowanie.**</span><span class="sxs-lookup"><span data-stu-id="0a5f5-140">Choose **Save** to save the settings and return to the **Publish** dialog.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-properties.png" alt-text="Okno dialogowe Ustawień profilu z wyróżnionym trybem wdrażania, docelowym środowiskiem uruchomieniowym i przycinaniem nieużywanych zestawów.":::

01. <span data-ttu-id="0a5f5-142">Wybierz **pozycję Publikuj,** aby opublikować przycięcie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0a5f5-142">Choose **Publish** to publish your app trimmed.</span></span>

<span data-ttu-id="0a5f5-143">Aby uzyskać więcej informacji, zobacz [Publikowanie aplikacji .NET Core w programie Visual Studio](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="0a5f5-143">For more information, see [Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>

## <a name="trim-your-app---visual-studio-for-mac"></a><span data-ttu-id="0a5f5-144">Przycinanie aplikacji — Visual Studio dla komputerów Mac</span><span class="sxs-lookup"><span data-stu-id="0a5f5-144">Trim your app - Visual Studio for Mac</span></span>

<span data-ttu-id="0a5f5-145">Program Visual Studio dla komputerów Mac nie udostępnia opcji przycinania aplikacji podczas publikowania.</span><span class="sxs-lookup"><span data-stu-id="0a5f5-145">Visual Studio for Mac doesn't provide options to trim your app during publish.</span></span> <span data-ttu-id="0a5f5-146">Musisz opublikować ręcznie, postępując zgodnie z instrukcjami z sekcji [Przytnij aplikację — cli.](#trim-your-app---cli)</span><span class="sxs-lookup"><span data-stu-id="0a5f5-146">You'll need to publish manually by following the instructions from the [Trim your app - CLI](#trim-your-app---cli) section.</span></span> <span data-ttu-id="0a5f5-147">Aby uzyskać więcej informacji, zobacz [Publikowanie aplikacji .NET Core w pliku .NET Core CLI](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="0a5f5-147">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0a5f5-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0a5f5-148">See also</span></span>

- <span data-ttu-id="0a5f5-149">[Wdrożenie aplikacji .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="0a5f5-149">[.NET Core application deployment](index.md).</span></span>
- <span data-ttu-id="0a5f5-150">[Publikowanie aplikacji .NET Core za pomocą interfejsu wiersza polecenia .NET Core](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="0a5f5-150">[Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>
- <span data-ttu-id="0a5f5-151">[Publikowanie aplikacji .NET Core w programie Visual Studio](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="0a5f5-151">[Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>
- <span data-ttu-id="0a5f5-152">[polecenie publikowania dotnet](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="0a5f5-152">[dotnet publish command](../tools/dotnet-publish.md).</span></span>

---
title: Przycinanie samodzielnych aplikacji
description: Dowiedz się, jak przycinać samodzielne aplikacje, aby zmniejszyć ich rozmiar. .NET Core pakiety środowiska wykonawczego z aplikacją, która jest publikowana samodzielnie i zazwyczaj zawiera więcej środowiska wykonawczego, a następnie jest konieczne.
author: jamshedd
ms.author: jamshedd
ms.date: 01/23/2020
ms.openlocfilehash: 5206ca255c500b382402ac4e7dd3300b7face1cf
ms.sourcegitcommit: 45cced471d59d5dac3f0c92abc9d4849716098a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/04/2020
ms.locfileid: "80665636"
---
# <a name="trim-self-contained-deployments-and-executables"></a><span data-ttu-id="aad12-104">Przycinanie samodzielnych wdrożeń i plików wykonywalnych</span><span class="sxs-lookup"><span data-stu-id="aad12-104">Trim self-contained deployments and executables</span></span>

<span data-ttu-id="aad12-105">Podczas publikowania aplikacji samodzielny, .NET Core środowiska uruchomieniowego jest powiązany z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="aad12-105">When publishing an application self-contained, the .NET Core runtime is bundled together with the application.</span></span> <span data-ttu-id="aad12-106">Ten pakiet dodaje znaczną ilość zawartości do spakowanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aad12-106">This bundling adds a significant amount of content to your packaged application.</span></span>

<span data-ttu-id="aad12-107">Jeśli chodzi o wdrażanie aplikacji, rozmiar jest często ważnym czynnikiem.</span><span class="sxs-lookup"><span data-stu-id="aad12-107">When it comes to deploying your application, size is often an important factor.</span></span> <span data-ttu-id="aad12-108">Utrzymanie rozmiaru aplikacji pakietu tak małe, jak to możliwe jest zazwyczaj celem dla deweloperów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aad12-108">Keeping the size of the package application as small as possible is typically a goal for application developers.</span></span>

<span data-ttu-id="aad12-109">W zależności od złożoności aplikacji do uruchomienia aplikacji wymagany jest tylko podzbiór środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="aad12-109">Depending on the complexity of the application, only a subset of the runtime is required to run the application.</span></span> <span data-ttu-id="aad12-110">Te nieużywane części środowiska wykonawczego są niepotrzebne i mogą być przycinane z spakowanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aad12-110">These unused parts of the runtime are unnecessary and can be trimmed from the packaged application.</span></span>

> [!NOTE]
> <span data-ttu-id="aad12-111">Przycinanie jest funkcją eksperymentalną w .NET Core 3.1 i jest dostępne _tylko_ dla aplikacji, które są publikowane samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="aad12-111">Trimming is an experimental feature in .NET Core 3.1 and is _only_ available to applications that are published self-contained.</span></span>

## <a name="trim-your-application"></a><span data-ttu-id="aad12-112">Przycinanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="aad12-112">Trim your application</span></span>

<span data-ttu-id="aad12-113">W poniższym przykładzie pokazano, jak przyciąć aplikację za pomocą polecenia [publikowania dotnetu:](../tools/dotnet-publish.md)</span><span class="sxs-lookup"><span data-stu-id="aad12-113">The following example shows how to trim your application using the [dotnet publish](../tools/dotnet-publish.md) command:</span></span>

```dotnetcli
dotnet publish -c Release -r win10-x64 --self-contained true /p:PublishSingleFile=false /p:PublishTrimmed=true
```

<span data-ttu-id="aad12-114">Funkcja przycinania działa przez sprawdzenie plików binarnych aplikacji w celu odnajdywania i tworzenia wykresu wymaganych zestawów środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="aad12-114">The trimming feature works by examining the application binaries to discover and build a graph of the required runtime assemblies.</span></span> <span data-ttu-id="aad12-115">Pozostałe zestawy środowiska wykonawczego, do których nie ma odniesienia, są przycinane.</span><span class="sxs-lookup"><span data-stu-id="aad12-115">The remaining runtime assemblies that aren't referenced are trimmed.</span></span>

## <a name="trimming-issues-when-using-reflection"></a><span data-ttu-id="aad12-116">Problemy z przycinaniem podczas korzystania z odbicia</span><span class="sxs-lookup"><span data-stu-id="aad12-116">Trimming issues when using reflection</span></span>

<span data-ttu-id="aad12-117">Istnieją scenariusze, w których funkcja przycinania nie będzie wykryć odwołań.</span><span class="sxs-lookup"><span data-stu-id="aad12-117">There are scenarios in which the trimming functionality will fail to detect references.</span></span> <span data-ttu-id="aad12-118">Na przykład aplikacja, która używa odbicia może uruchomić w tym problemie, ponieważ zależność od zestawu będzie znana tylko w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="aad12-118">For example, an application that uses reflection could run into this issue because the dependency on the assembly will only be known at run time.</span></span>

<span data-ttu-id="aad12-119">Przycinanie jest tylko problem, jeśli użycie odbicia zależy od zestawu środowiska wykonawczego, który nie odwołuje się bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="aad12-119">Trimming is only a problem if the reflection usage depends on a runtime assembly that isn't referenced directly.</span></span> <span data-ttu-id="aad12-120">Należy pamiętać, że kod aplikacji może nie używać odbicia bezpośrednio, ale zestaw innych firm, do którego się odwołujesz, może go używać.</span><span class="sxs-lookup"><span data-stu-id="aad12-120">Keep in mind that your application code may not be using reflection directly, but a third-party assembly you're referencing may be using it.</span></span>

<span data-ttu-id="aad12-121">Gdy kod odwołuje się do interfejsu API za pomocą odbicia i nie chcesz, aby konsolidator przycinał zestaw zawierający ten interfejs API, można zmodyfikować plik projektu, aby wykluczyć zestaw z procesu przycinania.</span><span class="sxs-lookup"><span data-stu-id="aad12-121">When the code is referencing an API through reflection and you don't want the linker to trim the assembly that contains that API, you can modify your project file to exclude the assembly from the trimming process.</span></span> <span data-ttu-id="aad12-122">W poniższym przykładzie pokazano, `System.Security` jak zapobiec przycinaniu zestawu wywoływanego:</span><span class="sxs-lookup"><span data-stu-id="aad12-122">The following example shows how to prevent an assembly called `System.Security` from being trimmed:</span></span>

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="see-also"></a><span data-ttu-id="aad12-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aad12-123">See also</span></span>

- [<span data-ttu-id="aad12-124">Wdrożenie aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="aad12-124">.NET Core application deployment</span></span>](index.md)

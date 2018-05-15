---
title: -subsystemversion (opcje kompilatora C#)
ms.date: 07/20/2015
ms.assetid: a99fce81-9d92-4813-9874-bee777041445
ms.openlocfilehash: 25391dd504fb8a2b9458fd9495477258fc23d81a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-subsystemversion-c-compiler-options"></a><span data-ttu-id="c5673-102">-subsystemversion (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="c5673-102">-subsystemversion (C# Compiler Options)</span></span>
<span data-ttu-id="c5673-103">Określa minimalną wersję podsystemu, na którym można uruchomić wygenerowanego pliku wykonywalnego, określając wersje systemu Windows, na którym można uruchomić pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="c5673-103">Specifies the minimum version of the subsystem on which the generated executable file can run, thereby determining the versions of Windows on which the executable file can run.</span></span> <span data-ttu-id="c5673-104">Najczęściej ta opcja zapewnia, że plik wykonywalny mogą korzystać z funkcji zabezpieczeń, które nie są dostępne w starszych wersjach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="c5673-104">Most commonly, this option ensures that the executable file can leverage particular security features that aren’t available with older versions of Windows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5673-105">Aby określić podsystem, użyj [-docelowy](../../../csharp/language-reference/compiler-options/target-compiler-option.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="c5673-105">To specify the subsystem itself, use the [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) compiler option.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5673-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5673-106">Syntax</span></span>  
  
```console  
-subsystemversion:major.minor  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5673-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5673-107">Parameters</span></span>  
 `major.minor`  
 <span data-ttu-id="c5673-108">Minimalna wymagana wersja podsystemu, wyrażone w kropkowego dla wersji głównej i pomocniczej.</span><span class="sxs-lookup"><span data-stu-id="c5673-108">The minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="c5673-109">Na przykład można określić, że aplikacja nie można uruchomić w systemie operacyjnym, który jest starsze niż Windows 7 można ustawić wartości tej opcji 6.01, zgodnie z opisem w tabeli w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="c5673-109">For example, you can specify that an application can't run on an operating system that's older than Windows 7 if you set the value of this option to 6.01, as the table later in this topic describes.</span></span> <span data-ttu-id="c5673-110">Należy określić wartości `major` i `minor` liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="c5673-110">You must specify the values for `major` and `minor` as integers.</span></span>  
  
 <span data-ttu-id="c5673-111">Wiodące wyzerowania `minor` wersji nie zmieniają wersji, ale czy końcowe zera.</span><span class="sxs-lookup"><span data-stu-id="c5673-111">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="c5673-112">Na przykład 6.1 i 6.01 odwołują się do tej samej wersji, ale 6.10 odwołuje się do innej wersji.</span><span class="sxs-lookup"><span data-stu-id="c5673-112">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="c5673-113">Firma Microsoft zaleca, przedstawiając wersja pomocnicza jako dwie cyfry, aby uniknąć pomyłek.</span><span class="sxs-lookup"><span data-stu-id="c5673-113">We recommend expressing the minor version as two digits to avoid confusion.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5673-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c5673-114">Remarks</span></span>  
 <span data-ttu-id="c5673-115">W poniższej tabeli wymieniono typowe podsystemu wersjach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="c5673-115">The following table lists common subsystem versions of Windows.</span></span>  
  
|<span data-ttu-id="c5673-116">Wersja systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c5673-116">Windows version</span></span>|<span data-ttu-id="c5673-117">Wersję podsystemu</span><span class="sxs-lookup"><span data-stu-id="c5673-117">Subsystem version</span></span>|  
|---------------------|-----------------------|  
|<span data-ttu-id="c5673-118">Windows 2000</span><span class="sxs-lookup"><span data-stu-id="c5673-118">Windows 2000</span></span>|<span data-ttu-id="c5673-119">5.00</span><span class="sxs-lookup"><span data-stu-id="c5673-119">5.00</span></span>|  
|<span data-ttu-id="c5673-120">Windows XP</span><span class="sxs-lookup"><span data-stu-id="c5673-120">Windows XP</span></span>|<span data-ttu-id="c5673-121">5.01</span><span class="sxs-lookup"><span data-stu-id="c5673-121">5.01</span></span>|  
|<span data-ttu-id="c5673-122">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="c5673-122">Windows Server 2003</span></span>|<span data-ttu-id="c5673-123">5.02</span><span class="sxs-lookup"><span data-stu-id="c5673-123">5.02</span></span>|  
|<span data-ttu-id="c5673-124">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="c5673-124">Windows Vista</span></span>|<span data-ttu-id="c5673-125">6.00</span><span class="sxs-lookup"><span data-stu-id="c5673-125">6.00</span></span>|  
|<span data-ttu-id="c5673-126">Windows 7</span><span class="sxs-lookup"><span data-stu-id="c5673-126">Windows 7</span></span>|<span data-ttu-id="c5673-127">6.01</span><span class="sxs-lookup"><span data-stu-id="c5673-127">6.01</span></span>|  
|<span data-ttu-id="c5673-128">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="c5673-128">Windows Server 2008</span></span>|<span data-ttu-id="c5673-129">6.01</span><span class="sxs-lookup"><span data-stu-id="c5673-129">6.01</span></span>|  
|[!INCLUDE[win8](~/includes/win8-md.md)]|<span data-ttu-id="c5673-130">6.02</span><span class="sxs-lookup"><span data-stu-id="c5673-130">6.02</span></span>|  
  
## <a name="default-values"></a><span data-ttu-id="c5673-131">Wartości domyślne</span><span class="sxs-lookup"><span data-stu-id="c5673-131">Default values</span></span>  
 <span data-ttu-id="c5673-132">Wartość domyślna **- subsystemversion** — opcja kompilatora zależy od warunków na poniższej liście:</span><span class="sxs-lookup"><span data-stu-id="c5673-132">The default value of the **-subsystemversion** compiler option depends on the conditions in the following list:</span></span>  
  
-   <span data-ttu-id="c5673-133">Wartość domyślna to 6.02, jeśli ustawiono żadnych — opcja kompilatora na poniższej liście:</span><span class="sxs-lookup"><span data-stu-id="c5673-133">The default value is 6.02 if any compiler option in the following list is set:</span></span>  
  
    -   [<span data-ttu-id="c5673-134">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="c5673-134">-target:appcontainerexe</span></span>](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
  
    -   [<span data-ttu-id="c5673-135">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="c5673-135">-target:winmdobj</span></span>](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
  
    -   [<span data-ttu-id="c5673-136">-platform: arm</span><span class="sxs-lookup"><span data-stu-id="c5673-136">-platform:arm</span></span>](../../../csharp/language-reference/compiler-options/platform-compiler-option.md)  
  
-   <span data-ttu-id="c5673-137">Wartość domyślna to 6,00, jeśli używasz programu MSBuild, docelowych [!INCLUDE[net_v45](~/includes/net-v45-md.md)], i nie zostały jeszcze skonfigurowane opcje kompilatora, które zostały określone we wcześniejszej części tej listy.</span><span class="sxs-lookup"><span data-stu-id="c5673-137">The default value is 6.00 if you're using MSBuild, you're targeting [!INCLUDE[net_v45](~/includes/net-v45-md.md)], and you haven't set any of the compiler options that were specified earlier in this list.</span></span>  
  
-   <span data-ttu-id="c5673-138">Wartość domyślna to 4.00, jeśli żaden z powyższych warunków nie jest spełniony.</span><span class="sxs-lookup"><span data-stu-id="c5673-138">The default value is 4.00 if none of the previous conditions is true.</span></span>  
  
## <a name="setting-this-option"></a><span data-ttu-id="c5673-139">Ustawienie tej opcji</span><span class="sxs-lookup"><span data-stu-id="c5673-139">Setting this option</span></span>  
 <span data-ttu-id="c5673-140">Aby ustawić **- subsystemversion** — opcja kompilatora w programie Visual Studio, należy otworzyć pliku .csproj i określić wartość dla `SubsystemVersion` właściwości w kodzie XML programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="c5673-140">To set the **-subsystemversion** compiler option in Visual Studio, you must open the .csproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML.</span></span> <span data-ttu-id="c5673-141">Nie można ustawić tej opcji w programie Visual Studio IDE.</span><span class="sxs-lookup"><span data-stu-id="c5673-141">You can't set this option in the Visual Studio IDE.</span></span> <span data-ttu-id="c5673-142">Aby uzyskać więcej informacji, zobacz "Wartości domyślnej" we wcześniejszej części tego tematu lub [wspólne właściwości projektów MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="c5673-142">For more information, see "Default values" earlier in this topic or [Common MSBuild Project Properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5673-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c5673-143">See Also</span></span>  
 [<span data-ttu-id="c5673-144">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="c5673-144">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)

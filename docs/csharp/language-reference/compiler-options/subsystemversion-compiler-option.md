---
title: -subsystemversion (opcje kompilatora C#)
ms.date: 07/20/2015
ms.assetid: a99fce81-9d92-4813-9874-bee777041445
ms.openlocfilehash: ff4cd196edc1ec04f8abcecfa1a7a4e99e32dd56
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44098888"
---
# <a name="-subsystemversion-c-compiler-options"></a><span data-ttu-id="66ca5-102">-subsystemversion (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="66ca5-102">-subsystemversion (C# Compiler Options)</span></span>
<span data-ttu-id="66ca5-103">Określa minimalną wersję podsystemu, na którym można uruchomić wygenerowany plik wykonywalny, określając w ten sposób wersje systemu Windows, na którym można uruchomić pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="66ca5-103">Specifies the minimum version of the subsystem on which the generated executable file can run, thereby determining the versions of Windows on which the executable file can run.</span></span> <span data-ttu-id="66ca5-104">Najczęściej ta opcja zapewnia, że plik wykonywalny mogą korzystać z funkcji zabezpieczeń, które nie są dostępne ze starszymi wersjami systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="66ca5-104">Most commonly, this option ensures that the executable file can leverage particular security features that aren’t available with older versions of Windows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66ca5-105">Aby określić samego podsystemu, użyj [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="66ca5-105">To specify the subsystem itself, use the [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) compiler option.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66ca5-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="66ca5-106">Syntax</span></span>  
  
```console  
-subsystemversion:major.minor  
```  
  
#### <a name="parameters"></a><span data-ttu-id="66ca5-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="66ca5-107">Parameters</span></span>  
 `major.minor`  
 <span data-ttu-id="66ca5-108">Minimalna wymagana wersja podsystemu, wyrażone w notacji z kropką dla wersji głównych i pomocniczych.</span><span class="sxs-lookup"><span data-stu-id="66ca5-108">The minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="66ca5-109">Na przykład można określić, że aplikacja nie może działać w system operacyjny starszy niż Windows 7 po ustawieniu wartości tej opcji na 6.01, zgodnie z opisem w tabeli w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="66ca5-109">For example, you can specify that an application can't run on an operating system that's older than Windows 7 if you set the value of this option to 6.01, as the table later in this topic describes.</span></span> <span data-ttu-id="66ca5-110">Należy określić wartości dla `major` i `minor` jako liczby całkowite.</span><span class="sxs-lookup"><span data-stu-id="66ca5-110">You must specify the values for `major` and `minor` as integers.</span></span>  
  
 <span data-ttu-id="66ca5-111">Wiodące wyzerowania `minor` wersji nie zmieniają wersji, ale czy końcowe zera.</span><span class="sxs-lookup"><span data-stu-id="66ca5-111">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="66ca5-112">Na przykład 6.1 i 6.01 odwołują się do tej samej wersji, ale 6.10 odwołuje się do innej wersji.</span><span class="sxs-lookup"><span data-stu-id="66ca5-112">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="66ca5-113">Zaleca się, wyrażanie wersję pomocniczą w postaci dwóch cyfr, aby uniknąć mylenia go.</span><span class="sxs-lookup"><span data-stu-id="66ca5-113">We recommend expressing the minor version as two digits to avoid confusion.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66ca5-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="66ca5-114">Remarks</span></span>  
 <span data-ttu-id="66ca5-115">W poniższej tabeli wymieniono typowe wersji podsystemu Windows.</span><span class="sxs-lookup"><span data-stu-id="66ca5-115">The following table lists common subsystem versions of Windows.</span></span>  
  
|<span data-ttu-id="66ca5-116">Wersja Windows</span><span class="sxs-lookup"><span data-stu-id="66ca5-116">Windows version</span></span>|<span data-ttu-id="66ca5-117">Wersję podsystemu</span><span class="sxs-lookup"><span data-stu-id="66ca5-117">Subsystem version</span></span>|  
|---------------------|-----------------------|  
|<span data-ttu-id="66ca5-118">Windows 2000</span><span class="sxs-lookup"><span data-stu-id="66ca5-118">Windows 2000</span></span>|<span data-ttu-id="66ca5-119">5.00</span><span class="sxs-lookup"><span data-stu-id="66ca5-119">5.00</span></span>|  
|<span data-ttu-id="66ca5-120">Windows XP</span><span class="sxs-lookup"><span data-stu-id="66ca5-120">Windows XP</span></span>|<span data-ttu-id="66ca5-121">5.01</span><span class="sxs-lookup"><span data-stu-id="66ca5-121">5.01</span></span>|  
|<span data-ttu-id="66ca5-122">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="66ca5-122">Windows Server 2003</span></span>|<span data-ttu-id="66ca5-123">5.02</span><span class="sxs-lookup"><span data-stu-id="66ca5-123">5.02</span></span>|  
|<span data-ttu-id="66ca5-124">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="66ca5-124">Windows Vista</span></span>|<span data-ttu-id="66ca5-125">6.00</span><span class="sxs-lookup"><span data-stu-id="66ca5-125">6.00</span></span>|  
|<span data-ttu-id="66ca5-126">Windows 7</span><span class="sxs-lookup"><span data-stu-id="66ca5-126">Windows 7</span></span>|<span data-ttu-id="66ca5-127">6.01</span><span class="sxs-lookup"><span data-stu-id="66ca5-127">6.01</span></span>|  
|<span data-ttu-id="66ca5-128">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="66ca5-128">Windows Server 2008</span></span>|<span data-ttu-id="66ca5-129">6.01</span><span class="sxs-lookup"><span data-stu-id="66ca5-129">6.01</span></span>|  
|[!INCLUDE[win8](~/includes/win8-md.md)]|<span data-ttu-id="66ca5-130">6.02</span><span class="sxs-lookup"><span data-stu-id="66ca5-130">6.02</span></span>|  
  
## <a name="default-values"></a><span data-ttu-id="66ca5-131">Wartości domyślne</span><span class="sxs-lookup"><span data-stu-id="66ca5-131">Default values</span></span>  
 <span data-ttu-id="66ca5-132">Wartość domyślna **- subsystemversion** — opcja kompilatora jest zależna od warunki na poniższej liście:</span><span class="sxs-lookup"><span data-stu-id="66ca5-132">The default value of the **-subsystemversion** compiler option depends on the conditions in the following list:</span></span>  
  
-   <span data-ttu-id="66ca5-133">Wartość domyślna to 6.02, jeśli jest ustawiona na poniższej liście wszelkie — opcja kompilatora:</span><span class="sxs-lookup"><span data-stu-id="66ca5-133">The default value is 6.02 if any compiler option in the following list is set:</span></span>  
  
    -   [<span data-ttu-id="66ca5-134">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="66ca5-134">-target:appcontainerexe</span></span>](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
  
    -   [<span data-ttu-id="66ca5-135">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="66ca5-135">-target:winmdobj</span></span>](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
  
    -   [<span data-ttu-id="66ca5-136">-platform: arm</span><span class="sxs-lookup"><span data-stu-id="66ca5-136">-platform:arm</span></span>](../../../csharp/language-reference/compiler-options/platform-compiler-option.md)  
  
-   <span data-ttu-id="66ca5-137">Wartość domyślna to 6.00, jeśli używasz programu MSBuild, gdy elementem docelowym [!INCLUDE[net_v45](~/includes/net-v45-md.md)], i nie został ustawiony opcji kompilatora, które zostały określone we wcześniejszej części tej listy.</span><span class="sxs-lookup"><span data-stu-id="66ca5-137">The default value is 6.00 if you're using MSBuild, you're targeting [!INCLUDE[net_v45](~/includes/net-v45-md.md)], and you haven't set any of the compiler options that were specified earlier in this list.</span></span>  
  
-   <span data-ttu-id="66ca5-138">Wartość domyślna to 4.00, jeśli żaden z poprzednich warunków jest spełniony.</span><span class="sxs-lookup"><span data-stu-id="66ca5-138">The default value is 4.00 if none of the previous conditions is true.</span></span>  
  
## <a name="setting-this-option"></a><span data-ttu-id="66ca5-139">Ustawienie tej opcji</span><span class="sxs-lookup"><span data-stu-id="66ca5-139">Setting this option</span></span>  
 <span data-ttu-id="66ca5-140">Aby ustawić **- subsystemversion** — opcja kompilatora w programie Visual Studio, możesz Otwórz plik .csproj i określić wartość dla `SubsystemVersion` właściwość MSBuild XML.</span><span class="sxs-lookup"><span data-stu-id="66ca5-140">To set the **-subsystemversion** compiler option in Visual Studio, you must open the .csproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML.</span></span> <span data-ttu-id="66ca5-141">Nie można ustawić tę opcję w środowisku IDE programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="66ca5-141">You can't set this option in the Visual Studio IDE.</span></span> <span data-ttu-id="66ca5-142">Aby uzyskać więcej informacji, zobacz "Wartości domyślnej" wcześniej w tym temacie lub [wspólne właściwości projektów MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="66ca5-142">For more information, see "Default values" earlier in this topic or [Common MSBuild Project Properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66ca5-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="66ca5-143">See Also</span></span>  

- [<span data-ttu-id="66ca5-144">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="66ca5-144">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)

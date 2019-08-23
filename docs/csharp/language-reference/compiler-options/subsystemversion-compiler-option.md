---
title: -subsystemversion (C# opcje kompilatora)
ms.date: 07/20/2015
ms.assetid: a99fce81-9d92-4813-9874-bee777041445
ms.openlocfilehash: f70389f87bf49ffccded4aef775c27ed0d034e1f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922450"
---
# <a name="-subsystemversion-c-compiler-options"></a><span data-ttu-id="f8a08-102">-subsystemversion (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="f8a08-102">-subsystemversion (C# Compiler Options)</span></span>

<span data-ttu-id="f8a08-103">Określa minimalną wersję podsystemu, w którym można uruchomić wygenerowany plik wykonywalny, a tym samym określa wersje systemu Windows, w których można uruchomić plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="f8a08-103">Specifies the minimum version of the subsystem on which the generated executable file can run, thereby determining the versions of Windows on which the executable file can run.</span></span> <span data-ttu-id="f8a08-104">Najczęściej ta opcja zapewnia, że plik wykonywalny może korzystać z określonych funkcji zabezpieczeń, które nie są dostępne w starszych wersjach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="f8a08-104">Most commonly, this option ensures that the executable file can leverage particular security features that aren’t available with older versions of Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="f8a08-105">Aby określić podsystem, użyj opcji kompilatora [-Target](./target-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="f8a08-105">To specify the subsystem itself, use the [-target](./target-compiler-option.md) compiler option.</span></span>

## <a name="syntax"></a><span data-ttu-id="f8a08-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="f8a08-106">Syntax</span></span>

```console
-subsystemversion:major.minor
```

## <a name="parameters"></a><span data-ttu-id="f8a08-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8a08-107">Parameters</span></span>

`major.minor`

<span data-ttu-id="f8a08-108">Minimalna wymagana wersja podsystemu, wyrażona w notacji kropkowej dla wersji głównych i pomocniczych.</span><span class="sxs-lookup"><span data-stu-id="f8a08-108">The minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="f8a08-109">Można na przykład określić, że aplikacja nie może działać w systemie operacyjnym starszym niż Windows 7, jeśli wartość tej opcji zostanie ustawiona na 6,01, jak w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="f8a08-109">For example, you can specify that an application can't run on an operating system that's older than Windows 7 if you set the value of this option to 6.01, as the table later in this topic describes.</span></span> <span data-ttu-id="f8a08-110">Należy określić wartości dla `major` i `minor` jako liczby całkowite.</span><span class="sxs-lookup"><span data-stu-id="f8a08-110">You must specify the values for `major` and `minor` as integers.</span></span>

<span data-ttu-id="f8a08-111">Zera wiodące w `minor` wersji nie zmieniają wersji, ale końcowe zera to.</span><span class="sxs-lookup"><span data-stu-id="f8a08-111">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="f8a08-112">Na przykład 6,1 i 6,01 odnoszą się do tej samej wersji, ale 6,10 odwołuje się do innej wersji.</span><span class="sxs-lookup"><span data-stu-id="f8a08-112">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="f8a08-113">Zalecamy wyrażenie wersji pomocniczej jako dwóch cyfr, aby uniknąć pomyłek.</span><span class="sxs-lookup"><span data-stu-id="f8a08-113">We recommend expressing the minor version as two digits to avoid confusion.</span></span>

## <a name="remarks"></a><span data-ttu-id="f8a08-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f8a08-114">Remarks</span></span>

<span data-ttu-id="f8a08-115">W poniższej tabeli wymieniono typowe wersje podsystemów systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="f8a08-115">The following table lists common subsystem versions of Windows.</span></span>

|<span data-ttu-id="f8a08-116">Wersja systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f8a08-116">Windows version</span></span>|<span data-ttu-id="f8a08-117">Wersja podsystemu</span><span class="sxs-lookup"><span data-stu-id="f8a08-117">Subsystem version</span></span>|
|---------------------|-----------------------|
|<span data-ttu-id="f8a08-118">Windows 2000</span><span class="sxs-lookup"><span data-stu-id="f8a08-118">Windows 2000</span></span>|<span data-ttu-id="f8a08-119">5.00</span><span class="sxs-lookup"><span data-stu-id="f8a08-119">5.00</span></span>|
|<span data-ttu-id="f8a08-120">Windows XP</span><span class="sxs-lookup"><span data-stu-id="f8a08-120">Windows XP</span></span>|<span data-ttu-id="f8a08-121">5.01</span><span class="sxs-lookup"><span data-stu-id="f8a08-121">5.01</span></span>|
|<span data-ttu-id="f8a08-122">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="f8a08-122">Windows Server 2003</span></span>|<span data-ttu-id="f8a08-123">5.02</span><span class="sxs-lookup"><span data-stu-id="f8a08-123">5.02</span></span>|
|<span data-ttu-id="f8a08-124">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="f8a08-124">Windows Vista</span></span>|<span data-ttu-id="f8a08-125">6.00</span><span class="sxs-lookup"><span data-stu-id="f8a08-125">6.00</span></span>|
|<span data-ttu-id="f8a08-126">Windows 7</span><span class="sxs-lookup"><span data-stu-id="f8a08-126">Windows 7</span></span>|<span data-ttu-id="f8a08-127">6.01</span><span class="sxs-lookup"><span data-stu-id="f8a08-127">6.01</span></span>|
|<span data-ttu-id="f8a08-128">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="f8a08-128">Windows Server 2008</span></span>|<span data-ttu-id="f8a08-129">6.01</span><span class="sxs-lookup"><span data-stu-id="f8a08-129">6.01</span></span>|
|[!INCLUDE[win8](~/includes/win8-md.md)]|<span data-ttu-id="f8a08-130">6.02</span><span class="sxs-lookup"><span data-stu-id="f8a08-130">6.02</span></span>|

## <a name="default-values"></a><span data-ttu-id="f8a08-131">Wartości domyślne</span><span class="sxs-lookup"><span data-stu-id="f8a08-131">Default values</span></span>

<span data-ttu-id="f8a08-132">Wartość domyślna opcji kompilatora **-subsystemversion** zależy od warunków z poniższej listy:</span><span class="sxs-lookup"><span data-stu-id="f8a08-132">The default value of the **-subsystemversion** compiler option depends on the conditions in the following list:</span></span>

- <span data-ttu-id="f8a08-133">Wartość domyślna to 6,02, jeśli ustawiona jest jakakolwiek opcja kompilatora na poniższej liście:</span><span class="sxs-lookup"><span data-stu-id="f8a08-133">The default value is 6.02 if any compiler option in the following list is set:</span></span>

  - [<span data-ttu-id="f8a08-134">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="f8a08-134">-target:appcontainerexe</span></span>](./target-appcontainerexe-compiler-option.md)

  - [<span data-ttu-id="f8a08-135">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="f8a08-135">-target:winmdobj</span></span>](./target-winmdobj-compiler-option.md)

  - [<span data-ttu-id="f8a08-136">-Platforma: ARM</span><span class="sxs-lookup"><span data-stu-id="f8a08-136">-platform:arm</span></span>](./platform-compiler-option.md)

- <span data-ttu-id="f8a08-137">Wartość domyślna to 6,00, jeśli używasz programu MSBuild, jesteś celem .NET Framework 4,5 i nie ustawisz żadnych opcji kompilatora określonych wcześniej na tej liście.</span><span class="sxs-lookup"><span data-stu-id="f8a08-137">The default value is 6.00 if you're using MSBuild, you're targeting .NET Framework 4.5, and you haven't set any of the compiler options that were specified earlier in this list.</span></span>

- <span data-ttu-id="f8a08-138">Wartość domyślna to 4,00, jeśli żaden z poprzednich warunków nie ma wartości true.</span><span class="sxs-lookup"><span data-stu-id="f8a08-138">The default value is 4.00 if none of the previous conditions is true.</span></span>

## <a name="setting-this-option"></a><span data-ttu-id="f8a08-139">Ustawienie tej opcji</span><span class="sxs-lookup"><span data-stu-id="f8a08-139">Setting this option</span></span>

<span data-ttu-id="f8a08-140">Aby ustawić opcję kompilatora **-subsystemversion** w programie Visual Studio, należy otworzyć plik. csproj i określić wartość `SubsystemVersion` właściwości w kodzie XML programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="f8a08-140">To set the **-subsystemversion** compiler option in Visual Studio, you must open the .csproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML.</span></span> <span data-ttu-id="f8a08-141">Nie można ustawić tej opcji w środowisku IDE programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f8a08-141">You can't set this option in the Visual Studio IDE.</span></span> <span data-ttu-id="f8a08-142">Aby uzyskać więcej informacji, zobacz "wartości domyślne" wcześniej w tym temacie lub [wspólnych właściwościach projektu MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="f8a08-142">For more information, see "Default values" earlier in this topic or [Common MSBuild Project Properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="see-also"></a><span data-ttu-id="f8a08-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f8a08-143">See also</span></span>

- [<span data-ttu-id="f8a08-144">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="f8a08-144">C# Compiler Options</span></span>](./index.md)

---
title: -subsystemversion (Opcje kompilatora C#)
ms.date: 07/20/2015
ms.assetid: a99fce81-9d92-4813-9874-bee777041445
ms.openlocfilehash: d76c9424340b4b6f3c211c849b466be55eb79d1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74802033"
---
# <a name="-subsystemversion-c-compiler-options"></a><span data-ttu-id="d5577-102">-subsystemversion (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="d5577-102">-subsystemversion (C# Compiler Options)</span></span>

<span data-ttu-id="d5577-103">Określa minimalną wersję podsystemu, na którym można uruchomić wygenerowany plik wykonywalny, określając w ten sposób wersje systemu Windows, na których można uruchomić plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="d5577-103">Specifies the minimum version of the subsystem on which the generated executable file can run, thereby determining the versions of Windows on which the executable file can run.</span></span> <span data-ttu-id="d5577-104">Najczęściej ta opcja gwarantuje, że plik wykonywalny może korzystać z określonych funkcji zabezpieczeń, które nie są dostępne w starszych wersjach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d5577-104">Most commonly, this option ensures that the executable file can leverage particular security features that aren’t available with older versions of Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="d5577-105">Aby określić sam podsystem, należy użyć opcji [-target](./target-compiler-option.md) kompilatora.</span><span class="sxs-lookup"><span data-stu-id="d5577-105">To specify the subsystem itself, use the [-target](./target-compiler-option.md) compiler option.</span></span>

## <a name="syntax"></a><span data-ttu-id="d5577-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="d5577-106">Syntax</span></span>

```console
-subsystemversion:major.minor
```

## <a name="parameters"></a><span data-ttu-id="d5577-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5577-107">Parameters</span></span>

`major.minor`

<span data-ttu-id="d5577-108">Minimalna wymagana wersja podsystemu, wyrażona w notacji kropkowej dla wersji głównych i pomocniczych.</span><span class="sxs-lookup"><span data-stu-id="d5577-108">The minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="d5577-109">Na przykład można określić, że aplikacja nie może działać w systemie operacyjnym starszym niż Windows 7, jeśli ustawisz wartość tej opcji na 6.01, jak opisano w dalszej tabeli w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="d5577-109">For example, you can specify that an application can't run on an operating system that's older than Windows 7 if you set the value of this option to 6.01, as the table later in this topic describes.</span></span> <span data-ttu-id="d5577-110">Należy określić wartości `major` dla `minor` i jako liczby całkowite.</span><span class="sxs-lookup"><span data-stu-id="d5577-110">You must specify the values for `major` and `minor` as integers.</span></span>

<span data-ttu-id="d5577-111">Początkowe zera w `minor` wersji nie zmieniają wersji, ale końcowe zera zrobić.</span><span class="sxs-lookup"><span data-stu-id="d5577-111">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="d5577-112">Na przykład 6.1 i 6.01 odnoszą się do tej samej wersji, ale 6.10 odnosi się do innej wersji.</span><span class="sxs-lookup"><span data-stu-id="d5577-112">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="d5577-113">Zalecamy wyrażenie wersji pomocniczej jako dwucyfrowej, aby uniknąć nieporozumień.</span><span class="sxs-lookup"><span data-stu-id="d5577-113">We recommend expressing the minor version as two digits to avoid confusion.</span></span>

## <a name="remarks"></a><span data-ttu-id="d5577-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d5577-114">Remarks</span></span>

<span data-ttu-id="d5577-115">W poniższej tabeli wymieniono typowe wersje systemu Windows w podsystemowych.</span><span class="sxs-lookup"><span data-stu-id="d5577-115">The following table lists common subsystem versions of Windows.</span></span>

|<span data-ttu-id="d5577-116">Wersja systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d5577-116">Windows version</span></span>|<span data-ttu-id="d5577-117">Wersja podsystemu</span><span class="sxs-lookup"><span data-stu-id="d5577-117">Subsystem version</span></span>|
|---------------------|-----------------------|
|<span data-ttu-id="d5577-118">Windows 2000</span><span class="sxs-lookup"><span data-stu-id="d5577-118">Windows 2000</span></span>|<span data-ttu-id="d5577-119">5,00</span><span class="sxs-lookup"><span data-stu-id="d5577-119">5.00</span></span>|
|<span data-ttu-id="d5577-120">Windows XP</span><span class="sxs-lookup"><span data-stu-id="d5577-120">Windows XP</span></span>|<span data-ttu-id="d5577-121">5.01</span><span class="sxs-lookup"><span data-stu-id="d5577-121">5.01</span></span>|
|<span data-ttu-id="d5577-122">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="d5577-122">Windows Server 2003</span></span>|<span data-ttu-id="d5577-123">5.02</span><span class="sxs-lookup"><span data-stu-id="d5577-123">5.02</span></span>|
|<span data-ttu-id="d5577-124">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="d5577-124">Windows Vista</span></span>|<span data-ttu-id="d5577-125">6.00</span><span class="sxs-lookup"><span data-stu-id="d5577-125">6.00</span></span>|
|<span data-ttu-id="d5577-126">Windows 7</span><span class="sxs-lookup"><span data-stu-id="d5577-126">Windows 7</span></span>|<span data-ttu-id="d5577-127">6.01</span><span class="sxs-lookup"><span data-stu-id="d5577-127">6.01</span></span>|
|<span data-ttu-id="d5577-128">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="d5577-128">Windows Server 2008</span></span>|<span data-ttu-id="d5577-129">6.01</span><span class="sxs-lookup"><span data-stu-id="d5577-129">6.01</span></span>|
|<span data-ttu-id="d5577-130">Windows 8</span><span class="sxs-lookup"><span data-stu-id="d5577-130">Windows 8</span></span>|<span data-ttu-id="d5577-131">6.02</span><span class="sxs-lookup"><span data-stu-id="d5577-131">6.02</span></span>|

## <a name="default-values"></a><span data-ttu-id="d5577-132">Wartości domyślne</span><span class="sxs-lookup"><span data-stu-id="d5577-132">Default values</span></span>

<span data-ttu-id="d5577-133">Wartość domyślna opcji kompilatora **-subsystemversion** zależy od warunków na poniższej liście:</span><span class="sxs-lookup"><span data-stu-id="d5577-133">The default value of the **-subsystemversion** compiler option depends on the conditions in the following list:</span></span>

- <span data-ttu-id="d5577-134">Wartość domyślna to 6,02, jeśli ustawiona jest dowolna opcja kompilatora na poniższej liście:</span><span class="sxs-lookup"><span data-stu-id="d5577-134">The default value is 6.02 if any compiler option in the following list is set:</span></span>

  - [<span data-ttu-id="d5577-135">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="d5577-135">-target:appcontainerexe</span></span>](./target-appcontainerexe-compiler-option.md)

  - [<span data-ttu-id="d5577-136">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="d5577-136">-target:winmdobj</span></span>](./target-winmdobj-compiler-option.md)

  - [<span data-ttu-id="d5577-137">-platforma:ramię</span><span class="sxs-lookup"><span data-stu-id="d5577-137">-platform:arm</span></span>](./platform-compiler-option.md)

- <span data-ttu-id="d5577-138">Wartość domyślna to 6,00, jeśli używasz MSBuild, jesteś przeznaczony do .NET Framework 4.5 i nie ustawiono żadnej z opcji kompilatora, które zostały określone wcześniej na tej liście.</span><span class="sxs-lookup"><span data-stu-id="d5577-138">The default value is 6.00 if you're using MSBuild, you're targeting .NET Framework 4.5, and you haven't set any of the compiler options that were specified earlier in this list.</span></span>

- <span data-ttu-id="d5577-139">Wartość domyślna to 4,00, jeśli żaden z poprzednich warunków nie jest spełniony.</span><span class="sxs-lookup"><span data-stu-id="d5577-139">The default value is 4.00 if none of the previous conditions is true.</span></span>

## <a name="setting-this-option"></a><span data-ttu-id="d5577-140">Ustawienie tej opcji</span><span class="sxs-lookup"><span data-stu-id="d5577-140">Setting this option</span></span>

<span data-ttu-id="d5577-141">Aby ustawić opcję **kompilatora -subsystemversion** w programie Visual Studio, należy otworzyć `SubsystemVersion` plik csproj i określić wartość właściwości w pliku MSBuild XML.</span><span class="sxs-lookup"><span data-stu-id="d5577-141">To set the **-subsystemversion** compiler option in Visual Studio, you must open the .csproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML.</span></span> <span data-ttu-id="d5577-142">Nie można ustawić tej opcji w programie Visual Studio IDE.</span><span class="sxs-lookup"><span data-stu-id="d5577-142">You can't set this option in the Visual Studio IDE.</span></span> <span data-ttu-id="d5577-143">Aby uzyskać więcej informacji, zobacz "Wartości domyślne" wcześniej w tym temacie lub [Wspólne właściwości projektu MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="d5577-143">For more information, see "Default values" earlier in this topic or [Common MSBuild Project Properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="see-also"></a><span data-ttu-id="d5577-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d5577-144">See also</span></span>

- [<span data-ttu-id="d5577-145">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="d5577-145">C# Compiler Options</span></span>](./index.md)

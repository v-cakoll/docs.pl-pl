---
title: 'Instrukcje: Określanie, które wersje programu .NET Framework są zainstalowane.'
ms.date: 03/18/2019
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c4ad3ca5694457637a82a36c8db4534df43a9d7
ms.sourcegitcommit: 8258515adc6c37ab6278e5a3d102d593246f8672
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2019
ms.locfileid: "58504434"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="ae601-102">Instrukcje: Określanie, które wersje programu .NET Framework są zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="ae601-102">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="ae601-103">Użytkownicy mogą [zainstalować](https://docs.microsoft.com/dotnet/framework/install) i uruchamiania wielu wersji programu .NET Framework na swoich komputerach.</span><span class="sxs-lookup"><span data-stu-id="ae601-103">Users can [install](https://docs.microsoft.com/dotnet/framework/install) and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="ae601-104">Podczas tworzenia lub wdrażania aplikacji, może być konieczne wiedzieć, które wersje programu .NET Framework są zainstalowane na komputerze użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ae601-104">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span> 

<span data-ttu-id="ae601-105">.NET Framework składa się z dwóch głównych składników, które są określane oddzielnie:</span><span class="sxs-lookup"><span data-stu-id="ae601-105">The .NET Framework consists of two main components, which are versioned separately:</span></span>  
  
- <span data-ttu-id="ae601-106">Zbiór zestawów, które są kolekcjami typów i zasobów zapewniających funkcje dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ae601-106">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="ae601-107">.NET Framework i zestawy współużytkują ten sam numer wersji.</span><span class="sxs-lookup"><span data-stu-id="ae601-107">The .NET Framework and assemblies share the same version number.</span></span>  
  
- <span data-ttu-id="ae601-108">Środowisko uruchomieniowe języka wspólnego (CLR) zarządza, która wykonuje kod w swojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ae601-108">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="ae601-109">Środowisko CLR jest identyfikowane za pomocą własnego numeru wersji (zobacz [wersje i zależności](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span><span class="sxs-lookup"><span data-stu-id="ae601-109">The CLR is identified by its own version number (see [Versions and Dependencies](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span></span>  

> [!NOTE]
> <span data-ttu-id="ae601-110">Każda nowa wersja programu .NET Framework zachowuje funkcje z poprzednich wersji i dodaje nowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="ae601-110">Each new version of the .NET Framework retains features from the previous versions and adds new features.</span></span> <span data-ttu-id="ae601-111">W tym samym czasie, co oznacza, że bez konieczności odinstalowywania poprzednich wersji można zainstalować środowiska .NET Framework, można załadować wiele wersji programu .NET Framework na pojedynczym komputerze.</span><span class="sxs-lookup"><span data-stu-id="ae601-111">You can load multiple versions of the .NET Framework on a single computer at the same time, which means that you can install the .NET Framework without having to uninstall previous versions.</span></span> <span data-ttu-id="ae601-112">Ogólnie rzecz biorąc nie należy odinstalować poprzednie wersje programu .NET Framework, ponieważ aplikacja może zależeć od określonej wersji i mogą przestać działać, jeśli ta wersja została usunięta.</span><span class="sxs-lookup"><span data-stu-id="ae601-112">In general, you shouldn't uninstall previous versions of the .NET Framework, because an application you use may depend on a specific version and may break if that version is removed.</span></span>
>
> <span data-ttu-id="ae601-113">Istnieje następująca różnica między wersją .NET Framework i wersji środowiska CLR:</span><span class="sxs-lookup"><span data-stu-id="ae601-113">There is a difference between the .NET Framework version and the CLR version:</span></span> 
> - <span data-ttu-id="ae601-114">Wersja .NET Framework jest oparta na zbiór zestawów, które tworzą biblioteki klas .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ae601-114">The .NET Framework version is based on the set of assemblies that form the .NET Framework class library.</span></span> <span data-ttu-id="ae601-115">Na przykład .NET Framework w wersji obejmują 4.5, 4.6.1 i 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="ae601-115">For example, .NET Framework versions include 4.5, 4.6.1, and 4.7.2.</span></span> 
>- <span data-ttu-id="ae601-116">Wersja środowiska CLR jest oparty na środowiska uruchomieniowego, w którym wykonywane aplikacji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ae601-116">The CLR version is based on the runtime on which .NET Framework applications execute.</span></span> <span data-ttu-id="ae601-117">Jednej wersji środowiska CLR zazwyczaj obsługuje wiele wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ae601-117">A single CLR version typically supports multiple .NET Framework versions.</span></span> <span data-ttu-id="ae601-118">Na przykład środowisko CLR w wersji 4.0.30319. *xxxxx* obsługuje wersje programu .NET Framework 4 za pośrednictwem 4.5.2 i wersji środowiska CLR 4.0.30319.42000 obsługuje wersje programu .NET Framework, począwszy od programu .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="ae601-118">For example, CLR version 4.0.30319.*xxxxx* supports .NET Framework versions 4 through 4.5.2 and CLR version 4.0.30319.42000 supports .NET Framework versions starting with .NET Framework 4.6.</span></span> 
>
> <span data-ttu-id="ae601-119">Aby uzyskać więcej informacji na temat wersji, zobacz [wersje programu .NET Framework i zależności](versions-and-dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="ae601-119">For more information about versions, see [.NET Framework versions and dependencies](versions-and-dependencies.md).</span></span>


<span data-ttu-id="ae601-120">Aby uzyskać listę wersji programu .NET Framework zainstalowana na komputerze, możesz uzyskać dostępu do rejestru.</span><span class="sxs-lookup"><span data-stu-id="ae601-120">To get a list of the .NET Framework versions installed on a computer, you access the registry.</span></span> <span data-ttu-id="ae601-121">Można albo użyj Edytora rejestru, aby wyświetlić rejestr lub wykonuje zapytania za pomocą kodu:</span><span class="sxs-lookup"><span data-stu-id="ae601-121">You can either use the Registry Editor to view the registry or use code to query it:</span></span>
 
- <span data-ttu-id="ae601-122">Znajdź nowszej wersji programu .NET Framework (4.5 i nowsze):</span><span class="sxs-lookup"><span data-stu-id="ae601-122">Find newer .NET Framework versions (4.5 and later):</span></span> 
     - [<span data-ttu-id="ae601-123">Użyj Edytora rejestru, aby znaleźć wersji programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ae601-123">Use the Registry Editor to find .NET Framework versions</span></span>](#net_b)  
     - [<span data-ttu-id="ae601-124">Wykonaj zapytanie dotyczące rejestru dla wersji programu .NET Framework przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="ae601-124">Use code to query the registry for .NET Framework versions</span></span>](#net_d)  
     - [<span data-ttu-id="ae601-125">Wykonaj zapytanie dotyczące rejestru dla wersji programu .NET Framework za pomocą programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="ae601-125">Use PowerShell to query the registry for .NET Framework versions</span></span>](#ps_a)
- <span data-ttu-id="ae601-126">Znajdź starsze wersje programu .NET Framework (1&#8211;4):</span><span class="sxs-lookup"><span data-stu-id="ae601-126">Find older .NET Framework versions (1&#8211;4):</span></span>
     - [<span data-ttu-id="ae601-127">Użyj Edytora rejestru, aby znaleźć wersji programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ae601-127">Use the Registry Editor to find .NET Framework versions</span></span>](#net_a)
     - [<span data-ttu-id="ae601-128">Wykonaj zapytanie dotyczące rejestru dla wersji programu .NET Framework przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="ae601-128">Use code to query the registry for .NET Framework versions</span></span>](#net_c)   

<span data-ttu-id="ae601-129">Aby uzyskać listę wersji środowiska CLR, zainstalowane na komputerze, użyj narzędzia lub kodu:</span><span class="sxs-lookup"><span data-stu-id="ae601-129">To get a list of the CLR versions installed on a computer, use a tool or code:</span></span>  
  
- [<span data-ttu-id="ae601-130">Użyj narzędzia Clrver</span><span class="sxs-lookup"><span data-stu-id="ae601-130">Use the Clrver tool</span></span>](#clr_a)  
- [<span data-ttu-id="ae601-131">Tworzenie zapytania klasę Environment przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="ae601-131">Use code to query the Environment class</span></span>](#clr_b)  

<span data-ttu-id="ae601-132">Aby uzyskać informacje dotyczące wykrywania zainstalowanych aktualizacji dla każdej wersji programu .NET Framework, zobacz [jak: Określanie, które aktualizacje programu .NET Framework są zainstalowane](how-to-determine-which-net-framework-updates-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="ae601-132">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine which .NET Framework updates are installed](how-to-determine-which-net-framework-updates-are-installed.md).</span></span> 
  

## <a name="find-newer-net-framework-versions-45-and-later"></a><span data-ttu-id="ae601-133">Znajdź nowszej wersji programu .NET Framework (4.5 i nowsze)</span><span class="sxs-lookup"><span data-stu-id="ae601-133">Find newer .NET Framework versions (4.5 and later)</span></span>

<a name="net_b"></a> 
### <a name="find-net-framework-versions-45-and-later-in-the-registry"></a><span data-ttu-id="ae601-134">Znajdź wersje programu .NET Framework 4.5 i nowsze w rejestrze</span><span class="sxs-lookup"><span data-stu-id="ae601-134">Find .NET Framework versions 4.5 and later in the registry</span></span>

1. <span data-ttu-id="ae601-135">Z **Start** menu, wybierz **Uruchom**, wprowadź *regedit*, a następnie wybierz pozycję **OK**.</span><span class="sxs-lookup"><span data-stu-id="ae601-135">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

     <span data-ttu-id="ae601-136">Musi mieć poświadczenia administracyjne, aby uruchomić program regedit.</span><span class="sxs-lookup"><span data-stu-id="ae601-136">You must have administrative credentials to run regedit.</span></span>

2. <span data-ttu-id="ae601-137">W Edytorze rejestru otwórz następujący podklucz: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**.</span><span class="sxs-lookup"><span data-stu-id="ae601-137">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**.</span></span> <span data-ttu-id="ae601-138">Jeśli **pełne** podklucz nie będą dostępne, a następnie nie ma programu .NET Framework 4.5 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="ae601-138">If the **Full** subkey isn't present, then you don't have the .NET Framework 4.5 or later installed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ae601-139">**NET Framework Setup** lokalizacji w rejestrze nie rozpoczyna się kropką.</span><span class="sxs-lookup"><span data-stu-id="ae601-139">The **NET Framework Setup** folder in the registry does not begin with a period.</span></span>

3. <span data-ttu-id="ae601-140">Sprawdź, czy wpis typu DWORD o nazwie **wersji**.</span><span class="sxs-lookup"><span data-stu-id="ae601-140">Check for a DWORD entry named **Release**.</span></span> <span data-ttu-id="ae601-141">Jeśli istnieje, musisz .NET Framework 4.5 lub nowszy zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="ae601-141">If it exists, then you have .NET Framework 4.5 or later versions installed.</span></span> <span data-ttu-id="ae601-142">Jego wartość to klucz wersji, który odnosi się do określonej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ae601-142">Its value is a release key that corresponds to a particular version of the .NET Framework.</span></span> <span data-ttu-id="ae601-143">Na poniższej ilustracji, na przykład, wartość **wersji** wpis jest *378389*, czyli na klucz wersji .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="ae601-143">In the following figure, for example, the value of the **Release** entry is *378389*, which is the release key for .NET Framework 4.5.</span></span> 

     <span data-ttu-id="ae601-144">![Wpis rejestru dla programu .NET Framework 4.5](media/clr-installdir.png "wpis rejestru dla programu .NET Framework 4.5")</span><span class="sxs-lookup"><span data-stu-id="ae601-144">![Registry entry for the .NET Framework 4.5](media/clr-installdir.png "Registry entry for the .NET Framework 4.5")</span></span>

<span data-ttu-id="ae601-145">W poniższej tabeli przedstawiono minimalną wartość **wersji** wpis dla każdej wersji systemu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ae601-145">The following table lists the minimum value of the **Release** entry for each .NET Framework version.</span></span> <span data-ttu-id="ae601-146">Można użyć tych wartości w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ae601-146">You can use these values as follows:</span></span>

- <span data-ttu-id="ae601-147">Aby ustalić, czy minimalna wersja architektury .NET Framework jest obecny, test czy **wersji** wartość DWORD znaleziony w rejestrze jest *większa lub równa* wartości wymienione w tabeli.</span><span class="sxs-lookup"><span data-stu-id="ae601-147">To determine whether a minimum .NET Framework version is present, test whether the **Release** DWORD value found in the registry is *greater than or equal to* the value listed in the table.</span></span> <span data-ttu-id="ae601-148">Na przykład, jeśli aplikacja wymaga .NET Framework w wersji 4.7 lub nowszej, możesz przetestować dla wersji minimalnej wartości klucza *460798*.</span><span class="sxs-lookup"><span data-stu-id="ae601-148">For example, if your application requires the .NET Framework 4.7 or later, you test for a minimum release key value of *460798*.</span></span>

- <span data-ttu-id="ae601-149">Do testowania dla różnych wersji, zaczynają się od najnowszej wersji .NET Framework, a następnie przetestować każda kolejne starszej wersji.</span><span class="sxs-lookup"><span data-stu-id="ae601-149">To test for multiple versions, begin with the latest .NET Framework version, and then test for each successive earlier version.</span></span>

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

<a name="version_table"></a>

|<span data-ttu-id="ae601-150">Wersja programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ae601-150">.NET Framework version</span></span>|<span data-ttu-id="ae601-151">Wartość DWORD dotycząca wersji</span><span class="sxs-lookup"><span data-stu-id="ae601-151">Value of the Release DWORD</span></span>|
|--------------------------------|-------------|
|<span data-ttu-id="ae601-152">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="ae601-152">.NET Framework 4.5</span></span>|<span data-ttu-id="ae601-153">378389</span><span class="sxs-lookup"><span data-stu-id="ae601-153">378389</span></span>|
|<span data-ttu-id="ae601-154">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="ae601-154">.NET Framework 4.5.1</span></span>|<span data-ttu-id="ae601-155">378675</span><span class="sxs-lookup"><span data-stu-id="ae601-155">378675</span></span>|
|<span data-ttu-id="ae601-156">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="ae601-156">.NET Framework 4.5.2</span></span>|<span data-ttu-id="ae601-157">379893</span><span class="sxs-lookup"><span data-stu-id="ae601-157">379893</span></span>|
|<span data-ttu-id="ae601-158">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="ae601-158">.NET Framework 4.6</span></span>|<span data-ttu-id="ae601-159">393295</span><span class="sxs-lookup"><span data-stu-id="ae601-159">393295</span></span>|
|<span data-ttu-id="ae601-160">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="ae601-160">.NET Framework 4.6.1</span></span>|<span data-ttu-id="ae601-161">394254</span><span class="sxs-lookup"><span data-stu-id="ae601-161">394254</span></span>|
|<span data-ttu-id="ae601-162">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="ae601-162">.NET Framework 4.6.2</span></span>|<span data-ttu-id="ae601-163">394802</span><span class="sxs-lookup"><span data-stu-id="ae601-163">394802</span></span>|
|<span data-ttu-id="ae601-164">.NET framework 4.7</span><span class="sxs-lookup"><span data-stu-id="ae601-164">.NET Framework 4.7</span></span>|<span data-ttu-id="ae601-165">460798</span><span class="sxs-lookup"><span data-stu-id="ae601-165">460798</span></span>|
|<span data-ttu-id="ae601-166">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="ae601-166">.NET Framework 4.7.1</span></span>|<span data-ttu-id="ae601-167">461308</span><span class="sxs-lookup"><span data-stu-id="ae601-167">461308</span></span>|
|<span data-ttu-id="ae601-168">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="ae601-168">.NET Framework 4.7.2</span></span>|<span data-ttu-id="ae601-169">461808</span><span class="sxs-lookup"><span data-stu-id="ae601-169">461808</span></span>|

<span data-ttu-id="ae601-170">Aby uzyskać pełną tabelę klawiszy wersji dla programu .NET Framework dla określonej wersji systemu operacyjnego Windows, zobacz [kluczy wersji .NET Framework i wersji systemu operacyjnego Windows](release-keys-and-os-versions.md).</span><span class="sxs-lookup"><span data-stu-id="ae601-170">For a complete table of release keys for the .NET Framework for specific Windows operating system versions, see [.NET Framework release keys and Windows operating system versions](release-keys-and-os-versions.md).</span></span>


<a name="net_d"></a> 
### <a name="find-net-framework-versions-45-and-later-with-code"></a><span data-ttu-id="ae601-171">Znajdź wersje programu .NET Framework 4.5 lub nowszy z kodem</span><span class="sxs-lookup"><span data-stu-id="ae601-171">Find .NET Framework versions 4.5 and later with code</span></span>

1. <span data-ttu-id="ae601-172">Użyj <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> i <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> metod w celu uzyskania dostępu do **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework setup\ndp\v4\full ma** podkluczy w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ae601-172">Use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> methods to access the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey in the Windows registry.</span></span>

    <span data-ttu-id="ae601-173">Istnienie **wersji** wpis DWORD w **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework setup\ndp\v4\full ma** podklucz wskazuje na to, że jest .NET Framework 4.5 lub nowszej wersji. zainstalowana na komputerze.</span><span class="sxs-lookup"><span data-stu-id="ae601-173">The existence of the **Release** DWORD entry in the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey indicates that the .NET Framework 4.5 or a later version is installed on a computer.</span></span> 

2. <span data-ttu-id="ae601-174">Sprawdź wartość **wersji** wpis, aby ustalić zainstalowaną wersję.</span><span class="sxs-lookup"><span data-stu-id="ae601-174">Check the value of the **Release** entry to determine the installed version.</span></span> <span data-ttu-id="ae601-175">Być zgodne, sprawdź, czy wartość większą niż lub równa wartości na liście [tabeli wersji .NET Framework](#version_table).</span><span class="sxs-lookup"><span data-stu-id="ae601-175">To be forward-compatible, check for a value greater than or equal to the value listed in the [.NET Framework version table](#version_table).</span></span>

<span data-ttu-id="ae601-176">Poniższy przykład sprawdza wartość **wersji** wpis w rejestrze, aby znaleźć .NET Framework 4.5 i nowsze wersje, które są zainstalowane:</span><span class="sxs-lookup"><span data-stu-id="ae601-176">The following example checks the value of the **Release** entry in the registry to find the .NET Framework 4.5 and later versions that are installed:</span></span>

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

<span data-ttu-id="ae601-177">W tym przykładzie następuje zalecana praktyka dla kontroli wersji:</span><span class="sxs-lookup"><span data-stu-id="ae601-177">This example follows the recommended practice for version checking:</span></span>

- <span data-ttu-id="ae601-178">Sprawdza, czy wartość **wersji** wpis jest *większa lub równa* wartości kluczy znanych wydania.</span><span class="sxs-lookup"><span data-stu-id="ae601-178">It checks whether the value of the **Release** entry is *greater than or equal to* the value of the known release keys.</span></span>

- <span data-ttu-id="ae601-179">Sprawdza w kolejności od najbardziej aktualną wersję do najwcześniejszej wersji.</span><span class="sxs-lookup"><span data-stu-id="ae601-179">It checks in order from most recent version to earliest version.</span></span>

<a name="ps_a"></a> 
### <a name="check-for-a-minimum-required-net-framework-version-45-and-later-with-powershell"></a><span data-ttu-id="ae601-180">Sprawdź, czy są wymagane co najmniej .NET Framework w wersji (4.5 lub nowszy) za pomocą programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="ae601-180">Check for a minimum-required .NET Framework version (4.5 and later) with PowerShell</span></span>

- <span data-ttu-id="ae601-181">Użyj poleceń programu PowerShell, aby sprawdzić wartość **wersji** wpisu **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework setup\ndp\v4\full ma** podklucza.</span><span class="sxs-lookup"><span data-stu-id="ae601-181">Use PowerShell commands to check the value of the **Release** entry of the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** subkey.</span></span>

<span data-ttu-id="ae601-182">Poniższe przykłady należy sprawdzić wartość **wersji** wpis, aby określić, czy programu .NET Framework 4.6.2 lub nowszy jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="ae601-182">The following examples check the value of the **Release** entry to determine whether the .NET Framework 4.6.2 or later is installed.</span></span> <span data-ttu-id="ae601-183">Ten kod zwraca `True` Jeśli jest zainstalowany i `False` inaczej.</span><span class="sxs-lookup"><span data-stu-id="ae601-183">This code returns `True` if it's installed and `False` otherwise.</span></span>

```PowerShell
# PowerShell 5
 Get-ChildItem 'HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\' |  Get-ItemPropertyValue -Name Release | Foreach-Object { $_ -ge 394802 } 
 ```

```PowerShell
# PowerShell 4
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

<span data-ttu-id="ae601-184">Aby sprawdzić, czy inny minimalna wymagana wersja programu .NET Framework, należy zastąpić *394802* w tych przykładach za pomocą **wersji** wartość z [tabeli wersji .NET Framework](#version_table).</span><span class="sxs-lookup"><span data-stu-id="ae601-184">To check for a different minimum-required .NET Framework version, replace *394802* in these examples with a **Release** value from the [.NET Framework version table](#version_table).</span></span>

## <a name="find-older-net-framework-versions-182114"></a><span data-ttu-id="ae601-185">Znajdź starsze wersje programu .NET Framework (1&#8211;4)</span><span class="sxs-lookup"><span data-stu-id="ae601-185">Find older .NET Framework versions (1&#8211;4)</span></span>

<a name="net_a"></a>
### <a name="find-net-framework-versions-182114-in-the-registry"></a><span data-ttu-id="ae601-186">Znajdź .NET Framework w wersji 1&#8211;4 w rejestrze</span><span class="sxs-lookup"><span data-stu-id="ae601-186">Find .NET Framework versions 1&#8211;4 in the registry</span></span> 
  
1. <span data-ttu-id="ae601-187">Z **Start** menu, wybierz **Uruchom**, wprowadź *regedit*, a następnie wybierz pozycję **OK**.</span><span class="sxs-lookup"><span data-stu-id="ae601-187">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>
  
    <span data-ttu-id="ae601-188">Musi mieć poświadczenia administracyjne, aby uruchomić program regedit.</span><span class="sxs-lookup"><span data-stu-id="ae601-188">You must have administrative credentials to run regedit.</span></span>  

2. <span data-ttu-id="ae601-189">W Edytorze rejestru otwórz następujący podklucz: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**:</span><span class="sxs-lookup"><span data-stu-id="ae601-189">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**:</span></span>  

    - <span data-ttu-id="ae601-190">Dla wersji programu .NET Framework 1.1 przez 3.5 każdej zainstalowanej wersji jest wymieniony jako podklucza w **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP** podklucza.</span><span class="sxs-lookup"><span data-stu-id="ae601-190">For .NET Framework versions 1.1 through 3.5, each installed version is listed as a subkey under the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP** subkey.</span></span> <span data-ttu-id="ae601-191">Na przykład **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**.</span><span class="sxs-lookup"><span data-stu-id="ae601-191">For example, **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**.</span></span> <span data-ttu-id="ae601-192">Numer wersji jest przechowywany jako wartość podklucza wersji **wersji** wpisu.</span><span class="sxs-lookup"><span data-stu-id="ae601-192">The version number is stored as a value in the version subkey's **Version** entry.</span></span> 
     
    - <span data-ttu-id="ae601-193">.NET Framework 4 **wersji** wpis znajduje się w **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client** podklucz **HKEY_LOCAL_MACHINE\SOFTWARE\ Microsoft\NET Framework Setup\NDP\v4.0\Full** podklucza, lub w obu tych podkluczach.</span><span class="sxs-lookup"><span data-stu-id="ae601-193">For .NET Framework 4, the **Version** entry is under the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client** subkey, the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full** subkey, or under both subkeys.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ae601-194">**NET Framework Setup** lokalizacji w rejestrze nie rozpoczyna się kropką.</span><span class="sxs-lookup"><span data-stu-id="ae601-194">The **NET Framework Setup** folder in the registry does not begin with a period.</span></span>

    <span data-ttu-id="ae601-195">Na poniższej ilustracji przedstawiono podklucz i jego **wersji** wpis dla programu .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="ae601-195">The following figure shows the subkey and its **Version** entry for the .NET Framework 3.5.</span></span>

    <span data-ttu-id="ae601-196">![Wpis rejestru dla programu .NET Framework 3.5. ](media/net-4-and-earlier.png ".NET framework 3.5 i wcześniejszymi wersjami")</span><span class="sxs-lookup"><span data-stu-id="ae601-196">![The registry entry for the .NET Framework 3.5.](media/net-4-and-earlier.png ".NET Framework 3.5 and earlier versions")</span></span>

<a name="net_c"></a> 
### <a name="find-net-framework-versions-182114-with-code"></a><span data-ttu-id="ae601-197">Znajdź .NET Framework w wersji 1&#8211;4 przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="ae601-197">Find .NET Framework versions 1&#8211;4 with code</span></span>

- <span data-ttu-id="ae601-198">Użyj <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> klasy, aby uzyskać dostęp do **HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP** podkluczy w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ae601-198">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the **HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP** subkey in the Windows registry.</span></span>

<span data-ttu-id="ae601-199">Poniższy przykład umożliwia znalezienie .NET Framework 1&#8211;wersji 4, które są zainstalowane:</span><span class="sxs-lookup"><span data-stu-id="ae601-199">The following example finds the .NET Framework 1&#8211;4 versions that are installed:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]


## <a name="find-clr-versions"></a><span data-ttu-id="ae601-200">Znajdź wersji środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="ae601-200">Find CLR versions</span></span>
  
<a name="clr_a"></a> 
### <a name="find-the-current-clr-version-with-clrverexe"></a><span data-ttu-id="ae601-201">Znaleźć bieżącą wersję środowiska CLR przy użyciu Clrver.exe</span><span class="sxs-lookup"><span data-stu-id="ae601-201">Find the current CLR version with Clrver.exe</span></span>

<span data-ttu-id="ae601-202">Użyj [narzędzia wersji środowiska CLR (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) do określenia, które wersje środowiska CLR są instalowane na komputerze:</span><span class="sxs-lookup"><span data-stu-id="ae601-202">Use the [CLR Version tool (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) to determine which versions of the CLR are installed on a computer:</span></span>

- <span data-ttu-id="ae601-203">Z [wiersz polecenia programisty dla programu Visual Studio](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs), wprowadź `clrver`.</span><span class="sxs-lookup"><span data-stu-id="ae601-203">From a [Developer Command Prompt for Visual Studio](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs), enter `clrver`.</span></span>

    <span data-ttu-id="ae601-204">Przykładowe dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="ae601-204">Sample output:</span></span>

    ```console
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

<a name="clr_b"></a> 
### <a name="find-the-current-clr-version-with-the-environment-class"></a><span data-ttu-id="ae601-205">Znaleźć bieżącą wersję środowiska CLR przy użyciu klasy środowiska</span><span class="sxs-lookup"><span data-stu-id="ae601-205">Find the current CLR version with the Environment class</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ae601-206">.NET Framework 4.5 i nowsze wersje, nie należy używać <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwości do wykrywania wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="ae601-206">For the .NET Framework 4.5 and later versions, don't use the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the CLR.</span></span> <span data-ttu-id="ae601-207">Zamiast tego wykonaj zapytanie dotyczące rejestru zgodnie z opisem w [znaleźć .NET Framework w wersji 4.5 lub nowszy z kodem](#net_d).</span><span class="sxs-lookup"><span data-stu-id="ae601-207">Instead, query the registry as described in [Find .NET Framework versions 4.5 and later with code](#net_d).</span></span>

1. <span data-ttu-id="ae601-208">Zapytanie <xref:System.Environment.Version?displayProperty=nameWithType> właściwość służąca do pobierania <xref:System.Version> obiektu.</span><span class="sxs-lookup"><span data-stu-id="ae601-208">Query the <xref:System.Environment.Version?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object.</span></span> 

    <span data-ttu-id="ae601-209">Zwrócony `System.Version` obiektu określa wersję środowiska uruchomieniowego, które aktualnie wykonuje kod.</span><span class="sxs-lookup"><span data-stu-id="ae601-209">The returned `System.Version` object identifies the version of the runtime that's currently executing the code.</span></span> <span data-ttu-id="ae601-210">Nie zwraca wersji zestawu ani innych wersji środowiska uruchomieniowego, które mogą być zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="ae601-210">It doesn't return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

    <span data-ttu-id="ae601-211">W przypadku wersji .NET Framework 4, 4.5, 4.5.1 i 4.5.2, reprezentacja ciągu zwracanego <xref:System.Version> obiekt ma postać 4.0.30319. *XXXXX*.</span><span class="sxs-lookup"><span data-stu-id="ae601-211">For the .NET Framework versions 4, 4.5, 4.5.1, and 4.5.2, the string representation of the returned <xref:System.Version> object has the form 4.0.30319.*xxxxx*.</span></span> <span data-ttu-id="ae601-212">Dla platformy .NET Framework 4.6 i nowszymi wersjami posiada 4.0.30319.42000 formularza.</span><span class="sxs-lookup"><span data-stu-id="ae601-212">For the .NET Framework 4.6 and later versions, it has the form 4.0.30319.42000.</span></span>    

2. <span data-ttu-id="ae601-213">Po utworzeniu `Version` obiektów, badać je w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ae601-213">After you have the `Version` object, query it as follows:</span></span>

   - <span data-ttu-id="ae601-214">Dla głównej wersji identyfikator (na przykład *4* w wersji 4.0), użyj <xref:System.Version.Major%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ae601-214">For the major release identifier (for example, *4* for version 4.0), use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property.</span></span>

   - <span data-ttu-id="ae601-215">Dla osób nieletnich wersji identyfikator (na przykład *0* w wersji 4.0), użyj <xref:System.Version.Minor%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ae601-215">For the minor release identifier (for example, *0* for version 4.0), use the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property.</span></span>

   - <span data-ttu-id="ae601-216">Aby uzyskać całą wersję ciągu (na przykład *4.0.30319.18010*), użyj <xref:System.Version.ToString%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="ae601-216">For the entire version string (for example, *4.0.30319.18010*), use the <xref:System.Version.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ae601-217">Ta metoda zwraca pojedynczą wartość odzwierciedlającą wersję środowiska uruchomieniowego, które wykonuje kod.</span><span class="sxs-lookup"><span data-stu-id="ae601-217">This method returns a single value that reflects the version of the runtime that's executing the code.</span></span> <span data-ttu-id="ae601-218">Nie zwraca wersji zestawu ani innych wersji środowiska uruchomieniowego, które mogą być zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="ae601-218">It doesn't return assembly versions or other runtime versions that may be installed on the computer.</span></span>



<span data-ttu-id="ae601-219">W poniższym przykładzie użyto <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwość służąca do pobierania informacji o wersji środowiska CLR:</span><span class="sxs-lookup"><span data-stu-id="ae601-219">The following example uses the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve CLR version information:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a><span data-ttu-id="ae601-220">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ae601-220">See also</span></span>

- [<span data-ttu-id="ae601-221">Instrukcje: Określanie, które aktualizacje programu .NET Framework są zainstalowane</span><span class="sxs-lookup"><span data-stu-id="ae601-221">How to: Determine which .NET Framework updates are installed</span></span>](how-to-determine-which-net-framework-updates-are-installed.md)
- [<span data-ttu-id="ae601-222">Instalowanie programu .NET Framework dla deweloperów</span><span class="sxs-lookup"><span data-stu-id="ae601-222">Install the .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="ae601-223">Wersje programu .NET framework i zależności</span><span class="sxs-lookup"><span data-stu-id="ae601-223">.NET Framework versions and dependencies</span></span>](versions-and-dependencies.md)

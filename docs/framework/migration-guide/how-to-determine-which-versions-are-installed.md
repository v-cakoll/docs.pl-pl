---
title: 'Instrukcje: Określanie, które wersje programu .NET Framework są zainstalowane.'
ms.date: 02/20/2019
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
ms.openlocfilehash: d7661b3ebaa8f29d6d3b2adbc56c405c8f0945f3
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56584177"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="ab132-102">Instrukcje: Określanie, które wersje programu .NET Framework są zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="ab132-102">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="ab132-103">Użytkownicy mogą zainstalować i uruchamiać wiele wersji .NET Framework na swoich komputerach.</span><span class="sxs-lookup"><span data-stu-id="ab132-103">Users can install and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="ab132-104">Podczas tworzenia lub wdrażania aplikacji, może być konieczne wiedzieć, które wersje programu .NET Framework są zainstalowane na komputerze użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ab132-104">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span> <span data-ttu-id="ab132-105">Należy zwrócić uwagę na to, że .NET Framework składa się z dwóch głównych składników, które są określane oddzielnie:</span><span class="sxs-lookup"><span data-stu-id="ab132-105">Note that the .NET Framework consists of two main components, which are versioned separately:</span></span>  
  
- <span data-ttu-id="ab132-106">Zbiór zestawów, które są kolekcjami typów i zasobów zapewniających funkcje dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ab132-106">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="ab132-107">.NET Framework i zestawy współużytkują ten sam numer wersji.</span><span class="sxs-lookup"><span data-stu-id="ab132-107">The .NET Framework and assemblies share the same version number.</span></span>  
  
- <span data-ttu-id="ab132-108">Środowisko uruchomieniowe języka wspólnego (CLR) zarządza, która wykonuje kod w swojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ab132-108">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="ab132-109">Środowisko CLR jest identyfikowane za pomocą własnego numeru wersji (zobacz [wersje i zależności](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span><span class="sxs-lookup"><span data-stu-id="ab132-109">The CLR is identified by its own version number (see [Versions and Dependencies](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span></span>  
  
<span data-ttu-id="ab132-110">Aby uzyskać dokładne listę wersji programu .NET Framework zainstalowana na komputerze, można wyświetlić rejestr lub wykonaj zapytanie dotyczące rejestru w kodzie:</span><span class="sxs-lookup"><span data-stu-id="ab132-110">To get an accurate list of the .NET Framework versions installed on a computer, you can view the registry or query the registry in code:</span></span>  
  
 [<span data-ttu-id="ab132-111">Znajdź .NET Framework w wersji 1 – 4 w rejestrze</span><span class="sxs-lookup"><span data-stu-id="ab132-111">Find .NET Framework versions 1-4 in the registry</span></span>](#net_a)  
 [<span data-ttu-id="ab132-112">Znajdź wersje programu .NET Framework 4.5 i nowsze w rejestrze)</span><span class="sxs-lookup"><span data-stu-id="ab132-112">Find .NET Framework versions 4.5 and later in the registry)</span></span>](#net_b)  
 [<span data-ttu-id="ab132-113">Wykonaj zapytanie dotyczące rejestru (wersje 1 – 4) za pomocą kodu</span><span class="sxs-lookup"><span data-stu-id="ab132-113">Using code to query the registry (versions 1-4)</span></span>](#net_c)  
 [<span data-ttu-id="ab132-114">Wykonaj zapytanie dotyczące rejestru (w wersji 4.5 lub nowszy) za pomocą kodu</span><span class="sxs-lookup"><span data-stu-id="ab132-114">Using code to query the registry (version 4.5 and later)</span></span>](#net_d)  
 [<span data-ttu-id="ab132-115">Przy użyciu programu PowerShell do wykonywania zapytań w rejestrze (w wersji 4.5 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="ab132-115">Using PowerShell to query the registry (version 4.5 and later)</span></span>](#ps_a)  

 <span data-ttu-id="ab132-116">Aby znaleźć wersję środowiska CLR, można użyć narzędzia lub kodu:</span><span class="sxs-lookup"><span data-stu-id="ab132-116">To find the CLR version, you can use a tool or code:</span></span>  
  
 [<span data-ttu-id="ab132-117">Za pomocą narzędzia Clrver</span><span class="sxs-lookup"><span data-stu-id="ab132-117">Using the Clrver tool</span></span>](#clr_a)  
 [<span data-ttu-id="ab132-118">Aby wysłać zapytanie klasy System.Environment przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="ab132-118">Using code to query the System.Environment class</span></span>](#clr_b)  

> [!NOTE]
> <span data-ttu-id="ab132-119">Istnieje różnica między wersją .NET Framework i wspólne wersję środowiska uruchomieniowego języka (wspólnego CLR).</span><span class="sxs-lookup"><span data-stu-id="ab132-119">There is a difference between the .NET Framework version and the common language runtime (CLR) version.</span></span> <span data-ttu-id="ab132-120">Program .NET Framework jest wersjonowany na podstawie zestawu zestawów, które tworzą biblioteki klas programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ab132-120">The .NET Framework is versioned based on the set of assemblies that form the .NET Framework Class Library.</span></span> <span data-ttu-id="ab132-121">Na przykład .NET Framework w wersji obejmują 4.5, 4.6.1 i 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="ab132-121">For example, .NET Framework versions include 4.5, 4.6.1, and 4.7.2.</span></span> <span data-ttu-id="ab132-122">Środowisko CLR jest określonej wersji środowiska uruchomieniowego programu .NET Framework aplikacje są wykonywane w oparciu i jednej wersji środowiska CLR zazwyczaj obsługuje wiele wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ab132-122">The CLR is versioned based on the runtime on which .NET Framework applications execute, and a single CLR version typically supports multiple .NET Framework versions.</span></span> <span data-ttu-id="ab132-123">Środowisko CLR w wersji 4.30319. *xxxxx* obsługuje wersje programu .NET Framework 4, za pośrednictwem 4.5.2; Środowisko CLR w wersji 4.30319.42000 obsługuje wersje programu .NET Framework, począwszy od programu .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="ab132-123">CLR version 4.30319.*xxxxx* supports .NET Framework versions 4 through 4.5.2; CLR version 4.30319.42000 supports .NET Framework versions starting with .NET Framework 4.6.</span></span> <span data-ttu-id="ab132-124">Aby uzyskać więcej informacji, zobacz <xref:System.Environment.Version?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ab132-124">For more information, see the <xref:System.Environment.Version?displayProperty=nameWithType> property.</span></span>

 <span data-ttu-id="ab132-125">Aby uzyskać informacje dotyczące wykrywania zainstalowanych aktualizacji dla każdej wersji programu .NET Framework, zobacz [jak: Określanie, które aktualizacje programu .NET Framework są zainstalowane](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="ab132-125">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine Which .NET Framework Updates Are Installed](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md).</span></span> <span data-ttu-id="ab132-126">Aby uzyskać informacje o instalowaniu programu .NET Framework, zobacz [Instalowanie programu .NET Framework dla deweloperów](../../../docs/framework/install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="ab132-126">For information about installing the .NET Framework, see [Install the .NET Framework for developers](../../../docs/framework/install/guide-for-developers.md).</span></span>  
  
<a name="net_a"></a>   
## <a name="find-net-framework-versions-1-4-in-the-registry"></a><span data-ttu-id="ab132-127">Znajdź .NET Framework w wersji 1 – 4 w rejestrze</span><span class="sxs-lookup"><span data-stu-id="ab132-127">Find .NET Framework versions 1-4 in the registry</span></span> 
  
1.  <span data-ttu-id="ab132-128">Na **Start** menu, wybierz **Uruchom**.</span><span class="sxs-lookup"><span data-stu-id="ab132-128">On the **Start** menu, choose **Run**.</span></span>  
  
2.  <span data-ttu-id="ab132-129">W **Otwórz** wprowadź **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="ab132-129">In the **Open** box, enter **regedit.exe**.</span></span>  
  
     <span data-ttu-id="ab132-130">Musisz mieć poświadczenia administracyjne, aby uruchomić program regedit.exe.</span><span class="sxs-lookup"><span data-stu-id="ab132-130">You must have administrative credentials to run regedit.exe.</span></span>  
  
3.  <span data-ttu-id="ab132-131">W Edytorze rejestru otwórz następujący podklucz:</span><span class="sxs-lookup"><span data-stu-id="ab132-131">In the Registry Editor, open the following subkey:</span></span>  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP`  
  
     <span data-ttu-id="ab132-132">Dla wersji programu .NET Framework 1.1 przez 3.5 zainstalowane wersje są wymienione jako podklucze należące do `NDP` podklucza.</span><span class="sxs-lookup"><span data-stu-id="ab132-132">For .NET Framework versions 1.1 through 3.5, the installed versions are listed as subkeys under the `NDP` subkey.</span></span> <span data-ttu-id="ab132-133">Numer wersji jest przechowywany w podkluczu wersji **wersji** wpisu.</span><span class="sxs-lookup"><span data-stu-id="ab132-133">The version number is stored in the version subkey's **Version** entry.</span></span> 
     
     <span data-ttu-id="ab132-134">.NET Framework 4 **wersji** wpis znajduje się w `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client` podklucz `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full` podklucza, lub w obu tych podkluczach.</span><span class="sxs-lookup"><span data-stu-id="ab132-134">For .NET Framework 4, the **Version** entry is under the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client` subkey, the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full` subkey, or under both subkeys.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ab132-135">Folder „NET Framework Setup” w rejestrze nie rozpoczyna się kropką.</span><span class="sxs-lookup"><span data-stu-id="ab132-135">The "NET Framework Setup" folder in the registry does not begin with a period.</span></span>

    <span data-ttu-id="ab132-136">Poniższa ilustracja pokazuje, że podklucz programu .NET Framework 3.5, wraz z jego **wersji** wpisu.</span><span class="sxs-lookup"><span data-stu-id="ab132-136">The following figure shows that the subkey for the .NET Framework 3.5 along with its **Version** entry.</span></span>

     <span data-ttu-id="ab132-137">![Wpis rejestru dla programu .NET Framework 3.5. ](../../../docs/framework/migration-guide/media/net-4-and-earlier.png ".NET framework 4 i starszych wersji")</span><span class="sxs-lookup"><span data-stu-id="ab132-137">![The registry entry for the .NET Framework 3.5.](../../../docs/framework/migration-guide/media/net-4-and-earlier.png ".NET Framework 4 and earlier versions")</span></span>

<a name="net_b"></a> 
## <a name="find-net-framework-versions-45-and-later-in-the-registry"></a><span data-ttu-id="ab132-138">Znajdź wersje programu .NET Framework 4.5 i nowsze w rejestrze</span><span class="sxs-lookup"><span data-stu-id="ab132-138">Find .NET Framework versions 4.5 and later in the registry</span></span>

1. <span data-ttu-id="ab132-139">Na **Start** menu, wybierz **Uruchom**.</span><span class="sxs-lookup"><span data-stu-id="ab132-139">On the **Start** menu, choose **Run**.</span></span>

2. <span data-ttu-id="ab132-140">W **Otwórz** wprowadź **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="ab132-140">In the **Open** box, enter **regedit.exe**.</span></span>

     <span data-ttu-id="ab132-141">Musisz mieć poświadczenia administracyjne, aby uruchomić program regedit.exe.</span><span class="sxs-lookup"><span data-stu-id="ab132-141">You must have administrative credentials to run regedit.exe.</span></span>

3. <span data-ttu-id="ab132-142">W Edytorze rejestru otwórz następujący podklucz:</span><span class="sxs-lookup"><span data-stu-id="ab132-142">In the Registry Editor, open the following subkey:</span></span>

     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`

     <span data-ttu-id="ab132-143">Należy pamiętać, że ścieżka do `Full` podklucz obejmuje podklucz `Net Framework` zamiast `.NET Framework`.</span><span class="sxs-lookup"><span data-stu-id="ab132-143">Note that the path to the `Full` subkey includes the subkey `Net Framework` rather than `.NET Framework`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ab132-144">Jeśli `Full` podklucz nie jest obecny, a następnie nie ma programu .NET Framework 4.5 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="ab132-144">If the `Full` subkey is not present, then you do not have the .NET Framework 4.5 or later installed.</span></span>

     <span data-ttu-id="ab132-145">Wyszukaj wartość DWORD o nazwie `Release`.</span><span class="sxs-lookup"><span data-stu-id="ab132-145">Check for a DWORD value named `Release`.</span></span> <span data-ttu-id="ab132-146">Istnienie `Release` typu DWORD wskazuje, że zainstalowano .NET Framework 4.5 lub nowszej na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="ab132-146">The existence of the `Release` DWORD indicates that .NET Framework 4.5 or later has been installed on that computer.</span></span> <span data-ttu-id="ab132-147">Jego wartość to klucz wersji, który odnosi się do określonej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ab132-147">Its value is a release key that corresponds to a particular version of .NET Framework.</span></span> <span data-ttu-id="ab132-148">Na poniższej ilustracji, na przykład, wartość `Release` DWORD jest 378389, czyli na klucz wersji .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="ab132-148">In the following figure, for example, the value of the `Release` DWORD is 378389, which is the release key for .NET Framework 4.5.</span></span> 

     <span data-ttu-id="ab132-149">![Wpis rejestru dla programu .NET Framework 4.5. ](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span><span class="sxs-lookup"><span data-stu-id="ab132-149">![The registry entry for the .NET Framework 4.5.](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span></span>

<span data-ttu-id="ab132-150">W poniższej tabeli przedstawiono minimalną wartość `Release` DWORD dla każdej wersji systemu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ab132-150">The following table lists the minimum value of the `Release` DWORD for each .NET Framework version.</span></span> <span data-ttu-id="ab132-151">Można użyć tych wartości w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ab132-151">You can use these values as follows:</span></span>

- <span data-ttu-id="ab132-152">Aby ustalić, czy minimalna wersja architektury .NET Framework jest obecny, test czy `Release` wartość DWORD znaleziony w rejestrze jest *większa lub równa* wartości wymienione w tabeli.</span><span class="sxs-lookup"><span data-stu-id="ab132-152">To determine whether a minimum .NET Framework version is present, test whether the `Release` DWORD value found in the registry is *greater than or equal to* the value listed in the table.</span></span> <span data-ttu-id="ab132-153">Na przykład jeśli aplikacja wymaga .NET Framework w wersji 4.7 lub nowszej, czy test dla wersji minimalnej wartości klucza 460798.</span><span class="sxs-lookup"><span data-stu-id="ab132-153">For example, if your application requires .NET Framework 4.7 or later, you would test for a minimum release key value of 460798.</span></span>

- <span data-ttu-id="ab132-154">Do testowania dla różnych wersji, zaczynają się od najnowszej wersji .NET Framework, a następnie przetestować każda kolejne starszej wersji.</span><span class="sxs-lookup"><span data-stu-id="ab132-154">To test for multiple versions, begin with the latest .NET Framework version, and then test for each successive earlier version.</span></span>

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

|<span data-ttu-id="ab132-155">Wersja programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ab132-155">.NET Framework Version</span></span>|<span data-ttu-id="ab132-156">Wartość DWORD dotycząca wersji</span><span class="sxs-lookup"><span data-stu-id="ab132-156">Value of the Release DWORD</span></span>|
|--------------------------------|-------------|
|<span data-ttu-id="ab132-157">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="ab132-157">.NET Framework 4.5</span></span>|<span data-ttu-id="ab132-158">378389</span><span class="sxs-lookup"><span data-stu-id="ab132-158">378389</span></span>|
|<span data-ttu-id="ab132-159">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="ab132-159">.NET Framework 4.5.1</span></span>|<span data-ttu-id="ab132-160">378675</span><span class="sxs-lookup"><span data-stu-id="ab132-160">378675</span></span>|
|<span data-ttu-id="ab132-161">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="ab132-161">.NET Framework 4.5.2</span></span>|<span data-ttu-id="ab132-162">379893</span><span class="sxs-lookup"><span data-stu-id="ab132-162">379893</span></span>|
|<span data-ttu-id="ab132-163">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="ab132-163">.NET Framework 4.6</span></span>|<span data-ttu-id="ab132-164">393295</span><span class="sxs-lookup"><span data-stu-id="ab132-164">393295</span></span>|
|<span data-ttu-id="ab132-165">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="ab132-165">.NET Framework 4.6.1</span></span>|<span data-ttu-id="ab132-166">394254</span><span class="sxs-lookup"><span data-stu-id="ab132-166">394254</span></span>|
|<span data-ttu-id="ab132-167">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="ab132-167">.NET Framework 4.6.2</span></span>|<span data-ttu-id="ab132-168">394802</span><span class="sxs-lookup"><span data-stu-id="ab132-168">394802</span></span>|
|<span data-ttu-id="ab132-169">.NET framework 4.7</span><span class="sxs-lookup"><span data-stu-id="ab132-169">.NET Framework 4.7</span></span>|<span data-ttu-id="ab132-170">460798</span><span class="sxs-lookup"><span data-stu-id="ab132-170">460798</span></span>|
|<span data-ttu-id="ab132-171">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="ab132-171">.NET Framework 4.7.1</span></span>|<span data-ttu-id="ab132-172">461308</span><span class="sxs-lookup"><span data-stu-id="ab132-172">461308</span></span>|
|<span data-ttu-id="ab132-173">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="ab132-173">.NET Framework 4.7.2</span></span>|<span data-ttu-id="ab132-174">461808</span><span class="sxs-lookup"><span data-stu-id="ab132-174">461808</span></span>|

<span data-ttu-id="ab132-175">Aby uzyskać pełną tabelę klawiszy wersji dla programu .NET Framework dla określonej wersji systemu operacyjnego Windows, zobacz [kluczy wersji .NET Framework i wersji systemu operacyjnego Windows](release-keys-and-os-versions.md).</span><span class="sxs-lookup"><span data-stu-id="ab132-175">For a complete table of release keys for the .NET Framework for specific Windows operating system versions, see [.NET Framework release keys and Windows operating system versions](release-keys-and-os-versions.md).</span></span>

<a name="net_c"></a> 
## <a name="find-net-framework-versions-1-4-with-code"></a><span data-ttu-id="ab132-176">Znajdź .NET Framework w wersji 1 do 4 z kodem</span><span class="sxs-lookup"><span data-stu-id="ab132-176">Find .NET Framework versions 1-4 with code</span></span>

- <span data-ttu-id="ab132-177">Użyj <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> klasy, aby uzyskać dostęp do `Software\Microsoft\NET Framework Setup\NDP\` podkluczy w obszarze `HKEY_LOCAL_MACHINE` gałęzi w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ab132-177">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the `Software\Microsoft\NET Framework Setup\NDP\` subkey under `HKEY_LOCAL_MACHINE` branch in the Windows registry.</span></span>

     <span data-ttu-id="ab132-178">Poniższy kod przedstawia przykład tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="ab132-178">The following code shows an example of this query.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ab132-179">Ten kod nie pokazuje, jak wykrywać .NET Framework 4.5 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="ab132-179">This code does not show how to detect .NET Framework 4.5 or later.</span></span> <span data-ttu-id="ab132-180">Sprawdź `Release` DWORD, aby wykryć te wersje, zgodnie z opisem w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="ab132-180">Check the `Release` DWORD to detect those versions, as described in the previous section.</span></span> <span data-ttu-id="ab132-181">Kod, który wykrywa .NET Framework 4.5 lub nowszej wersji zobacz sekcję dalej w tym artykule.</span><span class="sxs-lookup"><span data-stu-id="ab132-181">For code that detects .NET Framework 4.5 or later versions, see the next section in this article.</span></span>

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

<a name="net_d"></a> 
## <a name="find-net-framework-versions-45-and-later-with-code"></a><span data-ttu-id="ab132-182">Znajdź wersje programu .NET Framework 4.5 lub nowszy z kodem</span><span class="sxs-lookup"><span data-stu-id="ab132-182">Find .NET Framework versions 4.5 and later with code</span></span>

1. <span data-ttu-id="ab132-183">Istnienie `Release` DWORD w `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` klucz wskazuje, że .NET Framework 4.5 lub nowszej jest zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="ab132-183">The existence of the `Release` DWORD in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key indicates that the .NET Framework 4.5 or later is installed on a computer.</span></span> <span data-ttu-id="ab132-184">Wartość słowa kluczowego wskazuje zainstalowanej wersji.</span><span class="sxs-lookup"><span data-stu-id="ab132-184">The value of the keyword indicates the installed version.</span></span> <span data-ttu-id="ab132-185">Aby sprawdzić to słowo kluczowe, użyj <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> i <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> metodach dostępu podkluczu w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ab132-185">To check this keyword, use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> methods to access the subkey in the Windows registry.</span></span>

2. <span data-ttu-id="ab132-186">Sprawdź wartość `Release` słowo kluczowe, aby ustalić zainstalowaną wersję.</span><span class="sxs-lookup"><span data-stu-id="ab132-186">Check the value of the `Release` keyword to determine the installed version.</span></span> <span data-ttu-id="ab132-187">Być zgodne, możesz sprawdzić wartość większa niż lub równa wartości wymienione w tabeli w [znaleźć .NET Framework w wersji 4.5 lub nowszy w rejestrze](#net_b) sekcji.</span><span class="sxs-lookup"><span data-stu-id="ab132-187">To be forward-compatible, you can check for a value greater than or equal to the value listed in the table in the [Find .NET Framework versions 4.5 and later in the registry](#net_b) section.</span></span>

<span data-ttu-id="ab132-188">Następujące testy przykład `Release` wartości w rejestrze, aby ustalić, czy jest zainstalowany program .NET Framework 4.5 lub nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="ab132-188">The following example checks the `Release` value in the registry to determine whether .NET Framework 4.5 or a later version is installed.</span></span>

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

<span data-ttu-id="ab132-189">W tym przykładzie następuje zalecana praktyka dla kontroli wersji:</span><span class="sxs-lookup"><span data-stu-id="ab132-189">This example follows the recommended practice for version checking:</span></span>

- <span data-ttu-id="ab132-190">Sprawdza, czy wartość `Release` wpis jest *większa lub równa* wartości kluczy znanych wydania.</span><span class="sxs-lookup"><span data-stu-id="ab132-190">It checks whether the value of the `Release` entry is *greater than or equal to* the value of the known release keys.</span></span>

- <span data-ttu-id="ab132-191">Sprawdza w kolejności od najbardziej aktualną wersję do najwcześniejszej wersji.</span><span class="sxs-lookup"><span data-stu-id="ab132-191">It checks in order from most recent version to earliest version.</span></span>

<a name="ps_a"></a> 
## <a name="check-for-a-minimum-required-net-framework-version-45-and-later-with-powershell"></a><span data-ttu-id="ab132-192">Sprawdź, czy minimalna wymagana .NET Framework w wersji (4.5 lub nowszy) za pomocą programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="ab132-192">Check for a minimum required .NET Framework version (4.5 and later) with PowerShell</span></span>

<span data-ttu-id="ab132-193">Poniższy przykład sprawdza wartość `Release` — słowo kluczowe, aby określić, czy platformy .NET Framework 4.6.2 lub nowszy jest zainstalowany (zwracanie `True` , gdy jest i `False` inaczej).</span><span class="sxs-lookup"><span data-stu-id="ab132-193">The following example checks the value of the `Release` keyword to determine whether .NET Framework 4.6.2 or higher is installed (returning `True` if it is and `False` otherwise).</span></span>

    ```PowerShell
    # PowerShell 5
    Get-ChildItem 'HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\' | Get-ItemPropertyValue -Name Release | Foreach-Object { $_ -ge 394802 } 
    ```

    ```PowerShell
    # PowerShell 4
    (Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -gt 394802
    ```

    You can replace `394802` in the previous example with another value from the following table in the [Find .NET Framework versions 4.5 and later in the registry](#net_b) section to check for a different minimum required .NET Framework version.
  
<a name="clr_a"></a> 
## <a name="find-the-current-clr-version-with-clrverexe"></a><span data-ttu-id="ab132-194">Znaleźć bieżącą wersję środowiska CLR przy użyciu Clrver.exe</span><span class="sxs-lookup"><span data-stu-id="ab132-194">Find the current CLR version with Clrver.exe</span></span>

<span data-ttu-id="ab132-195">Użyj narzędzia wersji środowiska CLR (Clrver.exe) w celu ustalenia, które wersje środowiska uruchomieniowego języka wspólnego są zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="ab132-195">Use the CLR Version Tool (Clrver.exe) to determine which versions of the common language runtime are installed on a computer.</span></span>

<span data-ttu-id="ab132-196">Wprowadź w wierszu polecenia dla deweloperów programu Visual Studio, `clrver`.</span><span class="sxs-lookup"><span data-stu-id="ab132-196">From a Developer Command Prompt for Visual Studio, enter `clrver`.</span></span> <span data-ttu-id="ab132-197">To polecenie tworzy dane wyjściowe podobne do poniższych:</span><span class="sxs-lookup"><span data-stu-id="ab132-197">This command produces output similar to the following:</span></span>

```console
Versions installed on the machine:
v2.0.50727
v4.0.30319
```

<span data-ttu-id="ab132-198">Aby uzyskać więcej informacji dotyczących używania tego narzędzia, zobacz [Clrver.exe (narzędzie wersji środowiska CLR)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).</span><span class="sxs-lookup"><span data-stu-id="ab132-198">For more information about using this tool, see [Clrver.exe (CLR Version Tool)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).</span></span>

<a name="clr_b"></a> 
## <a name="find-the-current-clr-version-with-the-environment-class"></a><span data-ttu-id="ab132-199">Znaleźć bieżącą wersję środowiska CLR przy użyciu klasy środowiska</span><span class="sxs-lookup"><span data-stu-id="ab132-199">Find the current CLR version with the Environment class</span></span>

<span data-ttu-id="ab132-200">Można pobrać wartość <xref:System.Environment.Version?displayProperty=nameWithType> właściwość służąca do pobierania <xref:System.Version> obiektu, który identyfikuje wersję środowiska uruchomieniowego, które aktualnie wykonuje kod.</span><span class="sxs-lookup"><span data-stu-id="ab132-200">You can retrieve the value of the <xref:System.Environment.Version?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object that identifies the version of the runtime that is currently executing the code.</span></span> <span data-ttu-id="ab132-201">Ta właściwość zwraca jedną wartość odzwierciedlającą wersję środowiska uruchomieniowego, które aktualnie wykonuje kod; nie zwraca wersji zestawu ani innych wersji środowiska uruchomieniowego, które mogą być zainstalowane na komputerze. Możesz użyć <xref:System.Version.Major%2A?displayProperty=nameWithType> właściwości, aby uzyskać identyfikator wersji głównej (na przykład "4" w wersji 4.0), <xref:System.Version.Minor%2A?displayProperty=nameWithType> właściwości, aby uzyskać identyfikator wersji pomocniczej (na przykład, "0" do wersji 4.0 lub nowszej), lub <xref:System.Version.ToString%2A?displayProperty=nameWithType> metodę, aby uzyskać całą wersję ciąg (na przykład "4.0.30319.18010", jak pokazano w poniższym kodzie).</span><span class="sxs-lookup"><span data-stu-id="ab132-201">This property returns a single value that reflects the version of the runtime that is currently executing the code; it does not return assembly versions or other versions of the runtime that may have been installed on the computer.You can use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property to get the major release identifier (for example, "4" for version 4.0), the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property to get the minor release identifier (for example, "0" for version 4.0), or the <xref:System.Version.ToString%2A?displayProperty=nameWithType> method to get the entire version string (for example, "4.0.30319.18010", as shown in the following code).</span></span> 

<span data-ttu-id="ab132-202">Dla platformy .NET Framework 4, 4.5, 4.5.1 i 4.5.2 <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwość zwraca <xref:System.Version> obiektu, którego reprezentacja ciągu ma postać `4.0.30319.xxxxx`.</span><span class="sxs-lookup"><span data-stu-id="ab132-202">For the .NET Framework Versions 4, 4.5, 4.5.1, and 4.5.2, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns a <xref:System.Version> object whose string representation has the form `4.0.30319.xxxxx`.</span></span> <span data-ttu-id="ab132-203">Dla programu .NET Framework 4.6 lub nowszy, ma on postać `4.0.30319.42000`.</span><span class="sxs-lookup"><span data-stu-id="ab132-203">For the .NET Framework 4.6 and later, it has the form `4.0.30319.42000`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ab132-204">Dla programu .NET Framework 4.5 lub nowszy, zaleca się używania <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwości do wykrywania wersji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="ab132-204">For the .NET Framework 4.5 and later, we do not recommend using the  <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the runtime.</span></span> <span data-ttu-id="ab132-205">Zamiast tego zaleca się zapytania rejestru zgodnie z opisem w [można znaleźć wersji programu .NET Framework, wykonując zapytanie w rejestrze w kodzie (.NET Framework 4.5 i nowsze)](#net_d) sekcji we wcześniejszej części tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="ab132-205">Instead, we recommend that you query the registry, as described in the [To find .NET Framework versions by querying the registry in code (.NET Framework 4.5 and later)](#net_d) section earlier in this article.</span></span>

<span data-ttu-id="ab132-206">W poniższym przykładzie użyto <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwość służąca do pobierania informacji o wersji środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="ab132-206">The following example used the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve runtime version information:</span></span>

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a><span data-ttu-id="ab132-207">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ab132-207">See also</span></span>

- [<span data-ttu-id="ab132-208">Instrukcje: Określanie, które aktualizacje programu .NET Framework są zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="ab132-208">How to: Determine Which .NET Framework Updates Are Installed</span></span>](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)
- [<span data-ttu-id="ab132-209">Instalowanie programu .NET Framework dla deweloperów</span><span class="sxs-lookup"><span data-stu-id="ab132-209">Install the .NET Framework for developers</span></span>](../../../docs/framework/install/guide-for-developers.md)
- [<span data-ttu-id="ab132-210">Wersje i zależności</span><span class="sxs-lookup"><span data-stu-id="ab132-210">Versions and Dependencies</span></span>](~/docs/framework/migration-guide/versions-and-dependencies.md)

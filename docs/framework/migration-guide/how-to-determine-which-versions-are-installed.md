---
title: 'Porady: Określanie, które wersje programu .NET Framework są zainstalowane'
ms.date: 04/10/2018
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
ms.openlocfilehash: 3677ff7cc27847d56802206c793a574d61b1464c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="9f850-102">Porady: Określanie, które wersje programu .NET Framework są zainstalowane</span><span class="sxs-lookup"><span data-stu-id="9f850-102">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="9f850-103">Użytkownicy mogą zainstalować i uruchamiać wiele wersji .NET Framework na swoich komputerach.</span><span class="sxs-lookup"><span data-stu-id="9f850-103">Users can install and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="9f850-104">Podczas opracowywania lub wdrożyć aplikację, konieczne może być wiedzieć, które wersje programu .NET Framework są zainstalowane na komputerze użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9f850-104">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span> <span data-ttu-id="9f850-105">Należy pamiętać, że programu .NET Framework składa się z dwóch głównych elementów, które numerów wersji oddzielnie:</span><span class="sxs-lookup"><span data-stu-id="9f850-105">Note that the .NET Framework consists of two main components, which are versioned separately:</span></span>  
  
-   <span data-ttu-id="9f850-106">Zbiór zestawów, które są kolekcjami typów i zasobów, które zapewniają funkcje dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9f850-106">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="9f850-107">.NET Framework i zestawy udostępnianie tego samego numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="9f850-107">The .NET Framework and assemblies share the same version number.</span></span>  
  
-   <span data-ttu-id="9f850-108">Środowisko uruchomieniowe języka wspólnego (CLR), która zarządza i wykonuje kod aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9f850-108">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="9f850-109">Środowisko CLR jest identyfikowany przez numer wersji (zobacz [wersje i zależności](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span><span class="sxs-lookup"><span data-stu-id="9f850-109">The CLR is identified by its own version number (see [Versions and Dependencies](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span></span>  
  
 <span data-ttu-id="9f850-110">Aby uzyskać dokładne listę zainstalowanych na komputerze wersji .NET Framework, można wyświetlić rejestru lub zapytanie dotyczące rejestru w kodzie:</span><span class="sxs-lookup"><span data-stu-id="9f850-110">To get an accurate list of the .NET Framework versions installed on a computer, you can view the registry or query the registry in code:</span></span>  
  
 [<span data-ttu-id="9f850-111">Wyświetlanie w rejestrze (wersje 1-4)</span><span class="sxs-lookup"><span data-stu-id="9f850-111">Viewing the registry (versions 1-4)</span></span>](#net_a)  
 [<span data-ttu-id="9f850-112">Wyświetlanie w rejestrze (w wersji 4.5 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="9f850-112">Viewing the registry (version 4.5 and later)</span></span>](#net_b)  
 [<span data-ttu-id="9f850-113">Zapytanie dotyczące rejestru (wersje 1-4) za pomocą kodu</span><span class="sxs-lookup"><span data-stu-id="9f850-113">Using code to query the registry (versions 1-4)</span></span>](#net_c)  
 [<span data-ttu-id="9f850-114">Zapytanie dotyczące rejestru (w wersji 4.5 lub nowszej) za pomocą kodu</span><span class="sxs-lookup"><span data-stu-id="9f850-114">Using code to query the registry (version 4.5 and later)</span></span>](#net_d)  
 [<span data-ttu-id="9f850-115">Zapytanie dotyczące rejestru (w wersji 4.5 lub nowszej) przy użyciu programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="9f850-115">Using PowerShell to query the registry (version 4.5 and later)</span></span>](#ps_a)  
  
 <span data-ttu-id="9f850-116">Aby znaleźć wersji środowiska CLR, można użyć narzędzia lub kodu:</span><span class="sxs-lookup"><span data-stu-id="9f850-116">To find the CLR version, you can use a tool or code:</span></span>  
  
 [<span data-ttu-id="9f850-117">Za pomocą narzędzia Clrver</span><span class="sxs-lookup"><span data-stu-id="9f850-117">Using the Clrver tool</span></span>](#clr_a)  
 [<span data-ttu-id="9f850-118">Do klasy System.Environment zapytania przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="9f850-118">Using code to query the System.Environment class</span></span>](#clr_b)  
  
 <span data-ttu-id="9f850-119">Uzyskać informacji o wykrywaniu zainstalowanych aktualizacji dla każdej wersji systemu .NET Framework, zobacz [porady: ustalić, które .NET Framework aktualizacje są instalowane](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="9f850-119">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine Which .NET Framework Updates Are Installed](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md).</span></span> <span data-ttu-id="9f850-120">Aby uzyskać informacje na temat Instalowanie programu .NET Framework, zobacz [Zainstaluj program .NET Framework dla deweloperów](../../../docs/framework/install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="9f850-120">For information about installing the .NET Framework, see [Install the .NET Framework for developers](../../../docs/framework/install/guide-for-developers.md).</span></span>  
  
<a name="net_a"></a>   
## <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-1-4"></a><span data-ttu-id="9f850-121">Aby znaleźć wersje programu .NET Framework, wyświetlając rejestru (.NET Framework 1-4)</span><span class="sxs-lookup"><span data-stu-id="9f850-121">To find .NET Framework versions by viewing the registry (.NET Framework 1-4)</span></span>  
  
1.  <span data-ttu-id="9f850-122">Na **Start** menu, wybierz **Uruchom**.</span><span class="sxs-lookup"><span data-stu-id="9f850-122">On the **Start** menu, choose **Run**.</span></span>  
  
2.  <span data-ttu-id="9f850-123">W **Otwórz** wprowadź **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="9f850-123">In the **Open** box, enter **regedit.exe**.</span></span>  
  
     <span data-ttu-id="9f850-124">Musisz mieć poświadczenia administracyjne, aby uruchomić program regedit.exe.</span><span class="sxs-lookup"><span data-stu-id="9f850-124">You must have administrative credentials to run regedit.exe.</span></span>  
  
3.  <span data-ttu-id="9f850-125">W Edytorze rejestru otwórz następujący podklucz:</span><span class="sxs-lookup"><span data-stu-id="9f850-125">In the Registry Editor, open the following subkey:</span></span>  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP`  
  
     <span data-ttu-id="9f850-126">Zainstalowane wersje są wymienione w podkluczu NDP.</span><span class="sxs-lookup"><span data-stu-id="9f850-126">The installed versions are listed under the NDP subkey.</span></span> <span data-ttu-id="9f850-127">Numer wersji jest zapisany w **wersji** wpisu.</span><span class="sxs-lookup"><span data-stu-id="9f850-127">The version number is stored in the **Version** entry.</span></span> <span data-ttu-id="9f850-128">Dla [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] **wersji** wpis podlega klienta lub pełne podklucz (w obszarze NPR) lub w obu podkluczach.</span><span class="sxs-lookup"><span data-stu-id="9f850-128">For the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] the **Version** entry is under the Client or Full subkey (under NDP), or under both subkeys.</span></span>  
  

    > [!NOTE]
    > <span data-ttu-id="9f850-129">Folder „NET Framework Setup” w rejestrze nie rozpoczyna się kropką.</span><span class="sxs-lookup"><span data-stu-id="9f850-129">The "NET Framework Setup" folder in the registry does not begin with a period.</span></span>

<a name="net_b"></a> 
## <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-45-and-later"></a><span data-ttu-id="9f850-130">Aby znaleźć wersje programu .NET Framework, wyświetlając rejestru (.NET Framework 4.5 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="9f850-130">To find .NET Framework versions by viewing the registry (.NET Framework 4.5 and later)</span></span>

1. <span data-ttu-id="9f850-131">Na **Start** menu, wybierz **Uruchom**.</span><span class="sxs-lookup"><span data-stu-id="9f850-131">On the **Start** menu, choose **Run**.</span></span>

2. <span data-ttu-id="9f850-132">W **Otwórz** wprowadź **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="9f850-132">In the **Open** box, enter **regedit.exe**.</span></span>

     <span data-ttu-id="9f850-133">Musisz mieć poświadczenia administracyjne, aby uruchomić program regedit.exe.</span><span class="sxs-lookup"><span data-stu-id="9f850-133">You must have administrative credentials to run regedit.exe.</span></span>

3. <span data-ttu-id="9f850-134">W Edytorze rejestru otwórz następujący podklucz:</span><span class="sxs-lookup"><span data-stu-id="9f850-134">In the Registry Editor, open the following subkey:</span></span>

     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`

     <span data-ttu-id="9f850-135">Należy pamiętać, że ścieżka do `Full` podklucz zawiera podklucz `Net Framework` zamiast `.NET Framework`.</span><span class="sxs-lookup"><span data-stu-id="9f850-135">Note that the path to the `Full` subkey includes the subkey `Net Framework` rather than `.NET Framework`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="9f850-136">Jeśli `Full` podklucz nie jest obecny, a następnie nie ma programu .NET Framework 4.5 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="9f850-136">If the `Full` subkey is not present, then you do not have the .NET Framework 4.5 or later installed.</span></span>

     <span data-ttu-id="9f850-137">Sprawdź, czy wartość DWORD o nazwie `Release`.</span><span class="sxs-lookup"><span data-stu-id="9f850-137">Check for a DWORD value named `Release`.</span></span> <span data-ttu-id="9f850-138">Istnienie `Release` DWORD wskazuje, że [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub nowszej został zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="9f850-138">The existence of the `Release` DWORD indicates that the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or newer has been installed on that computer.</span></span>

     <span data-ttu-id="9f850-139">![Wpis rejestru dla programu .NET Framework 4.5. ] (../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span><span class="sxs-lookup"><span data-stu-id="9f850-139">![The registry entry for the .NET Framework 4.5.](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span></span>

     <span data-ttu-id="9f850-140">Wartość `Release` DWORD wskazuje, która wersja architektury .NET Framework jest zainstalowana.</span><span class="sxs-lookup"><span data-stu-id="9f850-140">The value of the `Release` DWORD indicates which version of the .NET Framework is installed.</span></span>

    [!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

    |<span data-ttu-id="9f850-141">Wartość DWORD dotycząca wersji</span><span class="sxs-lookup"><span data-stu-id="9f850-141">Value of the Release DWORD</span></span>|<span data-ttu-id="9f850-142">Wersja</span><span class="sxs-lookup"><span data-stu-id="9f850-142">Version</span></span>|
    |--------------------------------|-------------|
    |<span data-ttu-id="9f850-143">378389</span><span class="sxs-lookup"><span data-stu-id="9f850-143">378389</span></span>|<span data-ttu-id="9f850-144">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="9f850-144">.NET Framework 4.5</span></span>|
    |<span data-ttu-id="9f850-145">378675</span><span class="sxs-lookup"><span data-stu-id="9f850-145">378675</span></span>|<span data-ttu-id="9f850-146">.NET framework 4.5.1 zainstalowaną w systemie Windows 8.1 lub Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="9f850-146">.NET Framework 4.5.1 installed with Windows 8.1 or Windows Server 2012 R2</span></span>|
    |<span data-ttu-id="9f850-147">378758</span><span class="sxs-lookup"><span data-stu-id="9f850-147">378758</span></span>|<span data-ttu-id="9f850-148">.NET framework 4.5.1 w systemie Windows 8, Windows 7 z dodatkiem SP1 lub Windows Vista z dodatkiem SP2</span><span class="sxs-lookup"><span data-stu-id="9f850-148">.NET Framework 4.5.1 installed on Windows 8, Windows 7 SP1, or Windows Vista SP2</span></span>|
    |<span data-ttu-id="9f850-149">379893</span><span class="sxs-lookup"><span data-stu-id="9f850-149">379893</span></span>|<span data-ttu-id="9f850-150">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="9f850-150">.NET Framework 4.5.2</span></span>|
    |<span data-ttu-id="9f850-151">Tylko w systemie Windows 10: 393295</span><span class="sxs-lookup"><span data-stu-id="9f850-151">On Windows 10 systems only: 393295</span></span><br /><br /> <span data-ttu-id="9f850-152">We wszystkich wersjach systemu operacyjnego: 393297</span><span class="sxs-lookup"><span data-stu-id="9f850-152">On all other OS versions: 393297</span></span>|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|
    |<span data-ttu-id="9f850-153">Tylko w systemie Windows 10 listopada Update: 394254</span><span class="sxs-lookup"><span data-stu-id="9f850-153">On Windows 10 November Update systems only: 394254</span></span><br /><br /> <span data-ttu-id="9f850-154">We wszystkich wersjach systemu operacyjnego: 394271</span><span class="sxs-lookup"><span data-stu-id="9f850-154">On all other OS versions: 394271</span></span>|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|
    |<span data-ttu-id="9f850-155">W systemie Windows 10 Anniversary zaktualizować tylko: 394802</span><span class="sxs-lookup"><span data-stu-id="9f850-155">On Windows 10 Anniversary Update only: 394802</span></span><br /><br /> <span data-ttu-id="9f850-156">We wszystkich wersjach systemu operacyjnego: 394806</span><span class="sxs-lookup"><span data-stu-id="9f850-156">On all other OS versions: 394806</span></span>|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]| 
    |<span data-ttu-id="9f850-157">Na twórców systemu Windows 10 zaktualizować tylko: 460798</span><span class="sxs-lookup"><span data-stu-id="9f850-157">On Windows 10 Creators Update only: 460798</span></span><br/><br/> <span data-ttu-id="9f850-158">We wszystkich wersjach systemu operacyjnego: 460805</span><span class="sxs-lookup"><span data-stu-id="9f850-158">On all other OS versions: 460805</span></span> | <span data-ttu-id="9f850-159">.NET framework 4.7</span><span class="sxs-lookup"><span data-stu-id="9f850-159">.NET Framework 4.7</span></span> |
    |<span data-ttu-id="9f850-160">W systemie Windows 10 twórców spadku zaktualizować tylko: 461308</span><span class="sxs-lookup"><span data-stu-id="9f850-160">On Windows 10 Fall Creators Update only: 461308</span></span><br/><br/> <span data-ttu-id="9f850-161">We wszystkich wersjach systemu operacyjnego: 461310</span><span class="sxs-lookup"><span data-stu-id="9f850-161">On all other OS versions: 461310</span></span> | <span data-ttu-id="9f850-162">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="9f850-162">.NET Framework 4.7.1</span></span> |
    |<span data-ttu-id="9f850-163">Na tylko aktualizacji systemu Windows 10 kwietnia 2018: 461808</span><span class="sxs-lookup"><span data-stu-id="9f850-163">On Windows 10 April 2018 Update only: 461808</span></span><br/><br/> <span data-ttu-id="9f850-164">We wszystkich wersjach systemu operacyjnego: 461814</span><span class="sxs-lookup"><span data-stu-id="9f850-164">On all other OS versions: 461814</span></span>| <span data-ttu-id="9f850-165">.NET framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="9f850-165">.NET Framework 4.7.2</span></span> |
    
<a name="net_c"></a> 
## <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-1-4"></a><span data-ttu-id="9f850-166">Aby znaleźć wersje programu .NET Framework, badając rejestru w kodzie (.NET Framework 1-4)</span><span class="sxs-lookup"><span data-stu-id="9f850-166">To find .NET Framework versions by querying the registry in code (.NET Framework 1-4)</span></span>

- <span data-ttu-id="9f850-167">Użyj <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> klasy do podklucza Software\Microsoft\NET Framework Setup\NDP\ w HKEY_LOCAL_MACHINE w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="9f850-167">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the Software\Microsoft\NET Framework Setup\NDP\ subkey under HKEY_LOCAL_MACHINE in the Windows registry.</span></span>

     <span data-ttu-id="9f850-168">Poniższy kod przedstawia przykład tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="9f850-168">The following code shows an example of this query.</span></span>

    > [!NOTE]
    > <span data-ttu-id="9f850-169">Ten kod nie przedstawiają sposób wykrywania [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="9f850-169">This code does not show how to detect the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or later.</span></span> <span data-ttu-id="9f850-170">Sprawdź `Release` DWORD, aby wykryć te wersje, zgodnie z opisem w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="9f850-170">Check the `Release` DWORD to detect those versions, as described in the previous section.</span></span> <span data-ttu-id="9f850-171">Dla kodu, które wykrywają [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub nowszych wersjach, zobacz następną sekcję w tym artykule.</span><span class="sxs-lookup"><span data-stu-id="9f850-171">For code that does detect the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or later versions, see the next section in this article.</span></span>

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

     <span data-ttu-id="9f850-172">W przykładzie są generowane dane wyjściowe podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="9f850-172">The example produces output that's similar to the following:</span></span>

    ```
    v2.0.50727  2.0.50727.4016  SP2
    v3.0  3.0.30729.4037  SP2
    v3.5  3.5.30729.01  SP1
    v4
      Client  4.0.30319
      Full  4.0.30319
    ```

<a name="net_d"></a> 
## <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-45-and-later"></a><span data-ttu-id="9f850-173">Aby znaleźć wersje programu .NET Framework, badając rejestru w kodzie (.NET Framework 4.5 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="9f850-173">To find .NET Framework versions by querying the registry in code (.NET Framework 4.5 and later)</span></span>

1. <span data-ttu-id="9f850-174">Istnienie `Release` DWORD wskazuje, że na komputerze zainstalowano .NET Framework 4.5 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="9f850-174">The existence of the `Release` DWORD indicates that the .NET Framework 4.5 or later has been installed on a computer.</span></span> <span data-ttu-id="9f850-175">Wartość słowa kluczowego wskazuje zainstalowanej wersji.</span><span class="sxs-lookup"><span data-stu-id="9f850-175">The value of the keyword indicates the installed version.</span></span> <span data-ttu-id="9f850-176">Aby sprawdzić to słowo kluczowe, użyj <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> i <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> metody <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> klasy do podklucza Software\Microsoft\NET Framework Setup\NDP\v4\Full w HKEY_LOCAL_MACHINE w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="9f850-176">To check this keyword, use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> methods of the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the Software\Microsoft\NET Framework Setup\NDP\v4\Full subkey under HKEY_LOCAL_MACHINE in the Windows registry.</span></span>

2. <span data-ttu-id="9f850-177">Sprawdź wartość `Release` — słowo kluczowe, aby określić zainstalowaną wersję.</span><span class="sxs-lookup"><span data-stu-id="9f850-177">Check the value of the `Release` keyword to determine the installed version.</span></span> <span data-ttu-id="9f850-178">Być zgodne z nowszymi, można sprawdzić wartość większa niż lub równa wartości wymienionych w tabeli.</span><span class="sxs-lookup"><span data-stu-id="9f850-178">To be forward-compatible, you can check for a value greater than or equal to the values listed in the table.</span></span> <span data-ttu-id="9f850-179">Poniżej przedstawiono wersje programu .NET Framework i skojarzone `Release` słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="9f850-179">Here are the .NET Framework versions and associated `Release` keywords.</span></span>

    [!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

    |<span data-ttu-id="9f850-180">Wersja</span><span class="sxs-lookup"><span data-stu-id="9f850-180">Version</span></span>|<span data-ttu-id="9f850-181">Wartość DWORD dotycząca wersji</span><span class="sxs-lookup"><span data-stu-id="9f850-181">Value of the Release DWORD</span></span>|
    |-------------|--------------------------------|
    |<span data-ttu-id="9f850-182">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="9f850-182">.NET Framework 4.5</span></span>|<span data-ttu-id="9f850-183">378389</span><span class="sxs-lookup"><span data-stu-id="9f850-183">378389</span></span>|
    |<span data-ttu-id="9f850-184">.NET framework 4.5.1 zainstalowane z Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="9f850-184">.NET Framework 4.5.1 installed with Windows 8.1</span></span>|<span data-ttu-id="9f850-185">378675</span><span class="sxs-lookup"><span data-stu-id="9f850-185">378675</span></span>|
    |<span data-ttu-id="9f850-186">.NET framework 4.5.1 w systemie Windows 8, Windows 7 z dodatkiem SP1 lub Windows Vista z dodatkiem SP2</span><span class="sxs-lookup"><span data-stu-id="9f850-186">.NET Framework 4.5.1 installed on Windows 8, Windows 7 SP1, or Windows Vista SP2</span></span>|<span data-ttu-id="9f850-187">378758</span><span class="sxs-lookup"><span data-stu-id="9f850-187">378758</span></span>|
    |<span data-ttu-id="9f850-188">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="9f850-188">.NET Framework 4.5.2</span></span>|<span data-ttu-id="9f850-189">379893</span><span class="sxs-lookup"><span data-stu-id="9f850-189">379893</span></span>|
    |<span data-ttu-id="9f850-190">.NET framework 4.6 zainstalowanego z systemem Windows 10</span><span class="sxs-lookup"><span data-stu-id="9f850-190">.NET Framework 4.6 installed with Windows 10</span></span>|<span data-ttu-id="9f850-191">393295</span><span class="sxs-lookup"><span data-stu-id="9f850-191">393295</span></span>|
    |<span data-ttu-id="9f850-192">.NET framework 4.6 zainstalowane we wszystkich wersjach systemu operacyjnego Windows</span><span class="sxs-lookup"><span data-stu-id="9f850-192">.NET Framework 4.6 installed on all other Windows OS versions</span></span>|<span data-ttu-id="9f850-193">393297</span><span class="sxs-lookup"><span data-stu-id="9f850-193">393297</span></span>|
    |<span data-ttu-id="9f850-194">.NET framework 4.6.1, systemie Windows 10</span><span class="sxs-lookup"><span data-stu-id="9f850-194">.NET Framework 4.6.1 installed on Windows 10</span></span>|<span data-ttu-id="9f850-195">394254</span><span class="sxs-lookup"><span data-stu-id="9f850-195">394254</span></span>|
    |<span data-ttu-id="9f850-196">.NET framework 4.6.1 zainstalowane we wszystkich wersjach systemu operacyjnego Windows</span><span class="sxs-lookup"><span data-stu-id="9f850-196">.NET Framework 4.6.1 installed on all other Windows OS versions</span></span>|<span data-ttu-id="9f850-197">394271</span><span class="sxs-lookup"><span data-stu-id="9f850-197">394271</span></span>|
    |<span data-ttu-id="9f850-198">.NET framework 4.6.2 z zainstalowanym systemem Windows 10 Anniversary aktualizacji</span><span class="sxs-lookup"><span data-stu-id="9f850-198">.NET Framework 4.6.2 installed on Windows 10 Anniversary Update</span></span>|<span data-ttu-id="9f850-199">394802</span><span class="sxs-lookup"><span data-stu-id="9f850-199">394802</span></span>|
    |<span data-ttu-id="9f850-200">.NET framework 4.6.2 zainstalowane we wszystkich wersjach systemu operacyjnego Windows</span><span class="sxs-lookup"><span data-stu-id="9f850-200">.NET Framework 4.6.2 installed on all other Windows OS versions</span></span>|<span data-ttu-id="9f850-201">394806</span><span class="sxs-lookup"><span data-stu-id="9f850-201">394806</span></span>|
    |<span data-ttu-id="9f850-202">4.7 framework .NET zainstalowany w systemie Windows 10 twórców Update</span><span class="sxs-lookup"><span data-stu-id="9f850-202">.NET Framework 4.7 installed on Windows 10 Creators Update</span></span>|<span data-ttu-id="9f850-203">460798</span><span class="sxs-lookup"><span data-stu-id="9f850-203">460798</span></span>|
    |<span data-ttu-id="9f850-204">4.7 framework .NET zainstalowany w innych wersjach systemu operacyjnego Windows</span><span class="sxs-lookup"><span data-stu-id="9f850-204">.NET Framework 4.7 installed on all other Windows OS versions</span></span>|<span data-ttu-id="9f850-205">460805</span><span class="sxs-lookup"><span data-stu-id="9f850-205">460805</span></span>|
    |<span data-ttu-id="9f850-206">.NET framework w systemie Windows 10 spadek twórców Update 4.7.1</span><span class="sxs-lookup"><span data-stu-id="9f850-206">.NET Framework 4.7.1 installed on Windows 10 Fall Creators Update</span></span>|<span data-ttu-id="9f850-207">461308</span><span class="sxs-lookup"><span data-stu-id="9f850-207">461308</span></span>|
    |<span data-ttu-id="9f850-208">.NET framework 4.7.1 zainstalowane we wszystkich wersjach systemu operacyjnego Windows</span><span class="sxs-lookup"><span data-stu-id="9f850-208">.NET Framework 4.7.1 installed on all other Windows OS versions</span></span>|<span data-ttu-id="9f850-209">461310</span><span class="sxs-lookup"><span data-stu-id="9f850-209">461310</span></span>|
    |<span data-ttu-id="9f850-210">.NET framework 4.7.2 zainstalowany w systemie Windows 10 kwietnia 2018 aktualizacji</span><span class="sxs-lookup"><span data-stu-id="9f850-210">.NET Framework 4.7.2 installed on Windows 10 April 2018 Update</span></span>|<span data-ttu-id="9f850-211">461808</span><span class="sxs-lookup"><span data-stu-id="9f850-211">461808</span></span>|
    |<span data-ttu-id="9f850-212">.NET framework 4.7.2 zainstalowane we wszystkich wersjach systemu operacyjnego Windows</span><span class="sxs-lookup"><span data-stu-id="9f850-212">.NET Framework 4.7.2 installed on all other Windows OS versions</span></span>|<span data-ttu-id="9f850-213">461814</span><span class="sxs-lookup"><span data-stu-id="9f850-213">461814</span></span>|
    
     <span data-ttu-id="9f850-214">Następujące testy przykład `Release` wartości rejestru w celu ustalenia, czy [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub nowsza wersja programu .NET Framework jest zainstalowana.</span><span class="sxs-lookup"><span data-stu-id="9f850-214">The following example checks the `Release` value in the registry to determine whether the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or a later version of the .NET Framework is installed.</span></span>

     [!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
     [!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

     <span data-ttu-id="9f850-215">W tym przykładzie zalecaną praktyką w kontroli wersji są następujące:</span><span class="sxs-lookup"><span data-stu-id="9f850-215">This example follows the recommended practice for version checking:</span></span>

    - <span data-ttu-id="9f850-216">Sprawdza, czy wartość `Release` wpis jest *większa niż lub równa* wartości kluczy znane wersji.</span><span class="sxs-lookup"><span data-stu-id="9f850-216">It checks whether the value of the `Release` entry is *greater than or equal to* the value of the known release keys.</span></span>

    - <span data-ttu-id="9f850-217">Sprawdza w celu najstarszą wersję z najnowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="9f850-217">It checks in order from most recent version to earliest version.</span></span>

<a name="ps_a"></a> 
## <a name="to-check-for-a-minimum-required-net-framework-version-by-querying-the-registry-in-powershell-net-framework-45-and-later"></a><span data-ttu-id="9f850-218">Aby sprawdzić minimalna wymagana wersja programu .NET Framework, badając rejestru w programie PowerShell (.NET Framework 4.5 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="9f850-218">To check for a minimum-required .NET Framework version by querying the registry in PowerShell (.NET Framework 4.5 and later)</span></span>

- <span data-ttu-id="9f850-219">Poniższy przykład sprawdza wartość `Release` — słowo kluczowe, aby określić, czy .NET Framework 4.6.2 lub nowszy jest zainstalowany, niezależnie od wersji systemu operacyjnego (zwracanie `True` Jeśli jest i `False` w przeciwnym razie).</span><span class="sxs-lookup"><span data-stu-id="9f850-219">The following example checks the value of the `Release` keyword to determine whether .NET Framework 4.6.2 or higher is installed, regardless of Windows OS version (returning `True` if it is and `False` otherwise).</span></span>

    ```PowerShell
    Get-ChildItem "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\" | Get-ItemPropertyValue -Name Release | ForEach-Object { $_ -ge 394802 } 
    ```

    <span data-ttu-id="9f850-220">Można zastąpić `394802` w poprzednim przykładzie z innej wartości z poniższej tabeli, aby wyszukać inny minimalna wymagana wersja programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9f850-220">You can replace `394802` in the previous example with another value from the following table to check for a different minimum-required .NET Framework version.</span></span>
  
    |<span data-ttu-id="9f850-221">Wersja</span><span class="sxs-lookup"><span data-stu-id="9f850-221">Version</span></span>|<span data-ttu-id="9f850-222">Minimalna wartość DWORD zlecenia</span><span class="sxs-lookup"><span data-stu-id="9f850-222">Minimum value of the Release DWORD</span></span>|
    |-------------|--------------------------------|
    |<span data-ttu-id="9f850-223">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="9f850-223">.NET Framework 4.5</span></span>|<span data-ttu-id="9f850-224">378389</span><span class="sxs-lookup"><span data-stu-id="9f850-224">378389</span></span>|
    |<span data-ttu-id="9f850-225">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="9f850-225">.NET Framework 4.5.1</span></span>|<span data-ttu-id="9f850-226">378675</span><span class="sxs-lookup"><span data-stu-id="9f850-226">378675</span></span>|
    |<span data-ttu-id="9f850-227">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="9f850-227">.NET Framework 4.5.2</span></span>|<span data-ttu-id="9f850-228">379893</span><span class="sxs-lookup"><span data-stu-id="9f850-228">379893</span></span>|
    |[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|<span data-ttu-id="9f850-229">393295</span><span class="sxs-lookup"><span data-stu-id="9f850-229">393295</span></span>|
    |[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|<span data-ttu-id="9f850-230">394254</span><span class="sxs-lookup"><span data-stu-id="9f850-230">394254</span></span>|
    |[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]|<span data-ttu-id="9f850-231">394802</span><span class="sxs-lookup"><span data-stu-id="9f850-231">394802</span></span>|
    |<span data-ttu-id="9f850-232">.NET framework 4.7</span><span class="sxs-lookup"><span data-stu-id="9f850-232">.NET Framework 4.7</span></span>|<span data-ttu-id="9f850-233">460798</span><span class="sxs-lookup"><span data-stu-id="9f850-233">460798</span></span>|
    |<span data-ttu-id="9f850-234">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="9f850-234">.NET Framework 4.7.1</span></span>|<span data-ttu-id="9f850-235">461308</span><span class="sxs-lookup"><span data-stu-id="9f850-235">461308</span></span>|
    |<span data-ttu-id="9f850-236">.NET framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="9f850-236">.NET Framework 4.7.2</span></span>|<span data-ttu-id="9f850-237">461808</span><span class="sxs-lookup"><span data-stu-id="9f850-237">461808</span></span>|

<a name="clr_a"></a> 
## <a name="to-find-the-current-runtime-version-by-using-the-clrver-tool"></a><span data-ttu-id="9f850-238">Aby znaleźć bieżącą wersję środowiska uruchomieniowego za pomocą narzędzia Clrver</span><span class="sxs-lookup"><span data-stu-id="9f850-238">To find the current runtime version by using the Clrver tool</span></span>

- <span data-ttu-id="9f850-239">Użyj narzędzia wersji środowiska CLR (Clrver.exe) w celu ustalenia, które wersje środowiska uruchomieniowego języka wspólnego są zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="9f850-239">Use the CLR Version Tool (Clrver.exe) to determine which versions of the common language runtime are installed on a computer.</span></span>

     <span data-ttu-id="9f850-240">Z programu Visual Studio wiersz polecenia, wprowadź `clrver`.</span><span class="sxs-lookup"><span data-stu-id="9f850-240">From a Visual Studio Command Prompt, enter `clrver`.</span></span> <span data-ttu-id="9f850-241">To polecenie tworzy dane wyjściowe podobne do poniższych:</span><span class="sxs-lookup"><span data-stu-id="9f850-241">This command produces output similar to the following:</span></span>

    ```
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

     <span data-ttu-id="9f850-242">Aby uzyskać więcej informacji na temat stosowania tego narzędzia, zobacz [Clrver.exe (narzędzie wersji środowiska CLR)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).</span><span class="sxs-lookup"><span data-stu-id="9f850-242">For more information about using this tool, see [Clrver.exe (CLR Version Tool)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).</span></span>

<a name="clr_b"></a> 
## <a name="to-find-the-current-runtime-version-by-querying-the-environment-class-in-code"></a><span data-ttu-id="9f850-243">Aby znaleźć bieżącą wersję środowiska uruchomieniowego, badając klasę Environment w kodzie</span><span class="sxs-lookup"><span data-stu-id="9f850-243">To find the current runtime version by querying the Environment class in code</span></span>

- <span data-ttu-id="9f850-244">Zapytanie <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwości do pobrania <xref:System.Version> obiekt, który identyfikuje wersję środowiska uruchomieniowego, który jest aktualnie wykonywany kod.</span><span class="sxs-lookup"><span data-stu-id="9f850-244">Query the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object that identifies the version of the runtime that is currently executing the code.</span></span> <span data-ttu-id="9f850-245">Można użyć <xref:System.Version.Major%2A?displayProperty=nameWithType> właściwości można pobrać identyfikatora wydaniem (na przykład "4" w wersji 4.0), <xref:System.Version.Minor%2A?displayProperty=nameWithType> właściwości, aby określić identyfikator wersji pomocniczej (na przykład "0" w wersji 4.0), lub <xref:System.Object.ToString%2A?displayProperty=nameWithType> metodę, aby pobrać całej wersji ciąg (na przykład "4.0.30319.18010", jak pokazano w poniższym kodzie).</span><span class="sxs-lookup"><span data-stu-id="9f850-245">You can use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property to get the major release identifier (for example, "4" for version 4.0), the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property to get the minor release identifier (for example, "0" for version 4.0), or the <xref:System.Object.ToString%2A?displayProperty=nameWithType> method to get the entire version string (for example, "4.0.30319.18010", as shown in the following code).</span></span> <span data-ttu-id="9f850-246">Ta właściwość zwraca jedną wartość odzwierciedlającą wersję środowiska uruchomieniowego, które aktualnie wykonuje kod. Właściwość nie zwraca wersji zestawu ani innych wersji środowiska uruchomieniowego, które mogą być zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="9f850-246">This property returns a single value that reflects the version of the runtime that is currently executing the code; it does not return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

     <span data-ttu-id="9f850-247">Dla wersji .NET Framework 4, 4.5.1, 4.5 i 4.5.2 <xref:System.Environment.Version%2A?displayProperty=nameWithType> zwraca <xref:System.Version> obiektu, którego reprezentacji ciągu ma postać `4.0.30319.xxxxx`.</span><span class="sxs-lookup"><span data-stu-id="9f850-247">For the .NET Framework Versions 4, 4.5, 4.5.1, and 4.5.2, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns a <xref:System.Version> object whose string representation has the form `4.0.30319.xxxxx`.</span></span> <span data-ttu-id="9f850-248">Dla programu .NET Framework 4.6 i nowszych, składa się z formularza `4.0.30319.42000`.</span><span class="sxs-lookup"><span data-stu-id="9f850-248">For the .NET Framework 4.6 and later, it has the form `4.0.30319.42000`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="9f850-249">Dla [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] i później, nie zaleca się przy użyciu <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwość, aby wykryć wersji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="9f850-249">For the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] and later, we do not recommend using the  <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the runtime.</span></span> <span data-ttu-id="9f850-250">Zamiast tego, firma Microsoft zaleca, aby zbadać rejestru, zgodnie z opisem w [można znaleźć wersji systemu .NET Framework, badając rejestru w kodzie (.NET Framework 4.5 lub nowszej)](#net_d) wcześniej w tym artykule.</span><span class="sxs-lookup"><span data-stu-id="9f850-250">Instead, we recommend that you query the registry, as described in the [To find .NET Framework versions by querying the registry in code (.NET Framework 4.5 and later)](#net_d) section earlier in this article.</span></span>

     <span data-ttu-id="9f850-251">Oto przykład kwerendy <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwości, aby uzyskać informacje o wersji środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="9f850-251">Here's an example of querying the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property for runtime version information:</span></span>

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

     <span data-ttu-id="9f850-252">W przykładzie są generowane dane wyjściowe podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="9f850-252">The example produces output that's similar to the following:</span></span>

    ```
    Version: 4.0.30319.18010
    ```

## <a name="see-also"></a><span data-ttu-id="9f850-253">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9f850-253">See also</span></span>

[<span data-ttu-id="9f850-254">Instrukcje: określanie, które aktualizacje programu .NET Framework są zainstalowane</span><span class="sxs-lookup"><span data-stu-id="9f850-254">How to: Determine Which .NET Framework Updates Are Installed</span></span>](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)  
[<span data-ttu-id="9f850-255">Zainstaluj program .NET Framework dla deweloperów</span><span class="sxs-lookup"><span data-stu-id="9f850-255">Install the .NET Framework for developers</span></span>](../../../docs/framework/install/guide-for-developers.md)  
[<span data-ttu-id="9f850-256">Wersje i zależności</span><span class="sxs-lookup"><span data-stu-id="9f850-256">Versions and Dependencies</span></span>](~/docs/framework/migration-guide/versions-and-dependencies.md)  

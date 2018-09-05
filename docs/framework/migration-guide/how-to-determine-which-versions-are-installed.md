---
title: 'Porady: Określanie, które wersje programu .NET Framework są zainstalowane.'
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
ms.openlocfilehash: 1874d5512f04f22b9c53bdc9e92d0c96e45d21c8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43562795"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="21a76-102">Porady: Określanie, które wersje programu .NET Framework są zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="21a76-102">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="21a76-103">Użytkownicy mogą zainstalować i uruchamiać wiele wersji .NET Framework na swoich komputerach.</span><span class="sxs-lookup"><span data-stu-id="21a76-103">Users can install and run multiple versions of the .NET Framework on their computers.</span></span> <span data-ttu-id="21a76-104">Podczas tworzenia lub wdrażania aplikacji, może być konieczne wiedzieć, które wersje programu .NET Framework są zainstalowane na komputerze użytkownika.</span><span class="sxs-lookup"><span data-stu-id="21a76-104">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user’s computer.</span></span> <span data-ttu-id="21a76-105">Należy zwrócić uwagę na to, że .NET Framework składa się z dwóch głównych składników, które są określane oddzielnie:</span><span class="sxs-lookup"><span data-stu-id="21a76-105">Note that the .NET Framework consists of two main components, which are versioned separately:</span></span>  
  
-   <span data-ttu-id="21a76-106">Zbiór zestawów, które są kolekcjami typów i zasobów zapewniających funkcje dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="21a76-106">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="21a76-107">.NET Framework i zestawy współużytkują ten sam numer wersji.</span><span class="sxs-lookup"><span data-stu-id="21a76-107">The .NET Framework and assemblies share the same version number.</span></span>  
  
-   <span data-ttu-id="21a76-108">Środowisko uruchomieniowe języka wspólnego (CLR) zarządza, która wykonuje kod w swojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="21a76-108">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="21a76-109">Środowisko CLR jest identyfikowane za pomocą własnego numeru wersji (zobacz [wersje i zależności](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span><span class="sxs-lookup"><span data-stu-id="21a76-109">The CLR is identified by its own version number (see [Versions and Dependencies](~/docs/framework/migration-guide/versions-and-dependencies.md)).</span></span>  
  
 <span data-ttu-id="21a76-110">Aby uzyskać dokładne listę wersji programu .NET Framework zainstalowana na komputerze, można wyświetlić rejestr lub wykonaj zapytanie dotyczące rejestru w kodzie:</span><span class="sxs-lookup"><span data-stu-id="21a76-110">To get an accurate list of the .NET Framework versions installed on a computer, you can view the registry or query the registry in code:</span></span>  
  
 [<span data-ttu-id="21a76-111">Wyświetlanie w rejestrze (wersje 1 – 4)</span><span class="sxs-lookup"><span data-stu-id="21a76-111">Viewing the registry (versions 1-4)</span></span>](#net_a)  
 [<span data-ttu-id="21a76-112">Wyświetlanie w rejestrze (w wersji 4.5 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="21a76-112">Viewing the registry (version 4.5 and later)</span></span>](#net_b)  
 [<span data-ttu-id="21a76-113">Wykonaj zapytanie dotyczące rejestru (wersje 1 – 4) za pomocą kodu</span><span class="sxs-lookup"><span data-stu-id="21a76-113">Using code to query the registry (versions 1-4)</span></span>](#net_c)  
 [<span data-ttu-id="21a76-114">Wykonaj zapytanie dotyczące rejestru (w wersji 4.5 lub nowszy) za pomocą kodu</span><span class="sxs-lookup"><span data-stu-id="21a76-114">Using code to query the registry (version 4.5 and later)</span></span>](#net_d)  
 [<span data-ttu-id="21a76-115">Przy użyciu programu PowerShell do wykonywania zapytań w rejestrze (w wersji 4.5 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="21a76-115">Using PowerShell to query the registry (version 4.5 and later)</span></span>](#ps_a)  
  
 <span data-ttu-id="21a76-116">Aby znaleźć wersję środowiska CLR, można użyć narzędzia lub kodu:</span><span class="sxs-lookup"><span data-stu-id="21a76-116">To find the CLR version, you can use a tool or code:</span></span>  
  
 [<span data-ttu-id="21a76-117">Za pomocą narzędzia Clrver</span><span class="sxs-lookup"><span data-stu-id="21a76-117">Using the Clrver tool</span></span>](#clr_a)  
 [<span data-ttu-id="21a76-118">Aby wysłać zapytanie klasy System.Environment przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="21a76-118">Using code to query the System.Environment class</span></span>](#clr_b)  
  
 <span data-ttu-id="21a76-119">Aby uzyskać informacje dotyczące wykrywania zainstalowanych aktualizacji dla każdej wersji programu .NET Framework, zobacz [jak: ustalić Which .NET Framework Updates Are Installed](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="21a76-119">For information about detecting the installed updates for each version of the .NET Framework, see [How to: Determine Which .NET Framework Updates Are Installed](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md).</span></span> <span data-ttu-id="21a76-120">Aby uzyskać informacje o instalowaniu programu .NET Framework, zobacz [Instalowanie programu .NET Framework dla deweloperów](../../../docs/framework/install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="21a76-120">For information about installing the .NET Framework, see [Install the .NET Framework for developers](../../../docs/framework/install/guide-for-developers.md).</span></span>  
  
<a name="net_a"></a>   
## <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-1-4"></a><span data-ttu-id="21a76-121">Aby znaleźć wersji programu .NET Framework, wyświetlając rejestru (.NET Framework 1 – 4)</span><span class="sxs-lookup"><span data-stu-id="21a76-121">To find .NET Framework versions by viewing the registry (.NET Framework 1-4)</span></span>  
  
1.  <span data-ttu-id="21a76-122">Na **Start** menu, wybierz **Uruchom**.</span><span class="sxs-lookup"><span data-stu-id="21a76-122">On the **Start** menu, choose **Run**.</span></span>  
  
2.  <span data-ttu-id="21a76-123">W **Otwórz** wprowadź **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="21a76-123">In the **Open** box, enter **regedit.exe**.</span></span>  
  
     <span data-ttu-id="21a76-124">Musisz mieć poświadczenia administracyjne, aby uruchomić program regedit.exe.</span><span class="sxs-lookup"><span data-stu-id="21a76-124">You must have administrative credentials to run regedit.exe.</span></span>  
  
3.  <span data-ttu-id="21a76-125">W Edytorze rejestru otwórz następujący podklucz:</span><span class="sxs-lookup"><span data-stu-id="21a76-125">In the Registry Editor, open the following subkey:</span></span>  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP`  
  
     <span data-ttu-id="21a76-126">Zainstalowane wersje są wymienione w podkluczu NDP.</span><span class="sxs-lookup"><span data-stu-id="21a76-126">The installed versions are listed under the NDP subkey.</span></span> <span data-ttu-id="21a76-127">Numer wersji jest przechowywany w **wersji** wpisu.</span><span class="sxs-lookup"><span data-stu-id="21a76-127">The version number is stored in the **Version** entry.</span></span> <span data-ttu-id="21a76-128">Aby uzyskać [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] **wersji** wpis jest klient lub pełny podklucz (pod NDP) lub w obu tych podkluczach.</span><span class="sxs-lookup"><span data-stu-id="21a76-128">For the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] the **Version** entry is under the Client or Full subkey (under NDP), or under both subkeys.</span></span>  
  

    > [!NOTE]
    > <span data-ttu-id="21a76-129">Folder „NET Framework Setup” w rejestrze nie rozpoczyna się kropką.</span><span class="sxs-lookup"><span data-stu-id="21a76-129">The "NET Framework Setup" folder in the registry does not begin with a period.</span></span>

<a name="net_b"></a> 
## <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-45-and-later"></a><span data-ttu-id="21a76-130">Aby znaleźć wersji programu .NET Framework, wyświetlając rejestru (.NET Framework 4.5 i nowsze)</span><span class="sxs-lookup"><span data-stu-id="21a76-130">To find .NET Framework versions by viewing the registry (.NET Framework 4.5 and later)</span></span>

1. <span data-ttu-id="21a76-131">Na **Start** menu, wybierz **Uruchom**.</span><span class="sxs-lookup"><span data-stu-id="21a76-131">On the **Start** menu, choose **Run**.</span></span>

2. <span data-ttu-id="21a76-132">W **Otwórz** wprowadź **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="21a76-132">In the **Open** box, enter **regedit.exe**.</span></span>

     <span data-ttu-id="21a76-133">Musisz mieć poświadczenia administracyjne, aby uruchomić program regedit.exe.</span><span class="sxs-lookup"><span data-stu-id="21a76-133">You must have administrative credentials to run regedit.exe.</span></span>

3. <span data-ttu-id="21a76-134">W Edytorze rejestru otwórz następujący podklucz:</span><span class="sxs-lookup"><span data-stu-id="21a76-134">In the Registry Editor, open the following subkey:</span></span>

     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`

     <span data-ttu-id="21a76-135">Należy pamiętać, że ścieżka do `Full` podklucz obejmuje podklucz `Net Framework` zamiast `.NET Framework`.</span><span class="sxs-lookup"><span data-stu-id="21a76-135">Note that the path to the `Full` subkey includes the subkey `Net Framework` rather than `.NET Framework`.</span></span>

    > [!NOTE]
    > <span data-ttu-id="21a76-136">Jeśli `Full` podklucz nie jest obecny, a następnie nie ma programu .NET Framework 4.5 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="21a76-136">If the `Full` subkey is not present, then you do not have the .NET Framework 4.5 or later installed.</span></span>

     <span data-ttu-id="21a76-137">Wyszukaj wartość DWORD o nazwie `Release`.</span><span class="sxs-lookup"><span data-stu-id="21a76-137">Check for a DWORD value named `Release`.</span></span> <span data-ttu-id="21a76-138">Istnienie `Release` DWORD oznacza, że [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub nowszej, została zainstalowana na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="21a76-138">The existence of the `Release` DWORD indicates that the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or newer has been installed on that computer.</span></span>

     <span data-ttu-id="21a76-139">![Wpis rejestru dla programu .NET Framework 4.5. ](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span><span class="sxs-lookup"><span data-stu-id="21a76-139">![The registry entry for the .NET Framework 4.5.](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")</span></span>

     <span data-ttu-id="21a76-140">Wartość `Release` typu DWORD wskazuje, która wersja programu .NET Framework jest zainstalowana.</span><span class="sxs-lookup"><span data-stu-id="21a76-140">The value of the `Release` DWORD indicates which version of the .NET Framework is installed.</span></span>

    [!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

    |<span data-ttu-id="21a76-141">Wartość DWORD dotycząca wersji</span><span class="sxs-lookup"><span data-stu-id="21a76-141">Value of the Release DWORD</span></span>|<span data-ttu-id="21a76-142">Wersja</span><span class="sxs-lookup"><span data-stu-id="21a76-142">Version</span></span>|
    |--------------------------------|-------------|
    |<span data-ttu-id="21a76-143">378389</span><span class="sxs-lookup"><span data-stu-id="21a76-143">378389</span></span>|<span data-ttu-id="21a76-144">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="21a76-144">.NET Framework 4.5</span></span>|
    |<span data-ttu-id="21a76-145">378675</span><span class="sxs-lookup"><span data-stu-id="21a76-145">378675</span></span>|<span data-ttu-id="21a76-146">.NET framework 4.5.1 zainstalowaną w systemie Windows 8.1 lub Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="21a76-146">.NET Framework 4.5.1 installed with Windows 8.1 or Windows Server 2012 R2</span></span>|
    |<span data-ttu-id="21a76-147">378758</span><span class="sxs-lookup"><span data-stu-id="21a76-147">378758</span></span>|<span data-ttu-id="21a76-148">.NET framework 4.5.1, w systemie Windows 8, Windows 7 z dodatkiem SP1 lub Windows Vista z dodatkiem SP2</span><span class="sxs-lookup"><span data-stu-id="21a76-148">.NET Framework 4.5.1 installed on Windows 8, Windows 7 SP1, or Windows Vista SP2</span></span>|
    |<span data-ttu-id="21a76-149">379893</span><span class="sxs-lookup"><span data-stu-id="21a76-149">379893</span></span>|<span data-ttu-id="21a76-150">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="21a76-150">.NET Framework 4.5.2</span></span>|
    |<span data-ttu-id="21a76-151">Tylko w systemach Windows 10: 393295</span><span class="sxs-lookup"><span data-stu-id="21a76-151">On Windows 10 systems only: 393295</span></span><br /><br /> <span data-ttu-id="21a76-152">W innych wersjach systemu operacyjnego: 393297</span><span class="sxs-lookup"><span data-stu-id="21a76-152">On all other OS versions: 393297</span></span>|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|
    |<span data-ttu-id="21a76-153">Tylko w systemach Windows 10 Listopadową aktualizacją: 394254</span><span class="sxs-lookup"><span data-stu-id="21a76-153">On Windows 10 November Update systems only: 394254</span></span><br /><br /> <span data-ttu-id="21a76-154">W innych wersjach systemu operacyjnego: 394271</span><span class="sxs-lookup"><span data-stu-id="21a76-154">On all other OS versions: 394271</span></span>|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|
    |<span data-ttu-id="21a76-155">W Rocznicowej aktualizacji systemu Windows 10 i Windows Server 2016:394802</span><span class="sxs-lookup"><span data-stu-id="21a76-155">On Windows 10 Anniversary Update and Windows Server 2016: 394802</span></span><br /><br /> <span data-ttu-id="21a76-156">W innych wersjach systemu operacyjnego: 394806</span><span class="sxs-lookup"><span data-stu-id="21a76-156">On all other OS versions: 394806</span></span>|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]| 
    |<span data-ttu-id="21a76-157">W systemie Windows 10 dla twórców tylko zaktualizować: 460798</span><span class="sxs-lookup"><span data-stu-id="21a76-157">On Windows 10 Creators Update only: 460798</span></span><br/><br/> <span data-ttu-id="21a76-158">W innych wersjach systemu operacyjnego: 460805</span><span class="sxs-lookup"><span data-stu-id="21a76-158">On all other OS versions: 460805</span></span> | <span data-ttu-id="21a76-159">.NET framework 4.7</span><span class="sxs-lookup"><span data-stu-id="21a76-159">.NET Framework 4.7</span></span> |
    |<span data-ttu-id="21a76-160">Na Windows 10 Fall Creators Update tylko: 461308</span><span class="sxs-lookup"><span data-stu-id="21a76-160">On Windows 10 Fall Creators Update only: 461308</span></span><br/><br/> <span data-ttu-id="21a76-161">W innych wersjach systemu operacyjnego: 461310</span><span class="sxs-lookup"><span data-stu-id="21a76-161">On all other OS versions: 461310</span></span> | <span data-ttu-id="21a76-162">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="21a76-162">.NET Framework 4.7.1</span></span> |
    |<span data-ttu-id="21a76-163">W usłudze Windows Update 10 kwietnia 2018 r. tylko: 461808</span><span class="sxs-lookup"><span data-stu-id="21a76-163">On Windows 10 April 2018 Update only: 461808</span></span><br/><br/> <span data-ttu-id="21a76-164">W innych wersjach systemu operacyjnego: 461814</span><span class="sxs-lookup"><span data-stu-id="21a76-164">On all other OS versions: 461814</span></span>| <span data-ttu-id="21a76-165">.NET framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="21a76-165">.NET Framework 4.7.2</span></span> |
    
<a name="net_c"></a> 
## <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-1-4"></a><span data-ttu-id="21a76-166">Można znaleźć wersji programu .NET Framework, wykonując zapytanie w rejestrze w kodzie (.NET Framework 1 – 4)</span><span class="sxs-lookup"><span data-stu-id="21a76-166">To find .NET Framework versions by querying the registry in code (.NET Framework 1-4)</span></span>

- <span data-ttu-id="21a76-167">Użyj <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> klasy, aby dostęp do podklucza Software\Microsoft\NET Framework Setup\NDP\ w kluczu HKEY_LOCAL_MACHINE w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="21a76-167">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the Software\Microsoft\NET Framework Setup\NDP\ subkey under HKEY_LOCAL_MACHINE in the Windows registry.</span></span>

     <span data-ttu-id="21a76-168">Poniższy kod przedstawia przykład tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="21a76-168">The following code shows an example of this query.</span></span>

    > [!NOTE]
    > <span data-ttu-id="21a76-169">Ten kod nie pokazuje, jak wykrywać [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="21a76-169">This code does not show how to detect the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or later.</span></span> <span data-ttu-id="21a76-170">Sprawdź `Release` DWORD, aby wykryć te wersje, zgodnie z opisem w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="21a76-170">Check the `Release` DWORD to detect those versions, as described in the previous section.</span></span> <span data-ttu-id="21a76-171">Dla kodu, który wykrywa [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub nowsze wersje, zobacz następną sekcję w tym artykule.</span><span class="sxs-lookup"><span data-stu-id="21a76-171">For code that does detect the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or later versions, see the next section in this article.</span></span>

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

     <span data-ttu-id="21a76-172">W przykładzie są generowane dane wyjściowe podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="21a76-172">The example produces output that's similar to the following:</span></span>

    ```
    v2.0.50727  2.0.50727.4016  SP2
    v3.0  3.0.30729.4037  SP2
    v3.5  3.5.30729.01  SP1
    v4
      Client  4.0.30319
      Full  4.0.30319
    ```

<a name="net_d"></a> 
## <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-45-and-later"></a><span data-ttu-id="21a76-173">Można znaleźć wersji programu .NET Framework, wykonując zapytanie w rejestrze w kodzie (.NET Framework 4.5 i nowsze)</span><span class="sxs-lookup"><span data-stu-id="21a76-173">To find .NET Framework versions by querying the registry in code (.NET Framework 4.5 and later)</span></span>

1. <span data-ttu-id="21a76-174">Istnienie `Release` typu DWORD wskazuje, że na komputerze zainstalowano .NET Framework 4.5 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="21a76-174">The existence of the `Release` DWORD indicates that the .NET Framework 4.5 or later has been installed on a computer.</span></span> <span data-ttu-id="21a76-175">Wartość słowa kluczowego wskazuje zainstalowanej wersji.</span><span class="sxs-lookup"><span data-stu-id="21a76-175">The value of the keyword indicates the installed version.</span></span> <span data-ttu-id="21a76-176">Aby sprawdzić to słowo kluczowe, użyj <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> i <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> metody <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> klasy, aby dostęp do podklucza Software\Microsoft\NET Framework setup\ndp\v4\full ma w kluczu HKEY_LOCAL_MACHINE w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="21a76-176">To check this keyword, use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> methods of the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the Software\Microsoft\NET Framework Setup\NDP\v4\Full subkey under HKEY_LOCAL_MACHINE in the Windows registry.</span></span>

2. <span data-ttu-id="21a76-177">Sprawdź wartość `Release` słowo kluczowe, aby ustalić zainstalowaną wersję.</span><span class="sxs-lookup"><span data-stu-id="21a76-177">Check the value of the `Release` keyword to determine the installed version.</span></span> <span data-ttu-id="21a76-178">Być zgodne, można sprawdzić wartość większa niż lub równa wartości wymienione w tabeli.</span><span class="sxs-lookup"><span data-stu-id="21a76-178">To be forward-compatible, you can check for a value greater than or equal to the values listed in the table.</span></span> <span data-ttu-id="21a76-179">Poniżej przedstawiono wersje programu .NET Framework i skojarzone `Release` słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="21a76-179">Here are the .NET Framework versions and associated `Release` keywords.</span></span>

    [!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

    |<span data-ttu-id="21a76-180">Wersja</span><span class="sxs-lookup"><span data-stu-id="21a76-180">Version</span></span>|<span data-ttu-id="21a76-181">Wartość DWORD dotycząca wersji</span><span class="sxs-lookup"><span data-stu-id="21a76-181">Value of the Release DWORD</span></span>|
    |-------------|--------------------------------|
    |<span data-ttu-id="21a76-182">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="21a76-182">.NET Framework 4.5</span></span>|<span data-ttu-id="21a76-183">378389</span><span class="sxs-lookup"><span data-stu-id="21a76-183">378389</span></span>|
    |<span data-ttu-id="21a76-184">.NET framework 4.5.1 zainstalowane z Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="21a76-184">.NET Framework 4.5.1 installed with Windows 8.1</span></span>|<span data-ttu-id="21a76-185">378675</span><span class="sxs-lookup"><span data-stu-id="21a76-185">378675</span></span>|
    |<span data-ttu-id="21a76-186">.NET framework 4.5.1, w systemie Windows 8, Windows 7 z dodatkiem SP1 lub Windows Vista z dodatkiem SP2</span><span class="sxs-lookup"><span data-stu-id="21a76-186">.NET Framework 4.5.1 installed on Windows 8, Windows 7 SP1, or Windows Vista SP2</span></span>|<span data-ttu-id="21a76-187">378758</span><span class="sxs-lookup"><span data-stu-id="21a76-187">378758</span></span>|
    |<span data-ttu-id="21a76-188">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="21a76-188">.NET Framework 4.5.2</span></span>|<span data-ttu-id="21a76-189">379893</span><span class="sxs-lookup"><span data-stu-id="21a76-189">379893</span></span>|
    |<span data-ttu-id="21a76-190">.NET framework 4.6 zainstalowane z systemem Windows 10</span><span class="sxs-lookup"><span data-stu-id="21a76-190">.NET Framework 4.6 installed with Windows 10</span></span>|<span data-ttu-id="21a76-191">393295</span><span class="sxs-lookup"><span data-stu-id="21a76-191">393295</span></span>|
    |<span data-ttu-id="21a76-192">.NET framework 4.6 zainstalowany w innych wersjach systemu operacyjnego Windows</span><span class="sxs-lookup"><span data-stu-id="21a76-192">.NET Framework 4.6 installed on all other Windows OS versions</span></span>|<span data-ttu-id="21a76-193">393297</span><span class="sxs-lookup"><span data-stu-id="21a76-193">393297</span></span>|
    |<span data-ttu-id="21a76-194">Program .NET framework 4.6.1 zainstalowane w systemie Windows 10</span><span class="sxs-lookup"><span data-stu-id="21a76-194">.NET Framework 4.6.1 installed on Windows 10</span></span>|<span data-ttu-id="21a76-195">394254</span><span class="sxs-lookup"><span data-stu-id="21a76-195">394254</span></span>|
    |<span data-ttu-id="21a76-196">Program .NET framework 4.6.1 zainstalowany w innych wersjach systemu operacyjnego Windows</span><span class="sxs-lookup"><span data-stu-id="21a76-196">.NET Framework 4.6.1 installed on all other Windows OS versions</span></span>|<span data-ttu-id="21a76-197">394271</span><span class="sxs-lookup"><span data-stu-id="21a76-197">394271</span></span>|
    |<span data-ttu-id="21a76-198">.NET framework 4.6.2 w systemie Rocznicowa aktualizacja systemu Windows 10 i Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="21a76-198">.NET Framework 4.6.2 installed on Windows 10 Anniversary Update and Windows Server 2016</span></span>|<span data-ttu-id="21a76-199">394802</span><span class="sxs-lookup"><span data-stu-id="21a76-199">394802</span></span>|
    |<span data-ttu-id="21a76-200">.NET framework 4.6.2 zainstalowany w innych wersjach systemu operacyjnego Windows</span><span class="sxs-lookup"><span data-stu-id="21a76-200">.NET Framework 4.6.2 installed on all other Windows OS versions</span></span>|<span data-ttu-id="21a76-201">394806</span><span class="sxs-lookup"><span data-stu-id="21a76-201">394806</span></span>|
    |<span data-ttu-id="21a76-202">.NET framework 4.7 zainstalowanym systemem Windows 10 Creators Update</span><span class="sxs-lookup"><span data-stu-id="21a76-202">.NET Framework 4.7 installed on Windows 10 Creators Update</span></span>|<span data-ttu-id="21a76-203">460798</span><span class="sxs-lookup"><span data-stu-id="21a76-203">460798</span></span>|
    |<span data-ttu-id="21a76-204">.NET framework 4.7 zainstalowany w innych wersjach systemu operacyjnego Windows</span><span class="sxs-lookup"><span data-stu-id="21a76-204">.NET Framework 4.7 installed on all other Windows OS versions</span></span>|<span data-ttu-id="21a76-205">460805</span><span class="sxs-lookup"><span data-stu-id="21a76-205">460805</span></span>|
    |<span data-ttu-id="21a76-206">.NET framework 4.7.1 w systemie Windows 10 Fall Creators Update</span><span class="sxs-lookup"><span data-stu-id="21a76-206">.NET Framework 4.7.1 installed on Windows 10 Fall Creators Update</span></span>|<span data-ttu-id="21a76-207">461308</span><span class="sxs-lookup"><span data-stu-id="21a76-207">461308</span></span>|
    |<span data-ttu-id="21a76-208">.NET framework 4.7.1 zainstalowany w innych wersjach systemu operacyjnego Windows</span><span class="sxs-lookup"><span data-stu-id="21a76-208">.NET Framework 4.7.1 installed on all other Windows OS versions</span></span>|<span data-ttu-id="21a76-209">461310</span><span class="sxs-lookup"><span data-stu-id="21a76-209">461310</span></span>|
    |<span data-ttu-id="21a76-210">.NET framework 4.7.2 zainstalowany w systemie Windows 10 kwietnia 2018 r. Zaktualizuj</span><span class="sxs-lookup"><span data-stu-id="21a76-210">.NET Framework 4.7.2 installed on Windows 10 April 2018 Update</span></span>|<span data-ttu-id="21a76-211">461808</span><span class="sxs-lookup"><span data-stu-id="21a76-211">461808</span></span>|
    |<span data-ttu-id="21a76-212">.NET framework 4.7.2 zainstalowany w innych wersjach systemu operacyjnego Windows</span><span class="sxs-lookup"><span data-stu-id="21a76-212">.NET Framework 4.7.2 installed on all other Windows OS versions</span></span>|<span data-ttu-id="21a76-213">461814</span><span class="sxs-lookup"><span data-stu-id="21a76-213">461814</span></span>|
    
     <span data-ttu-id="21a76-214">Następujące testy przykład `Release` wartości w rejestrze, aby określić, czy [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub nowsza wersja programu .NET Framework jest zainstalowana.</span><span class="sxs-lookup"><span data-stu-id="21a76-214">The following example checks the `Release` value in the registry to determine whether the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] or a later version of the .NET Framework is installed.</span></span>

     [!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
     [!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

     <span data-ttu-id="21a76-215">W tym przykładzie następuje zalecana praktyka dla kontroli wersji:</span><span class="sxs-lookup"><span data-stu-id="21a76-215">This example follows the recommended practice for version checking:</span></span>

    - <span data-ttu-id="21a76-216">Sprawdza, czy wartość `Release` wpis jest *większa lub równa* wartości kluczy znanych wydania.</span><span class="sxs-lookup"><span data-stu-id="21a76-216">It checks whether the value of the `Release` entry is *greater than or equal to* the value of the known release keys.</span></span>

    - <span data-ttu-id="21a76-217">Sprawdza w kolejności od najbardziej aktualną wersję do najwcześniejszej wersji.</span><span class="sxs-lookup"><span data-stu-id="21a76-217">It checks in order from most recent version to earliest version.</span></span>

<a name="ps_a"></a> 
## <a name="to-check-for-a-minimum-required-net-framework-version-by-querying-the-registry-in-powershell-net-framework-45-and-later"></a><span data-ttu-id="21a76-218">Aby sprawdzić, czy są minimalna wymagana wersja programu .NET Framework, wykonując zapytanie w rejestrze w programie PowerShell (.NET Framework 4.5 i nowsze)</span><span class="sxs-lookup"><span data-stu-id="21a76-218">To check for a minimum-required .NET Framework version by querying the registry in PowerShell (.NET Framework 4.5 and later)</span></span>

- <span data-ttu-id="21a76-219">Poniższy przykład sprawdza wartość `Release` — słowo kluczowe, aby określić, czy platformy .NET Framework 4.6.2 lub nowszy jest zainstalowany, niezależnie od wersji systemu operacyjnego Windows (zwracanie `True` , gdy jest i `False` inaczej).</span><span class="sxs-lookup"><span data-stu-id="21a76-219">The following example checks the value of the `Release` keyword to determine whether .NET Framework 4.6.2 or higher is installed, regardless of Windows OS version (returning `True` if it is and `False` otherwise).</span></span>

    ```PowerShell
    Get-ChildItem "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\" | Get-ItemPropertyValue -Name Release | ForEach-Object { $_ -ge 394802 } 
    ```

    <span data-ttu-id="21a76-220">Możesz zastąpić `394802` w poprzednim przykładzie, za pomocą innej wartości z poniższej tabeli, aby sprawdzić, czy są dostępne różne minimalna wymagana wersja programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="21a76-220">You can replace `394802` in the previous example with another value from the following table to check for a different minimum-required .NET Framework version.</span></span>
  
    |<span data-ttu-id="21a76-221">Wersja</span><span class="sxs-lookup"><span data-stu-id="21a76-221">Version</span></span>|<span data-ttu-id="21a76-222">Minimalna wartość DWORD wydania</span><span class="sxs-lookup"><span data-stu-id="21a76-222">Minimum value of the Release DWORD</span></span>|
    |-------------|--------------------------------|
    |<span data-ttu-id="21a76-223">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="21a76-223">.NET Framework 4.5</span></span>|<span data-ttu-id="21a76-224">378389</span><span class="sxs-lookup"><span data-stu-id="21a76-224">378389</span></span>|
    |<span data-ttu-id="21a76-225">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="21a76-225">.NET Framework 4.5.1</span></span>|<span data-ttu-id="21a76-226">378675</span><span class="sxs-lookup"><span data-stu-id="21a76-226">378675</span></span>|
    |<span data-ttu-id="21a76-227">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="21a76-227">.NET Framework 4.5.2</span></span>|<span data-ttu-id="21a76-228">379893</span><span class="sxs-lookup"><span data-stu-id="21a76-228">379893</span></span>|
    |[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|<span data-ttu-id="21a76-229">393295</span><span class="sxs-lookup"><span data-stu-id="21a76-229">393295</span></span>|
    |[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|<span data-ttu-id="21a76-230">394254</span><span class="sxs-lookup"><span data-stu-id="21a76-230">394254</span></span>|
    |[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]|<span data-ttu-id="21a76-231">394802</span><span class="sxs-lookup"><span data-stu-id="21a76-231">394802</span></span>|
    |<span data-ttu-id="21a76-232">.NET framework 4.7</span><span class="sxs-lookup"><span data-stu-id="21a76-232">.NET Framework 4.7</span></span>|<span data-ttu-id="21a76-233">460798</span><span class="sxs-lookup"><span data-stu-id="21a76-233">460798</span></span>|
    |<span data-ttu-id="21a76-234">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="21a76-234">.NET Framework 4.7.1</span></span>|<span data-ttu-id="21a76-235">461308</span><span class="sxs-lookup"><span data-stu-id="21a76-235">461308</span></span>|
    |<span data-ttu-id="21a76-236">.NET framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="21a76-236">.NET Framework 4.7.2</span></span>|<span data-ttu-id="21a76-237">461808</span><span class="sxs-lookup"><span data-stu-id="21a76-237">461808</span></span>|

<a name="clr_a"></a> 
## <a name="to-find-the-current-runtime-version-by-using-the-clrver-tool"></a><span data-ttu-id="21a76-238">Aby znaleźć bieżącą wersję środowiska uruchomieniowego za pomocą narzędzia Clrver</span><span class="sxs-lookup"><span data-stu-id="21a76-238">To find the current runtime version by using the Clrver tool</span></span>

- <span data-ttu-id="21a76-239">Użyj narzędzia wersji środowiska CLR (Clrver.exe) w celu ustalenia, które wersje środowiska uruchomieniowego języka wspólnego są zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="21a76-239">Use the CLR Version Tool (Clrver.exe) to determine which versions of the common language runtime are installed on a computer.</span></span>

     <span data-ttu-id="21a76-240">Z wiersza polecenia Visual Studio, wprowadź `clrver`.</span><span class="sxs-lookup"><span data-stu-id="21a76-240">From a Visual Studio Command Prompt, enter `clrver`.</span></span> <span data-ttu-id="21a76-241">To polecenie tworzy dane wyjściowe podobne do poniższych:</span><span class="sxs-lookup"><span data-stu-id="21a76-241">This command produces output similar to the following:</span></span>

    ```
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

     <span data-ttu-id="21a76-242">Aby uzyskać więcej informacji dotyczących używania tego narzędzia, zobacz [Clrver.exe (narzędzie wersji środowiska CLR)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).</span><span class="sxs-lookup"><span data-stu-id="21a76-242">For more information about using this tool, see [Clrver.exe (CLR Version Tool)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).</span></span>

<a name="clr_b"></a> 
## <a name="to-find-the-current-runtime-version-by-querying-the-environment-class-in-code"></a><span data-ttu-id="21a76-243">Aby znaleźć bieżącą wersję środowiska uruchomieniowego, badając klasę Environment w kodzie</span><span class="sxs-lookup"><span data-stu-id="21a76-243">To find the current runtime version by querying the Environment class in code</span></span>

- <span data-ttu-id="21a76-244">Zapytanie <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwość służąca do pobierania <xref:System.Version> obiektu, który identyfikuje wersję środowiska uruchomieniowego, które aktualnie wykonuje kod.</span><span class="sxs-lookup"><span data-stu-id="21a76-244">Query the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object that identifies the version of the runtime that is currently executing the code.</span></span> <span data-ttu-id="21a76-245">Możesz użyć <xref:System.Version.Major%2A?displayProperty=nameWithType> właściwości, aby uzyskać identyfikator wersji głównej (na przykład "4" w wersji 4.0), <xref:System.Version.Minor%2A?displayProperty=nameWithType> właściwości, aby uzyskać identyfikator wersji pomocniczej (na przykład, "0" do wersji 4.0 lub nowszej), lub <xref:System.Object.ToString%2A?displayProperty=nameWithType> metodę, aby uzyskać całą wersję ciąg (na przykład "4.0.30319.18010", jak pokazano w poniższym kodzie).</span><span class="sxs-lookup"><span data-stu-id="21a76-245">You can use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property to get the major release identifier (for example, "4" for version 4.0), the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property to get the minor release identifier (for example, "0" for version 4.0), or the <xref:System.Object.ToString%2A?displayProperty=nameWithType> method to get the entire version string (for example, "4.0.30319.18010", as shown in the following code).</span></span> <span data-ttu-id="21a76-246">Ta właściwość zwraca jedną wartość odzwierciedlającą wersję środowiska uruchomieniowego, które aktualnie wykonuje kod. Właściwość nie zwraca wersji zestawu ani innych wersji środowiska uruchomieniowego, które mogą być zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="21a76-246">This property returns a single value that reflects the version of the runtime that is currently executing the code; it does not return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

     <span data-ttu-id="21a76-247">Dla platformy .NET Framework 4, 4.5, 4.5.1 i 4.5.2 <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwość zwraca <xref:System.Version> obiektu, którego reprezentacja ciągu ma postać `4.0.30319.xxxxx`.</span><span class="sxs-lookup"><span data-stu-id="21a76-247">For the .NET Framework Versions 4, 4.5, 4.5.1, and 4.5.2, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns a <xref:System.Version> object whose string representation has the form `4.0.30319.xxxxx`.</span></span> <span data-ttu-id="21a76-248">Dla programu .NET Framework 4.6 lub nowszy, ma on postać `4.0.30319.42000`.</span><span class="sxs-lookup"><span data-stu-id="21a76-248">For the .NET Framework 4.6 and later, it has the form `4.0.30319.42000`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="21a76-249">Aby uzyskać [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] i nowszym, nie zaleca się przy użyciu <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwości do wykrywania wersji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="21a76-249">For the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] and later, we do not recommend using the  <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the runtime.</span></span> <span data-ttu-id="21a76-250">Zamiast tego zaleca się zapytania rejestru zgodnie z opisem w [można znaleźć wersji programu .NET Framework, wykonując zapytanie w rejestrze w kodzie (.NET Framework 4.5 i nowsze)](#net_d) sekcji we wcześniejszej części tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="21a76-250">Instead, we recommend that you query the registry, as described in the [To find .NET Framework versions by querying the registry in code (.NET Framework 4.5 and later)](#net_d) section earlier in this article.</span></span>

     <span data-ttu-id="21a76-251">Poniżej przedstawiono przykład zapytania dotyczącego <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwości, aby uzyskać informacje o wersji środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="21a76-251">Here's an example of querying the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property for runtime version information:</span></span>

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

     <span data-ttu-id="21a76-252">W przykładzie są generowane dane wyjściowe podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="21a76-252">The example produces output that's similar to the following:</span></span>

    ```
    Version: 4.0.30319.18010
    ```

## <a name="see-also"></a><span data-ttu-id="21a76-253">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="21a76-253">See also</span></span>

[<span data-ttu-id="21a76-254">Instrukcje: określanie, które aktualizacje programu .NET Framework są zainstalowane</span><span class="sxs-lookup"><span data-stu-id="21a76-254">How to: Determine Which .NET Framework Updates Are Installed</span></span>](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)  
[<span data-ttu-id="21a76-255">Instalowanie programu .NET Framework dla deweloperów</span><span class="sxs-lookup"><span data-stu-id="21a76-255">Install the .NET Framework for developers</span></span>](../../../docs/framework/install/guide-for-developers.md)  
[<span data-ttu-id="21a76-256">Wersje i zależności</span><span class="sxs-lookup"><span data-stu-id="21a76-256">Versions and Dependencies</span></span>](~/docs/framework/migration-guide/versions-and-dependencies.md)  

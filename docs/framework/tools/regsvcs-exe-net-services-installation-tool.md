---
title: Regsvcs.exe (Narzędzie instalacji usług .NET)
ms.date: 03/30/2017
helpviewer_keywords:
- Regsvcs.exe
- .NET Services Installation tool
- loading assemblies
- assemblies [.NET Framework], registering
- type libraries
- registering assemblies
ms.assetid: 5220fe58-5aaf-4e8e-8bc3-b78c63025804
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b80df56c9f45f7dd195e1f7bbd03063fa30abb3a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466763"
---
# <a name="regsvcsexe-net-services-installation-tool"></a><span data-ttu-id="c2df7-102">Regsvcs.exe (Narzędzie instalacji usług .NET)</span><span class="sxs-lookup"><span data-stu-id="c2df7-102">Regsvcs.exe (.NET Services Installation Tool)</span></span>
<span data-ttu-id="c2df7-103">Narzędzie instalacji usług platformy .NET wykonuje następujące akcje:</span><span class="sxs-lookup"><span data-stu-id="c2df7-103">The .NET Services Installation tool performs the following actions:</span></span>  
  
-   <span data-ttu-id="c2df7-104">Ładuje i rejestruje zestawy.</span><span class="sxs-lookup"><span data-stu-id="c2df7-104">Loads and registers an assembly.</span></span>  
  
-   <span data-ttu-id="c2df7-105">Generuje, rejestruje i instaluje biblioteki typów w określonej aplikacji COM+.</span><span class="sxs-lookup"><span data-stu-id="c2df7-105">Generates, registers, and installs a type library into a specified COM+ application.</span></span>  
  
-   <span data-ttu-id="c2df7-106">Konfiguruje usługi, które zostały programowo dodane do klasy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c2df7-106">Configures services that you have added programmatically to your class.</span></span>  
  
 <span data-ttu-id="c2df7-107">Aby uruchomić narzędzie, należy użyć wiersz polecenia programisty dla programu Visual Studio (lub wiersza polecenia programu Visual Studio Windows 7).</span><span class="sxs-lookup"><span data-stu-id="c2df7-107">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="c2df7-108">Aby uzyskać więcej informacji, zobacz [wiersz polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="c2df7-108">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="c2df7-109">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="c2df7-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2df7-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2df7-110">Syntax</span></span>  
  
```  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll   
```  
  
## <a name="parameters"></a><span data-ttu-id="c2df7-111">Parametry</span><span class="sxs-lookup"><span data-stu-id="c2df7-111">Parameters</span></span>  
  
|<span data-ttu-id="c2df7-112">Argument</span><span class="sxs-lookup"><span data-stu-id="c2df7-112">Argument</span></span>|<span data-ttu-id="c2df7-113">Opis</span><span class="sxs-lookup"><span data-stu-id="c2df7-113">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="c2df7-114">*assemblyFile.dll*</span><span class="sxs-lookup"><span data-stu-id="c2df7-114">*assemblyFile.dll*</span></span>|<span data-ttu-id="c2df7-115">Plik zestawu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="c2df7-115">The source assembly file.</span></span> <span data-ttu-id="c2df7-116">Zestaw musi być podpisany za pomocą silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="c2df7-116">The assembly must be signed with a strong name.</span></span> <span data-ttu-id="c2df7-117">Aby uzyskać więcej informacji, zobacz [podpisywanie zestawu za pomocą silnej nazwy](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="c2df7-117">For more information, see [Signing an Assembly with a Strong Name](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>|  
  
|<span data-ttu-id="c2df7-118">Opcja</span><span class="sxs-lookup"><span data-stu-id="c2df7-118">Option</span></span>|<span data-ttu-id="c2df7-119">Opis</span><span class="sxs-lookup"><span data-stu-id="c2df7-119">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="c2df7-120">**/appdir:** *ścieżki*</span><span class="sxs-lookup"><span data-stu-id="c2df7-120">**/appdir:** *path*</span></span>|<span data-ttu-id="c2df7-121">Określa katalog główny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c2df7-121">Specifies the root directory of the application.</span></span>|  
|<span data-ttu-id="c2df7-122">**operacji:** *applicationName*</span><span class="sxs-lookup"><span data-stu-id="c2df7-122">**/appname:** *applicationName*</span></span>|<span data-ttu-id="c2df7-123">Określa nazwę aplikacji COM+, która ma zostać znaleziona lub utworzona.</span><span class="sxs-lookup"><span data-stu-id="c2df7-123">Specifies the name of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="c2df7-124">**/c**</span><span class="sxs-lookup"><span data-stu-id="c2df7-124">**/c**</span></span>|<span data-ttu-id="c2df7-125">Tworzy aplikację docelową.</span><span class="sxs-lookup"><span data-stu-id="c2df7-125">Creates the target application.</span></span>|  
|<span data-ttu-id="c2df7-126">**componly**</span><span class="sxs-lookup"><span data-stu-id="c2df7-126">**/componly**</span></span>|<span data-ttu-id="c2df7-127">Konfiguruje tylko składniki; ignoruje metody i interfejsy.</span><span class="sxs-lookup"><span data-stu-id="c2df7-127">Configures components only; ignores methods and interfaces.</span></span>|  
|<span data-ttu-id="c2df7-128">**/exapp**</span><span class="sxs-lookup"><span data-stu-id="c2df7-128">**/exapp**</span></span>|<span data-ttu-id="c2df7-129">Określa, że narzędzie ma oczekiwać istniejącej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c2df7-129">Specifies to the tool to expect an existing application.</span></span>|  
|<span data-ttu-id="c2df7-130">**/extlb**</span><span class="sxs-lookup"><span data-stu-id="c2df7-130">**/extlb**</span></span>|<span data-ttu-id="c2df7-131">Używa istniejącej biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="c2df7-131">Uses an existing type library.</span></span>|  
|<span data-ttu-id="c2df7-132">**/fc**</span><span class="sxs-lookup"><span data-stu-id="c2df7-132">**/fc**</span></span>|<span data-ttu-id="c2df7-133">Znajduje lub tworzy aplikację docelową.</span><span class="sxs-lookup"><span data-stu-id="c2df7-133">Finds or creates the target application.</span></span>|  
|<span data-ttu-id="c2df7-134">**/help**</span><span class="sxs-lookup"><span data-stu-id="c2df7-134">**/help**</span></span>|<span data-ttu-id="c2df7-135">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="c2df7-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="c2df7-136">**/noreconfig**</span><span class="sxs-lookup"><span data-stu-id="c2df7-136">**/noreconfig**</span></span>|<span data-ttu-id="c2df7-137">Nie konfiguruje ponownie istniejącej aplikacji docelowej.</span><span class="sxs-lookup"><span data-stu-id="c2df7-137">Does not reconfigure an existing target application.</span></span>|  
|<span data-ttu-id="c2df7-138">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="c2df7-138">**/nologo**</span></span>|<span data-ttu-id="c2df7-139">Pomija wyświetlanie transparentu startowego firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c2df7-139">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="c2df7-140">**/parname:** *nazwy*</span><span class="sxs-lookup"><span data-stu-id="c2df7-140">**/parname:** *name*</span></span>|<span data-ttu-id="c2df7-141">Określa nazwę lub identyfikator aplikacji COM+, która ma zostać znaleziona lub utworzona.</span><span class="sxs-lookup"><span data-stu-id="c2df7-141">Specifies the name or id of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="c2df7-142">**/reconfig**</span><span class="sxs-lookup"><span data-stu-id="c2df7-142">**/reconfig**</span></span>|<span data-ttu-id="c2df7-143">Konfiguruje ponownie istniejącą aplikację docelową.</span><span class="sxs-lookup"><span data-stu-id="c2df7-143">Reconfigures an existing target application.</span></span> <span data-ttu-id="c2df7-144">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="c2df7-144">This is the default.</span></span>|  
|<span data-ttu-id="c2df7-145">**/ TLB:** *plik_biblioteki_typów*</span><span class="sxs-lookup"><span data-stu-id="c2df7-145">**/tlb:** *typelibraryfile*</span></span>|<span data-ttu-id="c2df7-146">Określa plik biblioteki typów do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="c2df7-146">Specifies the type library file to install.</span></span>|  
|<span data-ttu-id="c2df7-147">**/u**</span><span class="sxs-lookup"><span data-stu-id="c2df7-147">**/u**</span></span>|<span data-ttu-id="c2df7-148">Odinstalowuje aplikację docelową.</span><span class="sxs-lookup"><span data-stu-id="c2df7-148">Uninstalls the target application.</span></span>|  
|<span data-ttu-id="c2df7-149">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="c2df7-149">**/quiet**</span></span>|<span data-ttu-id="c2df7-150">Określa tryb cichy; pomija wyświetlanie logo i komunikatów o sukcesie.</span><span class="sxs-lookup"><span data-stu-id="c2df7-150">Specifies quiet mode; suppresses the logo and success message display.</span></span>|  
|<span data-ttu-id="c2df7-151">**/?**</span><span class="sxs-lookup"><span data-stu-id="c2df7-151">**/?**</span></span>|<span data-ttu-id="c2df7-152">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="c2df7-152">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2df7-153">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c2df7-153">Remarks</span></span>  
 <span data-ttu-id="c2df7-154">Regsvcs.exe wymaga pliku zestawu źródłowego określonego przez *Plikzestawu.dll*.</span><span class="sxs-lookup"><span data-stu-id="c2df7-154">Regsvcs.exe requires a source assembly file specified by *assemblyFile.dll*.</span></span> <span data-ttu-id="c2df7-155">Ten zestaw musi być podpisany za pomocą silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="c2df7-155">This assembly must be signed with a strong name.</span></span> <span data-ttu-id="c2df7-156">Aby uzyskać więcej informacji na temat podpisywania silnymi nazwami, zobacz [podpisywanie zestawu za pomocą silnej nazwy](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="c2df7-156">For more information on strong name signing, see [Signing an Assembly with a Strong Name](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span> <span data-ttu-id="c2df7-157">Nazwy aplikacji docelowej i pliku biblioteki typów są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="c2df7-157">The names of the target application and the type library file are optional.</span></span> <span data-ttu-id="c2df7-158">*ApplicationName* argument może zostać wygenerowany na podstawie pliku zestawu źródłowego i zostanie utworzona przez Regsvcs.exe, jeśli jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="c2df7-158">The *applicationName* argument can be generated from the source assembly file and will be created by Regsvcs.exe, if it does not already exist.</span></span> <span data-ttu-id="c2df7-159">*Plik_biblioteki_typów* argument może określać nazwę biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="c2df7-159">The *typelibraryfile* argument can specify a type library name.</span></span> <span data-ttu-id="c2df7-160">Jeśli nie zostanie określona nazwa biblioteki typów, program Regsvcs.exe użyje nazwy zestawu jako wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="c2df7-160">If you do not specify a type library name, Regsvcs.exe uses the assembly name as the default.</span></span>  
  
 <span data-ttu-id="c2df7-161">Gdy Regsvcs.exe rejestruje metody składnika, jest podlegają [zapotrzebowanie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) i [link zapotrzebowanie](../../../docs/framework/misc/link-demands.md) w tych metodach.</span><span class="sxs-lookup"><span data-stu-id="c2df7-161">When Regsvcs.exe registers a component's methods, it is subject to the [demands](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) and [link demands](../../../docs/framework/misc/link-demands.md) on those methods.</span></span> <span data-ttu-id="c2df7-162">To narzędzie działa we w pełni zaufanym środowisku, więc większość żądań uprawnienia kończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="c2df7-162">Because the tool executes in a fully-trusted environment, most demands for a permission succeed.</span></span> <span data-ttu-id="c2df7-163">Jednak Regsvcs.exe nie może rejestrować składników z metodami chronionymi przez żądania demand lub linkdemand dla <xref:System.Security.Permissions.StrongNameIdentityPermission> lub <xref:System.Security.Permissions.PublisherIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="c2df7-163">However, Regsvcs.exe cannot register components with methods protected by a demand or link demand for the <xref:System.Security.Permissions.StrongNameIdentityPermission> or the <xref:System.Security.Permissions.PublisherIdentityPermission>.</span></span>  
  
 <span data-ttu-id="c2df7-164">Aby używać programu Regsvcs.exe, trzeba mieć uprawnienia administracyjne na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="c2df7-164">You must have administrative privileges on the local computer to use Regsvcs.exe.</span></span>  
  
 <span data-ttu-id="c2df7-165">Jeśli podczas wykonywania dowolnej z tych akcji w programie Regsvcs.exe wystąpi błąd, zostaną wyświetlone odpowiednie komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="c2df7-165">If Regsvcs.exe fails while performing any of these actions, it displays corresponding error messages.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c2df7-166">Przykłady</span><span class="sxs-lookup"><span data-stu-id="c2df7-166">Examples</span></span>  
 <span data-ttu-id="c2df7-167">Następujące polecenie dodaje wszystkie klasy publiczne zawarte w `myTest.dll` do `myTargetApp` (istniejąca aplikacja COM +) i tworzy `myTest.tlb` biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="c2df7-167">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `myTest.tlb` type library.</span></span>  
  
```  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 <span data-ttu-id="c2df7-168">Następujące polecenie dodaje wszystkie klasy publiczne zawarte w `myTest.dll` do `myTargetApp` (istniejąca aplikacja COM +) i tworzy `newTest.tlb` biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="c2df7-168">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `newTest.tlb` type library.</span></span>  
  
```  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="c2df7-169">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c2df7-169">See also</span></span>
- [<span data-ttu-id="c2df7-170">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="c2df7-170">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="c2df7-171">Instrukcje: Podpisywanie zestawu silną nazwą</span><span class="sxs-lookup"><span data-stu-id="c2df7-171">How to: Sign an Assembly with a Strong Name</span></span>](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)
- [<span data-ttu-id="c2df7-172">Wiersze polecenia</span><span class="sxs-lookup"><span data-stu-id="c2df7-172">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

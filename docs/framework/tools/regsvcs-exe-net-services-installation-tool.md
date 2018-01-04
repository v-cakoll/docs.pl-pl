---
title: "Regsvcs.exe (Narzędzie instalacji usług .NET)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Regsvcs.exe
- .NET Services Installation tool
- loading assemblies
- assemblies [.NET Framework], registering
- type libraries
- registering assemblies
ms.assetid: 5220fe58-5aaf-4e8e-8bc3-b78c63025804
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd7f50d591232feda0259ecefdb5b9e39514ccb2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="regsvcsexe-net-services-installation-tool"></a><span data-ttu-id="4a511-102">Regsvcs.exe (Narzędzie instalacji usług .NET)</span><span class="sxs-lookup"><span data-stu-id="4a511-102">Regsvcs.exe (.NET Services Installation Tool)</span></span>
<span data-ttu-id="4a511-103">Narzędzie instalacji usług platformy .NET wykonuje następujące akcje:</span><span class="sxs-lookup"><span data-stu-id="4a511-103">The .NET Services Installation tool performs the following actions:</span></span>  
  
-   <span data-ttu-id="4a511-104">Ładuje i rejestruje zestawy.</span><span class="sxs-lookup"><span data-stu-id="4a511-104">Loads and registers an assembly.</span></span>  
  
-   <span data-ttu-id="4a511-105">Generuje, rejestruje i instaluje biblioteki typów w określonej aplikacji COM+.</span><span class="sxs-lookup"><span data-stu-id="4a511-105">Generates, registers, and installs a type library into a specified COM+ application.</span></span>  
  
-   <span data-ttu-id="4a511-106">Konfiguruje usługi, które zostały programowo dodane do klasy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4a511-106">Configures services that you have added programmatically to your class.</span></span>  
  
 <span data-ttu-id="4a511-107">Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7).</span><span class="sxs-lookup"><span data-stu-id="4a511-107">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="4a511-108">Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="4a511-108">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="4a511-109">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="4a511-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a511-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="4a511-110">Syntax</span></span>  
  
```  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll   
```  
  
#### <a name="parameters"></a><span data-ttu-id="4a511-111">Parametry</span><span class="sxs-lookup"><span data-stu-id="4a511-111">Parameters</span></span>  
  
|<span data-ttu-id="4a511-112">Argument</span><span class="sxs-lookup"><span data-stu-id="4a511-112">Argument</span></span>|<span data-ttu-id="4a511-113">Opis</span><span class="sxs-lookup"><span data-stu-id="4a511-113">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="4a511-114">*assemblyFile.dll*</span><span class="sxs-lookup"><span data-stu-id="4a511-114">*assemblyFile.dll*</span></span>|<span data-ttu-id="4a511-115">Plik zestawu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="4a511-115">The source assembly file.</span></span> <span data-ttu-id="4a511-116">Zestaw musi być podpisany za pomocą silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="4a511-116">The assembly must be signed with a strong name.</span></span> <span data-ttu-id="4a511-117">Aby uzyskać więcej informacji, zobacz [podpisywanie zestawu o silnej nazwie](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="4a511-117">For more information, see [Signing an Assembly with a Strong Name](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>|  
  
|<span data-ttu-id="4a511-118">Opcja</span><span class="sxs-lookup"><span data-stu-id="4a511-118">Option</span></span>|<span data-ttu-id="4a511-119">Opis</span><span class="sxs-lookup"><span data-stu-id="4a511-119">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4a511-120">**/appdir:** *ścieżki*</span><span class="sxs-lookup"><span data-stu-id="4a511-120">**/appdir:** *path*</span></span>|<span data-ttu-id="4a511-121">Określa katalog główny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4a511-121">Specifies the root directory of the application.</span></span>|  
|<span data-ttu-id="4a511-122">**elementów/appname:** *applicationName*</span><span class="sxs-lookup"><span data-stu-id="4a511-122">**/appname:** *applicationName*</span></span>|<span data-ttu-id="4a511-123">Określa nazwę aplikacji COM+, która ma zostać znaleziona lub utworzona.</span><span class="sxs-lookup"><span data-stu-id="4a511-123">Specifies the name of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="4a511-124">**/c**</span><span class="sxs-lookup"><span data-stu-id="4a511-124">**/c**</span></span>|<span data-ttu-id="4a511-125">Tworzy aplikację docelową.</span><span class="sxs-lookup"><span data-stu-id="4a511-125">Creates the target application.</span></span>|  
|<span data-ttu-id="4a511-126">**componly**</span><span class="sxs-lookup"><span data-stu-id="4a511-126">**/componly**</span></span>|<span data-ttu-id="4a511-127">Konfiguruje tylko składniki; ignoruje metody i interfejsy.</span><span class="sxs-lookup"><span data-stu-id="4a511-127">Configures components only; ignores methods and interfaces.</span></span>|  
|<span data-ttu-id="4a511-128">**/exapp**</span><span class="sxs-lookup"><span data-stu-id="4a511-128">**/exapp**</span></span>|<span data-ttu-id="4a511-129">Określa, że narzędzie ma oczekiwać istniejącej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4a511-129">Specifies to the tool to expect an existing application.</span></span>|  
|<span data-ttu-id="4a511-130">**/extlb**</span><span class="sxs-lookup"><span data-stu-id="4a511-130">**/extlb**</span></span>|<span data-ttu-id="4a511-131">Używa istniejącej biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="4a511-131">Uses an existing type library.</span></span>|  
|<span data-ttu-id="4a511-132">**/FC**</span><span class="sxs-lookup"><span data-stu-id="4a511-132">**/fc**</span></span>|<span data-ttu-id="4a511-133">Znajduje lub tworzy aplikację docelową.</span><span class="sxs-lookup"><span data-stu-id="4a511-133">Finds or creates the target application.</span></span>|  
|<span data-ttu-id="4a511-134">**/ Help**</span><span class="sxs-lookup"><span data-stu-id="4a511-134">**/help**</span></span>|<span data-ttu-id="4a511-135">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="4a511-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="4a511-136">**/noreconfig**</span><span class="sxs-lookup"><span data-stu-id="4a511-136">**/noreconfig**</span></span>|<span data-ttu-id="4a511-137">Nie konfiguruje ponownie istniejącej aplikacji docelowej.</span><span class="sxs-lookup"><span data-stu-id="4a511-137">Does not reconfigure an existing target application.</span></span>|  
|<span data-ttu-id="4a511-138">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="4a511-138">**/nologo**</span></span>|<span data-ttu-id="4a511-139">Pomija wyświetlanie transparentu startowego firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4a511-139">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="4a511-140">**/parname:** *nazwy*</span><span class="sxs-lookup"><span data-stu-id="4a511-140">**/parname:** *name*</span></span>|<span data-ttu-id="4a511-141">Określa nazwę lub identyfikator aplikacji COM+, która ma zostać znaleziona lub utworzona.</span><span class="sxs-lookup"><span data-stu-id="4a511-141">Specifies the name or id of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="4a511-142">**/reconfig**</span><span class="sxs-lookup"><span data-stu-id="4a511-142">**/reconfig**</span></span>|<span data-ttu-id="4a511-143">Konfiguruje ponownie istniejącą aplikację docelową.</span><span class="sxs-lookup"><span data-stu-id="4a511-143">Reconfigures an existing target application.</span></span> <span data-ttu-id="4a511-144">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="4a511-144">This is the default.</span></span>|  
|<span data-ttu-id="4a511-145">**/ TLB:** *typelibraryfile*</span><span class="sxs-lookup"><span data-stu-id="4a511-145">**/tlb:** *typelibraryfile*</span></span>|<span data-ttu-id="4a511-146">Określa plik biblioteki typów do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="4a511-146">Specifies the type library file to install.</span></span>|  
|<span data-ttu-id="4a511-147">**/u**</span><span class="sxs-lookup"><span data-stu-id="4a511-147">**/u**</span></span>|<span data-ttu-id="4a511-148">Odinstalowuje aplikację docelową.</span><span class="sxs-lookup"><span data-stu-id="4a511-148">Uninstalls the target application.</span></span>|  
|<span data-ttu-id="4a511-149">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="4a511-149">**/quiet**</span></span>|<span data-ttu-id="4a511-150">Określa tryb cichy; pomija wyświetlanie logo i komunikatów o sukcesie.</span><span class="sxs-lookup"><span data-stu-id="4a511-150">Specifies quiet mode; suppresses the logo and success message display.</span></span>|  
|<span data-ttu-id="4a511-151">**/?**</span><span class="sxs-lookup"><span data-stu-id="4a511-151">**/?**</span></span>|<span data-ttu-id="4a511-152">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="4a511-152">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a511-153">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4a511-153">Remarks</span></span>  
 <span data-ttu-id="4a511-154">Regsvcs.exe wymaga pliku zestawu źródłowego określonego przez *assemblyFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="4a511-154">Regsvcs.exe requires a source assembly file specified by *assemblyFile.dll*.</span></span> <span data-ttu-id="4a511-155">Ten zestaw musi być podpisany za pomocą silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="4a511-155">This assembly must be signed with a strong name.</span></span> <span data-ttu-id="4a511-156">Aby uzyskać więcej informacji dotyczących podpisywanie silną nazwą, zobacz [podpisywanie zestawu o silnej nazwie](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="4a511-156">For more information on strong name signing, see [Signing an Assembly with a Strong Name](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span> <span data-ttu-id="4a511-157">Nazwy aplikacji docelowej i pliku biblioteki typów są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="4a511-157">The names of the target application and the type library file are optional.</span></span> <span data-ttu-id="4a511-158">*ApplicationName* argument mogą być generowane ze źródłowego pliku zestawu i zostanie utworzony przez Regsvcs.exe, jeśli jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="4a511-158">The *applicationName* argument can be generated from the source assembly file and will be created by Regsvcs.exe, if it does not already exist.</span></span> <span data-ttu-id="4a511-159">*Typelibraryfile* argument można określić nazwy biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="4a511-159">The *typelibraryfile* argument can specify a type library name.</span></span> <span data-ttu-id="4a511-160">Jeśli nie zostanie określona nazwa biblioteki typów, program Regsvcs.exe użyje nazwy zestawu jako wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="4a511-160">If you do not specify a type library name, Regsvcs.exe uses the assembly name as the default.</span></span>  
  
 <span data-ttu-id="4a511-161">Regsvcs.exe rejestrujący metod składnika, jest warunkiem [wymagań](http://msdn.microsoft.com/en-us/e5283e28-2366-4519-b27d-ef5c1ddc1f48) i [link zapotrzebowanie](../../../docs/framework/misc/link-demands.md) na jednej z tych metod.</span><span class="sxs-lookup"><span data-stu-id="4a511-161">When Regsvcs.exe registers a component's methods, it is subject to the [demands](http://msdn.microsoft.com/en-us/e5283e28-2366-4519-b27d-ef5c1ddc1f48) and [link demands](../../../docs/framework/misc/link-demands.md) on those methods.</span></span> <span data-ttu-id="4a511-162">To narzędzie działa we w pełni zaufanym środowisku, więc większość żądań uprawnienia kończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="4a511-162">Because the tool executes in a fully-trusted environment, most demands for a permission succeed.</span></span> <span data-ttu-id="4a511-163">Jednak Regsvcs.exe nie można zarejestrować składników za pomocą metod chroniony przez żądanie lub linkdemand dla <xref:System.Security.Permissions.StrongNameIdentityPermission> lub <xref:System.Security.Permissions.PublisherIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="4a511-163">However, Regsvcs.exe cannot register components with methods protected by a demand or link demand for the <xref:System.Security.Permissions.StrongNameIdentityPermission> or the <xref:System.Security.Permissions.PublisherIdentityPermission>.</span></span>  
  
 <span data-ttu-id="4a511-164">Aby używać programu Regsvcs.exe, trzeba mieć uprawnienia administracyjne na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="4a511-164">You must have administrative privileges on the local computer to use Regsvcs.exe.</span></span>  
  
 <span data-ttu-id="4a511-165">Jeśli podczas wykonywania dowolnej z tych akcji w programie Regsvcs.exe wystąpi błąd, zostaną wyświetlone odpowiednie komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="4a511-165">If Regsvcs.exe fails while performing any of these actions, it displays corresponding error messages.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="4a511-166">Przykłady</span><span class="sxs-lookup"><span data-stu-id="4a511-166">Examples</span></span>  
 <span data-ttu-id="4a511-167">Polecenie dodaje wszystkie klasy publicznej zawarte w `myTest.dll` do `myTargetApp` (istniejącej aplikacji COM +) i tworzy `myTest.tlb` biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="4a511-167">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `myTest.tlb` type library.</span></span>  
  
```  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 <span data-ttu-id="4a511-168">Polecenie dodaje wszystkie klasy publicznej zawarte w `myTest.dll` do `myTargetApp` (istniejącej aplikacji COM +) i tworzy `newTest.tlb` biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="4a511-168">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `newTest.tlb` type library.</span></span>  
  
```  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="4a511-169">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4a511-169">See Also</span></span>  
 [<span data-ttu-id="4a511-170">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="4a511-170">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="4a511-171">Instrukcje: podpisywanie zestawu silną nazwą</span><span class="sxs-lookup"><span data-stu-id="4a511-171">How to: Sign an Assembly with a Strong Name</span></span>](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [<span data-ttu-id="4a511-172">Wiersze polecenia</span><span class="sxs-lookup"><span data-stu-id="4a511-172">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

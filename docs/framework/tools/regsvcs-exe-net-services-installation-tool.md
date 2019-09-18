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
ms.openlocfilehash: 032f43aa16dbca0f4ab0477d586e7568230b7381
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044264"
---
# <a name="regsvcsexe-net-services-installation-tool"></a><span data-ttu-id="d6de4-102">Regsvcs.exe (Narzędzie instalacji usług .NET)</span><span class="sxs-lookup"><span data-stu-id="d6de4-102">Regsvcs.exe (.NET Services Installation Tool)</span></span>
<span data-ttu-id="d6de4-103">Narzędzie instalacji usług platformy .NET wykonuje następujące akcje:</span><span class="sxs-lookup"><span data-stu-id="d6de4-103">The .NET Services Installation tool performs the following actions:</span></span>  
  
- <span data-ttu-id="d6de4-104">Ładuje i rejestruje zestawy.</span><span class="sxs-lookup"><span data-stu-id="d6de4-104">Loads and registers an assembly.</span></span>  
  
- <span data-ttu-id="d6de4-105">Generuje, rejestruje i instaluje biblioteki typów w określonej aplikacji COM+.</span><span class="sxs-lookup"><span data-stu-id="d6de4-105">Generates, registers, and installs a type library into a specified COM+ application.</span></span>  
  
- <span data-ttu-id="d6de4-106">Konfiguruje usługi, które zostały programowo dodane do klasy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d6de4-106">Configures services that you have added programmatically to your class.</span></span>  
  
 <span data-ttu-id="d6de4-107">Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7).</span><span class="sxs-lookup"><span data-stu-id="d6de4-107">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="d6de4-108">Aby uzyskać więcej informacji, zobacz [wiersza polecenia](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="d6de4-108">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="d6de4-109">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="d6de4-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6de4-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="d6de4-110">Syntax</span></span>  
  
```console  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll   
```  
  
## <a name="parameters"></a><span data-ttu-id="d6de4-111">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6de4-111">Parameters</span></span>  
  
|<span data-ttu-id="d6de4-112">Argument</span><span class="sxs-lookup"><span data-stu-id="d6de4-112">Argument</span></span>|<span data-ttu-id="d6de4-113">Opis</span><span class="sxs-lookup"><span data-stu-id="d6de4-113">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="d6de4-114">*assemblyFile.dll*</span><span class="sxs-lookup"><span data-stu-id="d6de4-114">*assemblyFile.dll*</span></span>|<span data-ttu-id="d6de4-115">Plik zestawu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="d6de4-115">The source assembly file.</span></span> <span data-ttu-id="d6de4-116">Zestaw musi być podpisany za pomocą silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="d6de4-116">The assembly must be signed with a strong name.</span></span> <span data-ttu-id="d6de4-117">Aby uzyskać więcej informacji, zobacz [podpisywanie zestawu za pomocą silnej nazwy](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="d6de4-117">For more information, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span>|  
  
|<span data-ttu-id="d6de4-118">Opcja</span><span class="sxs-lookup"><span data-stu-id="d6de4-118">Option</span></span>|<span data-ttu-id="d6de4-119">Opis</span><span class="sxs-lookup"><span data-stu-id="d6de4-119">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="d6de4-120">**/Appdir:** *ścieżka*</span><span class="sxs-lookup"><span data-stu-id="d6de4-120">**/appdir:** *path*</span></span>|<span data-ttu-id="d6de4-121">Określa katalog główny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d6de4-121">Specifies the root directory of the application.</span></span>|  
|<span data-ttu-id="d6de4-122">**/APPNAME:** *ApplicationName*</span><span class="sxs-lookup"><span data-stu-id="d6de4-122">**/appname:** *applicationName*</span></span>|<span data-ttu-id="d6de4-123">Określa nazwę aplikacji COM+, która ma zostać znaleziona lub utworzona.</span><span class="sxs-lookup"><span data-stu-id="d6de4-123">Specifies the name of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="d6de4-124">**/c**</span><span class="sxs-lookup"><span data-stu-id="d6de4-124">**/c**</span></span>|<span data-ttu-id="d6de4-125">Tworzy aplikację docelową.</span><span class="sxs-lookup"><span data-stu-id="d6de4-125">Creates the target application.</span></span>|  
|<span data-ttu-id="d6de4-126">**/componly**</span><span class="sxs-lookup"><span data-stu-id="d6de4-126">**/componly**</span></span>|<span data-ttu-id="d6de4-127">Konfiguruje tylko składniki; ignoruje metody i interfejsy.</span><span class="sxs-lookup"><span data-stu-id="d6de4-127">Configures components only; ignores methods and interfaces.</span></span>|  
|<span data-ttu-id="d6de4-128">**/exapp**</span><span class="sxs-lookup"><span data-stu-id="d6de4-128">**/exapp**</span></span>|<span data-ttu-id="d6de4-129">Określa, że narzędzie ma oczekiwać istniejącej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d6de4-129">Specifies to the tool to expect an existing application.</span></span>|  
|<span data-ttu-id="d6de4-130">**/extlb**</span><span class="sxs-lookup"><span data-stu-id="d6de4-130">**/extlb**</span></span>|<span data-ttu-id="d6de4-131">Używa istniejącej biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="d6de4-131">Uses an existing type library.</span></span>|  
|<span data-ttu-id="d6de4-132">**/fc**</span><span class="sxs-lookup"><span data-stu-id="d6de4-132">**/fc**</span></span>|<span data-ttu-id="d6de4-133">Znajduje lub tworzy aplikację docelową.</span><span class="sxs-lookup"><span data-stu-id="d6de4-133">Finds or creates the target application.</span></span>|  
|<span data-ttu-id="d6de4-134">**/help**</span><span class="sxs-lookup"><span data-stu-id="d6de4-134">**/help**</span></span>|<span data-ttu-id="d6de4-135">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="d6de4-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="d6de4-136">**/noreconfig**</span><span class="sxs-lookup"><span data-stu-id="d6de4-136">**/noreconfig**</span></span>|<span data-ttu-id="d6de4-137">Nie konfiguruje ponownie istniejącej aplikacji docelowej.</span><span class="sxs-lookup"><span data-stu-id="d6de4-137">Does not reconfigure an existing target application.</span></span>|  
|<span data-ttu-id="d6de4-138">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="d6de4-138">**/nologo**</span></span>|<span data-ttu-id="d6de4-139">Pomija wyświetlanie transparentu startowego firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d6de4-139">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="d6de4-140">**/parName:** *Nazwa*</span><span class="sxs-lookup"><span data-stu-id="d6de4-140">**/parname:** *name*</span></span>|<span data-ttu-id="d6de4-141">Określa nazwę lub identyfikator aplikacji COM+, która ma zostać znaleziona lub utworzona.</span><span class="sxs-lookup"><span data-stu-id="d6de4-141">Specifies the name or id of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="d6de4-142">**/reconfig**</span><span class="sxs-lookup"><span data-stu-id="d6de4-142">**/reconfig**</span></span>|<span data-ttu-id="d6de4-143">Konfiguruje ponownie istniejącą aplikację docelową.</span><span class="sxs-lookup"><span data-stu-id="d6de4-143">Reconfigures an existing target application.</span></span> <span data-ttu-id="d6de4-144">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="d6de4-144">This is the default.</span></span>|  
|<span data-ttu-id="d6de4-145">**/tlb:** *TypeLibraryFile*</span><span class="sxs-lookup"><span data-stu-id="d6de4-145">**/tlb:** *typelibraryfile*</span></span>|<span data-ttu-id="d6de4-146">Określa plik biblioteki typów do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="d6de4-146">Specifies the type library file to install.</span></span>|  
|<span data-ttu-id="d6de4-147">**/u**</span><span class="sxs-lookup"><span data-stu-id="d6de4-147">**/u**</span></span>|<span data-ttu-id="d6de4-148">Odinstalowuje aplikację docelową.</span><span class="sxs-lookup"><span data-stu-id="d6de4-148">Uninstalls the target application.</span></span>|  
|<span data-ttu-id="d6de4-149">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="d6de4-149">**/quiet**</span></span>|<span data-ttu-id="d6de4-150">Określa tryb cichy; pomija wyświetlanie logo i komunikatów o sukcesie.</span><span class="sxs-lookup"><span data-stu-id="d6de4-150">Specifies quiet mode; suppresses the logo and success message display.</span></span>|  
|<span data-ttu-id="d6de4-151">**/?**</span><span class="sxs-lookup"><span data-stu-id="d6de4-151">**/?**</span></span>|<span data-ttu-id="d6de4-152">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="d6de4-152">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6de4-153">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d6de4-153">Remarks</span></span>  
 <span data-ttu-id="d6de4-154">Regsvcs. exe wymaga pliku zestawu źródłowego określonego przez *assemblyFile. dll*.</span><span class="sxs-lookup"><span data-stu-id="d6de4-154">Regsvcs.exe requires a source assembly file specified by *assemblyFile.dll*.</span></span> <span data-ttu-id="d6de4-155">Ten zestaw musi być podpisany za pomocą silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="d6de4-155">This assembly must be signed with a strong name.</span></span> <span data-ttu-id="d6de4-156">Aby uzyskać więcej informacji na temat podpisywania silnej nazwy, zobacz [podpisywanie zestawu za pomocą silnej nazwy](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="d6de4-156">For more information on strong name signing, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span> <span data-ttu-id="d6de4-157">Nazwy aplikacji docelowej i pliku biblioteki typów są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="d6de4-157">The names of the target application and the type library file are optional.</span></span> <span data-ttu-id="d6de4-158">Argument *ApplicationName* można wygenerować z pliku zestawu źródłowego i zostanie utworzony przez Regsvcs. exe, jeśli jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="d6de4-158">The *applicationName* argument can be generated from the source assembly file and will be created by Regsvcs.exe, if it does not already exist.</span></span> <span data-ttu-id="d6de4-159">Argument *TypeLibraryFile* może określać nazwę biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="d6de4-159">The *typelibraryfile* argument can specify a type library name.</span></span> <span data-ttu-id="d6de4-160">Jeśli nie zostanie określona nazwa biblioteki typów, program Regsvcs.exe użyje nazwy zestawu jako wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="d6de4-160">If you do not specify a type library name, Regsvcs.exe uses the assembly name as the default.</span></span>  
  
 <span data-ttu-id="d6de4-161">Gdy Regsvcs. exe rejestruje metody składnika, podlega [zapotrzebowaniu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) i [łącznym potrzebom](../misc/link-demands.md) dotyczącym tych metod.</span><span class="sxs-lookup"><span data-stu-id="d6de4-161">When Regsvcs.exe registers a component's methods, it is subject to the [demands](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) and [link demands](../misc/link-demands.md) on those methods.</span></span> <span data-ttu-id="d6de4-162">To narzędzie działa we w pełni zaufanym środowisku, więc większość żądań uprawnienia kończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d6de4-162">Because the tool executes in a fully-trusted environment, most demands for a permission succeed.</span></span> <span data-ttu-id="d6de4-163">Jednak Regsvcs. exe nie może zarejestrować składników przy użyciu metod chronionych przez zapotrzebowanie lub żądanie linku dla <xref:System.Security.Permissions.StrongNameIdentityPermission> <xref:System.Security.Permissions.PublisherIdentityPermission>lub.</span><span class="sxs-lookup"><span data-stu-id="d6de4-163">However, Regsvcs.exe cannot register components with methods protected by a demand or link demand for the <xref:System.Security.Permissions.StrongNameIdentityPermission> or the <xref:System.Security.Permissions.PublisherIdentityPermission>.</span></span>  
  
 <span data-ttu-id="d6de4-164">Aby używać programu Regsvcs.exe, trzeba mieć uprawnienia administracyjne na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="d6de4-164">You must have administrative privileges on the local computer to use Regsvcs.exe.</span></span>  
  
 <span data-ttu-id="d6de4-165">Jeśli podczas wykonywania dowolnej z tych akcji w programie Regsvcs.exe wystąpi błąd, zostaną wyświetlone odpowiednie komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="d6de4-165">If Regsvcs.exe fails while performing any of these actions, it displays corresponding error messages.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="d6de4-166">Przykłady</span><span class="sxs-lookup"><span data-stu-id="d6de4-166">Examples</span></span>  
 <span data-ttu-id="d6de4-167">Następujące polecenie dodaje wszystkie klasy publiczne zawarte w `myTest.dll` do `myTargetApp` (istniejąca `myTest.tlb` aplikacja com+) i tworzy bibliotekę typów.</span><span class="sxs-lookup"><span data-stu-id="d6de4-167">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `myTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 <span data-ttu-id="d6de4-168">Następujące polecenie dodaje wszystkie klasy publiczne zawarte w `myTest.dll` do `myTargetApp` (istniejąca `newTest.tlb` aplikacja com+) i tworzy bibliotekę typów.</span><span class="sxs-lookup"><span data-stu-id="d6de4-168">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `newTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="d6de4-169">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d6de4-169">See also</span></span>

- [<span data-ttu-id="d6de4-170">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="d6de4-170">Tools</span></span>](index.md)
- [<span data-ttu-id="d6de4-171">Instrukcje: Podpisz zestaw silną nazwą</span><span class="sxs-lookup"><span data-stu-id="d6de4-171">How to: Sign an Assembly with a Strong Name</span></span>](../../standard/assembly/sign-strong-name.md)
- [<span data-ttu-id="d6de4-172">Wiersze polecenia</span><span class="sxs-lookup"><span data-stu-id="d6de4-172">Command Prompts</span></span>](developer-command-prompt-for-vs.md)

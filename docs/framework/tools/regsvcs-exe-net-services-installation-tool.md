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
ms.openlocfilehash: aecd2f6894558b45898c7f22dd333617d9e2e327
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180359"
---
# <a name="regsvcsexe-net-services-installation-tool"></a><span data-ttu-id="39a29-102">Regsvcs.exe (Narzędzie instalacji usług .NET)</span><span class="sxs-lookup"><span data-stu-id="39a29-102">Regsvcs.exe (.NET Services Installation Tool)</span></span>
<span data-ttu-id="39a29-103">Narzędzie instalacji usług platformy .NET wykonuje następujące akcje:</span><span class="sxs-lookup"><span data-stu-id="39a29-103">The .NET Services Installation tool performs the following actions:</span></span>  
  
- <span data-ttu-id="39a29-104">Ładuje i rejestruje zestawy.</span><span class="sxs-lookup"><span data-stu-id="39a29-104">Loads and registers an assembly.</span></span>  
  
- <span data-ttu-id="39a29-105">Generuje, rejestruje i instaluje biblioteki typów w określonej aplikacji COM+.</span><span class="sxs-lookup"><span data-stu-id="39a29-105">Generates, registers, and installs a type library into a specified COM+ application.</span></span>  
  
- <span data-ttu-id="39a29-106">Konfiguruje usługi, które zostały programowo dodane do klasy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="39a29-106">Configures services that you have added programmatically to your class.</span></span>  
  
 <span data-ttu-id="39a29-107">Aby uruchomić narzędzie, użyj wiersza polecenia dewelopera dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7).</span><span class="sxs-lookup"><span data-stu-id="39a29-107">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="39a29-108">Aby uzyskać więcej informacji, zobacz [Wiersze poleceń](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="39a29-108">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="39a29-109">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="39a29-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39a29-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="39a29-110">Syntax</span></span>  
  
```console  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll
```  
  
## <a name="parameters"></a><span data-ttu-id="39a29-111">Parametry</span><span class="sxs-lookup"><span data-stu-id="39a29-111">Parameters</span></span>  
  
|<span data-ttu-id="39a29-112">Argument</span><span class="sxs-lookup"><span data-stu-id="39a29-112">Argument</span></span>|<span data-ttu-id="39a29-113">Opis</span><span class="sxs-lookup"><span data-stu-id="39a29-113">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="39a29-114">*assemblyFile.dll*</span><span class="sxs-lookup"><span data-stu-id="39a29-114">*assemblyFile.dll*</span></span>|<span data-ttu-id="39a29-115">Plik zestawu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="39a29-115">The source assembly file.</span></span> <span data-ttu-id="39a29-116">Zestaw musi być podpisany za pomocą silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="39a29-116">The assembly must be signed with a strong name.</span></span> <span data-ttu-id="39a29-117">Aby uzyskać więcej informacji, zobacz [Podpisywanie zestawu z silną nazwą](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="39a29-117">For more information, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span>|  
  
|<span data-ttu-id="39a29-118">Opcja</span><span class="sxs-lookup"><span data-stu-id="39a29-118">Option</span></span>|<span data-ttu-id="39a29-119">Opis</span><span class="sxs-lookup"><span data-stu-id="39a29-119">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="39a29-120">**/appdir:** *ścieżka*</span><span class="sxs-lookup"><span data-stu-id="39a29-120">**/appdir:** *path*</span></span>|<span data-ttu-id="39a29-121">Określa katalog główny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="39a29-121">Specifies the root directory of the application.</span></span>|  
|<span data-ttu-id="39a29-122">**/appname:** *nazwa aplikacji*</span><span class="sxs-lookup"><span data-stu-id="39a29-122">**/appname:** *applicationName*</span></span>|<span data-ttu-id="39a29-123">Określa nazwę aplikacji COM+, która ma zostać znaleziona lub utworzona.</span><span class="sxs-lookup"><span data-stu-id="39a29-123">Specifies the name of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="39a29-124">**/c**</span><span class="sxs-lookup"><span data-stu-id="39a29-124">**/c**</span></span>|<span data-ttu-id="39a29-125">Tworzy aplikację docelową.</span><span class="sxs-lookup"><span data-stu-id="39a29-125">Creates the target application.</span></span>|  
|<span data-ttu-id="39a29-126">**/componly**</span><span class="sxs-lookup"><span data-stu-id="39a29-126">**/componly**</span></span>|<span data-ttu-id="39a29-127">Konfiguruje tylko składniki; ignoruje metody i interfejsy.</span><span class="sxs-lookup"><span data-stu-id="39a29-127">Configures components only; ignores methods and interfaces.</span></span>|  
|<span data-ttu-id="39a29-128">**/exapp**</span><span class="sxs-lookup"><span data-stu-id="39a29-128">**/exapp**</span></span>|<span data-ttu-id="39a29-129">Określa, że narzędzie ma oczekiwać istniejącej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="39a29-129">Specifies to the tool to expect an existing application.</span></span>|  
|<span data-ttu-id="39a29-130">**/extlb**</span><span class="sxs-lookup"><span data-stu-id="39a29-130">**/extlb**</span></span>|<span data-ttu-id="39a29-131">Używa istniejącej biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="39a29-131">Uses an existing type library.</span></span>|  
|<span data-ttu-id="39a29-132">**/fc**</span><span class="sxs-lookup"><span data-stu-id="39a29-132">**/fc**</span></span>|<span data-ttu-id="39a29-133">Znajduje lub tworzy aplikację docelową.</span><span class="sxs-lookup"><span data-stu-id="39a29-133">Finds or creates the target application.</span></span>|  
|<span data-ttu-id="39a29-134">**/help**</span><span class="sxs-lookup"><span data-stu-id="39a29-134">**/help**</span></span>|<span data-ttu-id="39a29-135">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="39a29-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="39a29-136">**/noreconfig**</span><span class="sxs-lookup"><span data-stu-id="39a29-136">**/noreconfig**</span></span>|<span data-ttu-id="39a29-137">Nie konfiguruje ponownie istniejącej aplikacji docelowej.</span><span class="sxs-lookup"><span data-stu-id="39a29-137">Does not reconfigure an existing target application.</span></span>|  
|<span data-ttu-id="39a29-138">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="39a29-138">**/nologo**</span></span>|<span data-ttu-id="39a29-139">Pomija wyświetlanie transparentu startowego firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="39a29-139">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="39a29-140">**/parname:** *nazwa*</span><span class="sxs-lookup"><span data-stu-id="39a29-140">**/parname:** *name*</span></span>|<span data-ttu-id="39a29-141">Określa nazwę lub identyfikator aplikacji COM+, która ma zostać znaleziona lub utworzona.</span><span class="sxs-lookup"><span data-stu-id="39a29-141">Specifies the name or id of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="39a29-142">**/reconfig**</span><span class="sxs-lookup"><span data-stu-id="39a29-142">**/reconfig**</span></span>|<span data-ttu-id="39a29-143">Konfiguruje ponownie istniejącą aplikację docelową.</span><span class="sxs-lookup"><span data-stu-id="39a29-143">Reconfigures an existing target application.</span></span> <span data-ttu-id="39a29-144">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="39a29-144">This is the default.</span></span>|  
|<span data-ttu-id="39a29-145">**/tlb:** *plik maszynowy*</span><span class="sxs-lookup"><span data-stu-id="39a29-145">**/tlb:** *typelibraryfile*</span></span>|<span data-ttu-id="39a29-146">Określa plik biblioteki typów do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="39a29-146">Specifies the type library file to install.</span></span>|  
|<span data-ttu-id="39a29-147">**/u**</span><span class="sxs-lookup"><span data-stu-id="39a29-147">**/u**</span></span>|<span data-ttu-id="39a29-148">Odinstalowuje aplikację docelową.</span><span class="sxs-lookup"><span data-stu-id="39a29-148">Uninstalls the target application.</span></span>|  
|<span data-ttu-id="39a29-149">**/cichy**</span><span class="sxs-lookup"><span data-stu-id="39a29-149">**/quiet**</span></span>|<span data-ttu-id="39a29-150">Określa tryb cichy; pomija wyświetlanie logo i komunikatów o sukcesie.</span><span class="sxs-lookup"><span data-stu-id="39a29-150">Specifies quiet mode; suppresses the logo and success message display.</span></span>|  
|<span data-ttu-id="39a29-151">**/?**</span><span class="sxs-lookup"><span data-stu-id="39a29-151">**/?**</span></span>|<span data-ttu-id="39a29-152">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="39a29-152">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39a29-153">Uwagi</span><span class="sxs-lookup"><span data-stu-id="39a29-153">Remarks</span></span>  
 <span data-ttu-id="39a29-154">Regsvcs.exe wymaga pliku zestawu źródłowego określonego przez *plik assemblyFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="39a29-154">Regsvcs.exe requires a source assembly file specified by *assemblyFile.dll*.</span></span> <span data-ttu-id="39a29-155">Ten zestaw musi być podpisany za pomocą silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="39a29-155">This assembly must be signed with a strong name.</span></span> <span data-ttu-id="39a29-156">Aby uzyskać więcej informacji na temat podpisywania silnej nazwy, zobacz [Podpisywanie zestawu z silną nazwą](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="39a29-156">For more information on strong name signing, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span> <span data-ttu-id="39a29-157">Nazwy aplikacji docelowej i pliku biblioteki typów są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="39a29-157">The names of the target application and the type library file are optional.</span></span> <span data-ttu-id="39a29-158">Argument *applicationName* może być generowany z pliku zestawu źródłowego i zostanie utworzony przez regsvcs.exe, jeśli jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="39a29-158">The *applicationName* argument can be generated from the source assembly file and will be created by Regsvcs.exe, if it does not already exist.</span></span> <span data-ttu-id="39a29-159">Argument *typelibraryfile* może określać nazwę biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="39a29-159">The *typelibraryfile* argument can specify a type library name.</span></span> <span data-ttu-id="39a29-160">Jeśli nie zostanie określona nazwa biblioteki typów, program Regsvcs.exe użyje nazwy zestawu jako wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="39a29-160">If you do not specify a type library name, Regsvcs.exe uses the assembly name as the default.</span></span>  
  
 <span data-ttu-id="39a29-161">Gdy Regsvcs.exe rejestruje metody składnika, podlega [wymaganiom](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) i [wymaganiom łącza](../misc/link-demands.md) w przypadku tych metod.</span><span class="sxs-lookup"><span data-stu-id="39a29-161">When Regsvcs.exe registers a component's methods, it is subject to the [demands](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) and [link demands](../misc/link-demands.md) on those methods.</span></span> <span data-ttu-id="39a29-162">To narzędzie działa we w pełni zaufanym środowisku, więc większość żądań uprawnienia kończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="39a29-162">Because the tool executes in a fully-trusted environment, most demands for a permission succeed.</span></span> <span data-ttu-id="39a29-163">Jednak regsvcs.exe nie może zarejestrować składników z metod chronionych przez żądanie lub żądanie łącza dla <xref:System.Security.Permissions.StrongNameIdentityPermission> lub <xref:System.Security.Permissions.PublisherIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="39a29-163">However, Regsvcs.exe cannot register components with methods protected by a demand or link demand for the <xref:System.Security.Permissions.StrongNameIdentityPermission> or the <xref:System.Security.Permissions.PublisherIdentityPermission>.</span></span>  
  
 <span data-ttu-id="39a29-164">Aby używać programu Regsvcs.exe, trzeba mieć uprawnienia administracyjne na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="39a29-164">You must have administrative privileges on the local computer to use Regsvcs.exe.</span></span>  
  
 <span data-ttu-id="39a29-165">Jeśli podczas wykonywania dowolnej z tych akcji w programie Regsvcs.exe wystąpi błąd, zostaną wyświetlone odpowiednie komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="39a29-165">If Regsvcs.exe fails while performing any of these actions, it displays corresponding error messages.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="39a29-166">Przykłady</span><span class="sxs-lookup"><span data-stu-id="39a29-166">Examples</span></span>  
 <span data-ttu-id="39a29-167">Następujące polecenie dodaje wszystkie klasy `myTest.dll` publiczne `myTargetApp` zawarte w (istniejącej aplikacji `myTest.tlb` COM+) i tworzy bibliotekę typów.</span><span class="sxs-lookup"><span data-stu-id="39a29-167">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `myTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 <span data-ttu-id="39a29-168">Następujące polecenie dodaje wszystkie klasy `myTest.dll` publiczne `myTargetApp` zawarte w (istniejącej aplikacji `newTest.tlb` COM+) i tworzy bibliotekę typów.</span><span class="sxs-lookup"><span data-stu-id="39a29-168">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `newTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="39a29-169">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="39a29-169">See also</span></span>

- [<span data-ttu-id="39a29-170">narzędzia</span><span class="sxs-lookup"><span data-stu-id="39a29-170">Tools</span></span>](index.md)
- [<span data-ttu-id="39a29-171">Instrukcje: podpisywanie zestawu silną nazwą</span><span class="sxs-lookup"><span data-stu-id="39a29-171">How to: Sign an Assembly with a Strong Name</span></span>](../../standard/assembly/sign-strong-name.md)
- [<span data-ttu-id="39a29-172">Wiersz polecenia</span><span class="sxs-lookup"><span data-stu-id="39a29-172">Command Prompts</span></span>](developer-command-prompt-for-vs.md)

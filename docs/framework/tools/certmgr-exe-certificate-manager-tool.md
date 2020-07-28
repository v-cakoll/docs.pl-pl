---
title: Certmgr.exe (Menedżer certyfikatów)
description: Eksplorowanie Certmgr.exe, narzędzia Menedżer certyfikatów. To narzędzie zarządza certyfikatami, listami zaufania certyfikatów (CTL) i listami odwołania certyfikatów (CRL).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates, managing
- CRLs
- certificate trust lists
- Certmgr.exe
- Certificate Manager tool
- CTLs
- certificate revocation lists
ms.assetid: 7e953b43-1374-4bbc-814f-53ca1b6b52bb
ms.openlocfilehash: 43ab281e6ec28ff23ea584b03fd4278c6682e33e
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167269"
---
# <a name="certmgrexe-certificate-manager-tool"></a><span data-ttu-id="2eec2-104">Certmgr.exe (Menedżer certyfikatów)</span><span class="sxs-lookup"><span data-stu-id="2eec2-104">Certmgr.exe (Certificate Manager Tool)</span></span>
<span data-ttu-id="2eec2-105">Narzędzie Menedżer certyfikatów (Certmgr.exe) zarządza certyfikatami, listami zaufania certyfikatów (CTL) oraz listami odwołania certyfikatów (CRL).</span><span class="sxs-lookup"><span data-stu-id="2eec2-105">The Certificate Manager tool (Certmgr.exe) manages certificates, certificate trust lists (CTLs), and certificate revocation lists (CRLs).</span></span>  
  
 <span data-ttu-id="2eec2-106">Menedżer certyfikatów jest instalowany automatycznie z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2eec2-106">The Certificate Manager is automatically installed with Visual Studio.</span></span> <span data-ttu-id="2eec2-107">Aby uruchomić narzędzie, należy użyć [wiersza polecenia](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="2eec2-107">To start the tool, use the [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2eec2-108">Narzędzie Menedżer certyfikatów (Certmgr.exe) jest narzędziem wiersza polecenia, natomiast narzędzie Certyfikaty (Certmgr.msc) jest przystawką programu Microsoft Management Console (MMC).</span><span class="sxs-lookup"><span data-stu-id="2eec2-108">The Certificate Manager tool (Certmgr.exe) is a command-line utility, whereas Certificates (Certmgr.msc) is a Microsoft Management Console (MMC) snap-in.</span></span> <span data-ttu-id="2eec2-109">Ponieważ certmgr. msc zwykle znajduje się w katalogu systemu Windows, wprowadzenie `certmgr` w wierszu polecenia może załadować przystawkę MMC Certyfikaty, nawet jeśli otwarto wiersz polecenia dla deweloperów dla programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2eec2-109">Because Certmgr.msc is usually found in the Windows System directory, entering `certmgr` at the command line may load the Certificates MMC snap-in even if you have opened the Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="2eec2-110">Dzieje się tak, ponieważ ścieżka do przystawki ma pierwszeństwo przed ścieżką do narzędzia Menedżer certyfikatów w zmiennej środowiskowej PATH.</span><span class="sxs-lookup"><span data-stu-id="2eec2-110">This occurs because the path to the snap-in precedes the path to the Certificate Manager tool in the PATH environment variable.</span></span> <span data-ttu-id="2eec2-111">Jeśli wystąpi ten problem, można wykonywać polecenia programu Certmgr.exe, określając ścieżkę do pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="2eec2-111">If you encounter this problem, you can execute Certmgr.exe commands by specifying the path to the executable.</span></span>  
  
 <span data-ttu-id="2eec2-112">To narzędzie jest instalowane automatycznie z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2eec2-112">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="2eec2-113">Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7).</span><span class="sxs-lookup"><span data-stu-id="2eec2-113">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="2eec2-114">Aby uzyskać więcej informacji, zobacz [wiersza polecenia](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="2eec2-114">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="2eec2-115">Aby zapoznać się z omówieniem certyfikatów X. 509, zobacz [Praca z certyfikatami](../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="2eec2-115">For an overview of X.509 certificates, see [Working with Certificates](../wcf/feature-details/working-with-certificates.md).</span></span>  
  
 <span data-ttu-id="2eec2-116">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="2eec2-116">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2eec2-117">Składnia</span><span class="sxs-lookup"><span data-stu-id="2eec2-117">Syntax</span></span>  
  
```console  
      certmgr [/add | /del | /put] [options]  
[/s[/r registryLocation]] [sourceStorename]  
[/s[/r registryLocation]] [destinationStorename]  
```  
  
## <a name="parameters"></a><span data-ttu-id="2eec2-118">Parametry</span><span class="sxs-lookup"><span data-stu-id="2eec2-118">Parameters</span></span>  
  
|<span data-ttu-id="2eec2-119">Argument</span><span class="sxs-lookup"><span data-stu-id="2eec2-119">Argument</span></span>|<span data-ttu-id="2eec2-120">Opis</span><span class="sxs-lookup"><span data-stu-id="2eec2-120">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="2eec2-121">*sourceStorename*</span><span class="sxs-lookup"><span data-stu-id="2eec2-121">*sourceStorename*</span></span>|<span data-ttu-id="2eec2-122">Magazyn certyfikatów zawierający istniejące certyfikaty, listy CTL lub CRL do dodania, zapisania lub wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="2eec2-122">The certificate store that contains the existing certificates, CTLs, or CRLs to add, delete, save, or display.</span></span> <span data-ttu-id="2eec2-123">Może to być plik magazynu lub magazyn systemowy.</span><span class="sxs-lookup"><span data-stu-id="2eec2-123">This can be a store file or a systems store.</span></span>|  
|<span data-ttu-id="2eec2-124">*destinationStorename*</span><span class="sxs-lookup"><span data-stu-id="2eec2-124">*destinationStorename*</span></span>|<span data-ttu-id="2eec2-125">Wyjściowy magazyn lub plik certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="2eec2-125">The output certificate store or file.</span></span>|  
  
|<span data-ttu-id="2eec2-126">Opcja</span><span class="sxs-lookup"><span data-stu-id="2eec2-126">Option</span></span>|<span data-ttu-id="2eec2-127">Opis</span><span class="sxs-lookup"><span data-stu-id="2eec2-127">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="2eec2-128">**/Add**</span><span class="sxs-lookup"><span data-stu-id="2eec2-128">**/add**</span></span>|<span data-ttu-id="2eec2-129">Dodaje certyfikaty oraz listy CTL i CRL do magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="2eec2-129">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>|  
|<span data-ttu-id="2eec2-130">**/All**</span><span class="sxs-lookup"><span data-stu-id="2eec2-130">**/all**</span></span>|<span data-ttu-id="2eec2-131">Dodaje wszystkie wpisy, gdy są używane z **/Add**.</span><span class="sxs-lookup"><span data-stu-id="2eec2-131">Adds all entries when used with **/add**.</span></span> <span data-ttu-id="2eec2-132">Usuwa wszystkie wpisy, gdy są używane z **/del**. Wyświetla wszystkie wpisy, gdy są używane bez opcji **/Add** lub **/del** .</span><span class="sxs-lookup"><span data-stu-id="2eec2-132">Deletes all entries when used with **/del**. Displays all entries when used without the **/add** or **/del** options.</span></span> <span data-ttu-id="2eec2-133">Opcja **/All** nie może być używana z **/Put**.</span><span class="sxs-lookup"><span data-stu-id="2eec2-133">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="2eec2-134">**/c**</span><span class="sxs-lookup"><span data-stu-id="2eec2-134">**/c**</span></span>|<span data-ttu-id="2eec2-135">Dodaje certyfikaty, gdy jest używany z **/Add**.</span><span class="sxs-lookup"><span data-stu-id="2eec2-135">Adds certificates when used with **/add**.</span></span> <span data-ttu-id="2eec2-136">Usuwa certyfikaty, gdy są używane z **/del**. Zapisuje certyfikaty, gdy są używane z **/Put**.</span><span class="sxs-lookup"><span data-stu-id="2eec2-136">Deletes certificates when used with **/del**. Saves certificates when used with **/put**.</span></span> <span data-ttu-id="2eec2-137">Wyświetla certyfikaty, gdy jest używana bez opcji **/Add**, **/del**lub **/Put** .</span><span class="sxs-lookup"><span data-stu-id="2eec2-137">Displays certificates when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="2eec2-138">**/CRL**</span><span class="sxs-lookup"><span data-stu-id="2eec2-138">**/CRL**</span></span>|<span data-ttu-id="2eec2-139">Dodaje listy CRL, gdy jest używana z opcją **/Add**.</span><span class="sxs-lookup"><span data-stu-id="2eec2-139">Adds CRLs when used with **/add**.</span></span> <span data-ttu-id="2eec2-140">Usuwa listy CRL, gdy są używane z **/del**. Zapisuje listy CRL, gdy są używane z **/Put**.</span><span class="sxs-lookup"><span data-stu-id="2eec2-140">Deletes CRLs when used with **/del**. Saves CRLs when used with **/put**.</span></span> <span data-ttu-id="2eec2-141">Wyświetla listę CRL, gdy jest używana bez opcji **/Add**, **/del**lub **/Put** .</span><span class="sxs-lookup"><span data-stu-id="2eec2-141">Displays CRLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="2eec2-142">**/CTL**</span><span class="sxs-lookup"><span data-stu-id="2eec2-142">**/CTL**</span></span>|<span data-ttu-id="2eec2-143">Dodaje listy CTL, gdy jest używana z opcją **/Add**.</span><span class="sxs-lookup"><span data-stu-id="2eec2-143">Adds CTLs when used with **/add**.</span></span> <span data-ttu-id="2eec2-144">Usuwa listy CTL, gdy jest używana z **/del**. Zapisuje listy CTL, gdy jest używana z **/Put**.</span><span class="sxs-lookup"><span data-stu-id="2eec2-144">Deletes CTLs when used with **/del**. Saves CTLs when used with **/put**.</span></span> <span data-ttu-id="2eec2-145">Wyświetla listę CTL, gdy jest używana bez opcji **/Add**, **/del**lub **/Put** .</span><span class="sxs-lookup"><span data-stu-id="2eec2-145">Displays CTLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="2eec2-146">**/del**</span><span class="sxs-lookup"><span data-stu-id="2eec2-146">**/del**</span></span>|<span data-ttu-id="2eec2-147">Usuwa certyfikaty oraz listy CTL i CRL z magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="2eec2-147">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>|  
|<span data-ttu-id="2eec2-148">**/e** — *EncodingType*</span><span class="sxs-lookup"><span data-stu-id="2eec2-148">**/e** *encodingType*</span></span>|<span data-ttu-id="2eec2-149">Określa typ kodowania certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="2eec2-149">Specifies the certificate encoding type.</span></span> <span data-ttu-id="2eec2-150">Wartość domyślna to `X509_ASN_ENCODING`.</span><span class="sxs-lookup"><span data-stu-id="2eec2-150">The default is `X509_ASN_ENCODING`.</span></span>|  
|<span data-ttu-id="2eec2-151">**/F** *flagiDW*</span><span class="sxs-lookup"><span data-stu-id="2eec2-151">**/f** *dwFlags*</span></span>|<span data-ttu-id="2eec2-152">Określa flagę otwarcia magazynu.</span><span class="sxs-lookup"><span data-stu-id="2eec2-152">Specifies the store open flag.</span></span> <span data-ttu-id="2eec2-153">Jest to parametr *flagiDW* przesłany do **CertOpenStore**.</span><span class="sxs-lookup"><span data-stu-id="2eec2-153">This is the *dwFlags* parameter passed to **CertOpenStore**.</span></span> <span data-ttu-id="2eec2-154">Wartość domyślna to CERT_SYSTEM_STORE_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="2eec2-154">The default value is CERT_SYSTEM_STORE_CURRENT_USER.</span></span> <span data-ttu-id="2eec2-155">Ta opcja jest uwzględniana tylko wtedy, gdy jest używana opcja **/y** .</span><span class="sxs-lookup"><span data-stu-id="2eec2-155">This option is considered only if the **/y** option is used.</span></span>|  
|<span data-ttu-id="2eec2-156">**/h**[**ELP**]</span><span class="sxs-lookup"><span data-stu-id="2eec2-156">**/h**[**elp**]</span></span>|<span data-ttu-id="2eec2-157">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="2eec2-157">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="2eec2-158">**/n** *nam*</span><span class="sxs-lookup"><span data-stu-id="2eec2-158">**/n** *nam*</span></span>|<span data-ttu-id="2eec2-159">Określa wspólną nazwę certyfikatu do dodania, usunięcia lub zapisania.</span><span class="sxs-lookup"><span data-stu-id="2eec2-159">Specifies the common name of the certificate to add, delete, or save.</span></span> <span data-ttu-id="2eec2-160">Tej opcji można używać tylko z certyfikatami; nie można używać jej z listami CTL i CRL.</span><span class="sxs-lookup"><span data-stu-id="2eec2-160">This option can only be used with certificates; it cannot be used with CTLs or CRLs.</span></span>|  
|<span data-ttu-id="2eec2-161">**/Put**</span><span class="sxs-lookup"><span data-stu-id="2eec2-161">**/put**</span></span>|<span data-ttu-id="2eec2-162">Zapisuje certyfikat X.509, listę CTL lub CRL z magazynu certyfikatów w pliku.</span><span class="sxs-lookup"><span data-stu-id="2eec2-162">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span> <span data-ttu-id="2eec2-163">Plik jest zapisywany w formacie X.509.</span><span class="sxs-lookup"><span data-stu-id="2eec2-163">The file is saved in X.509 format.</span></span> <span data-ttu-id="2eec2-164">Aby zapisać plik w formacie PKCS #7, można użyć opcji **/7** z opcją **/Put** .</span><span class="sxs-lookup"><span data-stu-id="2eec2-164">You can use the **/7** option with the **/put** option to save the file in PKCS #7 format.</span></span> <span data-ttu-id="2eec2-165">Po opcji **/Put** należy wykonać polecenie **/c**, **/CTL**lub **/CRL**.</span><span class="sxs-lookup"><span data-stu-id="2eec2-165">The **/put** option must be followed by either **/c**, **/CTL**, or **/CRL**.</span></span> <span data-ttu-id="2eec2-166">Opcja **/All** nie może być używana z **/Put**.</span><span class="sxs-lookup"><span data-stu-id="2eec2-166">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="2eec2-167">**/r** *Lokalizacja* /r</span><span class="sxs-lookup"><span data-stu-id="2eec2-167">**/r** *location*</span></span>|<span data-ttu-id="2eec2-168">Określa lokalizację w rejestrze magazynu systemowego.</span><span class="sxs-lookup"><span data-stu-id="2eec2-168">Identifies the registry location of the system store.</span></span> <span data-ttu-id="2eec2-169">Ta opcja jest uwzględniana tylko wtedy, gdy określono opcję **/s** .</span><span class="sxs-lookup"><span data-stu-id="2eec2-169">This option is considered only if you specify the **/s** option.</span></span> <span data-ttu-id="2eec2-170">*Lokalizacja* musi mieć jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="2eec2-170">*location* must be one of the following:</span></span><br /><br /> <span data-ttu-id="2eec2-171">-   `currentUser`wskazuje, że magazyn certyfikatów jest pod kluczem HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="2eec2-171">-   `currentUser` indicates that the certificate store is under the HKEY_CURRENT_USER key.</span></span> <span data-ttu-id="2eec2-172">Jest to opcja domyślna.</span><span class="sxs-lookup"><span data-stu-id="2eec2-172">This is the default.</span></span><br /><span data-ttu-id="2eec2-173">-   `localMachine`wskazuje, że magazyn certyfikatów jest pod kluczem HKEY_LOCAL_MACHINE.</span><span class="sxs-lookup"><span data-stu-id="2eec2-173">-   `localMachine` indicates that the certificate store is under the HKEY_LOCAL_MACHINE key.</span></span>|  
|<span data-ttu-id="2eec2-174">**/s**</span><span class="sxs-lookup"><span data-stu-id="2eec2-174">**/s**</span></span>|<span data-ttu-id="2eec2-175">Wskazuje, że magazyn certyfikatów jest magazynem systemowym.</span><span class="sxs-lookup"><span data-stu-id="2eec2-175">Indicates that the certificate store is a system store.</span></span> <span data-ttu-id="2eec2-176">Jeśli ta opcja nie zostanie określona, magazyn jest uznawany za **StoreFile**.</span><span class="sxs-lookup"><span data-stu-id="2eec2-176">If you do not specify this option, the store is considered to be a **StoreFile**.</span></span>|  
|<span data-ttu-id="2eec2-177">**/SHA1** *sha1Hash*</span><span class="sxs-lookup"><span data-stu-id="2eec2-177">**/sha1** *sha1Hash*</span></span>|<span data-ttu-id="2eec2-178">Określa skrót SHA1 certyfikatu, listy CTL lub CRL do dodania, usunięcia lub zapisania.</span><span class="sxs-lookup"><span data-stu-id="2eec2-178">Specifies the SHA1 hash of the certificate, CTL, or CRL to add, delete, or save.</span></span>|  
|<span data-ttu-id="2eec2-179">**przełącznika**</span><span class="sxs-lookup"><span data-stu-id="2eec2-179">**/v**</span></span>|<span data-ttu-id="2eec2-180">Określa tryb pełny; wyświetla szczegółowe informacje dotyczące certyfikatu oraz list CTL i CRL.</span><span class="sxs-lookup"><span data-stu-id="2eec2-180">Specifies verbose mode; displays detailed information about certificates, CTLs, and CRLs.</span></span> <span data-ttu-id="2eec2-181">Tej opcji nie można używać z opcjami **/Add**, **/del**i **/Put** .</span><span class="sxs-lookup"><span data-stu-id="2eec2-181">This option cannot be used with the **/add**, **/del**, or **/put** options.</span></span>|  
|<span data-ttu-id="2eec2-182">**/y** — *dostawca*</span><span class="sxs-lookup"><span data-stu-id="2eec2-182">**/y** *provider*</span></span>|<span data-ttu-id="2eec2-183">Określa nazwę dostawcy magazynu.</span><span class="sxs-lookup"><span data-stu-id="2eec2-183">Specifies the store provider name.</span></span>|  
|<span data-ttu-id="2eec2-184">**/7**</span><span class="sxs-lookup"><span data-stu-id="2eec2-184">**/7**</span></span>|<span data-ttu-id="2eec2-185">Zapisuje magazyn docelowy jako obiekt w formacie PKCS #7.</span><span class="sxs-lookup"><span data-stu-id="2eec2-185">Saves the destination store as a PKCS #7 object.</span></span>|  
|<span data-ttu-id="2eec2-186">**/?**</span><span class="sxs-lookup"><span data-stu-id="2eec2-186">**/?**</span></span>|<span data-ttu-id="2eec2-187">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="2eec2-187">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2eec2-188">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2eec2-188">Remarks</span></span>  
 <span data-ttu-id="2eec2-189">Program Certmgr.exe wykonuje następujące podstawowe funkcje:</span><span class="sxs-lookup"><span data-stu-id="2eec2-189">Certmgr.exe performs the following basic functions:</span></span>  
  
- <span data-ttu-id="2eec2-190">Wyświetla na konsoli certyfikaty oraz listy CTL i CRL.</span><span class="sxs-lookup"><span data-stu-id="2eec2-190">Displays certificates, CTLs, and CRLs to the console.</span></span>  
  
- <span data-ttu-id="2eec2-191">Dodaje certyfikaty oraz listy CTL i CRL do magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="2eec2-191">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>  
  
- <span data-ttu-id="2eec2-192">Usuwa certyfikaty oraz listy CTL i CRL z magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="2eec2-192">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>  
  
- <span data-ttu-id="2eec2-193">Zapisuje certyfikat X.509, listę CTL lub CRL z magazynu certyfikatów w pliku.</span><span class="sxs-lookup"><span data-stu-id="2eec2-193">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span>  
  
 <span data-ttu-id="2eec2-194">Certmgr.exe współpracuje z dwoma typami magazynów certyfikatów: **StoreFile** i magazynem systemowym.</span><span class="sxs-lookup"><span data-stu-id="2eec2-194">Certmgr.exe works with two types of certificate stores: **StoreFile** and system store.</span></span> <span data-ttu-id="2eec2-195">Nie jest konieczne określanie typu magazynu certyfikatów; program Certmgr.exe może zidentyfikować typ magazynu i wykonać odpowiednie operacje.</span><span class="sxs-lookup"><span data-stu-id="2eec2-195">It is not necessary to specify the type of certificate store; Certmgr.exe can identify the store type and perform the appropriate operations.</span></span>  
  
 <span data-ttu-id="2eec2-196">Uruchomienie programu Certmgr.exe bez określenia żadnej opcji spowoduje uruchomienie przystawki certmgr.msc wyposażonej w graficzny interfejs użytkownika ułatwiający wykonywanie zadań zarządzania certyfikatami, które są również dostępne w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="2eec2-196">Running Certmgr.exe without specifying any options launches the certmgr.msc snap-in, which has a GUI that helps with the certificate management tasks that are also available from the command line.</span></span> <span data-ttu-id="2eec2-197">Graficzny interfejs użytkownika dostarcza kreatora importu, który kopiuje certyfikaty oraz listy CTL i CRL z dysku do magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="2eec2-197">The GUI provides an import wizard, which copies certificates, CTLs, and CRLs from your disk to a certificate store.</span></span>  
  
 <span data-ttu-id="2eec2-198">Nazwy magazynów x509 można znaleźć dla `sourceStorename` parametrów i, `destinationStorename` kompilując i uruchamiając następujący kod.</span><span class="sxs-lookup"><span data-stu-id="2eec2-198">You can find the names of X509Certificate stores for the `sourceStorename` and `destinationStorename` parameters by compiling and running the following code.</span></span>  
  
 [!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)]
 [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]  
  
 <span data-ttu-id="2eec2-199">Aby uzyskać więcej informacji o certyfikatach, zobacz [Praca z certyfikatami](../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="2eec2-199">For more information about certificates, see [Working with Certificates](../wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="2eec2-200">Przykłady</span><span class="sxs-lookup"><span data-stu-id="2eec2-200">Examples</span></span>  
 <span data-ttu-id="2eec2-201">Następujące polecenie wyświetla domyślny magazyn systemowy o nazwie `my` z pełnymi danymi wyjściowymi.</span><span class="sxs-lookup"><span data-stu-id="2eec2-201">The following command displays a default system store called `my` with verbose output.</span></span>  
  
```console  
certmgr /v /s my  
```  
  
 <span data-ttu-id="2eec2-202">Następujące polecenie dodaje wszystkie certyfikaty w pliku o nazwie `myFile.ext` do nowego pliku o nazwie `newFile.ext` .</span><span class="sxs-lookup"><span data-stu-id="2eec2-202">The following command adds all the certificates in a file called `myFile.ext` to a new file called `newFile.ext`.</span></span>  
  
```console  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 <span data-ttu-id="2eec2-203">Poniższe polecenie dodaje certyfikat w pliku o nazwie `testcert.cer` do `my` magazynu systemowego.</span><span class="sxs-lookup"><span data-stu-id="2eec2-203">The following command adds the certificate in a file named `testcert.cer` to the `my` system store.</span></span>  
  
```console  
certmgr /add /c testcert.cer /s my  
```  
  
 <span data-ttu-id="2eec2-204">Poniższe polecenie dodaje certyfikat w pliku o nazwie `TrustedCert.cer` do głównego magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="2eec2-204">The following command adds the certificate in a file named `TrustedCert.cer` to the root certificate store.</span></span>  
  
```console  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 <span data-ttu-id="2eec2-205">Poniższe polecenie zapisuje certyfikat z nazwą pospolitą `myCert` w `my` magazynie systemowym do pliku o nazwie `newCert.cer` .</span><span class="sxs-lookup"><span data-stu-id="2eec2-205">The following command saves a certificate with the common name `myCert` in the `my` system store to a file called `newCert.cer`.</span></span>  
  
```console  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 <span data-ttu-id="2eec2-206">Następujące polecenie usuwa wszystkie listy CTL ze `my` sklepu systemowego i zapisuje przechowywany magazyn do pliku o nazwie `newStore.str` .</span><span class="sxs-lookup"><span data-stu-id="2eec2-206">The following command deletes all CTLs in the `my` system store and saves the resulting store to a file called `newStore.str`.</span></span>  
  
```console  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 <span data-ttu-id="2eec2-207">Poniższe polecenie zapisuje certyfikat w `my` magazynie systemowym w pliku `newFile` .</span><span class="sxs-lookup"><span data-stu-id="2eec2-207">The following command saves a certificate in the `my` system store in the file `newFile`.</span></span> <span data-ttu-id="2eec2-208">Zostanie wyświetlony monit o wprowadzenie numeru certyfikatu z `my` , który ma zostać umieszczony `newFile` .</span><span class="sxs-lookup"><span data-stu-id="2eec2-208">You will be prompted to enter the certificate number from `my` to put in `newFile`.</span></span>  
  
```console  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a><span data-ttu-id="2eec2-209">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2eec2-209">See also</span></span>

- [<span data-ttu-id="2eec2-210">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="2eec2-210">Tools</span></span>](index.md)
- [<span data-ttu-id="2eec2-211">Makecert.exe (narzędzie tworzenia certyfikatów)</span><span class="sxs-lookup"><span data-stu-id="2eec2-211">Makecert.exe (Certificate Creation Tool)</span></span>](/windows/desktop/SecCrypto/makecert)
- [<span data-ttu-id="2eec2-212">Wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="2eec2-212">Command Prompts</span></span>](developer-command-prompt-for-vs.md)

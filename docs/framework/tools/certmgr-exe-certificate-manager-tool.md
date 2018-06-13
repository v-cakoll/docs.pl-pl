---
title: Certmgr.exe (Menedżer certyfikatów)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 96edfd0f94240d51a224f4522573a450ab027330
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409922"
---
# <a name="certmgrexe-certificate-manager-tool"></a><span data-ttu-id="090ac-102">Certmgr.exe (Menedżer certyfikatów)</span><span class="sxs-lookup"><span data-stu-id="090ac-102">Certmgr.exe (Certificate Manager Tool)</span></span>
<span data-ttu-id="090ac-103">Narzędzie Menedżer certyfikatów (Certmgr.exe) zarządza certyfikatami, listami zaufania certyfikatów (CTL) oraz listami odwołania certyfikatów (CRL).</span><span class="sxs-lookup"><span data-stu-id="090ac-103">The Certificate Manager tool (Certmgr.exe) manages certificates, certificate trust lists (CTLs), and certificate revocation lists (CRLs).</span></span>  
  
 <span data-ttu-id="090ac-104">Menedżer certyfikatów jest instalowany automatycznie z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="090ac-104">The Certificate Manager is automatically installed with Visual Studio.</span></span> <span data-ttu-id="090ac-105">Aby uruchomić narzędzie, użyj [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="090ac-105">To start the tool, use the [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="090ac-106">Narzędzie Menedżer certyfikatów (Certmgr.exe) jest narzędziem wiersza polecenia, natomiast narzędzie Certyfikaty (Certmgr.msc) jest przystawką programu Microsoft Management Console (MMC).</span><span class="sxs-lookup"><span data-stu-id="090ac-106">The Certificate Manager tool (Certmgr.exe) is a command-line utility, whereas Certificates (Certmgr.msc) is a Microsoft Management Console (MMC) snap-in.</span></span> <span data-ttu-id="090ac-107">Ponieważ Certmgr.msc zazwyczaj znajduje się w katalogu systemu Windows, wprowadzając `certmgr` w wierszu polecenia może załadować przystawki certyfikatów konsoli MMC nawet, jeśli został otwarty wiersz polecenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="090ac-107">Because Certmgr.msc is usually found in the Windows System directory, entering `certmgr` at the command line may load the Certificates MMC snap-in even if you have opened the Visual Studio Command Prompt.</span></span> <span data-ttu-id="090ac-108">Dzieje się tak, ponieważ ścieżka do przystawki ma pierwszeństwo przed ścieżką do narzędzia Menedżer certyfikatów w zmiennej środowiskowej PATH.</span><span class="sxs-lookup"><span data-stu-id="090ac-108">This occurs because the path to the snap-in precedes the path to the Certificate Manager tool in the PATH environment variable.</span></span> <span data-ttu-id="090ac-109">Jeśli wystąpi ten problem, można wykonywać polecenia programu Certmgr.exe, określając ścieżkę do pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="090ac-109">If you encounter this problem, you can execute Certmgr.exe commands by specifying the path to the executable.</span></span>  
  
 <span data-ttu-id="090ac-110">To narzędzie jest instalowane automatycznie z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="090ac-110">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="090ac-111">Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7).</span><span class="sxs-lookup"><span data-stu-id="090ac-111">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="090ac-112">Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="090ac-112">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="090ac-113">Omówienie certyfikatów X.509, zobacz [Praca z certyfikatami](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="090ac-113">For an overview of X.509 certificates, see [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
 <span data-ttu-id="090ac-114">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="090ac-114">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="090ac-115">Składnia</span><span class="sxs-lookup"><span data-stu-id="090ac-115">Syntax</span></span>  
  
```  
      certmgr [/add | /del | /put] [options]  
[/s[/r registryLocation]] [sourceStorename]  
[/s[/r registryLocation]] [destinationStorename]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="090ac-116">Parametry</span><span class="sxs-lookup"><span data-stu-id="090ac-116">Parameters</span></span>  
  
|<span data-ttu-id="090ac-117">Argument</span><span class="sxs-lookup"><span data-stu-id="090ac-117">Argument</span></span>|<span data-ttu-id="090ac-118">Opis</span><span class="sxs-lookup"><span data-stu-id="090ac-118">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="090ac-119">*sourceStorename*</span><span class="sxs-lookup"><span data-stu-id="090ac-119">*sourceStorename*</span></span>|<span data-ttu-id="090ac-120">Magazyn certyfikatów zawierający istniejące certyfikaty, listy CTL lub CRL do dodania, zapisania lub wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="090ac-120">The certificate store that contains the existing certificates, CTLs, or CRLs to add, delete, save, or display.</span></span> <span data-ttu-id="090ac-121">Może to być plik magazynu lub magazyn systemowy.</span><span class="sxs-lookup"><span data-stu-id="090ac-121">This can be a store file or a systems store.</span></span>|  
|<span data-ttu-id="090ac-122">*destinationStorename*</span><span class="sxs-lookup"><span data-stu-id="090ac-122">*destinationStorename*</span></span>|<span data-ttu-id="090ac-123">Wyjściowy magazyn lub plik certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="090ac-123">The output certificate store or file.</span></span>|  
  
|<span data-ttu-id="090ac-124">Opcja</span><span class="sxs-lookup"><span data-stu-id="090ac-124">Option</span></span>|<span data-ttu-id="090ac-125">Opis</span><span class="sxs-lookup"><span data-stu-id="090ac-125">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="090ac-126">**/ add**</span><span class="sxs-lookup"><span data-stu-id="090ac-126">**/add**</span></span>|<span data-ttu-id="090ac-127">Dodaje certyfikaty oraz listy CTL i CRL do magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="090ac-127">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>|  
|<span data-ttu-id="090ac-128">**/ all**</span><span class="sxs-lookup"><span data-stu-id="090ac-128">**/all**</span></span>|<span data-ttu-id="090ac-129">Dodaje wszystkie wpisy z **/ add**.</span><span class="sxs-lookup"><span data-stu-id="090ac-129">Adds all entries when used with **/add**.</span></span> <span data-ttu-id="090ac-130">Usuwa wszystkie wpisy z **/del**. Wyświetla wszystkie wpisy użyte bez **/ add** lub **/del** opcje.</span><span class="sxs-lookup"><span data-stu-id="090ac-130">Deletes all entries when used with **/del**. Displays all entries when used without the **/add** or **/del** options.</span></span> <span data-ttu-id="090ac-131">**/All** nie można użyć opcji **/put**.</span><span class="sxs-lookup"><span data-stu-id="090ac-131">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="090ac-132">**/c**</span><span class="sxs-lookup"><span data-stu-id="090ac-132">**/c**</span></span>|<span data-ttu-id="090ac-133">Dodaje certyfikatów, gdy jest używany z **/ add**.</span><span class="sxs-lookup"><span data-stu-id="090ac-133">Adds certificates when used with **/add**.</span></span> <span data-ttu-id="090ac-134">Usuwa certyfikatów, gdy jest używany z **/del**. Zapisuje certyfikatów, gdy jest używany z **/put**.</span><span class="sxs-lookup"><span data-stu-id="090ac-134">Deletes certificates when used with **/del**. Saves certificates when used with **/put**.</span></span> <span data-ttu-id="090ac-135">Wyświetla certyfikaty używane bez **/ add**, **/del**, lub **/put** opcji.</span><span class="sxs-lookup"><span data-stu-id="090ac-135">Displays certificates when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="090ac-136">**/ LIST CRL**</span><span class="sxs-lookup"><span data-stu-id="090ac-136">**/CRL**</span></span>|<span data-ttu-id="090ac-137">Dodaje list CRL w przypadku użycia z **/ add**.</span><span class="sxs-lookup"><span data-stu-id="090ac-137">Adds CRLs when used with **/add**.</span></span> <span data-ttu-id="090ac-138">Usuwa listy CRL w przypadku użycia z **/del**. Zapisuje list CRL w przypadku użycia z **/put**.</span><span class="sxs-lookup"><span data-stu-id="090ac-138">Deletes CRLs when used with **/del**. Saves CRLs when used with **/put**.</span></span> <span data-ttu-id="090ac-139">Wyświetla list CRL, gdy jest używany bez **/ add**, **/del**, lub **/put** opcji.</span><span class="sxs-lookup"><span data-stu-id="090ac-139">Displays CRLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="090ac-140">**/ LIST CTL**</span><span class="sxs-lookup"><span data-stu-id="090ac-140">**/CTL**</span></span>|<span data-ttu-id="090ac-141">Dodaje listy CTL, gdy jest używany z **/ add**.</span><span class="sxs-lookup"><span data-stu-id="090ac-141">Adds CTLs when used with **/add**.</span></span> <span data-ttu-id="090ac-142">Usuwa listy CTL, gdy jest używany z **/del**. Zapisuje listy CTL, gdy jest używany z **/put**.</span><span class="sxs-lookup"><span data-stu-id="090ac-142">Deletes CTLs when used with **/del**. Saves CTLs when used with **/put**.</span></span> <span data-ttu-id="090ac-143">Wyświetla listy CTL, gdy jest używany bez **/ add**, **/del**, lub **/put** opcji.</span><span class="sxs-lookup"><span data-stu-id="090ac-143">Displays CTLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="090ac-144">**/ del**</span><span class="sxs-lookup"><span data-stu-id="090ac-144">**/del**</span></span>|<span data-ttu-id="090ac-145">Usuwa certyfikaty oraz listy CTL i CRL z magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="090ac-145">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>|  
|<span data-ttu-id="090ac-146">**/e** *encodingType*</span><span class="sxs-lookup"><span data-stu-id="090ac-146">**/e** *encodingType*</span></span>|<span data-ttu-id="090ac-147">Określa typ kodowania certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="090ac-147">Specifies the certificate encoding type.</span></span> <span data-ttu-id="090ac-148">Wartość domyślna to `X509_ASN_ENCODING`.</span><span class="sxs-lookup"><span data-stu-id="090ac-148">The default is `X509_ASN_ENCODING`.</span></span>|  
|<span data-ttu-id="090ac-149">**/f** *wartość elementu dwFlags*</span><span class="sxs-lookup"><span data-stu-id="090ac-149">**/f** *dwFlags*</span></span>|<span data-ttu-id="090ac-150">Określa flagę otwarcia magazynu.</span><span class="sxs-lookup"><span data-stu-id="090ac-150">Specifies the store open flag.</span></span> <span data-ttu-id="090ac-151">Jest to *wartość elementu dwFlags* parametr przekazany do **wywołanie funkcji CertOpenStore**.</span><span class="sxs-lookup"><span data-stu-id="090ac-151">This is the *dwFlags* parameter passed to **CertOpenStore**.</span></span> <span data-ttu-id="090ac-152">Wartość domyślna to CERT_SYSTEM_STORE_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="090ac-152">The default value is CERT_SYSTEM_STORE_CURRENT_USER.</span></span> <span data-ttu-id="090ac-153">Ta opcja jest uznawany za tylko wtedy, gdy **/y** jest używana opcja.</span><span class="sxs-lookup"><span data-stu-id="090ac-153">This option is considered only if the **/y** option is used.</span></span>|  
|<span data-ttu-id="090ac-154">**/h**[**elp**]</span><span class="sxs-lookup"><span data-stu-id="090ac-154">**/h**[**elp**]</span></span>|<span data-ttu-id="090ac-155">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="090ac-155">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="090ac-156">**/n** *nam*</span><span class="sxs-lookup"><span data-stu-id="090ac-156">**/n** *nam*</span></span>|<span data-ttu-id="090ac-157">Określa wspólną nazwę certyfikatu do dodania, usunięcia lub zapisania.</span><span class="sxs-lookup"><span data-stu-id="090ac-157">Specifies the common name of the certificate to add, delete, or save.</span></span> <span data-ttu-id="090ac-158">Tej opcji można używać tylko z certyfikatami; nie można używać jej z listami CTL i CRL.</span><span class="sxs-lookup"><span data-stu-id="090ac-158">This option can only be used with certificates; it cannot be used with CTLs or CRLs.</span></span>|  
|<span data-ttu-id="090ac-159">**/ put**</span><span class="sxs-lookup"><span data-stu-id="090ac-159">**/put**</span></span>|<span data-ttu-id="090ac-160">Zapisuje certyfikat X.509, listę CTL lub CRL z magazynu certyfikatów w pliku.</span><span class="sxs-lookup"><span data-stu-id="090ac-160">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span> <span data-ttu-id="090ac-161">Plik jest zapisywany w formacie X.509.</span><span class="sxs-lookup"><span data-stu-id="090ac-161">The file is saved in X.509 format.</span></span> <span data-ttu-id="090ac-162">Można użyć **/7** opcję z **/put** opcję, aby zapisać plik w formacie PKCS #7.</span><span class="sxs-lookup"><span data-stu-id="090ac-162">You can use the **/7** option with the **/put** option to save the file in PKCS #7 format.</span></span> <span data-ttu-id="090ac-163">**/Put** opcja musi następować albo **/c**, **/CTL**, lub **/CRL**.</span><span class="sxs-lookup"><span data-stu-id="090ac-163">The **/put** option must be followed by either **/c**, **/CTL**, or **/CRL**.</span></span> <span data-ttu-id="090ac-164">**/All** nie można użyć opcji **/put**.</span><span class="sxs-lookup"><span data-stu-id="090ac-164">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="090ac-165">**/r** *lokalizacji*</span><span class="sxs-lookup"><span data-stu-id="090ac-165">**/r** *location*</span></span>|<span data-ttu-id="090ac-166">Określa lokalizację w rejestrze magazynu systemowego.</span><span class="sxs-lookup"><span data-stu-id="090ac-166">Identifies the registry location of the system store.</span></span> <span data-ttu-id="090ac-167">Ta opcja jest uznawany za tylko w przypadku określenia **/s** opcji.</span><span class="sxs-lookup"><span data-stu-id="090ac-167">This option is considered only if you specify the **/s** option.</span></span> <span data-ttu-id="090ac-168">*Lokalizacja* musi mieć jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="090ac-168">*location* must be one of the following:</span></span><br /><br /> <span data-ttu-id="090ac-169">-   `currentUser` Wskazuje, że magazyn certyfikatów jest w kluczu HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="090ac-169">-   `currentUser` indicates that the certificate store is under the HKEY_CURRENT_USER key.</span></span> <span data-ttu-id="090ac-170">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="090ac-170">This is the default.</span></span><br /><span data-ttu-id="090ac-171">-   `localMachine` Wskazuje, że magazyn certyfikatów jest w kluczu HKEY_LOCAL_MACHINE.</span><span class="sxs-lookup"><span data-stu-id="090ac-171">-   `localMachine` indicates that the certificate store is under the HKEY_LOCAL_MACHINE key.</span></span>|  
|<span data-ttu-id="090ac-172">**/ s**</span><span class="sxs-lookup"><span data-stu-id="090ac-172">**/s**</span></span>|<span data-ttu-id="090ac-173">Wskazuje, że magazyn certyfikatów jest magazynem systemowym.</span><span class="sxs-lookup"><span data-stu-id="090ac-173">Indicates that the certificate store is a system store.</span></span> <span data-ttu-id="090ac-174">Jeśli ta opcja nie zostanie określony, magazynie jest uważany za **StoreFile**.</span><span class="sxs-lookup"><span data-stu-id="090ac-174">If you do not specify this option, the store is considered to be a **StoreFile**.</span></span>|  
|<span data-ttu-id="090ac-175">**/SHA1** *sha1Hash*</span><span class="sxs-lookup"><span data-stu-id="090ac-175">**/sha1** *sha1Hash*</span></span>|<span data-ttu-id="090ac-176">Określa skrót SHA1 certyfikatu, listy CTL lub CRL do dodania, usunięcia lub zapisania.</span><span class="sxs-lookup"><span data-stu-id="090ac-176">Specifies the SHA1 hash of the certificate, CTL, or CRL to add, delete, or save.</span></span>|  
|<span data-ttu-id="090ac-177">**/v**</span><span class="sxs-lookup"><span data-stu-id="090ac-177">**/v**</span></span>|<span data-ttu-id="090ac-178">Określa tryb pełny; wyświetla szczegółowe informacje dotyczące certyfikatu oraz list CTL i CRL.</span><span class="sxs-lookup"><span data-stu-id="090ac-178">Specifies verbose mode; displays detailed information about certificates, CTLs, and CRLs.</span></span> <span data-ttu-id="090ac-179">Nie można użyć tej opcji z **/ add**, **/del**, lub **/put** opcje.</span><span class="sxs-lookup"><span data-stu-id="090ac-179">This option cannot be used with the **/add**, **/del**, or **/put** options.</span></span>|  
|<span data-ttu-id="090ac-180">**/y** *dostawcy*</span><span class="sxs-lookup"><span data-stu-id="090ac-180">**/y** *provider*</span></span>|<span data-ttu-id="090ac-181">Określa nazwę dostawcy magazynu.</span><span class="sxs-lookup"><span data-stu-id="090ac-181">Specifies the store provider name.</span></span>|  
|<span data-ttu-id="090ac-182">**/7**</span><span class="sxs-lookup"><span data-stu-id="090ac-182">**/7**</span></span>|<span data-ttu-id="090ac-183">Zapisuje magazyn docelowy jako obiekt w formacie PKCS #7.</span><span class="sxs-lookup"><span data-stu-id="090ac-183">Saves the destination store as a PKCS #7 object.</span></span>|  
|<span data-ttu-id="090ac-184">**/?**</span><span class="sxs-lookup"><span data-stu-id="090ac-184">**/?**</span></span>|<span data-ttu-id="090ac-185">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="090ac-185">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="090ac-186">Uwagi</span><span class="sxs-lookup"><span data-stu-id="090ac-186">Remarks</span></span>  
 <span data-ttu-id="090ac-187">Program Certmgr.exe wykonuje następujące podstawowe funkcje:</span><span class="sxs-lookup"><span data-stu-id="090ac-187">Certmgr.exe performs the following basic functions:</span></span>  
  
-   <span data-ttu-id="090ac-188">Wyświetla na konsoli certyfikaty oraz listy CTL i CRL.</span><span class="sxs-lookup"><span data-stu-id="090ac-188">Displays certificates, CTLs, and CRLs to the console.</span></span>  
  
-   <span data-ttu-id="090ac-189">Dodaje certyfikaty oraz listy CTL i CRL do magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="090ac-189">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>  
  
-   <span data-ttu-id="090ac-190">Usuwa certyfikaty oraz listy CTL i CRL z magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="090ac-190">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>  
  
-   <span data-ttu-id="090ac-191">Zapisuje certyfikat X.509, listę CTL lub CRL z magazynu certyfikatów w pliku.</span><span class="sxs-lookup"><span data-stu-id="090ac-191">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span>  
  
 <span data-ttu-id="090ac-192">Certmgr.exe współpracuje z dwóch typów magazynów certyfikatów: **StoreFile** i magazynu systemu.</span><span class="sxs-lookup"><span data-stu-id="090ac-192">Certmgr.exe works with two types of certificate stores: **StoreFile** and system store.</span></span> <span data-ttu-id="090ac-193">Nie jest konieczne określanie typu magazynu certyfikatów; program Certmgr.exe może zidentyfikować typ magazynu i wykonać odpowiednie operacje.</span><span class="sxs-lookup"><span data-stu-id="090ac-193">It is not necessary to specify the type of certificate store; Certmgr.exe can identify the store type and perform the appropriate operations.</span></span>  
  
 <span data-ttu-id="090ac-194">Uruchomienie programu Certmgr.exe bez określenia żadnej opcji spowoduje uruchomienie przystawki certmgr.msc wyposażonej w graficzny interfejs użytkownika ułatwiający wykonywanie zadań zarządzania certyfikatami, które są również dostępne w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="090ac-194">Running Certmgr.exe without specifying any options launches the certmgr.msc snap-in, which has a GUI that helps with the certificate management tasks that are also available from the command line.</span></span> <span data-ttu-id="090ac-195">Graficzny interfejs użytkownika dostarcza kreatora importu, który kopiuje certyfikaty oraz listy CTL i CRL z dysku do magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="090ac-195">The GUI provides an import wizard, which copies certificates, CTLs, and CRLs from your disk to a certificate store.</span></span>  
  
 <span data-ttu-id="090ac-196">Można znaleźć nazw magazynów w certyfikacie x 509 dla `sourceStorename` i `destinationStorename` parametrów, kompilowania i uruchamiając poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="090ac-196">You can find the names of X509Certificate stores for the `sourceStorename` and `destinationStorename` parameters by compiling and running the following code.</span></span>  
  
 [!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)]
 [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]  
  
 <span data-ttu-id="090ac-197">Aby uzyskać więcej informacji o certyfikatach, zobacz [Praca z certyfikatami](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="090ac-197">For more information about certificates, see [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="090ac-198">Przykłady</span><span class="sxs-lookup"><span data-stu-id="090ac-198">Examples</span></span>  
 <span data-ttu-id="090ac-199">Następujące polecenie wyświetla domyślny magazyn systemu o nazwie `my` z pełnymi danymi wyjściowymi.</span><span class="sxs-lookup"><span data-stu-id="090ac-199">The following command displays a default system store called `my` with verbose output.</span></span>  
  
```  
certmgr /v /s my  
```  
  
 <span data-ttu-id="090ac-200">Polecenie dodaje wszystkie certyfikaty w pliku o nazwie `myFile.ext` do nowego pliku o nazwie `newFile.ext`.</span><span class="sxs-lookup"><span data-stu-id="090ac-200">The following command adds all the certificates in a file called `myFile.ext` to a new file called `newFile.ext`.</span></span>  
  
```  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 <span data-ttu-id="090ac-201">Polecenie dodaje certyfikat w pliku o nazwie `testcert.cer` do `my` magazynu systemu.</span><span class="sxs-lookup"><span data-stu-id="090ac-201">The following command adds the certificate in a file named `testcert.cer` to the `my` system store.</span></span>  
  
```  
certmgr /add /c testcert.cer /s my  
```  
  
 <span data-ttu-id="090ac-202">Polecenie dodaje certyfikat w pliku o nazwie `TrustedCert.cer` do katalogu głównego magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="090ac-202">The following command adds the certificate in a file named `TrustedCert.cer` to the root certificate store.</span></span>  
  
```  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 <span data-ttu-id="090ac-203">Poniższe polecenie zapisuje certyfikat z nazwą pospolitą `myCert` w `my` magazynu systemu do pliku o nazwie `newCert.cer`.</span><span class="sxs-lookup"><span data-stu-id="090ac-203">The following command saves a certificate with the common name `myCert` in the `my` system store to a file called `newCert.cer`.</span></span>  
  
```  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 <span data-ttu-id="090ac-204">Następujące polecenie usuwa wszystkie listy CTL w `my` magazynu systemu i zapisuje wynikowy magazynu w pliku o nazwie `newStore.str`.</span><span class="sxs-lookup"><span data-stu-id="090ac-204">The following command deletes all CTLs in the `my` system store and saves the resulting store to a file called `newStore.str`.</span></span>  
  
```  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 <span data-ttu-id="090ac-205">Poniższe polecenie zapisuje certyfikat w `my` magazynu systemu w pliku `newFile`.</span><span class="sxs-lookup"><span data-stu-id="090ac-205">The following command saves a certificate in the `my` system store in the file `newFile`.</span></span> <span data-ttu-id="090ac-206">Pojawi się monit o wprowadzenie numeru certyfikatu z `my` mają zostać umieszczone w `newFile`.</span><span class="sxs-lookup"><span data-stu-id="090ac-206">You will be prompted to enter the certificate number from `my` to put in `newFile`.</span></span>  
  
```  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a><span data-ttu-id="090ac-207">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="090ac-207">See Also</span></span>  
 [<span data-ttu-id="090ac-208">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="090ac-208">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="090ac-209">MakeCert.exe (narzędzie tworzenia certyfikatów)</span><span class="sxs-lookup"><span data-stu-id="090ac-209">Makecert.exe (Certificate Creation Tool)</span></span>](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)  
 [<span data-ttu-id="090ac-210">Wiersze polecenia</span><span class="sxs-lookup"><span data-stu-id="090ac-210">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

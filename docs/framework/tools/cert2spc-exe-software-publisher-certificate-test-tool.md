---
title: Cert2spc.exe (Narzędzie testowe certyfikatów wydawców oprogramowania)
description: Użyj Cert2spc.exe, narzędzia testowego certyfikatu wydawcy oprogramowania. To narzędzie tworzy certyfikat wydawcy oprogramowania (SPC) z co najmniej jednego certyfikatu X. 509.
ms.date: 03/30/2017
helpviewer_keywords:
- SPC
- Software Publisher Certificate Test tool
- Software Publisher Certificate
- Cert2spc.exe
- certificates, Software Publisher's Certificate
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
ms.openlocfilehash: 2eb6339aa6f5d23a5b87986410cbeaac2dac2bec
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167322"
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a><span data-ttu-id="50594-104">Cert2spc.exe (Narzędzie testowe certyfikatów wydawców oprogramowania)</span><span class="sxs-lookup"><span data-stu-id="50594-104">Cert2spc.exe (Software Publisher Certificate Test Tool)</span></span>
<span data-ttu-id="50594-105">Narzędzie testowe certyfikatów wydawców oprogramowania tworzy certyfikat wydawcy oprogramowania (SPC) z co najmniej jednego certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="50594-105">The Software Publisher Certificate Test tool creates a Software Publisher's Certificate (SPC) from one or more X.509 certificates.</span></span> <span data-ttu-id="50594-106">Cert2spc.exe służy tylko do celów testowych.</span><span class="sxs-lookup"><span data-stu-id="50594-106">Cert2spc.exe is for test purposes only.</span></span> <span data-ttu-id="50594-107">Prawidłowy SPC można uzyskać od urzędu certyfikacji, np. VeriSign lub Thawte.</span><span class="sxs-lookup"><span data-stu-id="50594-107">You can obtain a valid SPC from a Certification Authority such as VeriSign or Thawte.</span></span> <span data-ttu-id="50594-108">Aby uzyskać więcej informacji na temat tworzenia certyfikatów X. 509, zobacz [Makecert.exe (narzędzie tworzenia certyfikatów)](/windows/desktop/SecCrypto/makecert).</span><span class="sxs-lookup"><span data-stu-id="50594-108">For more information about creating X.509 certificates, see [Makecert.exe (Certificate Creation Tool)](/windows/desktop/SecCrypto/makecert).</span></span>  
  
 <span data-ttu-id="50594-109">To narzędzie jest instalowane automatycznie z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="50594-109">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="50594-110">Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7).</span><span class="sxs-lookup"><span data-stu-id="50594-110">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="50594-111">Aby uzyskać więcej informacji, zobacz [wiersza polecenia](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="50594-111">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="50594-112">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="50594-112">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50594-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="50594-113">Syntax</span></span>  
  
```console  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
## <a name="parameters"></a><span data-ttu-id="50594-114">Parametry</span><span class="sxs-lookup"><span data-stu-id="50594-114">Parameters</span></span>  
  
|<span data-ttu-id="50594-115">Argument</span><span class="sxs-lookup"><span data-stu-id="50594-115">Argument</span></span>|<span data-ttu-id="50594-116">Opis</span><span class="sxs-lookup"><span data-stu-id="50594-116">Description</span></span>|  
|--------------|-----------------|  
|`certN.cer`|<span data-ttu-id="50594-117">Nazwa certyfikatu X.509 do zawarcia w pliku SPC.</span><span class="sxs-lookup"><span data-stu-id="50594-117">The name of an X.509 certificate to include in the SPC file.</span></span> <span data-ttu-id="50594-118">Można określić wiele nazw i oddzielić je spacjami.</span><span class="sxs-lookup"><span data-stu-id="50594-118">You can specify multiple names separated by spaces.</span></span>|  
|`crlN.crl`|<span data-ttu-id="50594-119">Nazwa listy odwołania certyfikatów X.509 do zawarcia w pliku SPC.</span><span class="sxs-lookup"><span data-stu-id="50594-119">The name of a certificate revocation list to include in the SPC file.</span></span> <span data-ttu-id="50594-120">Można określić wiele nazw i oddzielić je spacjami.</span><span class="sxs-lookup"><span data-stu-id="50594-120">You can specify multiple names separated by spaces.</span></span>|  
|`outputSPCfile.spc`|<span data-ttu-id="50594-121">Nazwa obiektu PKCS #7, który zawiera certyfikaty X.509.</span><span class="sxs-lookup"><span data-stu-id="50594-121">The name of the PKCS #7 object that will contain the X.509 certificates.</span></span>|  
  
|<span data-ttu-id="50594-122">Opcja</span><span class="sxs-lookup"><span data-stu-id="50594-122">Option</span></span>|<span data-ttu-id="50594-123">Opis</span><span class="sxs-lookup"><span data-stu-id="50594-123">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="50594-124">**/?**</span><span class="sxs-lookup"><span data-stu-id="50594-124">**/?**</span></span>|<span data-ttu-id="50594-125">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="50594-125">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="50594-126">Przykłady</span><span class="sxs-lookup"><span data-stu-id="50594-126">Examples</span></span>  
 <span data-ttu-id="50594-127">Następujące polecenie tworzy SPC z `myCertificate.cer` i umieszcza go w `mySPCFile.spc` .</span><span class="sxs-lookup"><span data-stu-id="50594-127">The following command creates an SPC from `myCertificate.cer` and places it in `mySPCFile.spc`.</span></span>  
  
```console
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 <span data-ttu-id="50594-128">Następujące polecenie tworzy SPC z i i `oneCertificate.cer` `twoCertificate.cer` umieszcza go w `mySPCFile.spc` .</span><span class="sxs-lookup"><span data-stu-id="50594-128">The following command creates an SPC from `oneCertificate.cer` and `twoCertificate.cer`, and places it in `mySPCFile.spc`.</span></span>  
  
```console
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a><span data-ttu-id="50594-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50594-129">See also</span></span>

- [<span data-ttu-id="50594-130">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="50594-130">Tools</span></span>](index.md)
- [<span data-ttu-id="50594-131">Makecert.exe (narzędzie tworzenia certyfikatów)</span><span class="sxs-lookup"><span data-stu-id="50594-131">Makecert.exe (Certificate Creation Tool)</span></span>](/windows/desktop/SecCrypto/makecert)
- [<span data-ttu-id="50594-132">Wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="50594-132">Command Prompts</span></span>](developer-command-prompt-for-vs.md)

---
title: Cert2spc.exe (Narzędzie testowe certyfikatów wydawców oprogramowania)
ms.date: 03/30/2017
helpviewer_keywords:
- SPC
- Software Publisher Certificate Test tool
- Software Publisher Certificate
- Cert2spc.exe
- certificates, Software Publisher's Certificate
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
ms.openlocfilehash: 809b7d0383f172a5fbcb2ac4ac3ffb96ff0b8e20
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73129887"
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a><span data-ttu-id="abf1a-102">Cert2spc.exe (Narzędzie testowe certyfikatów wydawców oprogramowania)</span><span class="sxs-lookup"><span data-stu-id="abf1a-102">Cert2spc.exe (Software Publisher Certificate Test Tool)</span></span>
<span data-ttu-id="abf1a-103">Narzędzie testowe certyfikatów wydawców oprogramowania tworzy certyfikat wydawcy oprogramowania (SPC) z co najmniej jednego certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="abf1a-103">The Software Publisher Certificate Test tool creates a Software Publisher's Certificate (SPC) from one or more X.509 certificates.</span></span> <span data-ttu-id="abf1a-104">Cert2spc.exe służy tylko do celów testowych.</span><span class="sxs-lookup"><span data-stu-id="abf1a-104">Cert2spc.exe is for test purposes only.</span></span> <span data-ttu-id="abf1a-105">Prawidłowy SPC można uzyskać od urzędu certyfikacji, np. VeriSign lub Thawte.</span><span class="sxs-lookup"><span data-stu-id="abf1a-105">You can obtain a valid SPC from a Certification Authority such as VeriSign or Thawte.</span></span> <span data-ttu-id="abf1a-106">Aby uzyskać więcej informacji na temat tworzenia certyfikatów X.509, zobacz [Makecert.exe (Narzędzie do tworzenia certyfikatów).](/windows/desktop/SecCrypto/makecert)</span><span class="sxs-lookup"><span data-stu-id="abf1a-106">For more information about creating X.509 certificates, see [Makecert.exe (Certificate Creation Tool)](/windows/desktop/SecCrypto/makecert).</span></span>  
  
 <span data-ttu-id="abf1a-107">To narzędzie jest instalowane automatycznie z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="abf1a-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="abf1a-108">Aby uruchomić narzędzie, użyj wiersza polecenia dewelopera dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7).</span><span class="sxs-lookup"><span data-stu-id="abf1a-108">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="abf1a-109">Aby uzyskać więcej informacji, zobacz [Wiersze poleceń](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="abf1a-109">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="abf1a-110">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="abf1a-110">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abf1a-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="abf1a-111">Syntax</span></span>  
  
```console  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
## <a name="parameters"></a><span data-ttu-id="abf1a-112">Parametry</span><span class="sxs-lookup"><span data-stu-id="abf1a-112">Parameters</span></span>  
  
|<span data-ttu-id="abf1a-113">Argument</span><span class="sxs-lookup"><span data-stu-id="abf1a-113">Argument</span></span>|<span data-ttu-id="abf1a-114">Opis</span><span class="sxs-lookup"><span data-stu-id="abf1a-114">Description</span></span>|  
|--------------|-----------------|  
|`certN.cer`|<span data-ttu-id="abf1a-115">Nazwa certyfikatu X.509 do zawarcia w pliku SPC.</span><span class="sxs-lookup"><span data-stu-id="abf1a-115">The name of an X.509 certificate to include in the SPC file.</span></span> <span data-ttu-id="abf1a-116">Można określić wiele nazw i oddzielić je spacjami.</span><span class="sxs-lookup"><span data-stu-id="abf1a-116">You can specify multiple names separated by spaces.</span></span>|  
|`crlN.crl`|<span data-ttu-id="abf1a-117">Nazwa listy odwołania certyfikatów X.509 do zawarcia w pliku SPC.</span><span class="sxs-lookup"><span data-stu-id="abf1a-117">The name of a certificate revocation list to include in the SPC file.</span></span> <span data-ttu-id="abf1a-118">Można określić wiele nazw i oddzielić je spacjami.</span><span class="sxs-lookup"><span data-stu-id="abf1a-118">You can specify multiple names separated by spaces.</span></span>|  
|`outputSPCfile.spc`|<span data-ttu-id="abf1a-119">Nazwa obiektu PKCS #7, który zawiera certyfikaty X.509.</span><span class="sxs-lookup"><span data-stu-id="abf1a-119">The name of the PKCS #7 object that will contain the X.509 certificates.</span></span>|  
  
|<span data-ttu-id="abf1a-120">Opcja</span><span class="sxs-lookup"><span data-stu-id="abf1a-120">Option</span></span>|<span data-ttu-id="abf1a-121">Opis</span><span class="sxs-lookup"><span data-stu-id="abf1a-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="abf1a-122">**/?**</span><span class="sxs-lookup"><span data-stu-id="abf1a-122">**/?**</span></span>|<span data-ttu-id="abf1a-123">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="abf1a-123">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="abf1a-124">Przykłady</span><span class="sxs-lookup"><span data-stu-id="abf1a-124">Examples</span></span>  
 <span data-ttu-id="abf1a-125">Następujące polecenie tworzy chPL `myCertificate.cer` i `mySPCFile.spc`umieszcza go w pliku .</span><span class="sxs-lookup"><span data-stu-id="abf1a-125">The following command creates an SPC from `myCertificate.cer` and places it in `mySPCFile.spc`.</span></span>  
  
```console
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 <span data-ttu-id="abf1a-126">Następujące polecenie tworzy chPL z `oneCertificate.cer` i `twoCertificate.cer` `mySPCFile.spc`, i umieszcza go w .</span><span class="sxs-lookup"><span data-stu-id="abf1a-126">The following command creates an SPC from `oneCertificate.cer` and `twoCertificate.cer`, and places it in `mySPCFile.spc`.</span></span>  
  
```console
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a><span data-ttu-id="abf1a-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="abf1a-127">See also</span></span>

- [<span data-ttu-id="abf1a-128">narzędzia</span><span class="sxs-lookup"><span data-stu-id="abf1a-128">Tools</span></span>](index.md)
- [<span data-ttu-id="abf1a-129">Plik Makecert.exe (narzędzie do tworzenia certyfikatów)</span><span class="sxs-lookup"><span data-stu-id="abf1a-129">Makecert.exe (Certificate Creation Tool)</span></span>](/windows/desktop/SecCrypto/makecert)
- [<span data-ttu-id="abf1a-130">Wiersz polecenia</span><span class="sxs-lookup"><span data-stu-id="abf1a-130">Command Prompts</span></span>](developer-command-prompt-for-vs.md)

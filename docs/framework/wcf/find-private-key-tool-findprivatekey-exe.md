---
title: "Narzędzie do znajdowania klucza prywatnego (FindPrivateKey.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5e2110e129b293ffb04c8e3eb69a5c3bfe83c17b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="find-private-key-tool-findprivatekeyexe"></a><span data-ttu-id="a9509-102">Narzędzie do znajdowania klucza prywatnego (FindPrivateKey.exe)</span><span class="sxs-lookup"><span data-stu-id="a9509-102">Find Private Key Tool (FindPrivateKey.exe)</span></span>
<span data-ttu-id="a9509-103">To narzędzie wiersza polecenia można pobrać klucza prywatnego z magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="a9509-103">This command-line tool can be used to retrieve a private key from a certificate store.</span></span> <span data-ttu-id="a9509-104">FindPrivateKey.exe można na przykład, aby znaleźć lokalizację i nazwę pliku klucza prywatnego skojarzonego z certyfikatem X.509 określonej w magazynie certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="a9509-104">For example, FindPrivateKey.exe can be used to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a9509-105">Narzędzie FindPrivateKey jest dostarczana jako przykład WCF.</span><span class="sxs-lookup"><span data-stu-id="a9509-105">The FindPrivateKey tool is shipped as a WCF sample.</span></span> <span data-ttu-id="a9509-106">Aby uzyskać więcej informacji o tym, gdzie można znaleźć próbki i skompiluj go, zobacz</span><span class="sxs-lookup"><span data-stu-id="a9509-106">For more information about where to find the sample and how to build it, see</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9509-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="a9509-107">Syntax</span></span>  
  
```  
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]  
```  
  
## <a name="remarks"></a><span data-ttu-id="a9509-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a9509-108">Remarks</span></span>  
 <span data-ttu-id="a9509-109">W poniższych tabelach opisano argumenty i opcje, które mogą służyć za pomocą narzędzia Znajdź klucza prywatnego (FindPrivateKey.exe).</span><span class="sxs-lookup"><span data-stu-id="a9509-109">The following tables describe the arguments and the options that can be used with the Find Private Key tool (FindPrivateKey.exe).</span></span>  
  
|<span data-ttu-id="a9509-110">Argument</span><span class="sxs-lookup"><span data-stu-id="a9509-110">Argument</span></span>|<span data-ttu-id="a9509-111">Opis</span><span class="sxs-lookup"><span data-stu-id="a9509-111">Description</span></span>|  
|--------------|-----------------|  
|`storeName`|<span data-ttu-id="a9509-112">Nazwa magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="a9509-112">Name of the certificate store.</span></span>|  
|`storeLocation`|<span data-ttu-id="a9509-113">Lokalizacja magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="a9509-113">The location of the certificate store.</span></span>|  
  
|<span data-ttu-id="a9509-114">Opcja</span><span class="sxs-lookup"><span data-stu-id="a9509-114">Option</span></span>|<span data-ttu-id="a9509-115">Opis</span><span class="sxs-lookup"><span data-stu-id="a9509-115">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a9509-116">`/n <`*subjectName*`>`</span><span class="sxs-lookup"><span data-stu-id="a9509-116">`/n <` *subjectName* `>`</span></span>|<span data-ttu-id="a9509-117">Określa nazwę podmiotu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="a9509-117">Specifies the subject name of the certificate.</span></span>|  
|<span data-ttu-id="a9509-118">`/t <`*odcisk palca*`>`</span><span class="sxs-lookup"><span data-stu-id="a9509-118">`/t <` *thumbprint* `>`</span></span>|<span data-ttu-id="a9509-119">Określa odcisk palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="a9509-119">Specifies the thumbprint of the certificate.</span></span> <span data-ttu-id="a9509-120">Certmgr.exe umożliwia pobieranie odcisku palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="a9509-120">Use Certmgr.exe to retrieve the thumbprint of the certificate.</span></span>|  
|`/f`|<span data-ttu-id="a9509-121">Wyświetla tylko nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="a9509-121">Outputs the file name only.</span></span>|  
|`/d`|<span data-ttu-id="a9509-122">Wyświetla tylko katalog.</span><span class="sxs-lookup"><span data-stu-id="a9509-122">Outputs the directory only.</span></span>|  
|`/a`|<span data-ttu-id="a9509-123">Generuje bezwzględnej nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="a9509-123">Outputs the absolute file name.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="a9509-124">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a9509-124">Examples</span></span>  
 <span data-ttu-id="a9509-125">Polecenie pobiera klucz prywatny dla Jan Nowak.</span><span class="sxs-lookup"><span data-stu-id="a9509-125">The following command retrieves the private key for John Doe.</span></span>  
  
```  
FindPrivateKey My CurrentUser -n "CN=John Doe"  
```  
  
 <span data-ttu-id="a9509-126">Polecenie pobiera klucz prywatny dla komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="a9509-126">The following command retrieves the private key for the local machine.</span></span>  
  
```  
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a  
```

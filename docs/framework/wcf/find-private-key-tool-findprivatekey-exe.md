---
title: Narzędzie do znajdowania klucza prywatnego (FindPrivateKey.exe)
ms.date: 09/11/2017
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
ms.openlocfilehash: 8f156cbb2f4fad8d51e356bd4dee2d72d9397ffb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61929587"
---
# <a name="find-private-key-tool-findprivatekeyexe"></a><span data-ttu-id="09dcd-102">Narzędzie do znajdowania klucza prywatnego (FindPrivateKey.exe)</span><span class="sxs-lookup"><span data-stu-id="09dcd-102">Find Private Key Tool (FindPrivateKey.exe)</span></span>

<span data-ttu-id="09dcd-103">To narzędzie wiersza polecenia może służyć do pobierania klucza prywatnego z magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="09dcd-103">This command-line tool can be used to retrieve a private key from a certificate store.</span></span> <span data-ttu-id="09dcd-104">Na przykład *FindPrivateKey.exe* można znaleźć lokalizację i nazwę pliku klucza prywatnego skojarzonego z certyfikatem X.509 określonych w magazynie certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="09dcd-104">For example, *FindPrivateKey.exe* can be used to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="09dcd-105">Narzędzie FindPrivateKey jest dostarczany jako przykładowej usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="09dcd-105">The FindPrivateKey tool is shipped as a WCF sample.</span></span> <span data-ttu-id="09dcd-106">Aby uzyskać więcej informacji na temat miejsca znaleźć plik i jak ją skompilować, zobacz [FindPrivateKey](./samples/findprivatekey.md).</span><span class="sxs-lookup"><span data-stu-id="09dcd-106">For more information about where to find the sample and how to build it, see [FindPrivateKey](./samples/findprivatekey.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="09dcd-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="09dcd-107">Syntax</span></span>

```
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

## <a name="remarks"></a><span data-ttu-id="09dcd-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="09dcd-108">Remarks</span></span>

<span data-ttu-id="09dcd-109">W poniższych tabelach opisano argumentów i opcje, które mogą służyć za pomocą narzędzia Znajdź klucza prywatnego (FindPrivateKey.exe).</span><span class="sxs-lookup"><span data-stu-id="09dcd-109">The following tables describe the arguments and the options that can be used with the Find Private Key tool (FindPrivateKey.exe).</span></span>

|<span data-ttu-id="09dcd-110">Argument</span><span class="sxs-lookup"><span data-stu-id="09dcd-110">Argument</span></span>|<span data-ttu-id="09dcd-111">Opis</span><span class="sxs-lookup"><span data-stu-id="09dcd-111">Description</span></span>|
|--------------|-----------------|
|`storeName`|<span data-ttu-id="09dcd-112">Nazwa magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="09dcd-112">Name of the certificate store.</span></span>|
|`storeLocation`|<span data-ttu-id="09dcd-113">Lokalizacja magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="09dcd-113">The location of the certificate store.</span></span>|

|<span data-ttu-id="09dcd-114">Opcja</span><span class="sxs-lookup"><span data-stu-id="09dcd-114">Option</span></span>|<span data-ttu-id="09dcd-115">Opis</span><span class="sxs-lookup"><span data-stu-id="09dcd-115">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="09dcd-116">`/n <` *SubjectName* `>`</span><span class="sxs-lookup"><span data-stu-id="09dcd-116">`/n <` *subjectName* `>`</span></span>|<span data-ttu-id="09dcd-117">Określa nazwę podmiotu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="09dcd-117">Specifies the subject name of the certificate.</span></span>|
|<span data-ttu-id="09dcd-118">`/t <` *Odcisk palca* `>`</span><span class="sxs-lookup"><span data-stu-id="09dcd-118">`/t <` *thumbprint* `>`</span></span>|<span data-ttu-id="09dcd-119">Określa odcisk palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="09dcd-119">Specifies the thumbprint of the certificate.</span></span> <span data-ttu-id="09dcd-120">Certmgr.exe umożliwia pobieranie odcisku palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="09dcd-120">Use Certmgr.exe to retrieve the thumbprint of the certificate.</span></span>|
|`/f`|<span data-ttu-id="09dcd-121">Wyświetla tylko nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="09dcd-121">Outputs the file name only.</span></span>|
|`/d`|<span data-ttu-id="09dcd-122">Wyświetla tylko katalog.</span><span class="sxs-lookup"><span data-stu-id="09dcd-122">Outputs the directory only.</span></span>|
|`/a`|<span data-ttu-id="09dcd-123">Generuje bezwzględnej nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="09dcd-123">Outputs the absolute file name.</span></span>|

## <a name="examples"></a><span data-ttu-id="09dcd-124">Przykłady</span><span class="sxs-lookup"><span data-stu-id="09dcd-124">Examples</span></span>

<span data-ttu-id="09dcd-125">Następujące polecenie pobiera klucz prywatny dla John Doe:</span><span class="sxs-lookup"><span data-stu-id="09dcd-125">The following command retrieves the private key for John Doe:</span></span>

```
FindPrivateKey My CurrentUser -n "CN=John Doe"
```

<span data-ttu-id="09dcd-126">Następujące polecenie umożliwia pobranie klucza prywatnego na komputerze lokalnym:</span><span class="sxs-lookup"><span data-stu-id="09dcd-126">The following command retrieves the private key for the local machine:</span></span>

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a
```
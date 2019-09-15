---
title: Narzędzie do znajdowania klucza prywatnego (FindPrivateKey.exe)
ms.date: 09/11/2017
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
ms.openlocfilehash: 316f55b93cf4d867b99878bf483b73cb3f09ad04
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990350"
---
# <a name="find-private-key-tool-findprivatekeyexe"></a><span data-ttu-id="6d736-102">Narzędzie do znajdowania klucza prywatnego (FindPrivateKey.exe)</span><span class="sxs-lookup"><span data-stu-id="6d736-102">Find Private Key Tool (FindPrivateKey.exe)</span></span>

<span data-ttu-id="6d736-103">Za pomocą tego narzędzia wiersza polecenia można pobrać klucz prywatny z magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="6d736-103">This command-line tool can be used to retrieve a private key from a certificate store.</span></span> <span data-ttu-id="6d736-104">Na przykład można użyć *FindPrivateKey. exe* , aby znaleźć lokalizację i nazwę pliku klucza prywatnego skojarzonego z konkretnym certyfikatem X. 509 w magazynie certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="6d736-104">For example, *FindPrivateKey.exe* can be used to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6d736-105">Narzędzie FindPrivateKey jest dostarczane jako przykład WCF.</span><span class="sxs-lookup"><span data-stu-id="6d736-105">The FindPrivateKey tool is shipped as a WCF sample.</span></span> <span data-ttu-id="6d736-106">Aby uzyskać więcej informacji na temat miejsca znalezienia przykładu i sposobu jego kompilowania, zobacz [FindPrivateKey](./samples/findprivatekey.md).</span><span class="sxs-lookup"><span data-stu-id="6d736-106">For more information about where to find the sample and how to build it, see [FindPrivateKey](./samples/findprivatekey.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="6d736-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="6d736-107">Syntax</span></span>

```console
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

## <a name="remarks"></a><span data-ttu-id="6d736-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6d736-108">Remarks</span></span>

<span data-ttu-id="6d736-109">W poniższych tabelach opisano argumenty i opcje, które mogą być używane z narzędziem Znajdź klucz prywatny (FindPrivateKey. exe).</span><span class="sxs-lookup"><span data-stu-id="6d736-109">The following tables describe the arguments and the options that can be used with the Find Private Key tool (FindPrivateKey.exe).</span></span>

|<span data-ttu-id="6d736-110">Argument</span><span class="sxs-lookup"><span data-stu-id="6d736-110">Argument</span></span>|<span data-ttu-id="6d736-111">Opis</span><span class="sxs-lookup"><span data-stu-id="6d736-111">Description</span></span>|
|--------------|-----------------|
|`storeName`|<span data-ttu-id="6d736-112">Nazwa magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="6d736-112">Name of the certificate store.</span></span>|
|`storeLocation`|<span data-ttu-id="6d736-113">Lokalizacja magazynu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="6d736-113">The location of the certificate store.</span></span>|

|<span data-ttu-id="6d736-114">Opcja</span><span class="sxs-lookup"><span data-stu-id="6d736-114">Option</span></span>|<span data-ttu-id="6d736-115">Opis</span><span class="sxs-lookup"><span data-stu-id="6d736-115">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="6d736-116">`/n <`Nr *podmiotu*`>`</span><span class="sxs-lookup"><span data-stu-id="6d736-116">`/n <` *subjectName* `>`</span></span>|<span data-ttu-id="6d736-117">Określa nazwę podmiotu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="6d736-117">Specifies the subject name of the certificate.</span></span>|
|<span data-ttu-id="6d736-118">`/t <`*odcisk palca*`>`</span><span class="sxs-lookup"><span data-stu-id="6d736-118">`/t <` *thumbprint* `>`</span></span>|<span data-ttu-id="6d736-119">Określa odcisk palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="6d736-119">Specifies the thumbprint of the certificate.</span></span> <span data-ttu-id="6d736-120">Użyj certmgr. exe w celu pobrania odcisku palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="6d736-120">Use Certmgr.exe to retrieve the thumbprint of the certificate.</span></span>|
|`/f`|<span data-ttu-id="6d736-121">Wyświetla tylko nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="6d736-121">Outputs the file name only.</span></span>|
|`/d`|<span data-ttu-id="6d736-122">Wyświetla tylko katalog.</span><span class="sxs-lookup"><span data-stu-id="6d736-122">Outputs the directory only.</span></span>|
|`/a`|<span data-ttu-id="6d736-123">Wyprowadza bezwzględną nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="6d736-123">Outputs the absolute file name.</span></span>|

## <a name="examples"></a><span data-ttu-id="6d736-124">Przykłady</span><span class="sxs-lookup"><span data-stu-id="6d736-124">Examples</span></span>

<span data-ttu-id="6d736-125">Następujące polecenie pobiera klucz prywatny dla John Nowak:</span><span class="sxs-lookup"><span data-stu-id="6d736-125">The following command retrieves the private key for John Doe:</span></span>

```console
FindPrivateKey My CurrentUser -n "CN=John Doe"
```

<span data-ttu-id="6d736-126">Następujące polecenie pobiera klucz prywatny komputera lokalnego:</span><span class="sxs-lookup"><span data-stu-id="6d736-126">The following command retrieves the private key for the local machine:</span></span>

```console
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a
```

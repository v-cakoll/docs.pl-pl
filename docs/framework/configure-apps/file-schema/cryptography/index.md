---
title: Schemat ustawień kryptografii
ms.date: 03/30/2017
helpviewer_keywords:
- configuration schema [.NET Framework], cryptography
- elements [.NET Framework], cryptography
- schema configuration settings
- cryptography, settings schema
- cryptography, mapping algorithm names
- configuration sections [.NET Framework]
- configuration settings [.NET Framework], cryptography
ms.assetid: 1f55050a-b2a3-4868-a3c0-da20826150f3
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 71d2edac1dd9a84c9d3c92049d2494c7c5bd54b0
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47216347"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="02e44-102">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="02e44-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="02e44-103">Schemat ustawień kryptografii zawiera elementy, które określają sposób mapowania przyjazne nazwy algorytmu na klasy, które implementują algorytmy kryptograficzne.</span><span class="sxs-lookup"><span data-stu-id="02e44-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
 [<span data-ttu-id="02e44-104">**\<Konfiguracja >**</span><span class="sxs-lookup"><span data-stu-id="02e44-104">**\<configuration>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="02e44-105">**\<mscorlib >**</span><span class="sxs-lookup"><span data-stu-id="02e44-105">**\<mscorlib>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)  
  
 [<span data-ttu-id="02e44-106">**\<cryptographysettings — >**</span><span class="sxs-lookup"><span data-stu-id="02e44-106">**\<cryptographySettings>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)  
  
 [<span data-ttu-id="02e44-107">**\<cryptonamemapping — >**</span><span class="sxs-lookup"><span data-stu-id="02e44-107">**\<cryptoNameMapping>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)  
  
 [<span data-ttu-id="02e44-108">**\<cryptoclasses — >**</span><span class="sxs-lookup"><span data-stu-id="02e44-108">**\<cryptoClasses>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)  
  
 [<span data-ttu-id="02e44-109">**\<cryptoclass — >**</span><span class="sxs-lookup"><span data-stu-id="02e44-109">**\<cryptoClass>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)  
  
 [<span data-ttu-id="02e44-110">**\<nameentry — >**</span><span class="sxs-lookup"><span data-stu-id="02e44-110">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)  
  
 [<span data-ttu-id="02e44-111">**\<oidmap — >**</span><span class="sxs-lookup"><span data-stu-id="02e44-111">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)  
  
 [<span data-ttu-id="02e44-112">**\<oidentry — >**</span><span class="sxs-lookup"><span data-stu-id="02e44-112">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)  
  
|<span data-ttu-id="02e44-113">Element</span><span class="sxs-lookup"><span data-stu-id="02e44-113">Element</span></span>|<span data-ttu-id="02e44-114">Opis</span><span class="sxs-lookup"><span data-stu-id="02e44-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02e44-115">**\<cryptoclasses —**></span><span class="sxs-lookup"><span data-stu-id="02e44-115">**\<cryptoClasses**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)|<span data-ttu-id="02e44-116">Zawiera listę klas kryptografii, które mają mapowanie do przyjazną nazwę w  **\<nameentry — >** elementu.</span><span class="sxs-lookup"><span data-stu-id="02e44-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="02e44-117">**\<cryptoclass —**></span><span class="sxs-lookup"><span data-stu-id="02e44-117">**\<cryptoClass**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|<span data-ttu-id="02e44-118">Zawiera klasy kryptografii, która ma mapowania do przyjazną nazwę w  **\<nameentry — >** elementu.</span><span class="sxs-lookup"><span data-stu-id="02e44-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="02e44-119">**\<cryptographysettings —**></span><span class="sxs-lookup"><span data-stu-id="02e44-119">**\<cryptographySettings**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)|<span data-ttu-id="02e44-120">Zawiera ustawienia szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="02e44-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="02e44-121">**\<cryptonamemapping —**></span><span class="sxs-lookup"><span data-stu-id="02e44-121">**\<cryptoNameMapping**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|<span data-ttu-id="02e44-122">Zawiera mapowania klasy przyjazne nazwy.</span><span class="sxs-lookup"><span data-stu-id="02e44-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="02e44-123">**\<mscorlib >** element ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="02e44-123">**\<mscorlib>** element for cryptography settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="02e44-124">Zawiera  **\<cryptographysettings — >** elementu.</span><span class="sxs-lookup"><span data-stu-id="02e44-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="02e44-125">**\<nameentry — >**</span><span class="sxs-lookup"><span data-stu-id="02e44-125">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)|<span data-ttu-id="02e44-126">Mapuje nazwę klasy na nazwę algorytmu przyjazna, która umożliwia jednej klasy mają wiele przyjazne nazwy.</span><span class="sxs-lookup"><span data-stu-id="02e44-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="02e44-127">**\<oidentry — >**</span><span class="sxs-lookup"><span data-stu-id="02e44-127">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|<span data-ttu-id="02e44-128">Mapuje ASN.1 identyfikator obiektu (OID) przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="02e44-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="02e44-129">**\<oidmap — >**</span><span class="sxs-lookup"><span data-stu-id="02e44-129">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|<span data-ttu-id="02e44-130">Zawiera identyfikator OID ASN.1 mapowania do klas.</span><span class="sxs-lookup"><span data-stu-id="02e44-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="02e44-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="02e44-131">See Also</span></span>  
 [<span data-ttu-id="02e44-132">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="02e44-132">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="02e44-133">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="02e44-133">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)

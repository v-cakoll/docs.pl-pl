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
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47083707"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="48b14-102">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="48b14-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="48b14-103">Schemat ustawień kryptografii zawiera elementy, które określają sposób mapowania przyjazne nazwy algorytmu na klasy, które implementują algorytmy kryptograficzne.</span><span class="sxs-lookup"><span data-stu-id="48b14-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
 [<span data-ttu-id="48b14-104">**\<Konfiguracja >**</span><span class="sxs-lookup"><span data-stu-id="48b14-104">**\<configuration>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="48b14-105">**\<mscorlib >**</span><span class="sxs-lookup"><span data-stu-id="48b14-105">**\<mscorlib>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)  
  
 [<span data-ttu-id="48b14-106">**\<cryptographysettings — >**</span><span class="sxs-lookup"><span data-stu-id="48b14-106">**\<cryptographySettings>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)  
  
 [<span data-ttu-id="48b14-107">**\<cryptonamemapping — >**</span><span class="sxs-lookup"><span data-stu-id="48b14-107">**\<cryptoNameMapping>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)  
  
 [<span data-ttu-id="48b14-108">**\<cryptoclasses — >**</span><span class="sxs-lookup"><span data-stu-id="48b14-108">**\<cryptoClasses>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)  
  
 [<span data-ttu-id="48b14-109">**\<cryptoclass — >**</span><span class="sxs-lookup"><span data-stu-id="48b14-109">**\<cryptoClass>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)  
  
 [<span data-ttu-id="48b14-110">**\<nameentry — >**</span><span class="sxs-lookup"><span data-stu-id="48b14-110">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)  
  
 [<span data-ttu-id="48b14-111">**\<oidmap — >**</span><span class="sxs-lookup"><span data-stu-id="48b14-111">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)  
  
 [<span data-ttu-id="48b14-112">**\<oidentry — >**</span><span class="sxs-lookup"><span data-stu-id="48b14-112">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)  
  
|<span data-ttu-id="48b14-113">Element</span><span class="sxs-lookup"><span data-stu-id="48b14-113">Element</span></span>|<span data-ttu-id="48b14-114">Opis</span><span class="sxs-lookup"><span data-stu-id="48b14-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="48b14-115">**\<cryptoclasses —**></span><span class="sxs-lookup"><span data-stu-id="48b14-115">**\<cryptoClasses**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)|<span data-ttu-id="48b14-116">Zawiera listę klas kryptografii, które mają mapowanie do przyjazną nazwę w  **\<nameentry — >** elementu.</span><span class="sxs-lookup"><span data-stu-id="48b14-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="48b14-117">**\<cryptoclass —**></span><span class="sxs-lookup"><span data-stu-id="48b14-117">**\<cryptoClass**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|<span data-ttu-id="48b14-118">Zawiera klasy kryptografii, która ma mapowania do przyjazną nazwę w  **\<nameentry — >** elementu.</span><span class="sxs-lookup"><span data-stu-id="48b14-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="48b14-119">**\<cryptographysettings —**></span><span class="sxs-lookup"><span data-stu-id="48b14-119">**\<cryptographySettings**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)|<span data-ttu-id="48b14-120">Zawiera ustawienia szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="48b14-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="48b14-121">**\<cryptonamemapping —**></span><span class="sxs-lookup"><span data-stu-id="48b14-121">**\<cryptoNameMapping**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|<span data-ttu-id="48b14-122">Zawiera mapowania klasy przyjazne nazwy.</span><span class="sxs-lookup"><span data-stu-id="48b14-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="48b14-123">**\<mscorlib >** element ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="48b14-123">**\<mscorlib>** element for cryptography settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="48b14-124">Zawiera  **\<cryptographysettings — >** elementu.</span><span class="sxs-lookup"><span data-stu-id="48b14-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="48b14-125">**\<nameentry — >**</span><span class="sxs-lookup"><span data-stu-id="48b14-125">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)|<span data-ttu-id="48b14-126">Mapuje nazwę klasy na nazwę algorytmu przyjazna, która umożliwia jednej klasy mają wiele przyjazne nazwy.</span><span class="sxs-lookup"><span data-stu-id="48b14-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="48b14-127">**\<oidentry — >**</span><span class="sxs-lookup"><span data-stu-id="48b14-127">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|<span data-ttu-id="48b14-128">Mapuje ASN.1 identyfikator obiektu (OID) przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="48b14-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="48b14-129">**\<oidmap — >**</span><span class="sxs-lookup"><span data-stu-id="48b14-129">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|<span data-ttu-id="48b14-130">Zawiera identyfikator OID ASN.1 mapowania do klas.</span><span class="sxs-lookup"><span data-stu-id="48b14-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="48b14-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="48b14-131">See Also</span></span>  
 [<span data-ttu-id="48b14-132">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="48b14-132">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="48b14-133">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="48b14-133">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)

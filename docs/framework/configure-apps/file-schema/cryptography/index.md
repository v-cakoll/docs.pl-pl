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
ms.openlocfilehash: 9bf94c28522d42e1a763726469cf9b1a03ccd86e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50196755"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="e7a66-102">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="e7a66-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="e7a66-103">Schemat ustawień kryptografii zawiera elementy, które określają sposób mapowania przyjazne nazwy algorytmu na klasy, które implementują algorytmy kryptograficzne.</span><span class="sxs-lookup"><span data-stu-id="e7a66-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
 [<span data-ttu-id="e7a66-104">**\<Konfiguracja >**</span><span class="sxs-lookup"><span data-stu-id="e7a66-104">**\<configuration>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="e7a66-105">**\<mscorlib >**</span><span class="sxs-lookup"><span data-stu-id="e7a66-105">**\<mscorlib>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)  
  
 [<span data-ttu-id="e7a66-106">**\<cryptographysettings — >**</span><span class="sxs-lookup"><span data-stu-id="e7a66-106">**\<cryptographySettings>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)  
  
 [<span data-ttu-id="e7a66-107">**\<cryptonamemapping — >**</span><span class="sxs-lookup"><span data-stu-id="e7a66-107">**\<cryptoNameMapping>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)  
  
 [<span data-ttu-id="e7a66-108">**\<cryptoclasses — >**</span><span class="sxs-lookup"><span data-stu-id="e7a66-108">**\<cryptoClasses>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)  
  
 [<span data-ttu-id="e7a66-109">**\<cryptoclass — >**</span><span class="sxs-lookup"><span data-stu-id="e7a66-109">**\<cryptoClass>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)  
  
 [<span data-ttu-id="e7a66-110">**\<nameentry — >**</span><span class="sxs-lookup"><span data-stu-id="e7a66-110">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)  
  
 [<span data-ttu-id="e7a66-111">**\<oidmap — >**</span><span class="sxs-lookup"><span data-stu-id="e7a66-111">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)  
  
 [<span data-ttu-id="e7a66-112">**\<oidentry — >**</span><span class="sxs-lookup"><span data-stu-id="e7a66-112">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)  
  
|<span data-ttu-id="e7a66-113">Element</span><span class="sxs-lookup"><span data-stu-id="e7a66-113">Element</span></span>|<span data-ttu-id="e7a66-114">Opis</span><span class="sxs-lookup"><span data-stu-id="e7a66-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e7a66-115">**\<cryptoclasses —**></span><span class="sxs-lookup"><span data-stu-id="e7a66-115">**\<cryptoClasses**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)|<span data-ttu-id="e7a66-116">Zawiera listę klas kryptografii, które mają mapowanie do przyjazną nazwę w  **\<nameentry — >** elementu.</span><span class="sxs-lookup"><span data-stu-id="e7a66-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="e7a66-117">**\<cryptoclass —**></span><span class="sxs-lookup"><span data-stu-id="e7a66-117">**\<cryptoClass**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|<span data-ttu-id="e7a66-118">Zawiera klasy kryptografii, która ma mapowania do przyjazną nazwę w  **\<nameentry — >** elementu.</span><span class="sxs-lookup"><span data-stu-id="e7a66-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="e7a66-119">**\<cryptographysettings —**></span><span class="sxs-lookup"><span data-stu-id="e7a66-119">**\<cryptographySettings**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)|<span data-ttu-id="e7a66-120">Zawiera ustawienia szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="e7a66-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="e7a66-121">**\<cryptonamemapping —**></span><span class="sxs-lookup"><span data-stu-id="e7a66-121">**\<cryptoNameMapping**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|<span data-ttu-id="e7a66-122">Zawiera mapowania klasy przyjazne nazwy.</span><span class="sxs-lookup"><span data-stu-id="e7a66-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="e7a66-123">**\<mscorlib >** element ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="e7a66-123">**\<mscorlib>** element for cryptography settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="e7a66-124">Zawiera  **\<cryptographysettings — >** elementu.</span><span class="sxs-lookup"><span data-stu-id="e7a66-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="e7a66-125">**\<nameentry — >**</span><span class="sxs-lookup"><span data-stu-id="e7a66-125">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)|<span data-ttu-id="e7a66-126">Mapuje nazwę klasy na nazwę algorytmu przyjazna, która umożliwia jednej klasy mają wiele przyjazne nazwy.</span><span class="sxs-lookup"><span data-stu-id="e7a66-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="e7a66-127">**\<oidentry — >**</span><span class="sxs-lookup"><span data-stu-id="e7a66-127">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|<span data-ttu-id="e7a66-128">Mapuje ASN.1 identyfikator obiektu (OID) przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="e7a66-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="e7a66-129">**\<oidmap — >**</span><span class="sxs-lookup"><span data-stu-id="e7a66-129">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|<span data-ttu-id="e7a66-130">Zawiera identyfikator OID ASN.1 mapowania do klas.</span><span class="sxs-lookup"><span data-stu-id="e7a66-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7a66-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7a66-131">See Also</span></span>  
- [<span data-ttu-id="e7a66-132">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e7a66-132">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="e7a66-133">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="e7a66-133">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)

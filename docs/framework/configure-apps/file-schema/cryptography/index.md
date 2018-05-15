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
manager: markl
ms.openlocfilehash: b7f41bc477f8d8095bf73859c02b7e2fc2443c14
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="1ad3b-102">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="1ad3b-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="1ad3b-103">Schemat ustawień kryptografii zawiera elementy, które określają sposób odwzorowywania algorytm przyjaznej nazwy klasy, które implementują algorytmów kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="1ad3b-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
 [<span data-ttu-id="1ad3b-104">**\<Konfiguracja >**</span><span class="sxs-lookup"><span data-stu-id="1ad3b-104">**\<configuration>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="1ad3b-105">**\<mscorlib >**</span><span class="sxs-lookup"><span data-stu-id="1ad3b-105">**\<mscorlib>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)  
  
 [<span data-ttu-id="1ad3b-106">**\<cryptographysettings — >**</span><span class="sxs-lookup"><span data-stu-id="1ad3b-106">**\<cryptographySettings>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)  
  
 [<span data-ttu-id="1ad3b-107">**\<cryptonamemapping — >**</span><span class="sxs-lookup"><span data-stu-id="1ad3b-107">**\<cryptoNameMapping>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)  
  
 [<span data-ttu-id="1ad3b-108">**\<cryptoclasses — >**</span><span class="sxs-lookup"><span data-stu-id="1ad3b-108">**\<cryptoClasses>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)  
  
 [<span data-ttu-id="1ad3b-109">**\<cryptoclass — >**</span><span class="sxs-lookup"><span data-stu-id="1ad3b-109">**\<cryptoClass>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)  
  
 [<span data-ttu-id="1ad3b-110">**\<nameentry — >**</span><span class="sxs-lookup"><span data-stu-id="1ad3b-110">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)  
  
 [<span data-ttu-id="1ad3b-111">**\<oidmap — >**</span><span class="sxs-lookup"><span data-stu-id="1ad3b-111">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)  
  
 [<span data-ttu-id="1ad3b-112">**\<oidentry — >**</span><span class="sxs-lookup"><span data-stu-id="1ad3b-112">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)  
  
|<span data-ttu-id="1ad3b-113">Element</span><span class="sxs-lookup"><span data-stu-id="1ad3b-113">Element</span></span>|<span data-ttu-id="1ad3b-114">Opis</span><span class="sxs-lookup"><span data-stu-id="1ad3b-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1ad3b-115">**\<cryptoclasses —**></span><span class="sxs-lookup"><span data-stu-id="1ad3b-115">**\<cryptoClasses**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)|<span data-ttu-id="1ad3b-116">Zawiera listę klasy kryptografii, które ma mapowania do przyjazną nazwę w  **\<nameentry — >** elementu.</span><span class="sxs-lookup"><span data-stu-id="1ad3b-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="1ad3b-117">**\<cryptoclass —**></span><span class="sxs-lookup"><span data-stu-id="1ad3b-117">**\<cryptoClass**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|<span data-ttu-id="1ad3b-118">Zawiera klasy kryptografii, która ma mapowania przyjazną nazwę w  **\<nameentry — >** elementu.</span><span class="sxs-lookup"><span data-stu-id="1ad3b-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="1ad3b-119">**\<cryptographysettings —**></span><span class="sxs-lookup"><span data-stu-id="1ad3b-119">**\<cryptographySettings**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)|<span data-ttu-id="1ad3b-120">Zawiera ustawienia szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="1ad3b-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="1ad3b-121">**\<cryptonamemapping —**></span><span class="sxs-lookup"><span data-stu-id="1ad3b-121">**\<cryptoNameMapping**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|<span data-ttu-id="1ad3b-122">Zawiera mapowania klasy przyjazne nazwy.</span><span class="sxs-lookup"><span data-stu-id="1ad3b-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="1ad3b-123">**\<mscorlib >** element ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="1ad3b-123">**\<mscorlib>** element for cryptography settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="1ad3b-124">Zawiera  **\<cryptographysettings — >** elementu.</span><span class="sxs-lookup"><span data-stu-id="1ad3b-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="1ad3b-125">**\<nameentry — >**</span><span class="sxs-lookup"><span data-stu-id="1ad3b-125">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)|<span data-ttu-id="1ad3b-126">Mapuje nazwę klasy na nazwę algorytmu przyjazną, która umożliwia jedną klasę do mają wiele przyjaznej nazwy.</span><span class="sxs-lookup"><span data-stu-id="1ad3b-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="1ad3b-127">**\<oidentry — >**</span><span class="sxs-lookup"><span data-stu-id="1ad3b-127">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|<span data-ttu-id="1ad3b-128">Mapuje ASN.1 identyfikatora obiektu (OID) przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="1ad3b-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="1ad3b-129">**\<oidmap — >**</span><span class="sxs-lookup"><span data-stu-id="1ad3b-129">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|<span data-ttu-id="1ad3b-130">Zawiera identyfikator OID ASN.1 mapowania do klasy.</span><span class="sxs-lookup"><span data-stu-id="1ad3b-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1ad3b-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ad3b-131">See Also</span></span>  
 [<span data-ttu-id="1ad3b-132">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1ad3b-132">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="1ad3b-133">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="1ad3b-133">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)

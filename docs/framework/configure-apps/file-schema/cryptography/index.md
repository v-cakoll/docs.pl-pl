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
ms.openlocfilehash: 00b04cc2175f4bb4cc0b74602cd3c26f4a4e342f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184460"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="c0cff-102">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="c0cff-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="c0cff-103">Schemat ustawień kryptografii zawiera elementy, które określają sposób mapowania przyjazne nazwy algorytmu na klasy, które implementują algorytmy kryptograficzne.</span><span class="sxs-lookup"><span data-stu-id="c0cff-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
 [<span data-ttu-id="c0cff-104">**\<Konfiguracja >**</span><span class="sxs-lookup"><span data-stu-id="c0cff-104">**\<configuration>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="c0cff-105">**\<mscorlib>**</span><span class="sxs-lookup"><span data-stu-id="c0cff-105">**\<mscorlib>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)  
  
 [<span data-ttu-id="c0cff-106">**\<cryptographySettings>**</span><span class="sxs-lookup"><span data-stu-id="c0cff-106">**\<cryptographySettings>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)  
  
 [<span data-ttu-id="c0cff-107">**\<cryptoNameMapping>**</span><span class="sxs-lookup"><span data-stu-id="c0cff-107">**\<cryptoNameMapping>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)  
  
 [<span data-ttu-id="c0cff-108">**\<cryptoClasses>**</span><span class="sxs-lookup"><span data-stu-id="c0cff-108">**\<cryptoClasses>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)  
  
 [<span data-ttu-id="c0cff-109">**\<cryptoClass>**</span><span class="sxs-lookup"><span data-stu-id="c0cff-109">**\<cryptoClass>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)  
  
 [<span data-ttu-id="c0cff-110">**\<nameEntry>**</span><span class="sxs-lookup"><span data-stu-id="c0cff-110">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)  
  
 [<span data-ttu-id="c0cff-111">**\<oidMap>**</span><span class="sxs-lookup"><span data-stu-id="c0cff-111">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)  
  
 [<span data-ttu-id="c0cff-112">**\<oidEntry>**</span><span class="sxs-lookup"><span data-stu-id="c0cff-112">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)  
  
|<span data-ttu-id="c0cff-113">Element</span><span class="sxs-lookup"><span data-stu-id="c0cff-113">Element</span></span>|<span data-ttu-id="c0cff-114">Opis</span><span class="sxs-lookup"><span data-stu-id="c0cff-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0cff-115">**\<cryptoClasses**></span><span class="sxs-lookup"><span data-stu-id="c0cff-115">**\<cryptoClasses**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)|<span data-ttu-id="c0cff-116">Zawiera listę klas kryptografii, które mają mapowanie do przyjazną nazwę w  **\<nameentry — >** elementu.</span><span class="sxs-lookup"><span data-stu-id="c0cff-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="c0cff-117">**\<cryptoClass**></span><span class="sxs-lookup"><span data-stu-id="c0cff-117">**\<cryptoClass**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|<span data-ttu-id="c0cff-118">Zawiera klasy kryptografii, która ma mapowania do przyjazną nazwę w  **\<nameentry — >** elementu.</span><span class="sxs-lookup"><span data-stu-id="c0cff-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="c0cff-119">**\<cryptographySettings**></span><span class="sxs-lookup"><span data-stu-id="c0cff-119">**\<cryptographySettings**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)|<span data-ttu-id="c0cff-120">Zawiera ustawienia szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="c0cff-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="c0cff-121">**\<cryptoNameMapping**></span><span class="sxs-lookup"><span data-stu-id="c0cff-121">**\<cryptoNameMapping**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|<span data-ttu-id="c0cff-122">Zawiera mapowania klasy przyjazne nazwy.</span><span class="sxs-lookup"><span data-stu-id="c0cff-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="c0cff-123">**\<mscorlib >** element ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="c0cff-123">**\<mscorlib>** element for cryptography settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="c0cff-124">Zawiera  **\<cryptographysettings — >** elementu.</span><span class="sxs-lookup"><span data-stu-id="c0cff-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="c0cff-125">**\<nameEntry>**</span><span class="sxs-lookup"><span data-stu-id="c0cff-125">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)|<span data-ttu-id="c0cff-126">Mapuje nazwę klasy na nazwę algorytmu przyjazna, która umożliwia jednej klasy mają wiele przyjazne nazwy.</span><span class="sxs-lookup"><span data-stu-id="c0cff-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="c0cff-127">**\<oidEntry>**</span><span class="sxs-lookup"><span data-stu-id="c0cff-127">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|<span data-ttu-id="c0cff-128">Mapuje ASN.1 identyfikator obiektu (OID) przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="c0cff-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="c0cff-129">**\<oidMap>**</span><span class="sxs-lookup"><span data-stu-id="c0cff-129">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|<span data-ttu-id="c0cff-130">Zawiera identyfikator OID ASN.1 mapowania do klas.</span><span class="sxs-lookup"><span data-stu-id="c0cff-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c0cff-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c0cff-131">See also</span></span>

- [<span data-ttu-id="c0cff-132">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c0cff-132">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="c0cff-133">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="c0cff-133">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)

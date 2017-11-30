---
title: "Schemat ustawień kryptografii"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration schema [.NET Framework], cryptography
- elements [.NET Framework], cryptography
- schema configuration settings
- cryptography, settings schema
- cryptography, mapping algorithm names
- configuration sections [.NET Framework]
- configuration settings [.NET Framework], cryptography
ms.assetid: 1f55050a-b2a3-4868-a3c0-da20826150f3
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c7d1e193236528c96e8253668c742883090ae188
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="471fc-102">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="471fc-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="471fc-103">Schemat ustawień kryptografii zawiera elementy, które określają sposób odwzorowywania algorytm przyjaznej nazwy klasy, które implementują algorytmów kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="471fc-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
 [<span data-ttu-id="471fc-104">**\<Konfiguracja >**</span><span class="sxs-lookup"><span data-stu-id="471fc-104">**\<configuration>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="471fc-105">**\<mscorlib >**</span><span class="sxs-lookup"><span data-stu-id="471fc-105">**\<mscorlib>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)  
  
 [<span data-ttu-id="471fc-106">**\<cryptographysettings — >**</span><span class="sxs-lookup"><span data-stu-id="471fc-106">**\<cryptographySettings>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)  
  
 [<span data-ttu-id="471fc-107">**\<cryptonamemapping — >**</span><span class="sxs-lookup"><span data-stu-id="471fc-107">**\<cryptoNameMapping>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)  
  
 [<span data-ttu-id="471fc-108">**\<cryptoclasses — >**</span><span class="sxs-lookup"><span data-stu-id="471fc-108">**\<cryptoClasses>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)  
  
 [<span data-ttu-id="471fc-109">**\<cryptoclass — >**</span><span class="sxs-lookup"><span data-stu-id="471fc-109">**\<cryptoClass>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)  
  
 [<span data-ttu-id="471fc-110">**\<nameentry — >**</span><span class="sxs-lookup"><span data-stu-id="471fc-110">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)  
  
 [<span data-ttu-id="471fc-111">**\<oidmap — >**</span><span class="sxs-lookup"><span data-stu-id="471fc-111">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)  
  
 [<span data-ttu-id="471fc-112">**\<oidentry — >**</span><span class="sxs-lookup"><span data-stu-id="471fc-112">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)  
  
|<span data-ttu-id="471fc-113">Element</span><span class="sxs-lookup"><span data-stu-id="471fc-113">Element</span></span>|<span data-ttu-id="471fc-114">Opis</span><span class="sxs-lookup"><span data-stu-id="471fc-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="471fc-115">**\<cryptoclasses —**></span><span class="sxs-lookup"><span data-stu-id="471fc-115">**\<cryptoClasses**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)|<span data-ttu-id="471fc-116">Zawiera listę klasy kryptografii, które ma mapowania do przyjazną nazwę w  **\<nameentry — >** elementu.</span><span class="sxs-lookup"><span data-stu-id="471fc-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="471fc-117">**\<cryptoclass —**></span><span class="sxs-lookup"><span data-stu-id="471fc-117">**\<cryptoClass**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|<span data-ttu-id="471fc-118">Zawiera klasy kryptografii, która ma mapowania przyjazną nazwę w  **\<nameentry — >** elementu.</span><span class="sxs-lookup"><span data-stu-id="471fc-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="471fc-119">**\<cryptographysettings —**></span><span class="sxs-lookup"><span data-stu-id="471fc-119">**\<cryptographySettings**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)|<span data-ttu-id="471fc-120">Zawiera ustawienia szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="471fc-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="471fc-121">**\<cryptonamemapping —**></span><span class="sxs-lookup"><span data-stu-id="471fc-121">**\<cryptoNameMapping**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|<span data-ttu-id="471fc-122">Zawiera mapowania klasy przyjazne nazwy.</span><span class="sxs-lookup"><span data-stu-id="471fc-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="471fc-123">**\<mscorlib >** element ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="471fc-123">**\<mscorlib>** element for cryptography settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="471fc-124">Zawiera  **\<cryptographysettings — >** elementu.</span><span class="sxs-lookup"><span data-stu-id="471fc-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="471fc-125">**\<nameentry — >**</span><span class="sxs-lookup"><span data-stu-id="471fc-125">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)|<span data-ttu-id="471fc-126">Mapuje nazwę klasy na nazwę algorytmu przyjazną, która umożliwia jedną klasę do mają wiele przyjaznej nazwy.</span><span class="sxs-lookup"><span data-stu-id="471fc-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="471fc-127">**\<oidentry — >**</span><span class="sxs-lookup"><span data-stu-id="471fc-127">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|<span data-ttu-id="471fc-128">Mapuje ASN.1 identyfikatora obiektu (OID) przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="471fc-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="471fc-129">**\<oidmap — >**</span><span class="sxs-lookup"><span data-stu-id="471fc-129">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|<span data-ttu-id="471fc-130">Zawiera identyfikator OID ASN.1 mapowania do klasy.</span><span class="sxs-lookup"><span data-stu-id="471fc-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="471fc-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="471fc-131">See Also</span></span>  
 [<span data-ttu-id="471fc-132">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="471fc-132">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="471fc-133">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="471fc-133">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)

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
ms.openlocfilehash: a7964d01905be4e3dd6e8149e5533e9a2cfd9a71
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927631"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="a2dab-102">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="a2dab-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="a2dab-103">Schemat ustawień kryptografii zawiera elementy, które określają sposób mapowania przyjaznych nazw algorytmów na klasy implementujące algorytmy kryptografii.</span><span class="sxs-lookup"><span data-stu-id="a2dab-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
 [<span data-ttu-id="a2dab-104"> **\<> konfiguracji**</span><span class="sxs-lookup"><span data-stu-id="a2dab-104">**\<configuration>**</span></span>](../configuration-element.md)  
  
 [<span data-ttu-id="a2dab-105"> **\<mscorlib>** </span><span class="sxs-lookup"><span data-stu-id="a2dab-105">**\<mscorlib>**</span></span>](mscorlib-element-for-cryptography-settings.md)  
  
 [<span data-ttu-id="a2dab-106"> **\<cryptographySettings>** </span><span class="sxs-lookup"><span data-stu-id="a2dab-106">**\<cryptographySettings>**</span></span>](cryptographysettings-element.md)  
  
 [<span data-ttu-id="a2dab-107"> **\<cryptoNameMapping>** </span><span class="sxs-lookup"><span data-stu-id="a2dab-107">**\<cryptoNameMapping>**</span></span>](cryptonamemapping-element.md)  
  
 [<span data-ttu-id="a2dab-108"> **\<cryptoClasses>** </span><span class="sxs-lookup"><span data-stu-id="a2dab-108">**\<cryptoClasses>**</span></span>](cryptoclasses-element.md)  
  
 [<span data-ttu-id="a2dab-109"> **\<cryptoClass>** </span><span class="sxs-lookup"><span data-stu-id="a2dab-109">**\<cryptoClass>**</span></span>](cryptoclass-element.md)  
  
 [<span data-ttu-id="a2dab-110"> **\<nameEntry >** </span><span class="sxs-lookup"><span data-stu-id="a2dab-110">**\<nameEntry>**</span></span>](nameentry-element.md)  
  
 [<span data-ttu-id="a2dab-111"> **\<oidMap>** </span><span class="sxs-lookup"><span data-stu-id="a2dab-111">**\<oidMap>**</span></span>](oidmap-element.md)  
  
 [<span data-ttu-id="a2dab-112"> **\<oidEntry>** </span><span class="sxs-lookup"><span data-stu-id="a2dab-112">**\<oidEntry>**</span></span>](oidentry-element.md)  
  
|<span data-ttu-id="a2dab-113">Element</span><span class="sxs-lookup"><span data-stu-id="a2dab-113">Element</span></span>|<span data-ttu-id="a2dab-114">Opis</span><span class="sxs-lookup"><span data-stu-id="a2dab-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a2dab-115"> **\<cryptoClasses**></span><span class="sxs-lookup"><span data-stu-id="a2dab-115">**\<cryptoClasses**></span></span>](cryptoclasses-element.md)|<span data-ttu-id="a2dab-116">Zawiera listę klas kryptograficznych, które mają mapowanie do przyjaznej nazwy w  **\<elemencie nameEntry >** .</span><span class="sxs-lookup"><span data-stu-id="a2dab-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="a2dab-117"> **\<cryptoClass**></span><span class="sxs-lookup"><span data-stu-id="a2dab-117">**\<cryptoClass**></span></span>](cryptoclass-element.md)|<span data-ttu-id="a2dab-118">Zawiera klasę kryptografii, która ma mapowanie do przyjaznej nazwy w  **\<elemencie nameEntry >** .</span><span class="sxs-lookup"><span data-stu-id="a2dab-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="a2dab-119"> **\<cryptographySettings**></span><span class="sxs-lookup"><span data-stu-id="a2dab-119">**\<cryptographySettings**></span></span>](cryptographysettings-element.md)|<span data-ttu-id="a2dab-120">Zawiera ustawienia kryptografii.</span><span class="sxs-lookup"><span data-stu-id="a2dab-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="a2dab-121"> **\<cryptoNameMapping**></span><span class="sxs-lookup"><span data-stu-id="a2dab-121">**\<cryptoNameMapping**></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="a2dab-122">Zawiera mapowania klas do przyjaznych nazw.</span><span class="sxs-lookup"><span data-stu-id="a2dab-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="a2dab-123">Element > mscorlib dla ustawień kryptografii  **\<** </span><span class="sxs-lookup"><span data-stu-id="a2dab-123">**\<mscorlib>** element for cryptography settings</span></span>](mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="a2dab-124">Zawiera element **> cryptographySettings.\<**</span><span class="sxs-lookup"><span data-stu-id="a2dab-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="a2dab-125"> **\<nameEntry >** </span><span class="sxs-lookup"><span data-stu-id="a2dab-125">**\<nameEntry>**</span></span>](nameentry-element.md)|<span data-ttu-id="a2dab-126">Mapuje nazwę klasy na przyjazną nazwę algorytmu, która pozwala jednej klasie mieć wiele przyjaznych nazw.</span><span class="sxs-lookup"><span data-stu-id="a2dab-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="a2dab-127"> **\<oidEntry>** </span><span class="sxs-lookup"><span data-stu-id="a2dab-127">**\<oidEntry>**</span></span>](oidentry-element.md)|<span data-ttu-id="a2dab-128">Mapuje identyfikator obiektu ASN. 1 (OID) na przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="a2dab-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="a2dab-129"> **\<oidMap>** </span><span class="sxs-lookup"><span data-stu-id="a2dab-129">**\<oidMap>**</span></span>](oidmap-element.md)|<span data-ttu-id="a2dab-130">Zawiera mapowania identyfikatorów OID ASN. 1 do klas.</span><span class="sxs-lookup"><span data-stu-id="a2dab-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a2dab-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a2dab-131">See also</span></span>

- [<span data-ttu-id="a2dab-132">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a2dab-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a2dab-133">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="a2dab-133">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)

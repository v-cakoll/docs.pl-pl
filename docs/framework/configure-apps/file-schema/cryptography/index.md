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
ms.openlocfilehash: 474c3274bfba6803ebb17289f138251d755250e4
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699803"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="fa317-102">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="fa317-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="fa317-103">Schemat ustawień kryptografii zawiera elementy, które określają sposób mapowania przyjaznych nazw algorytmów na klasy implementujące algorytmy kryptografii.</span><span class="sxs-lookup"><span data-stu-id="fa317-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
[<span data-ttu-id="fa317-104"> **@no__t — 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="fa317-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="fa317-105">&nbsp; @ no__t-1[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="fa317-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="fa317-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<cryptographySettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="fa317-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>  
<span data-ttu-id="fa317-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<cryptoNameMapping >** ](cryptonamemapping-element.md)</span><span class="sxs-lookup"><span data-stu-id="fa317-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span></span>  
<span data-ttu-id="fa317-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0cryptoClasses >** ](cryptoclasses-element.md)</span><span class="sxs-lookup"><span data-stu-id="fa317-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)</span></span>  
<span data-ttu-id="fa317-109">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9[ **&nbsp;2cryptoClass >** ](cryptoclass-element.md)</span><span class="sxs-lookup"><span data-stu-id="fa317-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClass>**](cryptoclass-element.md)</span></span>  
<span data-ttu-id="fa317-110">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0nameEntry >** ](nameentry-element.md)</span><span class="sxs-lookup"><span data-stu-id="fa317-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<nameEntry>**](nameentry-element.md)</span></span>  
<span data-ttu-id="fa317-111">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<oidMap >** ](oidmap-element.md)</span><span class="sxs-lookup"><span data-stu-id="fa317-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)</span></span>  
<span data-ttu-id="fa317-112">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6[ **\<oidEntry >** ](oidentry-element.md)</span><span class="sxs-lookup"><span data-stu-id="fa317-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidEntry>**](oidentry-element.md)</span></span>  
  
|<span data-ttu-id="fa317-113">Element</span><span class="sxs-lookup"><span data-stu-id="fa317-113">Element</span></span>|<span data-ttu-id="fa317-114">Opis</span><span class="sxs-lookup"><span data-stu-id="fa317-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa317-115"> **\<cryptoClasses**></span><span class="sxs-lookup"><span data-stu-id="fa317-115">**\<cryptoClasses**></span></span>](cryptoclasses-element.md)|<span data-ttu-id="fa317-116">Zawiera listę klas kryptograficznych, które mają mapowanie do przyjaznej nazwy w elemencie **\<nameEntry >** .</span><span class="sxs-lookup"><span data-stu-id="fa317-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="fa317-117"> **\<cryptoClass**></span><span class="sxs-lookup"><span data-stu-id="fa317-117">**\<cryptoClass**></span></span>](cryptoclass-element.md)|<span data-ttu-id="fa317-118">Zawiera klasę kryptografii, która ma mapowanie do przyjaznej nazwy w elemencie **\<nameEntry >** .</span><span class="sxs-lookup"><span data-stu-id="fa317-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="fa317-119"> **\<cryptographySettings**></span><span class="sxs-lookup"><span data-stu-id="fa317-119">**\<cryptographySettings**></span></span>](cryptographysettings-element.md)|<span data-ttu-id="fa317-120">Zawiera ustawienia kryptografii.</span><span class="sxs-lookup"><span data-stu-id="fa317-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="fa317-121"> **\<cryptoNameMapping**></span><span class="sxs-lookup"><span data-stu-id="fa317-121">**\<cryptoNameMapping**></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="fa317-122">Zawiera mapowania klas do przyjaznych nazw.</span><span class="sxs-lookup"><span data-stu-id="fa317-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="fa317-123"> **\<mscorlib >** elementu dla ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="fa317-123">**\<mscorlib>** element for cryptography settings</span></span>](mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="fa317-124">Zawiera element **\<cryptographySettings >** .</span><span class="sxs-lookup"><span data-stu-id="fa317-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="fa317-125"> **@no__t — 2nameEntry >** </span><span class="sxs-lookup"><span data-stu-id="fa317-125">**\<nameEntry>**</span></span>](nameentry-element.md)|<span data-ttu-id="fa317-126">Mapuje nazwę klasy na przyjazną nazwę algorytmu, która pozwala jednej klasie mieć wiele przyjaznych nazw.</span><span class="sxs-lookup"><span data-stu-id="fa317-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="fa317-127"> **@no__t — 2oidEntry >** </span><span class="sxs-lookup"><span data-stu-id="fa317-127">**\<oidEntry>**</span></span>](oidentry-element.md)|<span data-ttu-id="fa317-128">Mapuje identyfikator obiektu ASN. 1 (OID) na przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="fa317-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="fa317-129"> **@no__t — 2oidMap >** </span><span class="sxs-lookup"><span data-stu-id="fa317-129">**\<oidMap>**</span></span>](oidmap-element.md)|<span data-ttu-id="fa317-130">Zawiera mapowania identyfikatorów OID ASN. 1 do klas.</span><span class="sxs-lookup"><span data-stu-id="fa317-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fa317-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fa317-131">See also</span></span>

- [<span data-ttu-id="fa317-132">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="fa317-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="fa317-133">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="fa317-133">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)

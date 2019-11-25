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
ms.openlocfilehash: c632a15552c8ba5743aac1309098b7d7ef949bbd
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088004"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="ad31b-102">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="ad31b-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="ad31b-103">Schemat ustawień kryptografii zawiera elementy, które określają sposób mapowania przyjaznych nazw algorytmów na klasy implementujące algorytmy kryptografii.</span><span class="sxs-lookup"><span data-stu-id="ad31b-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
<span data-ttu-id="ad31b-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="ad31b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ad31b-105">&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="ad31b-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>\
<span data-ttu-id="ad31b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptographySettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="ad31b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>\
<span data-ttu-id="ad31b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptoNameMapping**](cryptonamemapping-element.md) ></span><span class="sxs-lookup"><span data-stu-id="ad31b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span></span>\
<span data-ttu-id="ad31b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptoClasses >** ](cryptoclasses-element.md)</span><span class="sxs-lookup"><span data-stu-id="ad31b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)</span></span>\
<span data-ttu-id="ad31b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptoClass >** ](cryptoclass-element.md)</span><span class="sxs-lookup"><span data-stu-id="ad31b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClass>**](cryptoclass-element.md)</span></span>\
<span data-ttu-id="ad31b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<nameEntry >** ](nameentry-element.md)</span><span class="sxs-lookup"><span data-stu-id="ad31b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<nameEntry>**](nameentry-element.md)</span></span>\
<span data-ttu-id="ad31b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<oidMap**](oidmap-element.md) ></span><span class="sxs-lookup"><span data-stu-id="ad31b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)</span></span>\
<span data-ttu-id="ad31b-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<oidEntry >** ](oidentry-element.md)</span><span class="sxs-lookup"><span data-stu-id="ad31b-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidEntry>**](oidentry-element.md)</span></span>

|<span data-ttu-id="ad31b-113">Element</span><span class="sxs-lookup"><span data-stu-id="ad31b-113">Element</span></span>|<span data-ttu-id="ad31b-114">Opis</span><span class="sxs-lookup"><span data-stu-id="ad31b-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ad31b-115"> **\<cryptoClasses**></span><span class="sxs-lookup"><span data-stu-id="ad31b-115">**\<cryptoClasses**></span></span>](cryptoclasses-element.md)|<span data-ttu-id="ad31b-116">Zawiera listę klas kryptograficznych, które mają mapowanie do przyjaznej nazwy w **\<nameEntry >** elementu.</span><span class="sxs-lookup"><span data-stu-id="ad31b-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="ad31b-117"> **\<cryptoClass**></span><span class="sxs-lookup"><span data-stu-id="ad31b-117">**\<cryptoClass**></span></span>](cryptoclass-element.md)|<span data-ttu-id="ad31b-118">Zawiera klasę kryptografii, która ma mapowanie do przyjaznej nazwy w **\<nameEntry >** elementu.</span><span class="sxs-lookup"><span data-stu-id="ad31b-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="ad31b-119"> **\<cryptographySettings**></span><span class="sxs-lookup"><span data-stu-id="ad31b-119">**\<cryptographySettings**></span></span>](cryptographysettings-element.md)|<span data-ttu-id="ad31b-120">Zawiera ustawienia kryptografii.</span><span class="sxs-lookup"><span data-stu-id="ad31b-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="ad31b-121"> **\<cryptoNameMapping**></span><span class="sxs-lookup"><span data-stu-id="ad31b-121">**\<cryptoNameMapping**></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="ad31b-122">Zawiera mapowania klas do przyjaznych nazw.</span><span class="sxs-lookup"><span data-stu-id="ad31b-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="ad31b-123"> **\<element > mscorlib** dla ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="ad31b-123">**\<mscorlib>** element for cryptography settings</span></span>](mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="ad31b-124">Zawiera element **\<cryptographySettings >** .</span><span class="sxs-lookup"><span data-stu-id="ad31b-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="ad31b-125"> **\<nameEntry >** </span><span class="sxs-lookup"><span data-stu-id="ad31b-125">**\<nameEntry>**</span></span>](nameentry-element.md)|<span data-ttu-id="ad31b-126">Mapuje nazwę klasy na przyjazną nazwę algorytmu, która pozwala jednej klasie mieć wiele przyjaznych nazw.</span><span class="sxs-lookup"><span data-stu-id="ad31b-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="ad31b-127"> **\<oidEntry >** </span><span class="sxs-lookup"><span data-stu-id="ad31b-127">**\<oidEntry>**</span></span>](oidentry-element.md)|<span data-ttu-id="ad31b-128">Mapuje identyfikator obiektu ASN. 1 (OID) na przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="ad31b-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="ad31b-129"> **\<oidMap >** </span><span class="sxs-lookup"><span data-stu-id="ad31b-129">**\<oidMap>**</span></span>](oidmap-element.md)|<span data-ttu-id="ad31b-130">Zawiera mapowania identyfikatorów OID ASN. 1 do klas.</span><span class="sxs-lookup"><span data-stu-id="ad31b-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ad31b-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad31b-131">See also</span></span>

- [<span data-ttu-id="ad31b-132">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ad31b-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ad31b-133">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="ad31b-133">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)

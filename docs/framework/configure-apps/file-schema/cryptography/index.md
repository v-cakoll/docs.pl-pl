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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088004"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="9c22b-102">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="9c22b-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="9c22b-103">Schemat ustawień kryptografii zawiera elementy, które określają sposób mapowania przyjaznych nazw algorytmów na klasy implementujące algorytmy kryptografii.</span><span class="sxs-lookup"><span data-stu-id="9c22b-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClass>**](cryptoclass-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<nameEntry>**](nameentry-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidEntry>**](oidentry-element.md)

|<span data-ttu-id="9c22b-104">Element</span><span class="sxs-lookup"><span data-stu-id="9c22b-104">Element</span></span>|<span data-ttu-id="9c22b-105">Opis</span><span class="sxs-lookup"><span data-stu-id="9c22b-105">Description</span></span>|  
|-------------|-----------------|  
|[**\<cryptoClasses**>](cryptoclasses-element.md)|<span data-ttu-id="9c22b-106">Zawiera listę klas kryptograficznych, które mają mapowanie do przyjaznej nazwy w **\<nameEntry>** elemencie.</span><span class="sxs-lookup"><span data-stu-id="9c22b-106">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[**\<cryptoClass**>](cryptoclass-element.md)|<span data-ttu-id="9c22b-107">Zawiera klasę kryptografii, która ma mapowanie do przyjaznej nazwy w **\<nameEntry>** elemencie.</span><span class="sxs-lookup"><span data-stu-id="9c22b-107">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[**\<cryptographySettings**>](cryptographysettings-element.md)|<span data-ttu-id="9c22b-108">Zawiera ustawienia kryptografii.</span><span class="sxs-lookup"><span data-stu-id="9c22b-108">Contains cryptography settings.</span></span>|  
|[**\<cryptoNameMapping**>](cryptonamemapping-element.md)|<span data-ttu-id="9c22b-109">Zawiera mapowania klas do przyjaznych nazw.</span><span class="sxs-lookup"><span data-stu-id="9c22b-109">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="9c22b-110">**\<mscorlib>** element dla ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="9c22b-110">**\<mscorlib>** element for cryptography settings</span></span>](mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="9c22b-111">Zawiera **\<cryptographySettings>** element.</span><span class="sxs-lookup"><span data-stu-id="9c22b-111">Contains the **\<cryptographySettings>** element.</span></span>|  
|[**\<nameEntry>**](nameentry-element.md)|<span data-ttu-id="9c22b-112">Mapuje nazwę klasy na przyjazną nazwę algorytmu, która pozwala jednej klasie mieć wiele przyjaznych nazw.</span><span class="sxs-lookup"><span data-stu-id="9c22b-112">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[**\<oidEntry>**](oidentry-element.md)|<span data-ttu-id="9c22b-113">Mapuje identyfikator obiektu ASN. 1 (OID) na przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="9c22b-113">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[**\<oidMap>**](oidmap-element.md)|<span data-ttu-id="9c22b-114">Zawiera mapowania identyfikatorów OID ASN. 1 do klas.</span><span class="sxs-lookup"><span data-stu-id="9c22b-114">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9c22b-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9c22b-115">See also</span></span>

- [<span data-ttu-id="9c22b-116">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="9c22b-116">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="9c22b-117">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="9c22b-117">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)

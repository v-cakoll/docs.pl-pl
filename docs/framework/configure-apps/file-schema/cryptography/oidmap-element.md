---
title: <oidMap>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidMap
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap
helpviewer_keywords:
- <oidMap> element
- oidMap element
ms.assetid: 7f0c2246-c070-4748-b96a-2f66a296c539
ms.openlocfilehash: a28eaf68fe1e6ab3f26592eee5ae2d0f2e7a3256
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155170"
---
# <a name="oidmap-element"></a><span data-ttu-id="67a9f-102">\<oidMap> element</span><span class="sxs-lookup"><span data-stu-id="67a9f-102">\<oidMap> Element</span></span>
<span data-ttu-id="67a9f-103">Zawiera mapowania identyfikatora obiektu ASN.1 (OID) do klas.</span><span class="sxs-lookup"><span data-stu-id="67a9f-103">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>  

<span data-ttu-id="67a9f-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="67a9f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="67a9f-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="67a9f-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>\
<span data-ttu-id="67a9f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>kryptograficznych**](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="67a9f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>\
<span data-ttu-id="67a9f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>oidMap**</span><span class="sxs-lookup"><span data-stu-id="67a9f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidMap>**</span></span>

## <a name="syntax"></a><span data-ttu-id="67a9f-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="67a9f-108">Syntax</span></span>  
  
```xml  
<oidMap>
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67a9f-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="67a9f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="67a9f-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="67a9f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67a9f-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="67a9f-111">Attributes</span></span>  
 <span data-ttu-id="67a9f-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="67a9f-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="67a9f-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="67a9f-113">Child Elements</span></span>  
  
|<span data-ttu-id="67a9f-114">Element</span><span class="sxs-lookup"><span data-stu-id="67a9f-114">Element</span></span>|<span data-ttu-id="67a9f-115">Opis</span><span class="sxs-lookup"><span data-stu-id="67a9f-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="67a9f-116">\<>oidentry</span><span class="sxs-lookup"><span data-stu-id="67a9f-116">\<oidEntry></span></span>](oidentry-element.md)|<span data-ttu-id="67a9f-117">Mapuje ASN.1 OID na przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="67a9f-117">Maps an ASN.1 OID to a friendly name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="67a9f-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="67a9f-118">Parent Elements</span></span>  
  
|<span data-ttu-id="67a9f-119">Element</span><span class="sxs-lookup"><span data-stu-id="67a9f-119">Element</span></span>|<span data-ttu-id="67a9f-120">Opis</span><span class="sxs-lookup"><span data-stu-id="67a9f-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="67a9f-121">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="67a9f-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="67a9f-122">Zawiera ustawienia kryptografii.</span><span class="sxs-lookup"><span data-stu-id="67a9f-122">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="67a9f-123">Zawiera `cryptographySettings` element.</span><span class="sxs-lookup"><span data-stu-id="67a9f-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="67a9f-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="67a9f-124">Example</span></span>  
 <span data-ttu-id="67a9f-125">W poniższym przykładzie pokazano, jak używać \*\* \<oidMap>\*\* element, aby zawierać mapowanie OID dla algorytmu mieszania RIPEMD-160 do implementacji tego algorytmu mieszania.</span><span class="sxs-lookup"><span data-stu-id="67a9f-125">The following example shows how to use the **\<oidMap>** element to contain a mapping of an OID for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RIPEMD-160" class="MyCrypto"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"  name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="67a9f-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="67a9f-126">See also</span></span>

- [<span data-ttu-id="67a9f-127">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="67a9f-127">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="67a9f-128">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="67a9f-128">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="67a9f-129">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="67a9f-129">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="67a9f-130">Konfigurowanie klas kryptografii</span><span class="sxs-lookup"><span data-stu-id="67a9f-130">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="67a9f-131">Mapowanie identyfikatorów obiektów na algorytmy kryptografii</span><span class="sxs-lookup"><span data-stu-id="67a9f-131">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)

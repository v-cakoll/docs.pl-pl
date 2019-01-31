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
ms.openlocfilehash: d726965a921a11be1ff9c11d4fb348068b2ec0a3
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262520"
---
# <a name="oidmap-element"></a><span data-ttu-id="99b52-102">\<oidMap> Element</span><span class="sxs-lookup"><span data-stu-id="99b52-102">\<oidMap> Element</span></span>
<span data-ttu-id="99b52-103">Zawiera mapowania identyfikatora (OID) obiektów ASN.1 do klas.</span><span class="sxs-lookup"><span data-stu-id="99b52-103">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>  
  
 <span data-ttu-id="99b52-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="99b52-104">\<configuration></span></span>  
<span data-ttu-id="99b52-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="99b52-105">\<mscorlib></span></span>  
<span data-ttu-id="99b52-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="99b52-106">\<cryptographySettings></span></span>  
<span data-ttu-id="99b52-107">\<oidMap></span><span class="sxs-lookup"><span data-stu-id="99b52-107">\<oidMap></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99b52-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="99b52-108">Syntax</span></span>  
  
```xml  
<oidMap>   
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99b52-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="99b52-109">Attributes and Elements</span></span>  
 <span data-ttu-id="99b52-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="99b52-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99b52-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="99b52-111">Attributes</span></span>  
 <span data-ttu-id="99b52-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="99b52-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="99b52-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="99b52-113">Child Elements</span></span>  
  
|<span data-ttu-id="99b52-114">Element</span><span class="sxs-lookup"><span data-stu-id="99b52-114">Element</span></span>|<span data-ttu-id="99b52-115">Opis</span><span class="sxs-lookup"><span data-stu-id="99b52-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99b52-116">\<oidEntry></span><span class="sxs-lookup"><span data-stu-id="99b52-116">\<oidEntry></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|<span data-ttu-id="99b52-117">Mapuje ASN.1 OID przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="99b52-117">Maps an ASN.1 OID to a friendly name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="99b52-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="99b52-118">Parent Elements</span></span>  
  
|<span data-ttu-id="99b52-119">Element</span><span class="sxs-lookup"><span data-stu-id="99b52-119">Element</span></span>|<span data-ttu-id="99b52-120">Opis</span><span class="sxs-lookup"><span data-stu-id="99b52-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="99b52-121">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="99b52-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="99b52-122">Zawiera ustawienia szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="99b52-122">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="99b52-123">Zawiera `cryptographySettings` elementu.</span><span class="sxs-lookup"><span data-stu-id="99b52-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="99b52-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="99b52-124">Example</span></span>  
 <span data-ttu-id="99b52-125">Poniższy przykład pokazuje, jak używać  **\<oidmap — >** element zawiera mapowanie identyfikatora OID dla algorytmu wyznaczania wartości skrótu RIPEMD 160 implementacji tego algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="99b52-125">The following example shows how to use the **\<oidMap>** element to contain a mapping of an OID for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="99b52-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="99b52-126">See also</span></span>
- [<span data-ttu-id="99b52-127">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="99b52-127">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="99b52-128">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="99b52-128">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="99b52-129">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="99b52-129">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="99b52-130">Konfigurowanie klas kryptografii</span><span class="sxs-lookup"><span data-stu-id="99b52-130">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
- [<span data-ttu-id="99b52-131">Mapowanie identyfikatorów obiektów na algorytmy kryptografii</span><span class="sxs-lookup"><span data-stu-id="99b52-131">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)

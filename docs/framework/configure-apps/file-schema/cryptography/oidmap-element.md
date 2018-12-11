---
title: '&lt;oidmap —&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidMap
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap
helpviewer_keywords:
- <oidMap> element
- oidMap element
ms.assetid: 7f0c2246-c070-4748-b96a-2f66a296c539
author: mcleblanc
ms.author: markl
ms.openlocfilehash: badab8200a4b10fdc13987dfe39ebfebd4d1f7cf
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143171"
---
# <a name="ltoidmapgt-element"></a><span data-ttu-id="6c8b7-102">&lt;oidmap —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="6c8b7-102">&lt;oidMap&gt; Element</span></span>
<span data-ttu-id="6c8b7-103">Zawiera mapowania identyfikatora (OID) obiektów ASN.1 do klas.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-103">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>  
  
 <span data-ttu-id="6c8b7-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="6c8b7-104">\<configuration></span></span>  
<span data-ttu-id="6c8b7-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="6c8b7-105">\<mscorlib></span></span>  
<span data-ttu-id="6c8b7-106">\<cryptographysettings — ></span><span class="sxs-lookup"><span data-stu-id="6c8b7-106">\<cryptographySettings></span></span>  
<span data-ttu-id="6c8b7-107">\<oidmap — ></span><span class="sxs-lookup"><span data-stu-id="6c8b7-107">\<oidMap></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c8b7-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="6c8b7-108">Syntax</span></span>  
  
```xml  
<oidMap>   
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c8b7-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6c8b7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6c8b7-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c8b7-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6c8b7-111">Attributes</span></span>  
 <span data-ttu-id="6c8b7-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6c8b7-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6c8b7-113">Child Elements</span></span>  
  
|<span data-ttu-id="6c8b7-114">Element</span><span class="sxs-lookup"><span data-stu-id="6c8b7-114">Element</span></span>|<span data-ttu-id="6c8b7-115">Opis</span><span class="sxs-lookup"><span data-stu-id="6c8b7-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c8b7-116">\<oidentry — ></span><span class="sxs-lookup"><span data-stu-id="6c8b7-116">\<oidEntry></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|<span data-ttu-id="6c8b7-117">Mapuje ASN.1 OID przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-117">Maps an ASN.1 OID to a friendly name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6c8b7-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6c8b7-118">Parent Elements</span></span>  
  
|<span data-ttu-id="6c8b7-119">Element</span><span class="sxs-lookup"><span data-stu-id="6c8b7-119">Element</span></span>|<span data-ttu-id="6c8b7-120">Opis</span><span class="sxs-lookup"><span data-stu-id="6c8b7-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6c8b7-121">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="6c8b7-122">Zawiera ustawienia szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-122">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="6c8b7-123">Zawiera `cryptographySettings` elementu.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6c8b7-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="6c8b7-124">Example</span></span>  
 <span data-ttu-id="6c8b7-125">Poniższy przykład pokazuje, jak używać  **\<oidmap — >** element zawiera mapowanie identyfikatora OID dla algorytmu wyznaczania wartości skrótu RIPEMD 160 implementacji tego algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="6c8b7-125">The following example shows how to use the **\<oidMap>** element to contain a mapping of an OID for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6c8b7-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6c8b7-126">See Also</span></span>  
- [<span data-ttu-id="6c8b7-127">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6c8b7-127">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="6c8b7-128">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="6c8b7-128">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
- [<span data-ttu-id="6c8b7-129">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="6c8b7-129">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
- [<span data-ttu-id="6c8b7-130">Konfigurowanie klas kryptografii</span><span class="sxs-lookup"><span data-stu-id="6c8b7-130">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)  
- [<span data-ttu-id="6c8b7-131">Mapowanie identyfikatorów obiektów na algorytmy kryptografii</span><span class="sxs-lookup"><span data-stu-id="6c8b7-131">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)

---
title: '&lt;cryptographysettings —&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptographySettings
helpviewer_keywords:
- cryptographySettings element
- <cryptographySettings> element
ms.assetid: 6201b7da-bcb7-49f7-b9f5-ba1fe05573b9
author: mcleblanc
ms.author: markl
ms.openlocfilehash: dc55acd7a698ef37d45e8a412db684c13a3b8b16
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47203378"
---
# <a name="ltcryptographysettingsgt-element"></a><span data-ttu-id="48715-102">&lt;cryptographysettings —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="48715-102">&lt;cryptographySettings&gt; Element</span></span>
<span data-ttu-id="48715-103">Zawiera ustawienia szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="48715-103">Contains cryptography settings.</span></span>  
  
 <span data-ttu-id="48715-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="48715-104">\<configuration></span></span>  
<span data-ttu-id="48715-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="48715-105">\<mscorlib></span></span>  
<span data-ttu-id="48715-106">\<cryptographysettings — ></span><span class="sxs-lookup"><span data-stu-id="48715-106">\<cryptographySettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48715-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="48715-107">Syntax</span></span>  
  
```xml  
      <cryptographySettings>   
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48715-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="48715-108">Attributes and Elements</span></span>  
 <span data-ttu-id="48715-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="48715-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48715-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="48715-110">Attributes</span></span>  
 <span data-ttu-id="48715-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="48715-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="48715-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="48715-112">Child Elements</span></span>  
  
|<span data-ttu-id="48715-113">Element</span><span class="sxs-lookup"><span data-stu-id="48715-113">Element</span></span>|<span data-ttu-id="48715-114">Opis</span><span class="sxs-lookup"><span data-stu-id="48715-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="48715-115">\<cryptonamemapping — ></span><span class="sxs-lookup"><span data-stu-id="48715-115">\<cryptoNameMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|<span data-ttu-id="48715-116">Zawiera mapowania klasy przyjazne nazwy.</span><span class="sxs-lookup"><span data-stu-id="48715-116">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="48715-117">\<oidmap — ></span><span class="sxs-lookup"><span data-stu-id="48715-117">\<oidMap></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|<span data-ttu-id="48715-118">Zawiera mapowania identyfikatora (OID) obiektów ASN.1 do klas.</span><span class="sxs-lookup"><span data-stu-id="48715-118">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="48715-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="48715-119">Parent Elements</span></span>  
  
|<span data-ttu-id="48715-120">Element</span><span class="sxs-lookup"><span data-stu-id="48715-120">Element</span></span>|<span data-ttu-id="48715-121">Opis</span><span class="sxs-lookup"><span data-stu-id="48715-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="48715-122">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="48715-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="48715-123">Zawiera `cryptographySettings` elementu.</span><span class="sxs-lookup"><span data-stu-id="48715-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="48715-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="48715-124">Example</span></span>  
 <span data-ttu-id="48715-125">Poniższy przykład pokazuje jak używać  **\<cryptographysettings — >** element zawiera mapowania identyfikatora OID i mapowań nazw kryptografii.</span><span class="sxs-lookup"><span data-stu-id="48715-125">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="48715-126">Ten przykład umożliwia skonfigurowanie środowiska uruchomieniowego, aby <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> zwraca `MyHashClass` obiektu i `MyCryptoClass` klasy mapuje do identyfikatora obiektu 1.3.36.2.1.</span><span class="sxs-lookup"><span data-stu-id="48715-126">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyHash="MyHashClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MyHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="48715-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="48715-127">See Also</span></span>  
 [<span data-ttu-id="48715-128">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="48715-128">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="48715-129">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="48715-129">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="48715-130">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="48715-130">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)

---
title: "&lt;cryptographysettings —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptographySettings
helpviewer_keywords:
- cryptographySettings element
- <cryptographySettings> element
ms.assetid: 6201b7da-bcb7-49f7-b9f5-ba1fe05573b9
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 73a4f362be1612658e6911b7e7ea7a6c3e670e01
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltcryptographysettingsgt-element"></a><span data-ttu-id="fbad2-102">&lt;cryptographysettings —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="fbad2-102">&lt;cryptographySettings&gt; Element</span></span>
<span data-ttu-id="fbad2-103">Zawiera ustawienia szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="fbad2-103">Contains cryptography settings.</span></span>  
  
 <span data-ttu-id="fbad2-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="fbad2-104">\<configuration></span></span>  
<span data-ttu-id="fbad2-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="fbad2-105">\<mscorlib></span></span>  
<span data-ttu-id="fbad2-106">\<cryptographysettings — ></span><span class="sxs-lookup"><span data-stu-id="fbad2-106">\<cryptographySettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbad2-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="fbad2-107">Syntax</span></span>  
  
```xml  
      <cryptographySettings>   
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fbad2-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fbad2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fbad2-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fbad2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fbad2-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fbad2-110">Attributes</span></span>  
 <span data-ttu-id="fbad2-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="fbad2-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fbad2-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fbad2-112">Child Elements</span></span>  
  
|<span data-ttu-id="fbad2-113">Element</span><span class="sxs-lookup"><span data-stu-id="fbad2-113">Element</span></span>|<span data-ttu-id="fbad2-114">Opis</span><span class="sxs-lookup"><span data-stu-id="fbad2-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fbad2-115">\<cryptonamemapping — ></span><span class="sxs-lookup"><span data-stu-id="fbad2-115">\<cryptoNameMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|<span data-ttu-id="fbad2-116">Zawiera mapowania klasy przyjazne nazwy.</span><span class="sxs-lookup"><span data-stu-id="fbad2-116">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="fbad2-117">\<oidmap — ></span><span class="sxs-lookup"><span data-stu-id="fbad2-117">\<oidMap></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|<span data-ttu-id="fbad2-118">Zawiera ASN.1 obiektu (OID), identyfikator mapowania do klasy.</span><span class="sxs-lookup"><span data-stu-id="fbad2-118">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fbad2-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fbad2-119">Parent Elements</span></span>  
  
|<span data-ttu-id="fbad2-120">Element</span><span class="sxs-lookup"><span data-stu-id="fbad2-120">Element</span></span>|<span data-ttu-id="fbad2-121">Opis</span><span class="sxs-lookup"><span data-stu-id="fbad2-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fbad2-122">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fbad2-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="fbad2-123">Zawiera `cryptographySettings` elementu.</span><span class="sxs-lookup"><span data-stu-id="fbad2-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fbad2-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="fbad2-124">Example</span></span>  
 <span data-ttu-id="fbad2-125">Poniższy przykład przedstawia sposób użycia  **\<cryptographysettings — >** element zawiera mapowania nazw kryptografii i mapowania identyfikatora OID.</span><span class="sxs-lookup"><span data-stu-id="fbad2-125">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="fbad2-126">Ten przykład konfiguruje środowisko uruchomieniowe, aby <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> zwraca `MyHashClass` obiektu i `MyCryptoClass` klasy map do identyfikatora obiektu 1.3.36.2.1.</span><span class="sxs-lookup"><span data-stu-id="fbad2-126">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fbad2-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fbad2-127">See Also</span></span>  
 [<span data-ttu-id="fbad2-128">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="fbad2-128">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="fbad2-129">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="fbad2-129">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="fbad2-130">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="fbad2-130">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)

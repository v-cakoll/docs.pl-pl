---
title: <cryptographySettings> Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptographySettings
helpviewer_keywords:
- cryptographySettings element
- <cryptographySettings> element
ms.assetid: 6201b7da-bcb7-49f7-b9f5-ba1fe05573b9
ms.openlocfilehash: ca0a9a4b37f28eb03f58de4fd9b120cb7e654e0c
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088640"
---
# <a name="cryptographysettings-element"></a><span data-ttu-id="87401-102">\<element > cryptographySettings</span><span class="sxs-lookup"><span data-stu-id="87401-102">\<cryptographySettings> Element</span></span>
<span data-ttu-id="87401-103">Zawiera ustawienia kryptografii.</span><span class="sxs-lookup"><span data-stu-id="87401-103">Contains cryptography settings.</span></span>  

<span data-ttu-id="87401-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="87401-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="87401-105">&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="87401-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>\
<span data-ttu-id="87401-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<cryptographySettings >**</span><span class="sxs-lookup"><span data-stu-id="87401-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptographySettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="87401-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="87401-107">Syntax</span></span>  
  
```xml  
      <cryptographySettings>   
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87401-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="87401-108">Attributes and Elements</span></span>  
 <span data-ttu-id="87401-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="87401-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87401-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="87401-110">Attributes</span></span>  
 <span data-ttu-id="87401-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="87401-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="87401-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="87401-112">Child Elements</span></span>  
  
|<span data-ttu-id="87401-113">Element</span><span class="sxs-lookup"><span data-stu-id="87401-113">Element</span></span>|<span data-ttu-id="87401-114">Opis</span><span class="sxs-lookup"><span data-stu-id="87401-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87401-115">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="87401-115">\<cryptoNameMapping></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="87401-116">Zawiera mapowania klas do przyjaznych nazw.</span><span class="sxs-lookup"><span data-stu-id="87401-116">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="87401-117">\<oidMap ></span><span class="sxs-lookup"><span data-stu-id="87401-117">\<oidMap></span></span>](oidmap-element.md)|<span data-ttu-id="87401-118">Zawiera mapowania identyfikatorów obiektów ASN. 1 (OID) do klas.</span><span class="sxs-lookup"><span data-stu-id="87401-118">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="87401-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="87401-119">Parent Elements</span></span>  
  
|<span data-ttu-id="87401-120">Element</span><span class="sxs-lookup"><span data-stu-id="87401-120">Element</span></span>|<span data-ttu-id="87401-121">Opis</span><span class="sxs-lookup"><span data-stu-id="87401-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="87401-122">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="87401-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="87401-123">Zawiera element `cryptographySettings`.</span><span class="sxs-lookup"><span data-stu-id="87401-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="87401-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="87401-124">Example</span></span>  
 <span data-ttu-id="87401-125">Poniższy przykład pokazuje, jak używać elementu **\<cryptographySettings >** , aby zawierał mapowania nazw kryptograficznych i mapowania identyfikatorów OID.</span><span class="sxs-lookup"><span data-stu-id="87401-125">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="87401-126">Ten przykład umożliwia skonfigurowanie środowiska uruchomieniowego, tak aby <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> zwracał obiekt `MyHashClass`, a Klasa `MyCryptoClass` mapowana na identyfikator obiektu 1.3.36.2.1.</span><span class="sxs-lookup"><span data-stu-id="87401-126">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="87401-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87401-127">See also</span></span>

- [<span data-ttu-id="87401-128">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="87401-128">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="87401-129">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="87401-129">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="87401-130">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="87401-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)

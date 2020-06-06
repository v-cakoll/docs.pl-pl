---
title: <oidMap> Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidMap
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap
helpviewer_keywords:
- <oidMap> element
- oidMap element
ms.assetid: 7f0c2246-c070-4748-b96a-2f66a296c539
ms.openlocfilehash: a28eaf68fe1e6ab3f26592eee5ae2d0f2e7a3256
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155170"
---
# <a name="oidmap-element"></a><span data-ttu-id="40d55-102">\<oidMap> Element</span><span class="sxs-lookup"><span data-stu-id="40d55-102">\<oidMap> Element</span></span>
<span data-ttu-id="40d55-103">Zawiera mapowania identyfikatorów obiektów ASN. 1 (OID) do klas.</span><span class="sxs-lookup"><span data-stu-id="40d55-103">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidMap>**

## <a name="syntax"></a><span data-ttu-id="40d55-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="40d55-104">Syntax</span></span>  
  
```xml  
<oidMap>
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40d55-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="40d55-105">Attributes and Elements</span></span>  
 <span data-ttu-id="40d55-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="40d55-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40d55-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="40d55-107">Attributes</span></span>  
 <span data-ttu-id="40d55-108">Brak.</span><span class="sxs-lookup"><span data-stu-id="40d55-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="40d55-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="40d55-109">Child Elements</span></span>  
  
|<span data-ttu-id="40d55-110">Element</span><span class="sxs-lookup"><span data-stu-id="40d55-110">Element</span></span>|<span data-ttu-id="40d55-111">Opis</span><span class="sxs-lookup"><span data-stu-id="40d55-111">Description</span></span>|  
|-------------|-----------------|  
|[\<oidEntry>](oidentry-element.md)|<span data-ttu-id="40d55-112">Mapuje identyfikator OID ASN. 1 na przyjazną nazwę.</span><span class="sxs-lookup"><span data-stu-id="40d55-112">Maps an ASN.1 OID to a friendly name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="40d55-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="40d55-113">Parent Elements</span></span>  
  
|<span data-ttu-id="40d55-114">Element</span><span class="sxs-lookup"><span data-stu-id="40d55-114">Element</span></span>|<span data-ttu-id="40d55-115">Opis</span><span class="sxs-lookup"><span data-stu-id="40d55-115">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="40d55-116">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="40d55-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="40d55-117">Zawiera ustawienia kryptografii.</span><span class="sxs-lookup"><span data-stu-id="40d55-117">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="40d55-118">Zawiera `cryptographySettings` element.</span><span class="sxs-lookup"><span data-stu-id="40d55-118">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="40d55-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="40d55-119">Example</span></span>  
 <span data-ttu-id="40d55-120">Poniższy przykład pokazuje, jak użyć elementu, **\<oidMap>** aby zawierać mapowanie identyfikatora OID dla algorytmu wyznaczania wartości skrótu RIPEMD-160 do implementacji algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="40d55-120">The following example shows how to use the **\<oidMap>** element to contain a mapping of an OID for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="40d55-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40d55-121">See also</span></span>

- [<span data-ttu-id="40d55-122">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="40d55-122">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="40d55-123">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="40d55-123">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="40d55-124">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="40d55-124">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="40d55-125">Konfigurowanie klasy kryptografii</span><span class="sxs-lookup"><span data-stu-id="40d55-125">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="40d55-126">Mapowanie identyfikatorów obiektów na algorytmy kryptografii</span><span class="sxs-lookup"><span data-stu-id="40d55-126">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)

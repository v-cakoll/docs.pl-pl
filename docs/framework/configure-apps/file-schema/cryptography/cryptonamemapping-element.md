---
title: <cryptoNameMapping>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoNameMapping
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping
helpviewer_keywords:
- <cryptoNameMapping> element
- cryptoNameMapping element
ms.assetid: c59c9494-149b-4ce6-b38d-371f896ae85c
ms.openlocfilehash: d31c5cd52ffe0e2a6eb5784735e76436d216444b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155222"
---
# <a name="cryptonamemapping-element"></a><span data-ttu-id="7cdc5-102">\<cryptoNameMapping> Element</span><span class="sxs-lookup"><span data-stu-id="7cdc5-102">\<cryptoNameMapping> Element</span></span>
<span data-ttu-id="7cdc5-103">Zawiera mapowania klas do przyjaznych nazw.</span><span class="sxs-lookup"><span data-stu-id="7cdc5-103">Contains mappings of classes to friendly names.</span></span>  

<span data-ttu-id="7cdc5-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7cdc5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7cdc5-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="7cdc5-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>\
<span data-ttu-id="7cdc5-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>kryptograficznych**](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="7cdc5-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>\
<span data-ttu-id="7cdc5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>cryptoNameMapping**</span><span class="sxs-lookup"><span data-stu-id="7cdc5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoNameMapping>**</span></span>

## <a name="syntax"></a><span data-ttu-id="7cdc5-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="7cdc5-108">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7cdc5-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7cdc5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7cdc5-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7cdc5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7cdc5-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7cdc5-111">Attributes</span></span>  
 <span data-ttu-id="7cdc5-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="7cdc5-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7cdc5-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7cdc5-113">Child Elements</span></span>  
  
|<span data-ttu-id="7cdc5-114">Element</span><span class="sxs-lookup"><span data-stu-id="7cdc5-114">Element</span></span>|<span data-ttu-id="7cdc5-115">Opis</span><span class="sxs-lookup"><span data-stu-id="7cdc5-115">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="7cdc5-116">Zawiera listę klas kryptografii, które mają mapowanie do przyjaznej nazwy w \*\* \<nazwieEntry>\*\* element.</span><span class="sxs-lookup"><span data-stu-id="7cdc5-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="7cdc5-117">Mapuje nazwę klasy na przyjazną nazwę algorytmu, która umożliwia jednej klasie wiele przyjaznych nazw.</span><span class="sxs-lookup"><span data-stu-id="7cdc5-117">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7cdc5-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7cdc5-118">Parent Elements</span></span>  
  
|<span data-ttu-id="7cdc5-119">Element</span><span class="sxs-lookup"><span data-stu-id="7cdc5-119">Element</span></span>|<span data-ttu-id="7cdc5-120">Opis</span><span class="sxs-lookup"><span data-stu-id="7cdc5-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7cdc5-121">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7cdc5-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="7cdc5-122">Zawiera ustawienia kryptografii.</span><span class="sxs-lookup"><span data-stu-id="7cdc5-122">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="7cdc5-123">Zawiera mapowania klas do przyjaznych nazw.</span><span class="sxs-lookup"><span data-stu-id="7cdc5-123">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="7cdc5-124">\<Zawiera kryptografiaSzeńsze> element.</span><span class="sxs-lookup"><span data-stu-id="7cdc5-124">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7cdc5-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cdc5-125">Example</span></span>  
 <span data-ttu-id="7cdc5-126">W poniższym przykładzie pokazano, jak używać \*\* \<cryptoNameMapping>\*\* element do odwoływania się do klasy kryptografii i skonfigurować środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="7cdc5-126">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="7cdc5-127">Następnie można przekazać ciąg "RSA" <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> do metody <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> i użyć `MyCryptoRSAClass` metody, aby zwrócić obiekt.</span><span class="sxs-lookup"><span data-stu-id="7cdc5-127">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7cdc5-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7cdc5-128">See also</span></span>

- [<span data-ttu-id="7cdc5-129">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="7cdc5-129">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="7cdc5-130">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="7cdc5-130">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7cdc5-131">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="7cdc5-131">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="7cdc5-132">Konfigurowanie klas kryptografii</span><span class="sxs-lookup"><span data-stu-id="7cdc5-132">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

---
title: <cryptoClasses>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClasses
helpviewer_keywords:
- <cryptoClasses> element
- cryptoClasses element
ms.assetid: 290d5f96-946d-4f02-babb-1d31ec0b8295
ms.openlocfilehash: c93fadf51297d59ab499e25de283700364903049
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155249"
---
# <a name="cryptoclasses-element"></a><span data-ttu-id="6ebc3-102">\<cryptoClasses> Element</span><span class="sxs-lookup"><span data-stu-id="6ebc3-102">\<cryptoClasses> Element</span></span>
<span data-ttu-id="6ebc3-103">Zawiera listę klas kryptografii, które mają mapowanie do przyjaznej nazwy w [ \<nazwieEntry>](nameentry-element.md) element.</span><span class="sxs-lookup"><span data-stu-id="6ebc3-103">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  
  
[<span data-ttu-id="6ebc3-104">**\<>konfiguracyjne**</span><span class="sxs-lookup"><span data-stu-id="6ebc3-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="6ebc3-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="6ebc3-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="6ebc3-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>kryptograficznych**](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="6ebc3-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>  
<span data-ttu-id="6ebc3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>cryptoNameMapping**](cryptonamemapping-element.md)</span><span class="sxs-lookup"><span data-stu-id="6ebc3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span></span>  
<span data-ttu-id="6ebc3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>cryptoClasses**</span><span class="sxs-lookup"><span data-stu-id="6ebc3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClasses>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ebc3-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="6ebc3-109">Syntax</span></span>  
  
```xml  
<cryptoClasses>
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6ebc3-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6ebc3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6ebc3-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6ebc3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6ebc3-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6ebc3-112">Attributes</span></span>  
 <span data-ttu-id="6ebc3-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="6ebc3-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6ebc3-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6ebc3-114">Child Elements</span></span>  
  
|<span data-ttu-id="6ebc3-115">Element</span><span class="sxs-lookup"><span data-stu-id="6ebc3-115">Element</span></span>|<span data-ttu-id="6ebc3-116">Opis</span><span class="sxs-lookup"><span data-stu-id="6ebc3-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6ebc3-117">\<>cryptoClass</span><span class="sxs-lookup"><span data-stu-id="6ebc3-117">\<cryptoClass></span></span>](cryptoclass-element.md)|<span data-ttu-id="6ebc3-118">Zawiera klasę kryptografii, która ma mapowanie do przyjaznej nazwy w \*\* \<nazwieEntry>\*\* element.</span><span class="sxs-lookup"><span data-stu-id="6ebc3-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6ebc3-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6ebc3-119">Parent Elements</span></span>  
  
|<span data-ttu-id="6ebc3-120">Element</span><span class="sxs-lookup"><span data-stu-id="6ebc3-120">Element</span></span>|<span data-ttu-id="6ebc3-121">Opis</span><span class="sxs-lookup"><span data-stu-id="6ebc3-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6ebc3-122">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6ebc3-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="6ebc3-123">Zawiera ustawienia kryptografii.</span><span class="sxs-lookup"><span data-stu-id="6ebc3-123">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="6ebc3-124">Zawiera mapowania klas do przyjaznych nazw.</span><span class="sxs-lookup"><span data-stu-id="6ebc3-124">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="6ebc3-125">Zawiera `cryptographySettings` element.</span><span class="sxs-lookup"><span data-stu-id="6ebc3-125">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6ebc3-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="6ebc3-126">Example</span></span>  
 <span data-ttu-id="6ebc3-127">Poniższy przykład pokazuje, jak używać \*\* \<cryptoClass>\*\* element do odwoływania się do klasy kryptografii i skonfigurować środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="6ebc3-127">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="6ebc3-128">Następnie można przekazać ciąg "RSA" <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> do metody <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> i użyć `MyCryptoRSAClass` metody, aby zwrócić obiekt.</span><span class="sxs-lookup"><span data-stu-id="6ebc3-128">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <!-- Other cryptography classes go here. -->  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
             <!-- Mappings to other cryptography classes go here. -->  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6ebc3-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6ebc3-129">See also</span></span>

- <xref:System.Security.Cryptography>
- [<span data-ttu-id="6ebc3-130">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6ebc3-130">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="6ebc3-131">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="6ebc3-131">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6ebc3-132">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="6ebc3-132">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="6ebc3-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span><span class="sxs-lookup"><span data-stu-id="6ebc3-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A)
- [<span data-ttu-id="6ebc3-134">Konfigurowanie klas kryptografii</span><span class="sxs-lookup"><span data-stu-id="6ebc3-134">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

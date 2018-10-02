---
title: '&lt;cryptoclasses —&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClasses
helpviewer_keywords:
- <cryptoClasses> element
- cryptoClasses element
ms.assetid: 290d5f96-946d-4f02-babb-1d31ec0b8295
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 671302003c3a1f3a37e1773aeeae9cb09a457d13
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48033366"
---
# <a name="ltcryptoclassesgt-element"></a><span data-ttu-id="20531-102">&lt;cryptoclasses —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="20531-102">&lt;cryptoClasses&gt; Element</span></span>
<span data-ttu-id="20531-103">Zawiera listę klas kryptografii, które mają mapowanie do przyjazną nazwę w [ \<nameentry — >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="20531-103">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) element.</span></span>  
  
 <span data-ttu-id="20531-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="20531-104">\<configuration></span></span>  
<span data-ttu-id="20531-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="20531-105">\<mscorlib></span></span>  
<span data-ttu-id="20531-106">\<cryptographysettings — ></span><span class="sxs-lookup"><span data-stu-id="20531-106">\<cryptographySettings></span></span>  
<span data-ttu-id="20531-107">\<cryptonamemapping — ></span><span class="sxs-lookup"><span data-stu-id="20531-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="20531-108">\<cryptoclasses — ></span><span class="sxs-lookup"><span data-stu-id="20531-108">\<cryptoClasses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20531-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="20531-109">Syntax</span></span>  
  
```xml  
<cryptoClasses>   
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="20531-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="20531-110">Attributes and Elements</span></span>  
 <span data-ttu-id="20531-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="20531-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20531-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="20531-112">Attributes</span></span>  
 <span data-ttu-id="20531-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="20531-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="20531-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="20531-114">Child Elements</span></span>  
  
|<span data-ttu-id="20531-115">Element</span><span class="sxs-lookup"><span data-stu-id="20531-115">Element</span></span>|<span data-ttu-id="20531-116">Opis</span><span class="sxs-lookup"><span data-stu-id="20531-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20531-117">\<cryptoclass — ></span><span class="sxs-lookup"><span data-stu-id="20531-117">\<cryptoClass></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|<span data-ttu-id="20531-118">Zawiera klasy kryptografii, która ma mapowania do przyjazną nazwę w  **\<nameentry — >** elementu.</span><span class="sxs-lookup"><span data-stu-id="20531-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="20531-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="20531-119">Parent Elements</span></span>  
  
|<span data-ttu-id="20531-120">Element</span><span class="sxs-lookup"><span data-stu-id="20531-120">Element</span></span>|<span data-ttu-id="20531-121">Opis</span><span class="sxs-lookup"><span data-stu-id="20531-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="20531-122">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="20531-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="20531-123">Zawiera ustawienia szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="20531-123">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="20531-124">Zawiera mapowania klasy przyjazne nazwy.</span><span class="sxs-lookup"><span data-stu-id="20531-124">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="20531-125">Zawiera `cryptographySettings` elementu.</span><span class="sxs-lookup"><span data-stu-id="20531-125">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="20531-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="20531-126">Example</span></span>  
 <span data-ttu-id="20531-127">Poniższy przykład pokazuje jak używać  **\<cryptoclass — >** element odwołuje się do klasy kryptografii i konfigurowanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="20531-127">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="20531-128">Ciąg "RSA" można następnie przekazać do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metody i użyj <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodę, aby zwrócić `MyCryptoRSAClass` obiektu.</span><span class="sxs-lookup"><span data-stu-id="20531-128">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="20531-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="20531-129">See Also</span></span>  
 <xref:System.Security.Cryptography>  
 [<span data-ttu-id="20531-130">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="20531-130">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="20531-131">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="20531-131">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="20531-132">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="20531-132">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="20531-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span><span class="sxs-lookup"><span data-stu-id="20531-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](Overload:System.Security.Cryptography.CryptoConfig.CreateFromName)  
 [<span data-ttu-id="20531-134">Konfigurowanie klas kryptografii</span><span class="sxs-lookup"><span data-stu-id="20531-134">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)

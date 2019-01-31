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
ms.openlocfilehash: aa649a0ea83279a1b2bdb2dff33794002b8a6b7d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55274083"
---
# <a name="cryptoclasses-element"></a><span data-ttu-id="82c35-102">\<cryptoClasses> Element</span><span class="sxs-lookup"><span data-stu-id="82c35-102">\<cryptoClasses> Element</span></span>
<span data-ttu-id="82c35-103">Zawiera listę klas kryptografii, które mają mapowanie do przyjazną nazwę w [ \<nameentry — >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="82c35-103">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) element.</span></span>  
  
 <span data-ttu-id="82c35-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="82c35-104">\<configuration></span></span>  
<span data-ttu-id="82c35-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="82c35-105">\<mscorlib></span></span>  
<span data-ttu-id="82c35-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="82c35-106">\<cryptographySettings></span></span>  
<span data-ttu-id="82c35-107">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="82c35-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="82c35-108">\<cryptoClasses></span><span class="sxs-lookup"><span data-stu-id="82c35-108">\<cryptoClasses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82c35-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="82c35-109">Syntax</span></span>  
  
```xml  
<cryptoClasses>   
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="82c35-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="82c35-110">Attributes and Elements</span></span>  
 <span data-ttu-id="82c35-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="82c35-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="82c35-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="82c35-112">Attributes</span></span>  
 <span data-ttu-id="82c35-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="82c35-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="82c35-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="82c35-114">Child Elements</span></span>  
  
|<span data-ttu-id="82c35-115">Element</span><span class="sxs-lookup"><span data-stu-id="82c35-115">Element</span></span>|<span data-ttu-id="82c35-116">Opis</span><span class="sxs-lookup"><span data-stu-id="82c35-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="82c35-117">\<cryptoClass></span><span class="sxs-lookup"><span data-stu-id="82c35-117">\<cryptoClass></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|<span data-ttu-id="82c35-118">Zawiera klasy kryptografii, która ma mapowania do przyjazną nazwę w  **\<nameentry — >** elementu.</span><span class="sxs-lookup"><span data-stu-id="82c35-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="82c35-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="82c35-119">Parent Elements</span></span>  
  
|<span data-ttu-id="82c35-120">Element</span><span class="sxs-lookup"><span data-stu-id="82c35-120">Element</span></span>|<span data-ttu-id="82c35-121">Opis</span><span class="sxs-lookup"><span data-stu-id="82c35-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="82c35-122">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="82c35-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="82c35-123">Zawiera ustawienia szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="82c35-123">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="82c35-124">Zawiera mapowania klasy przyjazne nazwy.</span><span class="sxs-lookup"><span data-stu-id="82c35-124">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="82c35-125">Zawiera `cryptographySettings` elementu.</span><span class="sxs-lookup"><span data-stu-id="82c35-125">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="82c35-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="82c35-126">Example</span></span>  
 <span data-ttu-id="82c35-127">Poniższy przykład pokazuje jak używać  **\<cryptoclass — >** element odwołuje się do klasy kryptografii i konfigurowanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="82c35-127">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="82c35-128">Ciąg "RSA" można następnie przekazać do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metody i użyj <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodę, aby zwrócić `MyCryptoRSAClass` obiektu.</span><span class="sxs-lookup"><span data-stu-id="82c35-128">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="82c35-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="82c35-129">See also</span></span>
- <xref:System.Security.Cryptography>
- [<span data-ttu-id="82c35-130">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="82c35-130">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="82c35-131">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="82c35-131">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="82c35-132">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="82c35-132">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="82c35-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span><span class="sxs-lookup"><span data-stu-id="82c35-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](Overload:System.Security.Cryptography.CryptoConfig.CreateFromName)
- [<span data-ttu-id="82c35-134">Konfigurowanie klas kryptografii</span><span class="sxs-lookup"><span data-stu-id="82c35-134">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)

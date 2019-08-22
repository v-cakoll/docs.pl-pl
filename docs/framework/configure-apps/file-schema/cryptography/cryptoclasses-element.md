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
ms.openlocfilehash: dbe46e0b36d247005f933c82ee83687886b283d1
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659653"
---
# <a name="cryptoclasses-element"></a><span data-ttu-id="0c348-102">\<cryptoClasses> Element</span><span class="sxs-lookup"><span data-stu-id="0c348-102">\<cryptoClasses> Element</span></span>
<span data-ttu-id="0c348-103">Zawiera listę klas kryptograficznych, które mają mapowanie do przyjaznej nazwy w [ \<elemencie nameEntry >](nameentry-element.md) .</span><span class="sxs-lookup"><span data-stu-id="0c348-103">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  
  
 <span data-ttu-id="0c348-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="0c348-104">\<configuration></span></span>  
<span data-ttu-id="0c348-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="0c348-105">\<mscorlib></span></span>  
<span data-ttu-id="0c348-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="0c348-106">\<cryptographySettings></span></span>  
<span data-ttu-id="0c348-107">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="0c348-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="0c348-108">\<cryptoClasses></span><span class="sxs-lookup"><span data-stu-id="0c348-108">\<cryptoClasses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c348-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="0c348-109">Syntax</span></span>  
  
```xml  
<cryptoClasses>   
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c348-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0c348-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0c348-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0c348-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c348-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0c348-112">Attributes</span></span>  
 <span data-ttu-id="0c348-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="0c348-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0c348-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0c348-114">Child Elements</span></span>  
  
|<span data-ttu-id="0c348-115">Element</span><span class="sxs-lookup"><span data-stu-id="0c348-115">Element</span></span>|<span data-ttu-id="0c348-116">Opis</span><span class="sxs-lookup"><span data-stu-id="0c348-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0c348-117">\<cryptoClass></span><span class="sxs-lookup"><span data-stu-id="0c348-117">\<cryptoClass></span></span>](cryptoclass-element.md)|<span data-ttu-id="0c348-118">Zawiera klasę kryptografii, która ma mapowanie do przyjaznej nazwy w  **\<elemencie nameEntry >** .</span><span class="sxs-lookup"><span data-stu-id="0c348-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0c348-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0c348-119">Parent Elements</span></span>  
  
|<span data-ttu-id="0c348-120">Element</span><span class="sxs-lookup"><span data-stu-id="0c348-120">Element</span></span>|<span data-ttu-id="0c348-121">Opis</span><span class="sxs-lookup"><span data-stu-id="0c348-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0c348-122">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0c348-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="0c348-123">Zawiera ustawienia kryptografii.</span><span class="sxs-lookup"><span data-stu-id="0c348-123">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="0c348-124">Zawiera mapowania klas do przyjaznych nazw.</span><span class="sxs-lookup"><span data-stu-id="0c348-124">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="0c348-125">`cryptographySettings` Zawiera element.</span><span class="sxs-lookup"><span data-stu-id="0c348-125">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0c348-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="0c348-126">Example</span></span>  
 <span data-ttu-id="0c348-127">Poniższy przykład pokazuje,  **\<** jak używać elementu cryptoClass >, aby odwoływać się do klasy kryptografii i skonfigurować środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="0c348-127">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="0c348-128">Następnie można przekazać ciąg "RSA" do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metody i <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> użyć metody do zwrócenia `MyCryptoRSAClass` obiektu.</span><span class="sxs-lookup"><span data-stu-id="0c348-128">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0c348-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0c348-129">See also</span></span>

- <xref:System.Security.Cryptography>
- [<span data-ttu-id="0c348-130">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="0c348-130">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="0c348-131">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="0c348-131">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0c348-132">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="0c348-132">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="0c348-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span><span class="sxs-lookup"><span data-stu-id="0c348-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](Overload:System.Security.Cryptography.CryptoConfig.CreateFromName)
- [<span data-ttu-id="0c348-134">Konfigurowanie klas kryptografii</span><span class="sxs-lookup"><span data-stu-id="0c348-134">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

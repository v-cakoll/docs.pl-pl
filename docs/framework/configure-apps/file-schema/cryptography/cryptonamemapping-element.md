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
ms.openlocfilehash: c2652ac73c1d55f09a1f8511603003dc6d7291f9
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659645"
---
# <a name="cryptonamemapping-element"></a><span data-ttu-id="263de-102">\<cryptoNameMapping> Element</span><span class="sxs-lookup"><span data-stu-id="263de-102">\<cryptoNameMapping> Element</span></span>
<span data-ttu-id="263de-103">Zawiera mapowania klas do przyjaznych nazw.</span><span class="sxs-lookup"><span data-stu-id="263de-103">Contains mappings of classes to friendly names.</span></span>  
  
 <span data-ttu-id="263de-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="263de-104">\<configuration></span></span>  
<span data-ttu-id="263de-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="263de-105">\<mscorlib></span></span>  
<span data-ttu-id="263de-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="263de-106">\<cryptographySettings></span></span>  
<span data-ttu-id="263de-107">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="263de-107">\<cryptoNameMapping></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="263de-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="263de-108">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>   
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="263de-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="263de-109">Attributes and Elements</span></span>  
 <span data-ttu-id="263de-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="263de-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="263de-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="263de-111">Attributes</span></span>  
 <span data-ttu-id="263de-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="263de-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="263de-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="263de-113">Child Elements</span></span>  
  
|<span data-ttu-id="263de-114">Element</span><span class="sxs-lookup"><span data-stu-id="263de-114">Element</span></span>|<span data-ttu-id="263de-115">Opis</span><span class="sxs-lookup"><span data-stu-id="263de-115">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="263de-116">Zawiera listę klas kryptograficznych, które mają mapowanie do przyjaznej nazwy w  **\<elemencie nameEntry >** .</span><span class="sxs-lookup"><span data-stu-id="263de-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="263de-117">Mapuje nazwę klasy na przyjazną nazwę algorytmu, która pozwala jednej klasie mieć wiele przyjaznych nazw.</span><span class="sxs-lookup"><span data-stu-id="263de-117">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="263de-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="263de-118">Parent Elements</span></span>  
  
|<span data-ttu-id="263de-119">Element</span><span class="sxs-lookup"><span data-stu-id="263de-119">Element</span></span>|<span data-ttu-id="263de-120">Opis</span><span class="sxs-lookup"><span data-stu-id="263de-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="263de-121">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="263de-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="263de-122">Zawiera ustawienia kryptografii.</span><span class="sxs-lookup"><span data-stu-id="263de-122">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="263de-123">Zawiera mapowania klas do przyjaznych nazw.</span><span class="sxs-lookup"><span data-stu-id="263de-123">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="263de-124">Zawiera element > cryptographySettings. \<</span><span class="sxs-lookup"><span data-stu-id="263de-124">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="263de-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="263de-125">Example</span></span>  
 <span data-ttu-id="263de-126">Poniższy przykład pokazuje,  **\<** jak używać elementu cryptoNameMapping >, aby odwoływać się do klasy kryptografii i skonfigurować środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="263de-126">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="263de-127">Następnie można przekazać ciąg "RSA" do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metody i <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> użyć metody do zwrócenia `MyCryptoRSAClass` obiektu.</span><span class="sxs-lookup"><span data-stu-id="263de-127">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="263de-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="263de-128">See also</span></span>

- [<span data-ttu-id="263de-129">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="263de-129">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="263de-130">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="263de-130">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="263de-131">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="263de-131">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="263de-132">Konfigurowanie klas kryptografii</span><span class="sxs-lookup"><span data-stu-id="263de-132">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

---
title: <cryptoNameMapping> Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoNameMapping
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping
helpviewer_keywords:
- <cryptoNameMapping> element
- cryptoNameMapping element
ms.assetid: c59c9494-149b-4ce6-b38d-371f896ae85c
ms.openlocfilehash: bcf7894dba66736fcc1a30af9b5557549ef25e7d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092473"
---
# <a name="cryptonamemapping-element"></a><span data-ttu-id="f65ed-102">\<cryptoNameMapping> Element</span><span class="sxs-lookup"><span data-stu-id="f65ed-102">\<cryptoNameMapping> Element</span></span>
<span data-ttu-id="f65ed-103">Zawiera mapowania klasy przyjazne nazwy.</span><span class="sxs-lookup"><span data-stu-id="f65ed-103">Contains mappings of classes to friendly names.</span></span>  
  
 <span data-ttu-id="f65ed-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="f65ed-104">\<configuration></span></span>  
<span data-ttu-id="f65ed-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="f65ed-105">\<mscorlib></span></span>  
<span data-ttu-id="f65ed-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="f65ed-106">\<cryptographySettings></span></span>  
<span data-ttu-id="f65ed-107">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="f65ed-107">\<cryptoNameMapping></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f65ed-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="f65ed-108">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>   
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f65ed-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f65ed-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f65ed-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f65ed-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f65ed-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f65ed-111">Attributes</span></span>  
 <span data-ttu-id="f65ed-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="f65ed-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f65ed-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f65ed-113">Child Elements</span></span>  
  
|<span data-ttu-id="f65ed-114">Element</span><span class="sxs-lookup"><span data-stu-id="f65ed-114">Element</span></span>|<span data-ttu-id="f65ed-115">Opis</span><span class="sxs-lookup"><span data-stu-id="f65ed-115">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="f65ed-116">Zawiera listę klas kryptografii, które mają mapowanie do przyjazną nazwę w  **\<nameentry — >** elementu.</span><span class="sxs-lookup"><span data-stu-id="f65ed-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="f65ed-117">Mapuje nazwę klasy na nazwę algorytmu przyjazna, która umożliwia jednej klasy mają wiele przyjazne nazwy.</span><span class="sxs-lookup"><span data-stu-id="f65ed-117">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f65ed-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f65ed-118">Parent Elements</span></span>  
  
|<span data-ttu-id="f65ed-119">Element</span><span class="sxs-lookup"><span data-stu-id="f65ed-119">Element</span></span>|<span data-ttu-id="f65ed-120">Opis</span><span class="sxs-lookup"><span data-stu-id="f65ed-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f65ed-121">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f65ed-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="f65ed-122">Zawiera ustawienia szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="f65ed-122">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="f65ed-123">Zawiera mapowania klasy przyjazne nazwy.</span><span class="sxs-lookup"><span data-stu-id="f65ed-123">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="f65ed-124">Zawiera \<cryptographysettings — > element.</span><span class="sxs-lookup"><span data-stu-id="f65ed-124">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f65ed-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="f65ed-125">Example</span></span>  
 <span data-ttu-id="f65ed-126">Poniższy przykład pokazuje, jak używać  **\<cryptonamemapping — >** element odwołuje się do klasy kryptografii i konfigurowanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="f65ed-126">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="f65ed-127">Ciąg "RSA" można następnie przekazać do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metody i użyj <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodę, aby zwrócić `MyCryptoRSAClass` obiektu.</span><span class="sxs-lookup"><span data-stu-id="f65ed-127">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f65ed-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f65ed-128">See also</span></span>

- [<span data-ttu-id="f65ed-129">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f65ed-129">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="f65ed-130">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="f65ed-130">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="f65ed-131">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="f65ed-131">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="f65ed-132">Konfigurowanie klasy kryptografii</span><span class="sxs-lookup"><span data-stu-id="f65ed-132">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)

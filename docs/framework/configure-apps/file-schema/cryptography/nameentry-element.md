---
title: '&lt;nameentry —&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 1bffb72e7c68d10e2c0edd5ec3cb9bcff10cbc0a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743056"
---
# <a name="ltnameentrygt-element"></a><span data-ttu-id="fd343-102">&lt;nameentry —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="fd343-102">&lt;nameEntry&gt; Element</span></span>
<span data-ttu-id="fd343-103">Mapuje nazwę klasy na nazwę algorytmu przyjazną, która umożliwia jedną klasę do mają wiele przyjaznej nazwy.</span><span class="sxs-lookup"><span data-stu-id="fd343-103">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>  
  
 <span data-ttu-id="fd343-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="fd343-104">\<configuration></span></span>  
<span data-ttu-id="fd343-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="fd343-105">\<mscorlib></span></span>  
<span data-ttu-id="fd343-106">\<cryptographysettings — ></span><span class="sxs-lookup"><span data-stu-id="fd343-106">\<cryptographySettings></span></span>  
<span data-ttu-id="fd343-107">\<cryptonamemapping — ></span><span class="sxs-lookup"><span data-stu-id="fd343-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="fd343-108">\<nameentry — ></span><span class="sxs-lookup"><span data-stu-id="fd343-108">\<nameEntry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd343-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="fd343-109">Syntax</span></span>  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd343-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fd343-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fd343-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fd343-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd343-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fd343-112">Attributes</span></span>  
  
|<span data-ttu-id="fd343-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fd343-113">Attribute</span></span>|<span data-ttu-id="fd343-114">Opis</span><span class="sxs-lookup"><span data-stu-id="fd343-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fd343-115">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="fd343-115">**name**</span></span>|<span data-ttu-id="fd343-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="fd343-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="fd343-117">Określa przyjazną nazwę algorytmu, który implementuje klasy kryptografii.</span><span class="sxs-lookup"><span data-stu-id="fd343-117">Specifies the friendly name of the algorithm that the cryptography class implements.</span></span>|  
|<span data-ttu-id="fd343-118">**class**</span><span class="sxs-lookup"><span data-stu-id="fd343-118">**class**</span></span>|<span data-ttu-id="fd343-119">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="fd343-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="fd343-120">Określa wartość **nazwa** atrybutu w [ \<cryptoclass — >](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="fd343-120">Specifies the value for the **name** attribute in the [\<cryptoClass>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd343-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fd343-121">Child Elements</span></span>  
 <span data-ttu-id="fd343-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="fd343-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fd343-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fd343-123">Parent Elements</span></span>  
  
|<span data-ttu-id="fd343-124">Element</span><span class="sxs-lookup"><span data-stu-id="fd343-124">Element</span></span>|<span data-ttu-id="fd343-125">Opis</span><span class="sxs-lookup"><span data-stu-id="fd343-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fd343-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fd343-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.web`|<span data-ttu-id="fd343-127">Określa element root dla sekcji konfiguracji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fd343-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd343-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fd343-128">Remarks</span></span>  
 <span data-ttu-id="fd343-129">**Nazwa** atrybut może być nazwę jednej z klas abstrakcyjnych w <xref:System.Security.Cryptography> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="fd343-129">The **name** attribute can be the name of one of the abstract classes found in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="fd343-130">Podczas wywoływania **Utwórz** metody dla klasy abstrakcyjnej kryptografii, nazwa klasy abstrakcyjnej jest przekazywany do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="fd343-130">When you call the **Create** method on an abstract cryptography class, the abstract class name is passed to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> method.</span></span> <span data-ttu-id="fd343-131">**CreateFromName** zwraca wystąpienia typu oznaczonego **klasy** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="fd343-131">**CreateFromName** returns an instance of the type indicated by the **class** attribute.</span></span> <span data-ttu-id="fd343-132">Jeśli **nazwa** atrybut jest krótką nazwę, takich jak RSA, można użyć tej nazwy podczas wywoływania **CreateFromName** metody.</span><span class="sxs-lookup"><span data-stu-id="fd343-132">If the **name** attribute is a short name, such as RSA, you can use that name when calling the **CreateFromName** method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd343-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="fd343-133">Example</span></span>  
 <span data-ttu-id="fd343-134">Poniższy przykład przedstawia użycie  **\<nameentry — >** element odwołuje się do klasy kryptografii i skonfigurować środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="fd343-134">The following example shows how to use the **\<nameEntry>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="fd343-135">Ciąg "RSA" można następnie przekazać do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> — metoda i użyj <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodę, aby zwrócić `MyCryptoRSAClass` obiektu.</span><span class="sxs-lookup"><span data-stu-id="fd343-135">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fd343-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fd343-136">See Also</span></span>  
 [<span data-ttu-id="fd343-137">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="fd343-137">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="fd343-138">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="fd343-138">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="fd343-139">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="fd343-139">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="fd343-140">Konfigurowanie klas kryptografii</span><span class="sxs-lookup"><span data-stu-id="fd343-140">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)

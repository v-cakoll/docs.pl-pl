---
title: "&lt;nameentry —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 507c71b5c13deeb7c1a81b6a4dd9604c3bd919f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltnameentrygt-element"></a><span data-ttu-id="1a64b-102">&lt;nameentry —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="1a64b-102">&lt;nameEntry&gt; Element</span></span>
<span data-ttu-id="1a64b-103">Mapuje nazwę klasy na nazwę algorytmu przyjazną, która umożliwia jedną klasę do mają wiele przyjaznej nazwy.</span><span class="sxs-lookup"><span data-stu-id="1a64b-103">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>  
  
 <span data-ttu-id="1a64b-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="1a64b-104">\<configuration></span></span>  
<span data-ttu-id="1a64b-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="1a64b-105">\<mscorlib></span></span>  
<span data-ttu-id="1a64b-106">\<cryptographysettings — ></span><span class="sxs-lookup"><span data-stu-id="1a64b-106">\<cryptographySettings></span></span>  
<span data-ttu-id="1a64b-107">\<cryptonamemapping — ></span><span class="sxs-lookup"><span data-stu-id="1a64b-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="1a64b-108">\<nameentry — ></span><span class="sxs-lookup"><span data-stu-id="1a64b-108">\<nameEntry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a64b-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a64b-109">Syntax</span></span>  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a64b-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1a64b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1a64b-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1a64b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a64b-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1a64b-112">Attributes</span></span>  
  
|<span data-ttu-id="1a64b-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1a64b-113">Attribute</span></span>|<span data-ttu-id="1a64b-114">Opis</span><span class="sxs-lookup"><span data-stu-id="1a64b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1a64b-115">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="1a64b-115">**name**</span></span>|<span data-ttu-id="1a64b-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="1a64b-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="1a64b-117">Określa przyjazną nazwę algorytmu, który implementuje klasy kryptografii.</span><span class="sxs-lookup"><span data-stu-id="1a64b-117">Specifies the friendly name of the algorithm that the cryptography class implements.</span></span>|  
|<span data-ttu-id="1a64b-118">**klasy**</span><span class="sxs-lookup"><span data-stu-id="1a64b-118">**class**</span></span>|<span data-ttu-id="1a64b-119">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="1a64b-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="1a64b-120">Określa wartość **nazwa** atrybutu w [ \<cryptoclass — >](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="1a64b-120">Specifies the value for the **name** attribute in the [\<cryptoClass>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1a64b-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1a64b-121">Child Elements</span></span>  
 <span data-ttu-id="1a64b-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="1a64b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1a64b-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1a64b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="1a64b-124">Element</span><span class="sxs-lookup"><span data-stu-id="1a64b-124">Element</span></span>|<span data-ttu-id="1a64b-125">Opis</span><span class="sxs-lookup"><span data-stu-id="1a64b-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1a64b-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1a64b-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.web`|<span data-ttu-id="1a64b-127">Określa element root dla sekcji konfiguracji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="1a64b-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a64b-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1a64b-128">Remarks</span></span>  
 <span data-ttu-id="1a64b-129">**Nazwa** atrybut może być nazwę jednej z klas abstrakcyjnych w <xref:System.Security.Cryptography> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1a64b-129">The **name** attribute can be the name of one of the abstract classes found in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="1a64b-130">Podczas wywoływania **Utwórz** metody dla klasy abstrakcyjnej kryptografii, nazwa klasy abstrakcyjnej jest przekazywany do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1a64b-130">When you call the **Create** method on an abstract cryptography class, the abstract class name is passed to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> method.</span></span> <span data-ttu-id="1a64b-131">**CreateFromName** zwraca wystąpienia typu oznaczonego **klasy** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="1a64b-131">**CreateFromName** returns an instance of the type indicated by the **class** attribute.</span></span> <span data-ttu-id="1a64b-132">Jeśli **nazwa** atrybut jest krótką nazwę, takich jak RSA, można użyć tej nazwy podczas wywoływania **CreateFromName** metody.</span><span class="sxs-lookup"><span data-stu-id="1a64b-132">If the **name** attribute is a short name, such as RSA, you can use that name when calling the **CreateFromName** method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a64b-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="1a64b-133">Example</span></span>  
 <span data-ttu-id="1a64b-134">Poniższy przykład przedstawia użycie  **\<nameentry — >** element odwołuje się do klasy kryptografii i skonfigurować środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="1a64b-134">The following example shows how to use the **\<nameEntry>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="1a64b-135">Ciąg "RSA" można następnie przekazać do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> — metoda i użyj <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodę, aby zwrócić `MyCryptoRSAClass` obiektu.</span><span class="sxs-lookup"><span data-stu-id="1a64b-135">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1a64b-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1a64b-136">See Also</span></span>  
 [<span data-ttu-id="1a64b-137">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1a64b-137">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="1a64b-138">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="1a64b-138">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="1a64b-139">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="1a64b-139">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="1a64b-140">Konfigurowanie klasy kryptografii</span><span class="sxs-lookup"><span data-stu-id="1a64b-140">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)

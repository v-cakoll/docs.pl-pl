---
title: '&lt;cryptoclass —&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses/cryptoClass
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClass
helpviewer_keywords:
- cryptoClass element
- <cryptoClass> element
ms.assetid: 03db52ef-010e-44ea-b6fd-b9c900ecad50
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 728fff7b8626e227e692c713f4cb05049c14a9f1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742760"
---
# <a name="ltcryptoclassgt-element"></a><span data-ttu-id="7eaba-102">&lt;cryptoclass —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="7eaba-102">&lt;cryptoClass&gt; Element</span></span>
<span data-ttu-id="7eaba-103">Zawiera klasy kryptografii, która ma mapowania przyjazną nazwę w [ \<nameentry — >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="7eaba-103">Contains a cryptography class that has a mapping to a friendly name in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) element.</span></span>  
  
 <span data-ttu-id="7eaba-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="7eaba-104">\<configuration></span></span>  
<span data-ttu-id="7eaba-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="7eaba-105">\<mscorlib></span></span>  
<span data-ttu-id="7eaba-106">\<cryptographysettings — ></span><span class="sxs-lookup"><span data-stu-id="7eaba-106">\<cryptographySettings></span></span>  
<span data-ttu-id="7eaba-107">\<cryptonamemapping — ></span><span class="sxs-lookup"><span data-stu-id="7eaba-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="7eaba-108">\<cryptoclasses — ></span><span class="sxs-lookup"><span data-stu-id="7eaba-108">\<cryptoClasses></span></span>  
<span data-ttu-id="7eaba-109">\<cryptoclass — ></span><span class="sxs-lookup"><span data-stu-id="7eaba-109">\<cryptoClass></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7eaba-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="7eaba-110">Syntax</span></span>  
  
```xml  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7eaba-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7eaba-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7eaba-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7eaba-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7eaba-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7eaba-113">Attributes</span></span>  
  
|<span data-ttu-id="7eaba-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7eaba-114">Attribute</span></span>|<span data-ttu-id="7eaba-115">Opis</span><span class="sxs-lookup"><span data-stu-id="7eaba-115">Description</span></span>|  
|---------------|-----------------|  
|`customClassName`|<span data-ttu-id="7eaba-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="7eaba-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="7eaba-117">Zawiera informacje dotyczące klasy kryptografii.</span><span class="sxs-lookup"><span data-stu-id="7eaba-117">Contains the information for the cryptography class.</span></span> <span data-ttu-id="7eaba-118">Użyj tego atrybutu, aby podać krótkiej nazwy klasy.</span><span class="sxs-lookup"><span data-stu-id="7eaba-118">Use this attribute to provide a short name for your class.</span></span> <span data-ttu-id="7eaba-119">Należy określić ciąg, który spełnia wymagania określone w [określenie pełni kwalifikowane nazwy typów](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="7eaba-119">You must specify a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7eaba-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7eaba-120">Child Elements</span></span>  
 <span data-ttu-id="7eaba-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="7eaba-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7eaba-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7eaba-122">Parent Elements</span></span>  
  
|<span data-ttu-id="7eaba-123">Element</span><span class="sxs-lookup"><span data-stu-id="7eaba-123">Element</span></span>|<span data-ttu-id="7eaba-124">Opis</span><span class="sxs-lookup"><span data-stu-id="7eaba-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7eaba-125">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7eaba-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptoClasses`|<span data-ttu-id="7eaba-126">Zawiera listę klasy kryptografii, które ma mapowania do przyjazną nazwę w [ \<nameentry — >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="7eaba-126">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) element.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="7eaba-127">Zawiera ustawienia szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="7eaba-127">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="7eaba-128">Zawiera mapowania klasy przyjazne nazwy.</span><span class="sxs-lookup"><span data-stu-id="7eaba-128">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="7eaba-129">Zawiera [ \<cryptographysettings — >](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="7eaba-129">Contains the [\<cryptographySettings>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md) element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7eaba-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="7eaba-130">Example</span></span>  
 <span data-ttu-id="7eaba-131">Poniższy przykład przedstawia sposób użycia  **\<cryptoclass — >** element odwołuje się do klasy kryptografii i skonfigurować środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="7eaba-131">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="7eaba-132">Ciąg "RSA" można następnie przekazać do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> — metoda i użyj <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodę, aby zwrócić `MyCryptoRSAClass` obiektu.</span><span class="sxs-lookup"><span data-stu-id="7eaba-132">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7eaba-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7eaba-133">See Also</span></span>  
 [<span data-ttu-id="7eaba-134">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="7eaba-134">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="7eaba-135">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="7eaba-135">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="7eaba-136">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="7eaba-136">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="7eaba-137">Konfigurowanie klas kryptografii</span><span class="sxs-lookup"><span data-stu-id="7eaba-137">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)

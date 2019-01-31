---
title: <cryptoClass>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses/cryptoClass
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClass
helpviewer_keywords:
- cryptoClass element
- <cryptoClass> element
ms.assetid: 03db52ef-010e-44ea-b6fd-b9c900ecad50
ms.openlocfilehash: 161c9212600a417a97fa5a4e0edeac02db0f17a1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55287537"
---
# <a name="cryptoclass-element"></a><span data-ttu-id="1b0e6-102">\<cryptoClass> Element</span><span class="sxs-lookup"><span data-stu-id="1b0e6-102">\<cryptoClass> Element</span></span>
<span data-ttu-id="1b0e6-103">Zawiera klasy kryptografii, która ma mapowania do przyjazną nazwę w [ \<nameentry — >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="1b0e6-103">Contains a cryptography class that has a mapping to a friendly name in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) element.</span></span>  
  
 <span data-ttu-id="1b0e6-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="1b0e6-104">\<configuration></span></span>  
<span data-ttu-id="1b0e6-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="1b0e6-105">\<mscorlib></span></span>  
<span data-ttu-id="1b0e6-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="1b0e6-106">\<cryptographySettings></span></span>  
<span data-ttu-id="1b0e6-107">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="1b0e6-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="1b0e6-108">\<cryptoClasses></span><span class="sxs-lookup"><span data-stu-id="1b0e6-108">\<cryptoClasses></span></span>  
<span data-ttu-id="1b0e6-109">\<cryptoClass></span><span class="sxs-lookup"><span data-stu-id="1b0e6-109">\<cryptoClass></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b0e6-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="1b0e6-110">Syntax</span></span>  
  
```xml  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1b0e6-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1b0e6-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1b0e6-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1b0e6-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1b0e6-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1b0e6-113">Attributes</span></span>  
  
|<span data-ttu-id="1b0e6-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1b0e6-114">Attribute</span></span>|<span data-ttu-id="1b0e6-115">Opis</span><span class="sxs-lookup"><span data-stu-id="1b0e6-115">Description</span></span>|  
|---------------|-----------------|  
|`customClassName`|<span data-ttu-id="1b0e6-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="1b0e6-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="1b0e6-117">Zawiera informacje dla klasy kryptografii.</span><span class="sxs-lookup"><span data-stu-id="1b0e6-117">Contains the information for the cryptography class.</span></span> <span data-ttu-id="1b0e6-118">Podaj krótką nazwę klasy za pomocą tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="1b0e6-118">Use this attribute to provide a short name for your class.</span></span> <span data-ttu-id="1b0e6-119">Należy określić ciąg, który spełnia wymagania określone w [określanie w pełni kwalifikowanej nazwy typu](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="1b0e6-119">You must specify a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1b0e6-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1b0e6-120">Child Elements</span></span>  
 <span data-ttu-id="1b0e6-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="1b0e6-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1b0e6-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1b0e6-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1b0e6-123">Element</span><span class="sxs-lookup"><span data-stu-id="1b0e6-123">Element</span></span>|<span data-ttu-id="1b0e6-124">Opis</span><span class="sxs-lookup"><span data-stu-id="1b0e6-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1b0e6-125">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1b0e6-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptoClasses`|<span data-ttu-id="1b0e6-126">Zawiera listę klas kryptografii, które mają mapowanie do przyjazną nazwę w [ \<nameentry — >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="1b0e6-126">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) element.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="1b0e6-127">Zawiera ustawienia szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="1b0e6-127">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="1b0e6-128">Zawiera mapowania klasy przyjazne nazwy.</span><span class="sxs-lookup"><span data-stu-id="1b0e6-128">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="1b0e6-129">Zawiera [ \<cryptographysettings — >](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="1b0e6-129">Contains the [\<cryptographySettings>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md) element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1b0e6-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="1b0e6-130">Example</span></span>  
 <span data-ttu-id="1b0e6-131">Poniższy przykład pokazuje jak używać  **\<cryptoclass — >** element odwołuje się do klasy kryptografii i konfigurowanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="1b0e6-131">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="1b0e6-132">Ciąg "RSA" można następnie przekazać do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metody i użyj <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodę, aby zwrócić `MyCryptoRSAClass` obiektu.</span><span class="sxs-lookup"><span data-stu-id="1b0e6-132">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1b0e6-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1b0e6-133">See also</span></span>
- [<span data-ttu-id="1b0e6-134">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1b0e6-134">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="1b0e6-135">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="1b0e6-135">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="1b0e6-136">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="1b0e6-136">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="1b0e6-137">Konfigurowanie klas kryptografii</span><span class="sxs-lookup"><span data-stu-id="1b0e6-137">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)

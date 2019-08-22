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
ms.openlocfilehash: c8076fba1ebae693aa5e4c80e822b9ae840ff1c5
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664337"
---
# <a name="cryptoclass-element"></a><span data-ttu-id="51ebb-102">\<cryptoClass> Element</span><span class="sxs-lookup"><span data-stu-id="51ebb-102">\<cryptoClass> Element</span></span>
<span data-ttu-id="51ebb-103">Zawiera klasę kryptografii, która ma mapowanie do przyjaznej nazwy w [ \<elemencie nameEntry >](nameentry-element.md) .</span><span class="sxs-lookup"><span data-stu-id="51ebb-103">Contains a cryptography class that has a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  
  
 <span data-ttu-id="51ebb-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="51ebb-104">\<configuration></span></span>  
<span data-ttu-id="51ebb-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="51ebb-105">\<mscorlib></span></span>  
<span data-ttu-id="51ebb-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="51ebb-106">\<cryptographySettings></span></span>  
<span data-ttu-id="51ebb-107">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="51ebb-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="51ebb-108">\<cryptoClasses></span><span class="sxs-lookup"><span data-stu-id="51ebb-108">\<cryptoClasses></span></span>  
<span data-ttu-id="51ebb-109">\<cryptoClass></span><span class="sxs-lookup"><span data-stu-id="51ebb-109">\<cryptoClass></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51ebb-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="51ebb-110">Syntax</span></span>  
  
```xml  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="51ebb-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="51ebb-111">Attributes and Elements</span></span>  
 <span data-ttu-id="51ebb-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="51ebb-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="51ebb-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="51ebb-113">Attributes</span></span>  
  
|<span data-ttu-id="51ebb-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="51ebb-114">Attribute</span></span>|<span data-ttu-id="51ebb-115">Opis</span><span class="sxs-lookup"><span data-stu-id="51ebb-115">Description</span></span>|  
|---------------|-----------------|  
|`customClassName`|<span data-ttu-id="51ebb-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="51ebb-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="51ebb-117">Zawiera informacje dotyczące klasy kryptografii.</span><span class="sxs-lookup"><span data-stu-id="51ebb-117">Contains the information for the cryptography class.</span></span> <span data-ttu-id="51ebb-118">Użyj tego atrybutu, aby podać krótką nazwę klasy.</span><span class="sxs-lookup"><span data-stu-id="51ebb-118">Use this attribute to provide a short name for your class.</span></span> <span data-ttu-id="51ebb-119">Należy określić ciąg, który spełnia wymagania określone w polu [Określanie w pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="51ebb-119">You must specify a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="51ebb-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="51ebb-120">Child Elements</span></span>  
 <span data-ttu-id="51ebb-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="51ebb-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="51ebb-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="51ebb-122">Parent Elements</span></span>  
  
|<span data-ttu-id="51ebb-123">Element</span><span class="sxs-lookup"><span data-stu-id="51ebb-123">Element</span></span>|<span data-ttu-id="51ebb-124">Opis</span><span class="sxs-lookup"><span data-stu-id="51ebb-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="51ebb-125">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="51ebb-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptoClasses`|<span data-ttu-id="51ebb-126">Zawiera listę klas kryptograficznych, które mają mapowanie do przyjaznej nazwy w [ \<elemencie nameEntry >](nameentry-element.md) .</span><span class="sxs-lookup"><span data-stu-id="51ebb-126">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="51ebb-127">Zawiera ustawienia kryptografii.</span><span class="sxs-lookup"><span data-stu-id="51ebb-127">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="51ebb-128">Zawiera mapowania klas do przyjaznych nazw.</span><span class="sxs-lookup"><span data-stu-id="51ebb-128">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="51ebb-129">Zawiera element [> cryptographySettings.\<](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="51ebb-129">Contains the [\<cryptographySettings>](cryptographysettings-element.md) element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="51ebb-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="51ebb-130">Example</span></span>  
 <span data-ttu-id="51ebb-131">Poniższy przykład pokazuje,  **\<** jak używać elementu cryptoClass >, aby odwoływać się do klasy kryptografii i skonfigurować środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="51ebb-131">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="51ebb-132">Następnie można przekazać ciąg "RSA" do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metody i <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> użyć metody do zwrócenia `MyCryptoRSAClass` obiektu.</span><span class="sxs-lookup"><span data-stu-id="51ebb-132">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="51ebb-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="51ebb-133">See also</span></span>

- [<span data-ttu-id="51ebb-134">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="51ebb-134">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="51ebb-135">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="51ebb-135">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="51ebb-136">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="51ebb-136">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="51ebb-137">Konfigurowanie klas kryptografii</span><span class="sxs-lookup"><span data-stu-id="51ebb-137">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

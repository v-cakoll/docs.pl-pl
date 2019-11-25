---
title: <cryptoClass> Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses/cryptoClass
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClass
helpviewer_keywords:
- cryptoClass element
- <cryptoClass> element
ms.assetid: 03db52ef-010e-44ea-b6fd-b9c900ecad50
ms.openlocfilehash: 4872fbd6fa043902e8c69f158bee5d0c915ec83a
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088662"
---
# <a name="cryptoclass-element"></a><span data-ttu-id="6ed70-102">\<element > cryptoClass</span><span class="sxs-lookup"><span data-stu-id="6ed70-102">\<cryptoClass> Element</span></span>
<span data-ttu-id="6ed70-103">Zawiera klasę kryptografii, która ma mapowanie do przyjaznej nazwy w [\<nameEntry >](nameentry-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="6ed70-103">Contains a cryptography class that has a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  

<span data-ttu-id="6ed70-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="6ed70-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6ed70-105">&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="6ed70-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>\
<span data-ttu-id="6ed70-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptographySettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="6ed70-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>\
<span data-ttu-id="6ed70-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptoNameMapping**](cryptonamemapping-element.md) ></span><span class="sxs-lookup"><span data-stu-id="6ed70-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span></span>\
<span data-ttu-id="6ed70-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptoClasses >** ](cryptoclasses-element.md)</span><span class="sxs-lookup"><span data-stu-id="6ed70-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)</span></span>\
<span data-ttu-id="6ed70-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<cryptoClass >**</span><span class="sxs-lookup"><span data-stu-id="6ed70-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClass>**</span></span>

## <a name="syntax"></a><span data-ttu-id="6ed70-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="6ed70-110">Syntax</span></span>  
  
```xml  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6ed70-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6ed70-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6ed70-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6ed70-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6ed70-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6ed70-113">Attributes</span></span>  
  
|<span data-ttu-id="6ed70-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6ed70-114">Attribute</span></span>|<span data-ttu-id="6ed70-115">Opis</span><span class="sxs-lookup"><span data-stu-id="6ed70-115">Description</span></span>|  
|---------------|-----------------|  
|`customClassName`|<span data-ttu-id="6ed70-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="6ed70-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="6ed70-117">Zawiera informacje dotyczące klasy kryptografii.</span><span class="sxs-lookup"><span data-stu-id="6ed70-117">Contains the information for the cryptography class.</span></span> <span data-ttu-id="6ed70-118">Użyj tego atrybutu, aby podać krótką nazwę klasy.</span><span class="sxs-lookup"><span data-stu-id="6ed70-118">Use this attribute to provide a short name for your class.</span></span> <span data-ttu-id="6ed70-119">Należy określić ciąg, który spełnia wymagania określone w polu [Określanie w pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="6ed70-119">You must specify a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6ed70-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6ed70-120">Child Elements</span></span>  
 <span data-ttu-id="6ed70-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="6ed70-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6ed70-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6ed70-122">Parent Elements</span></span>  
  
|<span data-ttu-id="6ed70-123">Element</span><span class="sxs-lookup"><span data-stu-id="6ed70-123">Element</span></span>|<span data-ttu-id="6ed70-124">Opis</span><span class="sxs-lookup"><span data-stu-id="6ed70-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6ed70-125">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6ed70-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptoClasses`|<span data-ttu-id="6ed70-126">Zawiera listę klas kryptograficznych, które mają mapowanie do przyjaznej nazwy w [\<nameEntry >](nameentry-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="6ed70-126">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="6ed70-127">Zawiera ustawienia kryptografii.</span><span class="sxs-lookup"><span data-stu-id="6ed70-127">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="6ed70-128">Zawiera mapowania klas do przyjaznych nazw.</span><span class="sxs-lookup"><span data-stu-id="6ed70-128">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="6ed70-129">Zawiera element [\<cryptographySettings >](cryptographysettings-element.md) .</span><span class="sxs-lookup"><span data-stu-id="6ed70-129">Contains the [\<cryptographySettings>](cryptographysettings-element.md) element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6ed70-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="6ed70-130">Example</span></span>  
 <span data-ttu-id="6ed70-131">Poniższy przykład pokazuje, jak używać elementu **\<cryptoClass >** , aby odwoływać się do klasy kryptografii i skonfigurować środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="6ed70-131">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="6ed70-132">Następnie można przekazać ciąg "RSA" do metody <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> i użyć metody <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> do zwrócenia obiektu `MyCryptoRSAClass`.</span><span class="sxs-lookup"><span data-stu-id="6ed70-132">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6ed70-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6ed70-133">See also</span></span>

- [<span data-ttu-id="6ed70-134">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6ed70-134">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="6ed70-135">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="6ed70-135">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6ed70-136">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="6ed70-136">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="6ed70-137">Konfigurowanie klas kryptografii</span><span class="sxs-lookup"><span data-stu-id="6ed70-137">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

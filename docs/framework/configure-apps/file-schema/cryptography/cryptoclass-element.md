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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088662"
---
# <a name="cryptoclass-element"></a><span data-ttu-id="c5fd0-102">\<cryptoClass> Element</span><span class="sxs-lookup"><span data-stu-id="c5fd0-102">\<cryptoClass> Element</span></span>
<span data-ttu-id="c5fd0-103">Zawiera klasę kryptografii, która ma mapowanie do przyjaznej nazwy w [\<nameEntry>](nameentry-element.md) elemencie.</span><span class="sxs-lookup"><span data-stu-id="c5fd0-103">Contains a cryptography class that has a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClass>**

## <a name="syntax"></a><span data-ttu-id="c5fd0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5fd0-104">Syntax</span></span>  
  
```xml  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5fd0-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c5fd0-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c5fd0-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c5fd0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5fd0-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c5fd0-107">Attributes</span></span>  
  
|<span data-ttu-id="c5fd0-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c5fd0-108">Attribute</span></span>|<span data-ttu-id="c5fd0-109">Opis</span><span class="sxs-lookup"><span data-stu-id="c5fd0-109">Description</span></span>|  
|---------------|-----------------|  
|`customClassName`|<span data-ttu-id="c5fd0-110">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="c5fd0-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="c5fd0-111">Zawiera informacje dotyczące klasy kryptografii.</span><span class="sxs-lookup"><span data-stu-id="c5fd0-111">Contains the information for the cryptography class.</span></span> <span data-ttu-id="c5fd0-112">Użyj tego atrybutu, aby podać krótką nazwę klasy.</span><span class="sxs-lookup"><span data-stu-id="c5fd0-112">Use this attribute to provide a short name for your class.</span></span> <span data-ttu-id="c5fd0-113">Należy określić ciąg, który spełnia wymagania określone w polu [Określanie w pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="c5fd0-113">You must specify a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5fd0-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c5fd0-114">Child Elements</span></span>  
 <span data-ttu-id="c5fd0-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="c5fd0-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c5fd0-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c5fd0-116">Parent Elements</span></span>  
  
|<span data-ttu-id="c5fd0-117">Element</span><span class="sxs-lookup"><span data-stu-id="c5fd0-117">Element</span></span>|<span data-ttu-id="c5fd0-118">Opis</span><span class="sxs-lookup"><span data-stu-id="c5fd0-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c5fd0-119">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c5fd0-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptoClasses`|<span data-ttu-id="c5fd0-120">Zawiera listę klas kryptograficznych, które mają mapowanie do przyjaznej nazwy w [\<nameEntry>](nameentry-element.md) elemencie.</span><span class="sxs-lookup"><span data-stu-id="c5fd0-120">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="c5fd0-121">Zawiera ustawienia kryptografii.</span><span class="sxs-lookup"><span data-stu-id="c5fd0-121">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="c5fd0-122">Zawiera mapowania klas do przyjaznych nazw.</span><span class="sxs-lookup"><span data-stu-id="c5fd0-122">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="c5fd0-123">Zawiera [\<cryptographySettings>](cryptographysettings-element.md) element.</span><span class="sxs-lookup"><span data-stu-id="c5fd0-123">Contains the [\<cryptographySettings>](cryptographysettings-element.md) element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c5fd0-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="c5fd0-124">Example</span></span>  
 <span data-ttu-id="c5fd0-125">Poniższy przykład pokazuje, jak używać **\<cryptoClass>** elementu do odwoływania się do klasy kryptografii i konfigurowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="c5fd0-125">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="c5fd0-126">Następnie można przekazać ciąg "RSA" do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metody i użyć <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metody do zwrócenia `MyCryptoRSAClass` obiektu.</span><span class="sxs-lookup"><span data-stu-id="c5fd0-126">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c5fd0-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5fd0-127">See also</span></span>

- [<span data-ttu-id="c5fd0-128">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c5fd0-128">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="c5fd0-129">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="c5fd0-129">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c5fd0-130">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="c5fd0-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="c5fd0-131">Konfigurowanie klasy kryptografii</span><span class="sxs-lookup"><span data-stu-id="c5fd0-131">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

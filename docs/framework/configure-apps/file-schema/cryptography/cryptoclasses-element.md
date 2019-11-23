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
ms.openlocfilehash: 89f1d89ea397794e366b53205ac23b94d7892869
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699754"
---
# <a name="cryptoclasses-element"></a><span data-ttu-id="0b00e-102">\<cryptoClasses> Element</span><span class="sxs-lookup"><span data-stu-id="0b00e-102">\<cryptoClasses> Element</span></span>
<span data-ttu-id="0b00e-103">Zawiera listę klas kryptograficznych, które mają mapowanie do przyjaznej nazwy w [\<nameEntry >](nameentry-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="0b00e-103">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  
  
[<span data-ttu-id="0b00e-104"> **> konfiguracji \<** </span><span class="sxs-lookup"><span data-stu-id="0b00e-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="0b00e-105">&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="0b00e-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="0b00e-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptographySettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="0b00e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>  
<span data-ttu-id="0b00e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptoNameMapping >** ](cryptonamemapping-element.md)</span><span class="sxs-lookup"><span data-stu-id="0b00e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span></span>  
<span data-ttu-id="0b00e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<cryptoClasses >**</span><span class="sxs-lookup"><span data-stu-id="0b00e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClasses>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b00e-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="0b00e-109">Syntax</span></span>  
  
```xml  
<cryptoClasses>   
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0b00e-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0b00e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0b00e-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0b00e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0b00e-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0b00e-112">Attributes</span></span>  
 <span data-ttu-id="0b00e-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="0b00e-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0b00e-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0b00e-114">Child Elements</span></span>  
  
|<span data-ttu-id="0b00e-115">Element</span><span class="sxs-lookup"><span data-stu-id="0b00e-115">Element</span></span>|<span data-ttu-id="0b00e-116">Opis</span><span class="sxs-lookup"><span data-stu-id="0b00e-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0b00e-117">\<cryptoClass></span><span class="sxs-lookup"><span data-stu-id="0b00e-117">\<cryptoClass></span></span>](cryptoclass-element.md)|<span data-ttu-id="0b00e-118">Zawiera klasę kryptografii, która ma mapowanie do przyjaznej nazwy w **\<nameEntry >** elementu.</span><span class="sxs-lookup"><span data-stu-id="0b00e-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0b00e-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0b00e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="0b00e-120">Element</span><span class="sxs-lookup"><span data-stu-id="0b00e-120">Element</span></span>|<span data-ttu-id="0b00e-121">Opis</span><span class="sxs-lookup"><span data-stu-id="0b00e-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0b00e-122">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0b00e-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="0b00e-123">Zawiera ustawienia kryptografii.</span><span class="sxs-lookup"><span data-stu-id="0b00e-123">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="0b00e-124">Zawiera mapowania klas do przyjaznych nazw.</span><span class="sxs-lookup"><span data-stu-id="0b00e-124">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="0b00e-125">Zawiera element `cryptographySettings`.</span><span class="sxs-lookup"><span data-stu-id="0b00e-125">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0b00e-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="0b00e-126">Example</span></span>  
 <span data-ttu-id="0b00e-127">Poniższy przykład pokazuje, jak używać elementu **\<cryptoClass >** , aby odwoływać się do klasy kryptografii i skonfigurować środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="0b00e-127">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="0b00e-128">Następnie można przekazać ciąg "RSA" do metody <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> i użyć metody <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> do zwrócenia obiektu `MyCryptoRSAClass`.</span><span class="sxs-lookup"><span data-stu-id="0b00e-128">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0b00e-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0b00e-129">See also</span></span>

- <xref:System.Security.Cryptography>
- [<span data-ttu-id="0b00e-130">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="0b00e-130">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="0b00e-131">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="0b00e-131">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0b00e-132">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="0b00e-132">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="0b00e-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span><span class="sxs-lookup"><span data-stu-id="0b00e-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](Overload:System.Security.Cryptography.CryptoConfig.CreateFromName)
- [<span data-ttu-id="0b00e-134">Konfigurowanie klas kryptografii</span><span class="sxs-lookup"><span data-stu-id="0b00e-134">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

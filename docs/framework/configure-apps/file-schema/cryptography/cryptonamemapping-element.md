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
ms.openlocfilehash: 4b3495d17e07ca611a384bf958ee06e928eb2506
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088017"
---
# <a name="cryptonamemapping-element"></a><span data-ttu-id="6a71b-102">\<element > cryptoNameMapping</span><span class="sxs-lookup"><span data-stu-id="6a71b-102">\<cryptoNameMapping> Element</span></span>
<span data-ttu-id="6a71b-103">Zawiera mapowania klas do przyjaznych nazw.</span><span class="sxs-lookup"><span data-stu-id="6a71b-103">Contains mappings of classes to friendly names.</span></span>  

<span data-ttu-id="6a71b-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="6a71b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6a71b-105">&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="6a71b-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>\
<span data-ttu-id="6a71b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptographySettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="6a71b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>\
<span data-ttu-id="6a71b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<cryptoNameMapping >**</span><span class="sxs-lookup"><span data-stu-id="6a71b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoNameMapping>**</span></span>

## <a name="syntax"></a><span data-ttu-id="6a71b-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="6a71b-108">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>   
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6a71b-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6a71b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6a71b-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6a71b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6a71b-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6a71b-111">Attributes</span></span>  
 <span data-ttu-id="6a71b-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="6a71b-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6a71b-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6a71b-113">Child Elements</span></span>  
  
|<span data-ttu-id="6a71b-114">Element</span><span class="sxs-lookup"><span data-stu-id="6a71b-114">Element</span></span>|<span data-ttu-id="6a71b-115">Opis</span><span class="sxs-lookup"><span data-stu-id="6a71b-115">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="6a71b-116">Zawiera listę klas kryptograficznych, które mają mapowanie do przyjaznej nazwy w **\<nameEntry >** elementu.</span><span class="sxs-lookup"><span data-stu-id="6a71b-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="6a71b-117">Mapuje nazwę klasy na przyjazną nazwę algorytmu, która pozwala jednej klasie mieć wiele przyjaznych nazw.</span><span class="sxs-lookup"><span data-stu-id="6a71b-117">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6a71b-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6a71b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="6a71b-119">Element</span><span class="sxs-lookup"><span data-stu-id="6a71b-119">Element</span></span>|<span data-ttu-id="6a71b-120">Opis</span><span class="sxs-lookup"><span data-stu-id="6a71b-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6a71b-121">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6a71b-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="6a71b-122">Zawiera ustawienia kryptografii.</span><span class="sxs-lookup"><span data-stu-id="6a71b-122">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="6a71b-123">Zawiera mapowania klas do przyjaznych nazw.</span><span class="sxs-lookup"><span data-stu-id="6a71b-123">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="6a71b-124">Zawiera element \<cryptographySettings >.</span><span class="sxs-lookup"><span data-stu-id="6a71b-124">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6a71b-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="6a71b-125">Example</span></span>  
 <span data-ttu-id="6a71b-126">Poniższy przykład pokazuje, jak używać elementu **\<cryptoNameMapping >** , aby odwoływać się do klasy kryptografii i skonfigurować środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="6a71b-126">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="6a71b-127">Następnie można przekazać ciąg "RSA" do metody <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> i użyć metody <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> do zwrócenia obiektu `MyCryptoRSAClass`.</span><span class="sxs-lookup"><span data-stu-id="6a71b-127">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6a71b-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a71b-128">See also</span></span>

- [<span data-ttu-id="6a71b-129">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6a71b-129">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="6a71b-130">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="6a71b-130">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6a71b-131">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="6a71b-131">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="6a71b-132">Konfigurowanie klas kryptografii</span><span class="sxs-lookup"><span data-stu-id="6a71b-132">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

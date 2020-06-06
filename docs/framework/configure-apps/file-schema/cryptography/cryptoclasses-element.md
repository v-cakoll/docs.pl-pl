---
title: <cryptoClasses> Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClasses
helpviewer_keywords:
- <cryptoClasses> element
- cryptoClasses element
ms.assetid: 290d5f96-946d-4f02-babb-1d31ec0b8295
ms.openlocfilehash: c93fadf51297d59ab499e25de283700364903049
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155249"
---
# <a name="cryptoclasses-element"></a><span data-ttu-id="79e72-102">\<cryptoClasses> Element</span><span class="sxs-lookup"><span data-stu-id="79e72-102">\<cryptoClasses> Element</span></span>
<span data-ttu-id="79e72-103">Zawiera listę klas kryptograficznych, które mają mapowanie do przyjaznej nazwy w [\<nameEntry>](nameentry-element.md) elemencie.</span><span class="sxs-lookup"><span data-stu-id="79e72-103">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClasses>**  
  
## <a name="syntax"></a><span data-ttu-id="79e72-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="79e72-104">Syntax</span></span>  
  
```xml  
<cryptoClasses>
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79e72-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="79e72-105">Attributes and Elements</span></span>  
 <span data-ttu-id="79e72-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="79e72-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79e72-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="79e72-107">Attributes</span></span>  
 <span data-ttu-id="79e72-108">Brak.</span><span class="sxs-lookup"><span data-stu-id="79e72-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="79e72-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="79e72-109">Child Elements</span></span>  
  
|<span data-ttu-id="79e72-110">Element</span><span class="sxs-lookup"><span data-stu-id="79e72-110">Element</span></span>|<span data-ttu-id="79e72-111">Opis</span><span class="sxs-lookup"><span data-stu-id="79e72-111">Description</span></span>|  
|-------------|-----------------|  
|[\<cryptoClass>](cryptoclass-element.md)|<span data-ttu-id="79e72-112">Zawiera klasę kryptografii, która ma mapowanie do przyjaznej nazwy w **\<nameEntry>** elemencie.</span><span class="sxs-lookup"><span data-stu-id="79e72-112">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="79e72-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="79e72-113">Parent Elements</span></span>  
  
|<span data-ttu-id="79e72-114">Element</span><span class="sxs-lookup"><span data-stu-id="79e72-114">Element</span></span>|<span data-ttu-id="79e72-115">Opis</span><span class="sxs-lookup"><span data-stu-id="79e72-115">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="79e72-116">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="79e72-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="79e72-117">Zawiera ustawienia kryptografii.</span><span class="sxs-lookup"><span data-stu-id="79e72-117">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="79e72-118">Zawiera mapowania klas do przyjaznych nazw.</span><span class="sxs-lookup"><span data-stu-id="79e72-118">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="79e72-119">Zawiera `cryptographySettings` element.</span><span class="sxs-lookup"><span data-stu-id="79e72-119">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="79e72-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="79e72-120">Example</span></span>  
 <span data-ttu-id="79e72-121">Poniższy przykład pokazuje, jak używać **\<cryptoClass>** elementu do odwoływania się do klasy kryptografii i konfigurowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="79e72-121">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="79e72-122">Następnie można przekazać ciąg "RSA" do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metody i użyć <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metody do zwrócenia `MyCryptoRSAClass` obiektu.</span><span class="sxs-lookup"><span data-stu-id="79e72-122">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="79e72-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="79e72-123">See also</span></span>

- <xref:System.Security.Cryptography>
- [<span data-ttu-id="79e72-124">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="79e72-124">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="79e72-125">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="79e72-125">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="79e72-126">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="79e72-126">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="79e72-127">System. Security. Cryptography. obiektu CryptoConfig. isfromname</span><span class="sxs-lookup"><span data-stu-id="79e72-127">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A)
- [<span data-ttu-id="79e72-128">Konfigurowanie klasy kryptografii</span><span class="sxs-lookup"><span data-stu-id="79e72-128">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

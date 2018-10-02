---
title: '&lt;mscorlib&gt; Element ustawień kryptografii'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mscorlib
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib
helpviewer_keywords:
- mscorlib element
- <mscorlib> element
ms.assetid: d549668f-31f1-4b92-8021-a9135c09ca3c
author: mcleblanc
ms.author: markl
ms.openlocfilehash: b5da49ff22cfa6bd1c3e4d574865eb5e61dc73fb
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48028365"
---
# <a name="ltmscorlibgt-element-for-cryptography-settings"></a><span data-ttu-id="d1f97-102">&lt;mscorlib&gt; Element ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="d1f97-102">&lt;mscorlib&gt; Element for Cryptography Settings</span></span>
<span data-ttu-id="d1f97-103">Zawiera [ \<cryptographysettings — > element](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md).</span><span class="sxs-lookup"><span data-stu-id="d1f97-103">Contains the [\<cryptographySettings> element](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md).</span></span>  
  
 <span data-ttu-id="d1f97-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="d1f97-104">\<configuration></span></span>  
<span data-ttu-id="d1f97-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="d1f97-105">\<mscorlib></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1f97-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1f97-106">Syntax</span></span>  
  
```xml  
      <mscorlib>   
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1f97-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d1f97-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d1f97-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d1f97-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1f97-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d1f97-109">Attributes</span></span>  
 <span data-ttu-id="d1f97-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="d1f97-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d1f97-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d1f97-111">Child Elements</span></span>  
  
|<span data-ttu-id="d1f97-112">Element</span><span class="sxs-lookup"><span data-stu-id="d1f97-112">Element</span></span>|<span data-ttu-id="d1f97-113">Opis</span><span class="sxs-lookup"><span data-stu-id="d1f97-113">Description</span></span>|  
|-------------|-----------------|  
|`cryptographySettings`|<span data-ttu-id="d1f97-114">Zawiera ustawienia szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="d1f97-114">Contains cryptography settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d1f97-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d1f97-115">Parent Elements</span></span>  
  
|<span data-ttu-id="d1f97-116">Element</span><span class="sxs-lookup"><span data-stu-id="d1f97-116">Element</span></span>|<span data-ttu-id="d1f97-117">Opis</span><span class="sxs-lookup"><span data-stu-id="d1f97-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d1f97-118">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d1f97-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d1f97-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="d1f97-119">Example</span></span>  
 <span data-ttu-id="d1f97-120">Poniższy przykład pokazuje, jak używać  **\<mscorlib >** element odwołuje się do klasy kryptografii i konfigurowanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="d1f97-120">The following example shows how to use the **\<mscorlib>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="d1f97-121">Ciąg "RSA" można następnie przekazać do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metody i użyj <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodę, aby zwrócić `MyCryptoRSAClass` obiektu.</span><span class="sxs-lookup"><span data-stu-id="d1f97-121">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d1f97-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d1f97-122">See Also</span></span>  
 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>  
 <xref:System.Security.Cryptography>  
 [<span data-ttu-id="d1f97-123">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d1f97-123">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="d1f97-124">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="d1f97-124">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="d1f97-125">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="d1f97-125">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="d1f97-126">Konfigurowanie klas kryptografii</span><span class="sxs-lookup"><span data-stu-id="d1f97-126">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)

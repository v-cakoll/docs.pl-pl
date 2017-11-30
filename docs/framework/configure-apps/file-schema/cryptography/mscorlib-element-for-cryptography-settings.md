---
title: "&lt;mscorlib&gt; Element ustawień kryptografii"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mscorlib
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib
helpviewer_keywords:
- mscorlib element
- <mscorlib> element
ms.assetid: d549668f-31f1-4b92-8021-a9135c09ca3c
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 992e62575dccae3f68df27fb7dd027dceab91ffc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltmscorlibgt-element-for-cryptography-settings"></a><span data-ttu-id="f67d6-102">&lt;mscorlib&gt; Element ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="f67d6-102">&lt;mscorlib&gt; Element for Cryptography Settings</span></span>
<span data-ttu-id="f67d6-103">Zawiera [ \<cryptographysettings — > elementu](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md).</span><span class="sxs-lookup"><span data-stu-id="f67d6-103">Contains the [\<cryptographySettings> element](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md).</span></span>  
  
 <span data-ttu-id="f67d6-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="f67d6-104">\<configuration></span></span>  
<span data-ttu-id="f67d6-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="f67d6-105">\<mscorlib></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f67d6-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="f67d6-106">Syntax</span></span>  
  
```xml  
      <mscorlib>   
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f67d6-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f67d6-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f67d6-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f67d6-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f67d6-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f67d6-109">Attributes</span></span>  
 <span data-ttu-id="f67d6-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="f67d6-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f67d6-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f67d6-111">Child Elements</span></span>  
  
|<span data-ttu-id="f67d6-112">Element</span><span class="sxs-lookup"><span data-stu-id="f67d6-112">Element</span></span>|<span data-ttu-id="f67d6-113">Opis</span><span class="sxs-lookup"><span data-stu-id="f67d6-113">Description</span></span>|  
|-------------|-----------------|  
|`cryptographySettings`|<span data-ttu-id="f67d6-114">Zawiera ustawienia szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="f67d6-114">Contains cryptography settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f67d6-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f67d6-115">Parent Elements</span></span>  
  
|<span data-ttu-id="f67d6-116">Element</span><span class="sxs-lookup"><span data-stu-id="f67d6-116">Element</span></span>|<span data-ttu-id="f67d6-117">Opis</span><span class="sxs-lookup"><span data-stu-id="f67d6-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f67d6-118">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f67d6-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f67d6-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="f67d6-119">Example</span></span>  
 <span data-ttu-id="f67d6-120">Poniższy przykład przedstawia użycie  **\<mscorlib >** element odwołuje się do klasy kryptografii i skonfigurować środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="f67d6-120">The following example shows how to use the **\<mscorlib>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="f67d6-121">Ciąg "RSA" można następnie przekazać do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> — metoda i użyj <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodę, aby zwrócić `MyCryptoRSAClass` obiektu.</span><span class="sxs-lookup"><span data-stu-id="f67d6-121">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f67d6-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f67d6-122">See Also</span></span>  
 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>  
 <xref:System.Security.Cryptography>  
 [<span data-ttu-id="f67d6-123">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f67d6-123">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="f67d6-124">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="f67d6-124">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="f67d6-125">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="f67d6-125">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="f67d6-126">Konfigurowanie klasy kryptografii</span><span class="sxs-lookup"><span data-stu-id="f67d6-126">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)

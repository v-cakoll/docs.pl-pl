---
title: <mscorlib>, element ustawień kryptografii
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mscorlib
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib
helpviewer_keywords:
- mscorlib element
- <mscorlib> element
ms.assetid: d549668f-31f1-4b92-8021-a9135c09ca3c
ms.openlocfilehash: d1d805f7154c18dba2dcd4eb7228cc200d8da811
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155184"
---
# <a name="mscorlib-element-for-cryptography-settings"></a><span data-ttu-id="f0daf-102">\<mscorlib> element dla ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="f0daf-102">\<mscorlib> Element for Cryptography Settings</span></span>
<span data-ttu-id="f0daf-103">Zawiera [kryptografięSze> element . \<](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="f0daf-103">Contains the [\<cryptographySettings> element](cryptographysettings-element.md).</span></span>  
  
[<span data-ttu-id="f0daf-104">**\<>konfiguracyjne**</span><span class="sxs-lookup"><span data-stu-id="f0daf-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="f0daf-105">&nbsp;&nbsp;**\<mscorlib>**</span><span class="sxs-lookup"><span data-stu-id="f0daf-105">&nbsp;&nbsp;**\<mscorlib>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0daf-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="f0daf-106">Syntax</span></span>  
  
```xml  
      <mscorlib>
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0daf-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f0daf-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f0daf-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f0daf-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0daf-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f0daf-109">Attributes</span></span>  
 <span data-ttu-id="f0daf-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="f0daf-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f0daf-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f0daf-111">Child Elements</span></span>  
  
|<span data-ttu-id="f0daf-112">Element</span><span class="sxs-lookup"><span data-stu-id="f0daf-112">Element</span></span>|<span data-ttu-id="f0daf-113">Opis</span><span class="sxs-lookup"><span data-stu-id="f0daf-113">Description</span></span>|  
|-------------|-----------------|  
|`cryptographySettings`|<span data-ttu-id="f0daf-114">Zawiera ustawienia kryptografii.</span><span class="sxs-lookup"><span data-stu-id="f0daf-114">Contains cryptography settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f0daf-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f0daf-115">Parent Elements</span></span>  
  
|<span data-ttu-id="f0daf-116">Element</span><span class="sxs-lookup"><span data-stu-id="f0daf-116">Element</span></span>|<span data-ttu-id="f0daf-117">Opis</span><span class="sxs-lookup"><span data-stu-id="f0daf-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f0daf-118">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f0daf-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f0daf-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="f0daf-119">Example</span></span>  
 <span data-ttu-id="f0daf-120">W poniższym przykładzie pokazano, jak używać \*\* \<mscorlib>\*\* element do odwoływania się do klasy kryptografii i skonfigurować środowisko wykonawcze.</span><span class="sxs-lookup"><span data-stu-id="f0daf-120">The following example shows how to use the **\<mscorlib>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="f0daf-121">Następnie można przekazać ciąg "RSA" <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> do metody <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> i użyć `MyCryptoRSAClass` metody, aby zwrócić obiekt.</span><span class="sxs-lookup"><span data-stu-id="f0daf-121">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f0daf-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f0daf-122">See also</span></span>

- <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>
- <xref:System.Security.Cryptography>
- [<span data-ttu-id="f0daf-123">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f0daf-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="f0daf-124">Schemat ustawień kryptografii</span><span class="sxs-lookup"><span data-stu-id="f0daf-124">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f0daf-125">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="f0daf-125">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="f0daf-126">Konfigurowanie klas kryptografii</span><span class="sxs-lookup"><span data-stu-id="f0daf-126">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)

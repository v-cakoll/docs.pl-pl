---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 3f3d79d3567c1714a79423b7767ce3f454b9d52d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152791"
---
# <a name="certificatevalidator"></a><span data-ttu-id="773ce-101">\<certyfikatValidator></span><span class="sxs-lookup"><span data-stu-id="773ce-101">\<certificateValidator></span></span>
<span data-ttu-id="773ce-102">Określa typ niestandardowy sprawdzania poprawności certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="773ce-102">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="773ce-103">Ten typ jest używany `certificateValidationMode` tylko wtedy, gdy atrybut [ \<certificateValidation>](certificatevalidation.md) element jest ustawiony na "Niestandardowe".</span><span class="sxs-lookup"><span data-stu-id="773ce-103">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>  
  
<span data-ttu-id="773ce-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="773ce-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="773ce-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="773ce-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="773ce-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>konfiguracji tożsamości**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="773ce-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="773ce-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>certyfikatuWeracja**](certificatevalidation.md)</span><span class="sxs-lookup"><span data-stu-id="773ce-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<certificateValidation>**](certificatevalidation.md)</span></span>\
<span data-ttu-id="773ce-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certyfikatValidator>**</span><span class="sxs-lookup"><span data-stu-id="773ce-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidator>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="773ce-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="773ce-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation>  
      <certificateValidator type=xs:string>  
      </certificateValidator>  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="773ce-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="773ce-110">Attributes and Elements</span></span>  
 <span data-ttu-id="773ce-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="773ce-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="773ce-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="773ce-112">Attributes</span></span>  
  
|<span data-ttu-id="773ce-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="773ce-113">Attribute</span></span>|<span data-ttu-id="773ce-114">Opis</span><span class="sxs-lookup"><span data-stu-id="773ce-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="773ce-115">type</span><span class="sxs-lookup"><span data-stu-id="773ce-115">type</span></span>|<span data-ttu-id="773ce-116">Określa typ niestandardowy, który <xref:System.IdentityModel.Selectors.X509CertificateValidator> pochodzi z klasy.</span><span class="sxs-lookup"><span data-stu-id="773ce-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="773ce-117">Ustaw `certificateValidationMode` atrybut [ \<certificateValidation>](certificatevalidation.md) element na "Niestandardowe", aby użyć tego typu.</span><span class="sxs-lookup"><span data-stu-id="773ce-117">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="773ce-118">Aby uzyskać więcej informacji `type` na temat określania atrybutu, zobacz [Odwołania do typów niestandardowych](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="773ce-118">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="773ce-119">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="773ce-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="773ce-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="773ce-120">Child Elements</span></span>  
 <span data-ttu-id="773ce-121">Brak</span><span class="sxs-lookup"><span data-stu-id="773ce-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="773ce-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="773ce-122">Parent Elements</span></span>  
  
|<span data-ttu-id="773ce-123">Element</span><span class="sxs-lookup"><span data-stu-id="773ce-123">Element</span></span>|<span data-ttu-id="773ce-124">Opis</span><span class="sxs-lookup"><span data-stu-id="773ce-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="773ce-125">\<>certyfikatuWeracja</span><span class="sxs-lookup"><span data-stu-id="773ce-125">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="773ce-126">Steruje ustawieniami używanymi przez programy obsługi tokenów do sprawdzania poprawności certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="773ce-126">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="773ce-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="773ce-127">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />
</certificateValidation>
```

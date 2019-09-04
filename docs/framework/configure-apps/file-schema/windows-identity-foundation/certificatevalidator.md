---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 30f81dd5948a7d366c1116cffd347c85a396f5ae
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252122"
---
# <a name="certificatevalidator"></a><span data-ttu-id="8ee5a-101">\<certificateValidator></span><span class="sxs-lookup"><span data-stu-id="8ee5a-101">\<certificateValidator></span></span>
<span data-ttu-id="8ee5a-102">Określa typ niestandardowy na potrzeby walidacji certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="8ee5a-102">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="8ee5a-103">Ten typ jest używany tylko wtedy, `certificateValidationMode` gdy atrybut [ \<elementu certificateValidation >](certificatevalidation.md) jest ustawiony na wartość "Custom".</span><span class="sxs-lookup"><span data-stu-id="8ee5a-103">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>  
  
<span data-ttu-id="8ee5a-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8ee5a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8ee5a-105">&nbsp;&nbsp;[ **\<> System. identityModel**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="8ee5a-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="8ee5a-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="8ee5a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="8ee5a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<certificateValidation >** ](certificatevalidation.md)</span><span class="sxs-lookup"><span data-stu-id="8ee5a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<certificateValidation>**](certificatevalidation.md)</span></span>\
<span data-ttu-id="8ee5a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<certificateValidator >**</span><span class="sxs-lookup"><span data-stu-id="8ee5a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidator>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ee5a-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="8ee5a-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ee5a-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8ee5a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8ee5a-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8ee5a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ee5a-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8ee5a-112">Attributes</span></span>  
  
|<span data-ttu-id="8ee5a-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8ee5a-113">Attribute</span></span>|<span data-ttu-id="8ee5a-114">Opis</span><span class="sxs-lookup"><span data-stu-id="8ee5a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8ee5a-115">— typ</span><span class="sxs-lookup"><span data-stu-id="8ee5a-115">type</span></span>|<span data-ttu-id="8ee5a-116">Określa typ niestandardowy, który pochodzi od <xref:System.IdentityModel.Selectors.X509CertificateValidator> klasy.</span><span class="sxs-lookup"><span data-stu-id="8ee5a-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="8ee5a-117">`certificateValidationMode` Ustaw [atrybut certificateValidation\<elementu >](certificatevalidation.md) na wartość "Custom", aby użyć tego typu.</span><span class="sxs-lookup"><span data-stu-id="8ee5a-117">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="8ee5a-118">Aby uzyskać więcej informacji na temat sposobu określania `type` atrybutu, zobacz [odwołania do typów niestandardowych](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="8ee5a-118">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="8ee5a-119">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8ee5a-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8ee5a-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8ee5a-120">Child Elements</span></span>  
 <span data-ttu-id="8ee5a-121">Brak</span><span class="sxs-lookup"><span data-stu-id="8ee5a-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8ee5a-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8ee5a-122">Parent Elements</span></span>  
  
|<span data-ttu-id="8ee5a-123">Element</span><span class="sxs-lookup"><span data-stu-id="8ee5a-123">Element</span></span>|<span data-ttu-id="8ee5a-124">Opis</span><span class="sxs-lookup"><span data-stu-id="8ee5a-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8ee5a-125">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="8ee5a-125">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="8ee5a-126">Kontroluje ustawienia używane przez programy obsługi do sprawdzania poprawności certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="8ee5a-126">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8ee5a-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ee5a-127">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```

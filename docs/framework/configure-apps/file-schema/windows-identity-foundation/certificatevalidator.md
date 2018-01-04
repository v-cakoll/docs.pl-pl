---
title: '&lt;certificateValidator&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 98112b3f13ff0b8e4be50f158ce40b048b213248
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltcertificatevalidatorgt"></a><span data-ttu-id="1d228-102">&lt;certificateValidator&gt;</span><span class="sxs-lookup"><span data-stu-id="1d228-102">&lt;certificateValidator&gt;</span></span>
<span data-ttu-id="1d228-103">Określa typ niestandardowy o sprawdzenie poprawności certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="1d228-103">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="1d228-104">Ten typ jest używany tylko wtedy, gdy `certificateValidationMode` atrybutu [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element jest ustawiony na "Custom".</span><span class="sxs-lookup"><span data-stu-id="1d228-104">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>  
  
 <span data-ttu-id="1d228-105">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="1d228-105">\<system.identityModel></span></span>  
<span data-ttu-id="1d228-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1d228-106">\<identityConfiguration></span></span>  
<span data-ttu-id="1d228-107">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="1d228-107">\<certificateValidation></span></span>  
<span data-ttu-id="1d228-108">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="1d228-108">\<certificateValidator></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d228-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="1d228-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d228-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1d228-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1d228-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1d228-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d228-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1d228-112">Attributes</span></span>  
  
|<span data-ttu-id="1d228-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1d228-113">Attribute</span></span>|<span data-ttu-id="1d228-114">Opis</span><span class="sxs-lookup"><span data-stu-id="1d228-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1d228-115">— typ</span><span class="sxs-lookup"><span data-stu-id="1d228-115">type</span></span>|<span data-ttu-id="1d228-116">Określa typ niestandardowy, która jest pochodną <xref:System.IdentityModel.Selectors.X509CertificateValidator> klasy.</span><span class="sxs-lookup"><span data-stu-id="1d228-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="1d228-117">Ustaw `certificateValidationMode` atrybutu [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) elementu na "Custom", aby użyć tego typu.</span><span class="sxs-lookup"><span data-stu-id="1d228-117">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="1d228-118">Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołuje się do niestandardowego typu](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="1d228-118">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="1d228-119">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="1d228-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d228-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1d228-120">Child Elements</span></span>  
 <span data-ttu-id="1d228-121">Brak</span><span class="sxs-lookup"><span data-stu-id="1d228-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1d228-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1d228-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1d228-123">Element</span><span class="sxs-lookup"><span data-stu-id="1d228-123">Element</span></span>|<span data-ttu-id="1d228-124">Opis</span><span class="sxs-lookup"><span data-stu-id="1d228-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d228-125">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="1d228-125">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="1d228-126">Określa ustawienia, które programy obsługi token służący do weryfikowania certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="1d228-126">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1d228-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d228-127">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```

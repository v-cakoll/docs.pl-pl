---
title: '&lt;certificateValidator&gt;'
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 65b8aa6fa4422579ce0d1c5e33d3418ea051612a
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48849701"
---
# <a name="ltcertificatevalidatorgt"></a><span data-ttu-id="a5a3d-102">&lt;certificateValidator&gt;</span><span class="sxs-lookup"><span data-stu-id="a5a3d-102">&lt;certificateValidator&gt;</span></span>
<span data-ttu-id="a5a3d-103">Określa typ niestandardowy do weryfikacji certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="a5a3d-103">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="a5a3d-104">Ten typ jest używany tylko wtedy, gdy `certificateValidationMode` atrybutu [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element jest ustawiony na "Niestandardowe".</span><span class="sxs-lookup"><span data-stu-id="a5a3d-104">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>  
  
 <span data-ttu-id="a5a3d-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="a5a3d-105">\<system.identityModel></span></span>  
<span data-ttu-id="a5a3d-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="a5a3d-106">\<identityConfiguration></span></span>  
<span data-ttu-id="a5a3d-107">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="a5a3d-107">\<certificateValidation></span></span>  
<span data-ttu-id="a5a3d-108">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="a5a3d-108">\<certificateValidator></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5a3d-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="a5a3d-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5a3d-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a5a3d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a5a3d-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a5a3d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5a3d-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a5a3d-112">Attributes</span></span>  
  
|<span data-ttu-id="a5a3d-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a5a3d-113">Attribute</span></span>|<span data-ttu-id="a5a3d-114">Opis</span><span class="sxs-lookup"><span data-stu-id="a5a3d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a5a3d-115">— typ</span><span class="sxs-lookup"><span data-stu-id="a5a3d-115">type</span></span>|<span data-ttu-id="a5a3d-116">Określa typ niestandardowy, który pochodzi od klasy <xref:System.IdentityModel.Selectors.X509CertificateValidator> klasy.</span><span class="sxs-lookup"><span data-stu-id="a5a3d-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="a5a3d-117">Ustaw `certificateValidationMode` atrybutu [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element na "Niestandardowe", aby użyć tego typu.</span><span class="sxs-lookup"><span data-stu-id="a5a3d-117">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="a5a3d-118">Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołań do typu niestandardowego](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="a5a3d-118">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="a5a3d-119">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="a5a3d-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a5a3d-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a5a3d-120">Child Elements</span></span>  
 <span data-ttu-id="a5a3d-121">Brak</span><span class="sxs-lookup"><span data-stu-id="a5a3d-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a5a3d-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a5a3d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="a5a3d-123">Element</span><span class="sxs-lookup"><span data-stu-id="a5a3d-123">Element</span></span>|<span data-ttu-id="a5a3d-124">Opis</span><span class="sxs-lookup"><span data-stu-id="a5a3d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5a3d-125">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="a5a3d-125">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="a5a3d-126">Określa ustawienia, które programy obsługi tokenów służący do weryfikowania certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="a5a3d-126">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a5a3d-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5a3d-127">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```

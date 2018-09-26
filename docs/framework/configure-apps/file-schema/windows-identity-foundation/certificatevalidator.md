---
title: '&lt;certificateValidator&gt;'
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 65b8aa6fa4422579ce0d1c5e33d3418ea051612a
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47077658"
---
# <a name="ltcertificatevalidatorgt"></a><span data-ttu-id="64148-102">&lt;certificateValidator&gt;</span><span class="sxs-lookup"><span data-stu-id="64148-102">&lt;certificateValidator&gt;</span></span>
<span data-ttu-id="64148-103">Określa typ niestandardowy do weryfikacji certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="64148-103">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="64148-104">Ten typ jest używany tylko wtedy, gdy `certificateValidationMode` atrybutu [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element jest ustawiony na "Niestandardowe".</span><span class="sxs-lookup"><span data-stu-id="64148-104">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>  
  
 <span data-ttu-id="64148-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="64148-105">\<system.identityModel></span></span>  
<span data-ttu-id="64148-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="64148-106">\<identityConfiguration></span></span>  
<span data-ttu-id="64148-107">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="64148-107">\<certificateValidation></span></span>  
<span data-ttu-id="64148-108">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="64148-108">\<certificateValidator></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64148-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="64148-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="64148-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="64148-110">Attributes and Elements</span></span>  
 <span data-ttu-id="64148-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="64148-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="64148-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="64148-112">Attributes</span></span>  
  
|<span data-ttu-id="64148-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="64148-113">Attribute</span></span>|<span data-ttu-id="64148-114">Opis</span><span class="sxs-lookup"><span data-stu-id="64148-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="64148-115">— typ</span><span class="sxs-lookup"><span data-stu-id="64148-115">type</span></span>|<span data-ttu-id="64148-116">Określa typ niestandardowy, który pochodzi od klasy <xref:System.IdentityModel.Selectors.X509CertificateValidator> klasy.</span><span class="sxs-lookup"><span data-stu-id="64148-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="64148-117">Ustaw `certificateValidationMode` atrybutu [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element na "Niestandardowe", aby użyć tego typu.</span><span class="sxs-lookup"><span data-stu-id="64148-117">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="64148-118">Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołań do typu niestandardowego](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="64148-118">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="64148-119">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="64148-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="64148-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="64148-120">Child Elements</span></span>  
 <span data-ttu-id="64148-121">Brak</span><span class="sxs-lookup"><span data-stu-id="64148-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="64148-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="64148-122">Parent Elements</span></span>  
  
|<span data-ttu-id="64148-123">Element</span><span class="sxs-lookup"><span data-stu-id="64148-123">Element</span></span>|<span data-ttu-id="64148-124">Opis</span><span class="sxs-lookup"><span data-stu-id="64148-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="64148-125">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="64148-125">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="64148-126">Określa ustawienia, które programy obsługi tokenów służący do weryfikowania certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="64148-126">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="64148-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="64148-127">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```

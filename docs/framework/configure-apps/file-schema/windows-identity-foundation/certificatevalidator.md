---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: df52212305e0865b8c03fdd49068cb7c7da4fa38
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55277458"
---
# <a name="certificatevalidator"></a><span data-ttu-id="f79cc-101">\<certificateValidator></span><span class="sxs-lookup"><span data-stu-id="f79cc-101">\<certificateValidator></span></span>
<span data-ttu-id="f79cc-102">Określa typ niestandardowy do weryfikacji certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="f79cc-102">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="f79cc-103">Ten typ jest używany tylko wtedy, gdy `certificateValidationMode` atrybutu [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element jest ustawiony na "Niestandardowe".</span><span class="sxs-lookup"><span data-stu-id="f79cc-103">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>  
  
 <span data-ttu-id="f79cc-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="f79cc-104">\<system.identityModel></span></span>  
<span data-ttu-id="f79cc-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="f79cc-105">\<identityConfiguration></span></span>  
<span data-ttu-id="f79cc-106">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="f79cc-106">\<certificateValidation></span></span>  
<span data-ttu-id="f79cc-107">\<certificateValidator></span><span class="sxs-lookup"><span data-stu-id="f79cc-107">\<certificateValidator></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f79cc-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="f79cc-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f79cc-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f79cc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f79cc-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f79cc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f79cc-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f79cc-111">Attributes</span></span>  
  
|<span data-ttu-id="f79cc-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f79cc-112">Attribute</span></span>|<span data-ttu-id="f79cc-113">Opis</span><span class="sxs-lookup"><span data-stu-id="f79cc-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f79cc-114">— typ</span><span class="sxs-lookup"><span data-stu-id="f79cc-114">type</span></span>|<span data-ttu-id="f79cc-115">Określa typ niestandardowy, który pochodzi od klasy <xref:System.IdentityModel.Selectors.X509CertificateValidator> klasy.</span><span class="sxs-lookup"><span data-stu-id="f79cc-115">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="f79cc-116">Ustaw `certificateValidationMode` atrybutu [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element na "Niestandardowe", aby użyć tego typu.</span><span class="sxs-lookup"><span data-stu-id="f79cc-116">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="f79cc-117">Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołań do typu niestandardowego](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="f79cc-117">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="f79cc-118">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="f79cc-118">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f79cc-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f79cc-119">Child Elements</span></span>  
 <span data-ttu-id="f79cc-120">Brak</span><span class="sxs-lookup"><span data-stu-id="f79cc-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f79cc-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f79cc-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f79cc-122">Element</span><span class="sxs-lookup"><span data-stu-id="f79cc-122">Element</span></span>|<span data-ttu-id="f79cc-123">Opis</span><span class="sxs-lookup"><span data-stu-id="f79cc-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f79cc-124">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="f79cc-124">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="f79cc-125">Określa ustawienia, które programy obsługi tokenów służący do weryfikowania certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="f79cc-125">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f79cc-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="f79cc-126">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```

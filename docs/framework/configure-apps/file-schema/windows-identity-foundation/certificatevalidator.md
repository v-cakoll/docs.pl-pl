---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: c25f183679f41f51ffee4f482bfe7a64763647d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941907"
---
# <a name="certificatevalidator"></a><span data-ttu-id="93074-101">\<certificateValidator></span><span class="sxs-lookup"><span data-stu-id="93074-101">\<certificateValidator></span></span>
<span data-ttu-id="93074-102">Określa typ niestandardowy na potrzeby walidacji certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="93074-102">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="93074-103">Ten typ jest używany tylko wtedy, `certificateValidationMode` gdy atrybut [ \<elementu certificateValidation >](certificatevalidation.md) jest ustawiony na wartość "Custom".</span><span class="sxs-lookup"><span data-stu-id="93074-103">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>  
  
 <span data-ttu-id="93074-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="93074-104">\<system.identityModel></span></span>  
<span data-ttu-id="93074-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="93074-105">\<identityConfiguration></span></span>  
<span data-ttu-id="93074-106">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="93074-106">\<certificateValidation></span></span>  
<span data-ttu-id="93074-107">\<certificateValidator></span><span class="sxs-lookup"><span data-stu-id="93074-107">\<certificateValidator></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93074-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="93074-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93074-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="93074-109">Attributes and Elements</span></span>  
 <span data-ttu-id="93074-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="93074-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93074-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="93074-111">Attributes</span></span>  
  
|<span data-ttu-id="93074-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="93074-112">Attribute</span></span>|<span data-ttu-id="93074-113">Opis</span><span class="sxs-lookup"><span data-stu-id="93074-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="93074-114">— typ</span><span class="sxs-lookup"><span data-stu-id="93074-114">type</span></span>|<span data-ttu-id="93074-115">Określa typ niestandardowy, który pochodzi od <xref:System.IdentityModel.Selectors.X509CertificateValidator> klasy.</span><span class="sxs-lookup"><span data-stu-id="93074-115">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="93074-116">`certificateValidationMode` Ustaw [atrybut certificateValidation\<elementu >](certificatevalidation.md) na wartość "Custom", aby użyć tego typu.</span><span class="sxs-lookup"><span data-stu-id="93074-116">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="93074-117">Aby uzyskać więcej informacji na temat sposobu określania `type` atrybutu, zobacz [odwołania do typów niestandardowych](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="93074-117">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="93074-118">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="93074-118">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="93074-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="93074-119">Child Elements</span></span>  
 <span data-ttu-id="93074-120">Brak</span><span class="sxs-lookup"><span data-stu-id="93074-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="93074-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="93074-121">Parent Elements</span></span>  
  
|<span data-ttu-id="93074-122">Element</span><span class="sxs-lookup"><span data-stu-id="93074-122">Element</span></span>|<span data-ttu-id="93074-123">Opis</span><span class="sxs-lookup"><span data-stu-id="93074-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="93074-124">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="93074-124">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="93074-125">Kontroluje ustawienia używane przez programy obsługi do sprawdzania poprawności certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="93074-125">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="93074-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="93074-126">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```

---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 3f3d79d3567c1714a79423b7767ce3f454b9d52d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152791"
---
# \<certificateValidator>
<span data-ttu-id="0345f-101">Określa typ niestandardowy na potrzeby walidacji certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="0345f-101">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="0345f-102">Ten typ jest używany tylko wtedy, gdy `certificateValidationMode` atrybut [\<certificateValidation>](certificatevalidation.md) elementu jest ustawiony na wartość "Custom".</span><span class="sxs-lookup"><span data-stu-id="0345f-102">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<certificateValidation>**](certificatevalidation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidator>**  
  
## <a name="syntax"></a><span data-ttu-id="0345f-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="0345f-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0345f-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0345f-104">Attributes and Elements</span></span>  
 <span data-ttu-id="0345f-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0345f-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0345f-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0345f-106">Attributes</span></span>  
  
|<span data-ttu-id="0345f-107">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0345f-107">Attribute</span></span>|<span data-ttu-id="0345f-108">Opis</span><span class="sxs-lookup"><span data-stu-id="0345f-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0345f-109">typ</span><span class="sxs-lookup"><span data-stu-id="0345f-109">type</span></span>|<span data-ttu-id="0345f-110">Określa typ niestandardowy, który pochodzi od <xref:System.IdentityModel.Selectors.X509CertificateValidator> klasy.</span><span class="sxs-lookup"><span data-stu-id="0345f-110">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="0345f-111">Ustaw `certificateValidationMode` atrybut [\<certificateValidation>](certificatevalidation.md) elementu na wartość "Custom", aby użyć tego typu.</span><span class="sxs-lookup"><span data-stu-id="0345f-111">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="0345f-112">Aby uzyskać więcej informacji na temat sposobu określania `type` atrybutu, zobacz [odwołania do typów niestandardowych](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="0345f-112">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="0345f-113">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0345f-113">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0345f-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0345f-114">Child Elements</span></span>  
 <span data-ttu-id="0345f-115">Brak</span><span class="sxs-lookup"><span data-stu-id="0345f-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0345f-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0345f-116">Parent Elements</span></span>  
  
|<span data-ttu-id="0345f-117">Element</span><span class="sxs-lookup"><span data-stu-id="0345f-117">Element</span></span>|<span data-ttu-id="0345f-118">Opis</span><span class="sxs-lookup"><span data-stu-id="0345f-118">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateValidation>](certificatevalidation.md)|<span data-ttu-id="0345f-119">Kontroluje ustawienia używane przez programy obsługi do sprawdzania poprawności certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="0345f-119">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0345f-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="0345f-120">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />
</certificateValidation>
```

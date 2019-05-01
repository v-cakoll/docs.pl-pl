---
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: 17c4d4289cf90b66d52986c054d4807ecff2b3d8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793890"
---
# <a name="remove"></a><span data-ttu-id="16bde-101">\<remove></span><span class="sxs-lookup"><span data-stu-id="16bde-101">\<remove></span></span>
<span data-ttu-id="16bde-102">Usuwa programu obsługi tokenów zabezpieczeń określone z kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="16bde-102">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="16bde-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="16bde-103">\<system.identityModel></span></span>  
<span data-ttu-id="16bde-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="16bde-104">\<identityConfiguration></span></span>  
<span data-ttu-id="16bde-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="16bde-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="16bde-106">\<remove></span><span class="sxs-lookup"><span data-stu-id="16bde-106">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16bde-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="16bde-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <remove type=xs:string >  
      </remove>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16bde-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="16bde-108">Attributes and Elements</span></span>  
 <span data-ttu-id="16bde-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="16bde-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16bde-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="16bde-110">Attributes</span></span>  
  
|<span data-ttu-id="16bde-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="16bde-111">Attribute</span></span>|<span data-ttu-id="16bde-112">Opis</span><span class="sxs-lookup"><span data-stu-id="16bde-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="16bde-113">— typ</span><span class="sxs-lookup"><span data-stu-id="16bde-113">type</span></span>|<span data-ttu-id="16bde-114">Nazwa typu CLR programu obsługi tokenów do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="16bde-114">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="16bde-115">Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołań do typu niestandardowego](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="16bde-115">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span> <span data-ttu-id="16bde-116">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="16bde-116">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16bde-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="16bde-117">Child Elements</span></span>  
 <span data-ttu-id="16bde-118">Brak</span><span class="sxs-lookup"><span data-stu-id="16bde-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="16bde-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="16bde-119">Parent Elements</span></span>  
  
|<span data-ttu-id="16bde-120">Element</span><span class="sxs-lookup"><span data-stu-id="16bde-120">Element</span></span>|<span data-ttu-id="16bde-121">Opis</span><span class="sxs-lookup"><span data-stu-id="16bde-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="16bde-122">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="16bde-122">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="16bde-123">Określa kolekcję programy obsługi tokenów zabezpieczających, które są zarejestrowane z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="16bde-123">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="16bde-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="16bde-124">Example</span></span>  
 <span data-ttu-id="16bde-125">Następujący kody XML pokazuje użycie `<add>` i `<remove>` elementów, aby zastąpić domyślne sesji programu obsługi tokenów niestandardową sesję programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="16bde-125">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="16bde-126">Kod XML jest pobierana z `ClaimsAwareWebFarm` próbki.</span><span class="sxs-lookup"><span data-stu-id="16bde-126">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```

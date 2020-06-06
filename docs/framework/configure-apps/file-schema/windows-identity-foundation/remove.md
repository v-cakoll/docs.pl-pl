---
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: cfdfbb3aabde253ad17b221801b20c1ac9a45c2d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251928"
---
# \<remove>
<span data-ttu-id="d4014-101">Usuwa określony program obsługi tokenów zabezpieczających z kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="d4014-101">Removes the specified security token handler from the token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="d4014-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="d4014-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4014-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d4014-103">Attributes and Elements</span></span>  
 <span data-ttu-id="d4014-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d4014-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4014-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d4014-105">Attributes</span></span>  
  
|<span data-ttu-id="d4014-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d4014-106">Attribute</span></span>|<span data-ttu-id="d4014-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d4014-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d4014-108">typ</span><span class="sxs-lookup"><span data-stu-id="d4014-108">type</span></span>|<span data-ttu-id="d4014-109">Nazwa typu CLR programu obsługi tokenów, który ma zostać usunięty.</span><span class="sxs-lookup"><span data-stu-id="d4014-109">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="d4014-110">Aby uzyskać więcej informacji na temat sposobu określania `type` atrybutu, zobacz [odwołania do typów niestandardowych](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="d4014-110">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span> <span data-ttu-id="d4014-111">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="d4014-111">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4014-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d4014-112">Child Elements</span></span>  
 <span data-ttu-id="d4014-113">Brak</span><span class="sxs-lookup"><span data-stu-id="d4014-113">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d4014-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d4014-114">Parent Elements</span></span>  
  
|<span data-ttu-id="d4014-115">Element</span><span class="sxs-lookup"><span data-stu-id="d4014-115">Element</span></span>|<span data-ttu-id="d4014-116">Opis</span><span class="sxs-lookup"><span data-stu-id="d4014-116">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="d4014-117">Określa kolekcję programów obsługi tokenów zabezpieczających, które są zarejestrowane w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="d4014-117">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d4014-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="d4014-118">Example</span></span>  
 <span data-ttu-id="d4014-119">Poniższy kod XML pokazuje użycie `<add>` elementów i, `<remove>` Aby zastąpić domyślną procedurę obsługi tokena sesji za pomocą procedury obsługi niestandardowego tokenu sesji.</span><span class="sxs-lookup"><span data-stu-id="d4014-119">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="d4014-120">KOD XML jest pobierany z `ClaimsAwareWebFarm` przykładu.</span><span class="sxs-lookup"><span data-stu-id="d4014-120">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```

---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: bb2989ed52a88d805510d65e1dc1740df7bb55eb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73735940"
---
# \<useManagedPresentation>
<span data-ttu-id="989d6-101">Element powiązania używany do komunikowania się z usługą tokenu zabezpieczającego CardSpace obsługującą profil CardSpace usługi WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="989d6-101">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="989d6-102">Ten element nie ma atrybutu i jest obecny jako pusty przełącznik.</span><span class="sxs-lookup"><span data-stu-id="989d6-102">This element has no attribute and is present as an empty switch.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useManagedPresentation>**  
  
## <a name="syntax"></a><span data-ttu-id="989d6-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="989d6-103">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="989d6-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="989d6-104">Attributes and Elements</span></span>  
 <span data-ttu-id="989d6-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="989d6-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="989d6-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="989d6-106">Attributes</span></span>  
 <span data-ttu-id="989d6-107">Brak.</span><span class="sxs-lookup"><span data-stu-id="989d6-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="989d6-108">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="989d6-108">Child Elements</span></span>  
 <span data-ttu-id="989d6-109">Brak</span><span class="sxs-lookup"><span data-stu-id="989d6-109">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="989d6-110">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="989d6-110">Parent Elements</span></span>  
  
|<span data-ttu-id="989d6-111">Element</span><span class="sxs-lookup"><span data-stu-id="989d6-111">Element</span></span>|<span data-ttu-id="989d6-112">Opis</span><span class="sxs-lookup"><span data-stu-id="989d6-112">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="989d6-113">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="989d6-113">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="989d6-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="989d6-114">Remarks</span></span>  
 <span data-ttu-id="989d6-115">Ten element jest używany przez dostawcę tożsamości do wyrażenia w jego zasadom faktu, że obsługuje profil CardSpace usługi WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="989d6-115">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="989d6-116">Dostawcy tożsamości, którzy publikują takie potwierdzenie zasad, powinni mieć możliwość wystawiania tokenów opartych na tym profilu programu CardSpace.</span><span class="sxs-lookup"><span data-stu-id="989d6-116">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="989d6-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="989d6-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="989d6-118">Powiązania</span><span class="sxs-lookup"><span data-stu-id="989d6-118">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="989d6-119">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="989d6-119">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="989d6-120">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="989d6-120">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)

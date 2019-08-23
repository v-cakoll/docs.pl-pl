---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: e67cc316b8747ee785055ceb4f954988fa82a44c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940617"
---
# <a name="usemanagedpresentation"></a><span data-ttu-id="57ba0-101">\<useManagedPresentation ></span><span class="sxs-lookup"><span data-stu-id="57ba0-101">\<useManagedPresentation></span></span>
<span data-ttu-id="57ba0-102">Element powiązania używany do komunikowania się z usługą tokenu zabezpieczającego CardSpace obsługującą profil CardSpace usługi WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="57ba0-102">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="57ba0-103">Ten element nie ma atrybutu i jest obecny jako pusty przełącznik.</span><span class="sxs-lookup"><span data-stu-id="57ba0-103">This element has no attribute and is present as an empty switch.</span></span>  
  
 <span data-ttu-id="57ba0-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="57ba0-104">\<system.serviceModel></span></span>  
<span data-ttu-id="57ba0-105">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="57ba0-105">\<bindings></span></span>  
<span data-ttu-id="57ba0-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="57ba0-106">\<customBinding></span></span>  
<span data-ttu-id="57ba0-107">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="57ba0-107">\<binding></span></span>  
<span data-ttu-id="57ba0-108">\<useManagedPresentation ></span><span class="sxs-lookup"><span data-stu-id="57ba0-108">\<useManagedPresentation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57ba0-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="57ba0-109">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57ba0-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="57ba0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="57ba0-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="57ba0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57ba0-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="57ba0-112">Attributes</span></span>  
 <span data-ttu-id="57ba0-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="57ba0-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="57ba0-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="57ba0-114">Child Elements</span></span>  
 <span data-ttu-id="57ba0-115">Brak</span><span class="sxs-lookup"><span data-stu-id="57ba0-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="57ba0-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="57ba0-116">Parent Elements</span></span>  
  
|<span data-ttu-id="57ba0-117">Element</span><span class="sxs-lookup"><span data-stu-id="57ba0-117">Element</span></span>|<span data-ttu-id="57ba0-118">Opis</span><span class="sxs-lookup"><span data-stu-id="57ba0-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57ba0-119">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="57ba0-119">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="57ba0-120">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="57ba0-120">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57ba0-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="57ba0-121">Remarks</span></span>  
 <span data-ttu-id="57ba0-122">Ten element jest używany przez dostawcę tożsamości do wyrażenia w jego zasadom faktu, że obsługuje profil CardSpace usługi WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="57ba0-122">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="57ba0-123">Dostawcy tożsamości, którzy publikują takie potwierdzenie zasad, powinni mieć możliwość wystawiania tokenów opartych na tym profilu programu CardSpace.</span><span class="sxs-lookup"><span data-stu-id="57ba0-123">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57ba0-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="57ba0-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="57ba0-125">Powiązania</span><span class="sxs-lookup"><span data-stu-id="57ba0-125">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="57ba0-126">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="57ba0-126">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="57ba0-127">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="57ba0-127">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="57ba0-128">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="57ba0-128">\<customBinding></span></span>](custombinding.md)

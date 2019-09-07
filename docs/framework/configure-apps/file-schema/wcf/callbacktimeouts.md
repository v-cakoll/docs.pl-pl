---
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: e1b40718638ded54e59743730159ea6e65a51a57
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398181"
---
# <a name="callbacktimeouts"></a><span data-ttu-id="a4b5b-101">\<callbackTimeouts></span><span class="sxs-lookup"><span data-stu-id="a4b5b-101">\<callbackTimeouts></span></span>
<span data-ttu-id="a4b5b-102">Określa wartość limitu czasu podczas przepływu transakcji z serwera, aby client.in scenariusz dwustronnego kontraktu wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="a4b5b-102">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
<span data-ttu-id="a4b5b-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a4b5b-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a4b5b-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a4b5b-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a4b5b-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a4b5b-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="a4b5b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a4b5b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="a4b5b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a4b5b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="a4b5b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<callbackTimeOuts >**</span><span class="sxs-lookup"><span data-stu-id="a4b5b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackTimeOuts>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4b5b-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="a4b5b-109">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="a4b5b-110">Typ</span><span class="sxs-lookup"><span data-stu-id="a4b5b-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4b5b-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a4b5b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a4b5b-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a4b5b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4b5b-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a4b5b-113">Attributes</span></span>  
  
|<span data-ttu-id="a4b5b-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a4b5b-114">Attribute</span></span>|<span data-ttu-id="a4b5b-115">Opis</span><span class="sxs-lookup"><span data-stu-id="a4b5b-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="a4b5b-116"><xref:System.TimeSpan> Wartość, która określa przedział czasu, w którym transakcje muszą zostać ukończone lub automatycznie zakończone.</span><span class="sxs-lookup"><span data-stu-id="a4b5b-116">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="a4b5b-117">Wartość domyślna to "00:00:00".</span><span class="sxs-lookup"><span data-stu-id="a4b5b-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a4b5b-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a4b5b-118">Child Elements</span></span>  
 <span data-ttu-id="a4b5b-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="a4b5b-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a4b5b-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a4b5b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a4b5b-121">Element</span><span class="sxs-lookup"><span data-stu-id="a4b5b-121">Element</span></span>|<span data-ttu-id="a4b5b-122">Opis</span><span class="sxs-lookup"><span data-stu-id="a4b5b-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a4b5b-123">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="a4b5b-123">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="a4b5b-124">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="a4b5b-124">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a4b5b-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a4b5b-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>

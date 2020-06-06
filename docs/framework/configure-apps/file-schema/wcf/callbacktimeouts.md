---
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: e1b40718638ded54e59743730159ea6e65a51a57
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398181"
---
# \<callbackTimeouts>
<span data-ttu-id="79317-101">Określa wartość limitu czasu podczas przepływu transakcji z serwera, aby client.in scenariusz dwustronnego kontraktu wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="79317-101">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackTimeOuts>**  
  
## <a name="syntax"></a><span data-ttu-id="79317-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="79317-102">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="79317-103">Typ</span><span class="sxs-lookup"><span data-stu-id="79317-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79317-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="79317-104">Attributes and Elements</span></span>  
 <span data-ttu-id="79317-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="79317-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79317-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="79317-106">Attributes</span></span>  
  
|<span data-ttu-id="79317-107">Atrybut</span><span class="sxs-lookup"><span data-stu-id="79317-107">Attribute</span></span>|<span data-ttu-id="79317-108">Opis</span><span class="sxs-lookup"><span data-stu-id="79317-108">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="79317-109"><xref:System.TimeSpan>Wartość, która określa przedział czasu, w którym transakcje muszą zostać ukończone lub automatycznie zakończone.</span><span class="sxs-lookup"><span data-stu-id="79317-109">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="79317-110">Wartość domyślna to "00:00:00".</span><span class="sxs-lookup"><span data-stu-id="79317-110">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="79317-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="79317-111">Child Elements</span></span>  
 <span data-ttu-id="79317-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="79317-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="79317-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="79317-113">Parent Elements</span></span>  
  
|<span data-ttu-id="79317-114">Element</span><span class="sxs-lookup"><span data-stu-id="79317-114">Element</span></span>|<span data-ttu-id="79317-115">Opis</span><span class="sxs-lookup"><span data-stu-id="79317-115">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="79317-116">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="79317-116">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="79317-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="79317-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>

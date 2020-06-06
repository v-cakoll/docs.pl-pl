---
title: <callbackDebug>
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 92a8fa83b5cf5f429278ac8edc8439b627839aad
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400571"
---
# \<callbackDebug>
<span data-ttu-id="c7660-101">Określa debugowanie usługi dla obiektu wywołania zwrotnego Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c7660-101">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackDebug>**  
  
## <a name="syntax"></a><span data-ttu-id="c7660-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="c7660-102">Syntax</span></span>  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a><span data-ttu-id="c7660-103">Typ</span><span class="sxs-lookup"><span data-stu-id="c7660-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c7660-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c7660-104">Attributes and Elements</span></span>  
 <span data-ttu-id="c7660-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c7660-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c7660-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c7660-106">Attributes</span></span>  
  
|<span data-ttu-id="c7660-107">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c7660-107">Attribute</span></span>|<span data-ttu-id="c7660-108">Opis</span><span class="sxs-lookup"><span data-stu-id="c7660-108">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="c7660-109">Wartość określająca, czy obiekty wywołania zwrotnego klienta zwracają informacje o zarządzanym wyjątku w błędach protokołu SOAP z powrotem do usługi.</span><span class="sxs-lookup"><span data-stu-id="c7660-109">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="c7660-110">Jeśli ten atrybut zostanie ustawiony na `true` programowo, można włączyć przepływ informacji o zarządzanym wyjątku w obiekcie wywołania zwrotnego klienta z powrotem do usługi na potrzeby debugowania.</span><span class="sxs-lookup"><span data-stu-id="c7660-110">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="c7660-111">**Przestroga:**  Zwrócenie informacji o wyjątku zarządzanym do klientów może stanowić zagrożenie bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="c7660-111">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="c7660-112">Wynika to z faktu, że szczegóły wyjątku ujawniają informacje o implementacji wewnętrznej usługi, która może być używana przez nieautoryzowanych klientów.</span><span class="sxs-lookup"><span data-stu-id="c7660-112">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c7660-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c7660-113">Child Elements</span></span>  
 <span data-ttu-id="c7660-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="c7660-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c7660-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c7660-115">Parent Elements</span></span>  
  
|<span data-ttu-id="c7660-116">Element</span><span class="sxs-lookup"><span data-stu-id="c7660-116">Element</span></span>|<span data-ttu-id="c7660-117">Opis</span><span class="sxs-lookup"><span data-stu-id="c7660-117">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c7660-118">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="c7660-118">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c7660-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7660-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>

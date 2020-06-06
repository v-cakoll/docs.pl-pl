---
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 7c4d9ae29ca1e543217d444e05a661b48e2cbb62
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400074"
---
# \<persistenceProvider>
<span data-ttu-id="2c6e3-101">Określa typ implementacji dostawcy trwałości, a także limit czasu na potrzeby operacji trwałości.</span><span class="sxs-lookup"><span data-stu-id="2c6e3-101">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistenceProvider>**  
  
## <a name="syntax"></a><span data-ttu-id="2c6e3-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="2c6e3-102">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c6e3-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2c6e3-103">Attributes and Elements</span></span>  
 <span data-ttu-id="2c6e3-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2c6e3-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c6e3-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2c6e3-105">Attributes</span></span>  
  
|<span data-ttu-id="2c6e3-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2c6e3-106">Attribute</span></span>|<span data-ttu-id="2c6e3-107">Opis</span><span class="sxs-lookup"><span data-stu-id="2c6e3-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2c6e3-108">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="2c6e3-108">persistenceOperationTimeout</span></span>|<span data-ttu-id="2c6e3-109">Wartość określająca <xref:System.TimeSpan> limit czasu używany na potrzeby operacji trwałości.</span><span class="sxs-lookup"><span data-stu-id="2c6e3-109">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="2c6e3-110">Wartość domyślna to "00:00:30".</span><span class="sxs-lookup"><span data-stu-id="2c6e3-110">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="2c6e3-111">typ</span><span class="sxs-lookup"><span data-stu-id="2c6e3-111">type</span></span>|<span data-ttu-id="2c6e3-112">Ciąg określający typ fabryki dostawcy trwałości do użycia.</span><span class="sxs-lookup"><span data-stu-id="2c6e3-112">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2c6e3-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2c6e3-113">Child Elements</span></span>  
 <span data-ttu-id="2c6e3-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="2c6e3-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2c6e3-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2c6e3-115">Parent Elements</span></span>  
  
|<span data-ttu-id="2c6e3-116">Element</span><span class="sxs-lookup"><span data-stu-id="2c6e3-116">Element</span></span>|<span data-ttu-id="2c6e3-117">Opis</span><span class="sxs-lookup"><span data-stu-id="2c6e3-117">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="2c6e3-118">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="2c6e3-118">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c6e3-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2c6e3-119">Remarks</span></span>  
 <span data-ttu-id="2c6e3-120">Ten element określa dostawcę trwałości, który ma być używany do serializacji stanu usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="2c6e3-120">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="2c6e3-121">Powinna być używana razem z `wsHttpContextBinding` informacjami o stanie, które przechodzą w nagłówkach HTTP.</span><span class="sxs-lookup"><span data-stu-id="2c6e3-121">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c6e3-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2c6e3-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>

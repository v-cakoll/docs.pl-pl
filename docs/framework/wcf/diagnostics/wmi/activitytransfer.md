---
title: ActivityTransfer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: acbc346da940caf933868a03295744132bda4733
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="activitytransfer"></a><span data-ttu-id="7d032-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="7d032-102">ActivityTransfer</span></span>
<span data-ttu-id="7d032-103">Zdarzenie transferu aktywności</span><span class="sxs-lookup"><span data-stu-id="7d032-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d032-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d032-104">Syntax</span></span>  
  
```  
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7d032-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7d032-105">Methods</span></span>  
 <span data-ttu-id="7d032-106">Klasa ActivityTransfer nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="7d032-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7d032-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="7d032-107">Properties</span></span>  
 <span data-ttu-id="7d032-108">Klasa ActivityTransfer ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="7d032-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="7d032-109">Identyfikator działania</span><span class="sxs-lookup"><span data-stu-id="7d032-109">ActivityID</span></span>  
  
-   <span data-ttu-id="7d032-110">Typ danych: obiekt</span><span class="sxs-lookup"><span data-stu-id="7d032-110">Data type: object</span></span>  
    <span data-ttu-id="7d032-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="7d032-111">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="7d032-112">Identyfikator działania</span><span class="sxs-lookup"><span data-stu-id="7d032-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="7d032-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="7d032-113">RelatedActivityID</span></span>  
  
-   <span data-ttu-id="7d032-114">Typ danych: obiekt</span><span class="sxs-lookup"><span data-stu-id="7d032-114">Data type: object</span></span>  
    <span data-ttu-id="7d032-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="7d032-115">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="7d032-116">Identyfikator działania pokrewne</span><span class="sxs-lookup"><span data-stu-id="7d032-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d032-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7d032-117">Requirements</span></span>  
  
|<span data-ttu-id="7d032-118">MOF</span><span class="sxs-lookup"><span data-stu-id="7d032-118">MOF</span></span>|<span data-ttu-id="7d032-119">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="7d032-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7d032-120">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="7d032-120">Namespace</span></span>|<span data-ttu-id="7d032-121">Zdefiniowany w root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="7d032-121">Defined in root\ServiceModel.</span></span>|

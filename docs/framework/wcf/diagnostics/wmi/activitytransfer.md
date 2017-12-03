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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7c1caf0ae27efce858328e5db88434253be61d50
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="activitytransfer"></a><span data-ttu-id="05fea-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="05fea-102">ActivityTransfer</span></span>
<span data-ttu-id="05fea-103">Zdarzenie transferu aktywności</span><span class="sxs-lookup"><span data-stu-id="05fea-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05fea-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="05fea-104">Syntax</span></span>  
  
```  
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="05fea-105">Metody</span><span class="sxs-lookup"><span data-stu-id="05fea-105">Methods</span></span>  
 <span data-ttu-id="05fea-106">Klasa ActivityTransfer nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="05fea-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="05fea-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="05fea-107">Properties</span></span>  
 <span data-ttu-id="05fea-108">Klasa ActivityTransfer ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="05fea-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="05fea-109">Identyfikator działania</span><span class="sxs-lookup"><span data-stu-id="05fea-109">ActivityID</span></span>  
  
-   <span data-ttu-id="05fea-110">Typ danych: obiekt</span><span class="sxs-lookup"><span data-stu-id="05fea-110">Data type: object</span></span>  
    <span data-ttu-id="05fea-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="05fea-111">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="05fea-112">Identyfikator działania</span><span class="sxs-lookup"><span data-stu-id="05fea-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="05fea-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="05fea-113">RelatedActivityID</span></span>  
  
-   <span data-ttu-id="05fea-114">Typ danych: obiekt</span><span class="sxs-lookup"><span data-stu-id="05fea-114">Data type: object</span></span>  
    <span data-ttu-id="05fea-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="05fea-115">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="05fea-116">Identyfikator działania pokrewne</span><span class="sxs-lookup"><span data-stu-id="05fea-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05fea-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="05fea-117">Requirements</span></span>  
  
|<span data-ttu-id="05fea-118">MOF</span><span class="sxs-lookup"><span data-stu-id="05fea-118">MOF</span></span>|<span data-ttu-id="05fea-119">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="05fea-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="05fea-120">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="05fea-120">Namespace</span></span>|<span data-ttu-id="05fea-121">Zdefiniowany w root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="05fea-121">Defined in root\ServiceModel.</span></span>|

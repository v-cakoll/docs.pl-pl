---
title: WSAT_TraceRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d24f74d4086a5499d3bfd4ef6183d377528acc21
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="wsattracerecord"></a><span data-ttu-id="4d232-102">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="4d232-102">WSAT_TraceRecord</span></span>
<span data-ttu-id="4d232-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="4d232-103">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d232-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d232-104">Syntax</span></span>  
  
```  
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4d232-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4d232-105">Methods</span></span>  
 <span data-ttu-id="4d232-106">Klasa WSAT_TraceRecord nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="4d232-106">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4d232-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="4d232-107">Properties</span></span>  
 <span data-ttu-id="4d232-108">Klasa WSAT_TraceRecord ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="4d232-108">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="4d232-109">Identyfikator działania</span><span class="sxs-lookup"><span data-stu-id="4d232-109">ActivityID</span></span>  
 <span data-ttu-id="4d232-110">Typ danych: obiekt</span><span class="sxs-lookup"><span data-stu-id="4d232-110">Data type: object</span></span>  
<span data-ttu-id="4d232-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4d232-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4d232-112">Identyfikator działania rekordu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4d232-112">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="4d232-113">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="4d232-113">EventID</span></span>  
 <span data-ttu-id="4d232-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="4d232-114">Data type: sint32</span></span>  
<span data-ttu-id="4d232-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4d232-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4d232-116">Identyfikator zdarzenia Rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4d232-116">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="4d232-117">TraceRecord</span><span class="sxs-lookup"><span data-stu-id="4d232-117">TraceRecord</span></span>  
 <span data-ttu-id="4d232-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="4d232-118">Data type: string</span></span>  
<span data-ttu-id="4d232-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4d232-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4d232-120">Rekord śledzenia</span><span class="sxs-lookup"><span data-stu-id="4d232-120">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d232-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4d232-121">Requirements</span></span>  
  
|<span data-ttu-id="4d232-122">MOF</span><span class="sxs-lookup"><span data-stu-id="4d232-122">MOF</span></span>|<span data-ttu-id="4d232-123">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4d232-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4d232-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="4d232-124">Namespace</span></span>|<span data-ttu-id="4d232-125">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4d232-125">Defined in root\ServiceModel</span></span>|

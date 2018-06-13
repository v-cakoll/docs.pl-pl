---
title: WSAT_TraceRecord
ms.date: 03/30/2017
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
ms.openlocfilehash: 1136647ce668dbb69bdb8acf8ed62343831464b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487779"
---
# <a name="wsattracerecord"></a><span data-ttu-id="2a60b-102">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="2a60b-102">WSAT_TraceRecord</span></span>
<span data-ttu-id="2a60b-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="2a60b-103">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a60b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2a60b-104">Syntax</span></span>  
  
```  
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="2a60b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="2a60b-105">Methods</span></span>  
 <span data-ttu-id="2a60b-106">Klasa WSAT_TraceRecord nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="2a60b-106">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2a60b-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="2a60b-107">Properties</span></span>  
 <span data-ttu-id="2a60b-108">Klasa WSAT_TraceRecord ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="2a60b-108">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="2a60b-109">Identyfikator działania</span><span class="sxs-lookup"><span data-stu-id="2a60b-109">ActivityID</span></span>  
 <span data-ttu-id="2a60b-110">Typ danych: obiekt</span><span class="sxs-lookup"><span data-stu-id="2a60b-110">Data type: object</span></span>  
<span data-ttu-id="2a60b-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="2a60b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2a60b-112">Identyfikator działania rekordu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="2a60b-112">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="2a60b-113">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="2a60b-113">EventID</span></span>  
 <span data-ttu-id="2a60b-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="2a60b-114">Data type: sint32</span></span>  
<span data-ttu-id="2a60b-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="2a60b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2a60b-116">Identyfikator zdarzenia Rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="2a60b-116">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="2a60b-117">TraceRecord</span><span class="sxs-lookup"><span data-stu-id="2a60b-117">TraceRecord</span></span>  
 <span data-ttu-id="2a60b-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="2a60b-118">Data type: string</span></span>  
<span data-ttu-id="2a60b-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="2a60b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2a60b-120">Rekord śledzenia</span><span class="sxs-lookup"><span data-stu-id="2a60b-120">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a60b-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2a60b-121">Requirements</span></span>  
  
|<span data-ttu-id="2a60b-122">MOF</span><span class="sxs-lookup"><span data-stu-id="2a60b-122">MOF</span></span>|<span data-ttu-id="2a60b-123">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="2a60b-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2a60b-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="2a60b-124">Namespace</span></span>|<span data-ttu-id="2a60b-125">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2a60b-125">Defined in root\ServiceModel</span></span>|

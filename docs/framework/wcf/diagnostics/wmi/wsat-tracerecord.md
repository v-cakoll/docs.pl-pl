---
title: WSAT_TraceRecord
ms.date: 03/30/2017
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
ms.openlocfilehash: 907e764cf032e595c7aba455fd4808a640f68016
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61923412"
---
# <a name="wsattracerecord"></a><span data-ttu-id="f4921-102">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="f4921-102">WSAT_TraceRecord</span></span>
<span data-ttu-id="f4921-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="f4921-103">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4921-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f4921-104">Syntax</span></span>  
  
```csharp
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f4921-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f4921-105">Methods</span></span>  
 <span data-ttu-id="f4921-106">Klasa WSAT_TraceRecord nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="f4921-106">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f4921-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="f4921-107">Properties</span></span>  
 <span data-ttu-id="f4921-108">Klasa WSAT_TraceRecord ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="f4921-108">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="f4921-109">Identyfikator działania</span><span class="sxs-lookup"><span data-stu-id="f4921-109">ActivityID</span></span>  
 <span data-ttu-id="f4921-110">Typ danych: obiekt</span><span class="sxs-lookup"><span data-stu-id="f4921-110">Data type: object</span></span>  
<span data-ttu-id="f4921-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f4921-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f4921-112">Identyfikator działania rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="f4921-112">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="f4921-113">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f4921-113">EventID</span></span>  
 <span data-ttu-id="f4921-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="f4921-114">Data type: sint32</span></span>  
<span data-ttu-id="f4921-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f4921-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f4921-116">Identyfikator zdarzenia Rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="f4921-116">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="f4921-117">TraceRecord</span><span class="sxs-lookup"><span data-stu-id="f4921-117">TraceRecord</span></span>  
 <span data-ttu-id="f4921-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="f4921-118">Data type: string</span></span>  
<span data-ttu-id="f4921-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f4921-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f4921-120">Rekord śledzenia</span><span class="sxs-lookup"><span data-stu-id="f4921-120">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4921-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f4921-121">Requirements</span></span>  
  
|<span data-ttu-id="f4921-122">MOF</span><span class="sxs-lookup"><span data-stu-id="f4921-122">MOF</span></span>|<span data-ttu-id="f4921-123">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f4921-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f4921-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="f4921-124">Namespace</span></span>|<span data-ttu-id="f4921-125">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f4921-125">Defined in root\ServiceModel</span></span>|

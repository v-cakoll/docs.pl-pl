---
title: WSAT_TraceRecord
ms.date: 03/30/2017
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
ms.openlocfilehash: 907e764cf032e595c7aba455fd4808a640f68016
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194777"
---
# <a name="wsattracerecord"></a><span data-ttu-id="6d5c6-102">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="6d5c6-102">WSAT_TraceRecord</span></span>
<span data-ttu-id="6d5c6-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="6d5c6-103">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d5c6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6d5c6-104">Syntax</span></span>  
  
```csharp
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="6d5c6-105">Metody</span><span class="sxs-lookup"><span data-stu-id="6d5c6-105">Methods</span></span>  
 <span data-ttu-id="6d5c6-106">Klasa WSAT_TraceRecord nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="6d5c6-106">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6d5c6-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="6d5c6-107">Properties</span></span>  
 <span data-ttu-id="6d5c6-108">Klasa WSAT_TraceRecord ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="6d5c6-108">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="6d5c6-109">Identyfikator działania</span><span class="sxs-lookup"><span data-stu-id="6d5c6-109">ActivityID</span></span>  
 <span data-ttu-id="6d5c6-110">Typ danych: obiekt</span><span class="sxs-lookup"><span data-stu-id="6d5c6-110">Data type: object</span></span>  
<span data-ttu-id="6d5c6-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="6d5c6-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d5c6-112">Identyfikator działania rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="6d5c6-112">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="6d5c6-113">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6d5c6-113">EventID</span></span>  
 <span data-ttu-id="6d5c6-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="6d5c6-114">Data type: sint32</span></span>  
<span data-ttu-id="6d5c6-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="6d5c6-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d5c6-116">Identyfikator zdarzenia Rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="6d5c6-116">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="6d5c6-117">TraceRecord</span><span class="sxs-lookup"><span data-stu-id="6d5c6-117">TraceRecord</span></span>  
 <span data-ttu-id="6d5c6-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="6d5c6-118">Data type: string</span></span>  
<span data-ttu-id="6d5c6-119">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="6d5c6-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d5c6-120">Rekord śledzenia</span><span class="sxs-lookup"><span data-stu-id="6d5c6-120">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d5c6-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6d5c6-121">Requirements</span></span>  
  
|<span data-ttu-id="6d5c6-122">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="6d5c6-122">MOF</span></span>|<span data-ttu-id="6d5c6-123">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="6d5c6-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6d5c6-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="6d5c6-124">Namespace</span></span>|<span data-ttu-id="6d5c6-125">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6d5c6-125">Defined in root\ServiceModel</span></span>|

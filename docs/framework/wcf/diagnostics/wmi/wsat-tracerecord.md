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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3966311bc10b5ad2ee401ef9e3e13c8f36e14505
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="wsattracerecord"></a><span data-ttu-id="28352-102">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="28352-102">WSAT_TraceRecord</span></span>
<span data-ttu-id="28352-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="28352-103">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28352-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="28352-104">Syntax</span></span>  
  
```  
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="28352-105">Metody</span><span class="sxs-lookup"><span data-stu-id="28352-105">Methods</span></span>  
 <span data-ttu-id="28352-106">Klasa WSAT_TraceRecord nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="28352-106">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="28352-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="28352-107">Properties</span></span>  
 <span data-ttu-id="28352-108">Klasa WSAT_TraceRecord ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="28352-108">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="28352-109">Identyfikator działania</span><span class="sxs-lookup"><span data-stu-id="28352-109">ActivityID</span></span>  
 <span data-ttu-id="28352-110">Typ danych: obiekt</span><span class="sxs-lookup"><span data-stu-id="28352-110">Data type: object</span></span>  
<span data-ttu-id="28352-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="28352-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="28352-112">Identyfikator działania rekordu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="28352-112">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="28352-113">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="28352-113">EventID</span></span>  
 <span data-ttu-id="28352-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="28352-114">Data type: sint32</span></span>  
<span data-ttu-id="28352-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="28352-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="28352-116">Identyfikator zdarzenia Rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="28352-116">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="28352-117">TraceRecord</span><span class="sxs-lookup"><span data-stu-id="28352-117">TraceRecord</span></span>  
 <span data-ttu-id="28352-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="28352-118">Data type: string</span></span>  
<span data-ttu-id="28352-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="28352-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="28352-120">Rekord śledzenia</span><span class="sxs-lookup"><span data-stu-id="28352-120">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28352-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="28352-121">Requirements</span></span>  
  
|<span data-ttu-id="28352-122">MOF</span><span class="sxs-lookup"><span data-stu-id="28352-122">MOF</span></span>|<span data-ttu-id="28352-123">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="28352-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="28352-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="28352-124">Namespace</span></span>|<span data-ttu-id="28352-125">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="28352-125">Defined in root\ServiceModel</span></span>|

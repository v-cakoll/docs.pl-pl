---
title: "COR_PRF_CLAUSE_TYPE — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_CLAUSE_TYPE
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_CLAUSE_TYPE
helpviewer_keywords: COR_PRF_CLAUSE_TYPE enumeration [.NET Framework profiling]
ms.assetid: f64c325a-ed3a-4aaf-b847-a88edbc4fefc
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8bd34422656432b9bf8939b81ca0a8583c9d08e8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="corprfclausetype-enumeration"></a><span data-ttu-id="010db-102">COR_PRF_CLAUSE_TYPE — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="010db-102">COR_PRF_CLAUSE_TYPE Enumeration</span></span>
<span data-ttu-id="010db-103">Wskazuje typ klauzuli wyjątek, który właśnie wprowadzony kod lub w lewo.</span><span class="sxs-lookup"><span data-stu-id="010db-103">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="010db-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="010db-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_CLAUSE_NONE = 0,  
    COR_PRF_CLAUSE_FILTER = 1,  
    COR_PRF_CLAUSE_CATCH = 2,  
    COR_PRF_CLAUSE_FINALLY = 3,  
} COR_PRF_CLAUSE_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="010db-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="010db-105">Members</span></span>  
  
|<span data-ttu-id="010db-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="010db-106">Member</span></span>|<span data-ttu-id="010db-107">Opis</span><span class="sxs-lookup"><span data-stu-id="010db-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CLAUSE_NONE`|<span data-ttu-id="010db-108">Klauzula wyjątku jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="010db-108">The exception clause is not valid.</span></span>|  
|`COR_PRF_CLAUSE_FILTER`|<span data-ttu-id="010db-109">Klauzula wyjątku jest wyrażenie filtru.</span><span class="sxs-lookup"><span data-stu-id="010db-109">The exception clause is a filter expression.</span></span>|  
|`COR_PRF_CLAUSE_CATCH`|<span data-ttu-id="010db-110">Klauzula wyjątku jest `catch` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="010db-110">The exception clause is a `catch` statement.</span></span>|  
|`COR_PRF_CLAUSE_FINALLY`|<span data-ttu-id="010db-111">Klauzula wyjątku jest `finally` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="010db-111">The exception clause is a `finally` statement.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="010db-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="010db-112">Requirements</span></span>  
 <span data-ttu-id="010db-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="010db-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="010db-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="010db-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="010db-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="010db-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="010db-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="010db-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="010db-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="010db-117">See Also</span></span>  
 [<span data-ttu-id="010db-118">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="010db-118">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)

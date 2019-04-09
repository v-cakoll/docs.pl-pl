---
title: COR_PRF_CLAUSE_TYPE — Wyliczenie
ms.date: 03/30/2017
api_name:
- COR_PRF_CLAUSE_TYPE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CLAUSE_TYPE
helpviewer_keywords:
- COR_PRF_CLAUSE_TYPE enumeration [.NET Framework profiling]
ms.assetid: f64c325a-ed3a-4aaf-b847-a88edbc4fefc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 861f4c18f4c5151dc7215d300775928b88f018aa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090631"
---
# <a name="corprfclausetype-enumeration"></a><span data-ttu-id="fb02c-102">COR_PRF_CLAUSE_TYPE — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fb02c-102">COR_PRF_CLAUSE_TYPE Enumeration</span></span>
<span data-ttu-id="fb02c-103">Wskazuje typ klauzuli wyjątek, który po prostu wprowadzony kod lub po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="fb02c-103">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb02c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb02c-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_CLAUSE_NONE = 0,  
    COR_PRF_CLAUSE_FILTER = 1,  
    COR_PRF_CLAUSE_CATCH = 2,  
    COR_PRF_CLAUSE_FINALLY = 3,  
} COR_PRF_CLAUSE_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="fb02c-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="fb02c-105">Members</span></span>  
  
|<span data-ttu-id="fb02c-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="fb02c-106">Member</span></span>|<span data-ttu-id="fb02c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="fb02c-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CLAUSE_NONE`|<span data-ttu-id="fb02c-108">Klauzula wyjątek jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="fb02c-108">The exception clause is not valid.</span></span>|  
|`COR_PRF_CLAUSE_FILTER`|<span data-ttu-id="fb02c-109">Klauzula wyjątek jest wyrażenie filtru.</span><span class="sxs-lookup"><span data-stu-id="fb02c-109">The exception clause is a filter expression.</span></span>|  
|`COR_PRF_CLAUSE_CATCH`|<span data-ttu-id="fb02c-110">Klauzula wyjątek jest `catch` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="fb02c-110">The exception clause is a `catch` statement.</span></span>|  
|`COR_PRF_CLAUSE_FINALLY`|<span data-ttu-id="fb02c-111">Klauzula wyjątek jest `finally` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="fb02c-111">The exception clause is a `finally` statement.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fb02c-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fb02c-112">Requirements</span></span>  
 <span data-ttu-id="fb02c-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb02c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb02c-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fb02c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fb02c-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb02c-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="fb02c-116">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="fb02c-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fb02c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb02c-117">See also</span></span>

- [<span data-ttu-id="fb02c-118">Profilowanie — Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="fb02c-118">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)

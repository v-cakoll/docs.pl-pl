---
title: COR_VERSION — Struktura
ms.date: 03/30/2017
api_name:
- COR_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_VERSION
helpviewer_keywords:
- COR_VERSION structure [.NET Framework debugging]
ms.assetid: 5efaee1c-a001-4c73-9525-4160f4c71567
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e07487f536454d9d2dcfff15eb871124112d250e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634973"
---
# <a name="corversion-structure"></a><span data-ttu-id="c3ef4-102">COR_VERSION — Struktura</span><span class="sxs-lookup"><span data-stu-id="c3ef4-102">COR_VERSION Structure</span></span>
<span data-ttu-id="c3ef4-103">Przechowuje standardowe Czteroczęściowy numer środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="c3ef4-103">Stores the standard four-part version number of the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3ef4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c3ef4-104">Syntax</span></span>  
  
```  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="c3ef4-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c3ef4-105">Members</span></span>  
  
|<span data-ttu-id="c3ef4-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="c3ef4-106">Member</span></span>|<span data-ttu-id="c3ef4-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c3ef4-107">Description</span></span>|  
|------------|-----------------|  
|`dwMajor`|<span data-ttu-id="c3ef4-108">Główny numer wersji.</span><span class="sxs-lookup"><span data-stu-id="c3ef4-108">The major version number.</span></span>|  
|`dwMinor`|<span data-ttu-id="c3ef4-109">Pomocniczy numer wersji.</span><span class="sxs-lookup"><span data-stu-id="c3ef4-109">The minor version number.</span></span>|  
|`dwBuild`|<span data-ttu-id="c3ef4-110">Numer kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c3ef4-110">The build number.</span></span>|  
|`dwSubBuild`|<span data-ttu-id="c3ef4-111">Numer kompilacji podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="c3ef4-111">The sub-build number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3ef4-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c3ef4-112">Remarks</span></span>  
 <span data-ttu-id="c3ef4-113">Jeśli numer wersji jest 1.0.3705.288, 1 to główny numer wersji, 0 to pomocniczy numer wersji, 3705 jest numerem kompilacji i 288 jest numer kompilackji podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="c3ef4-113">If the version number is 1.0.3705.288, 1 is the major version number, 0 is the minor version number, 3705 is the build number, and 288 is the sub-build number.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3ef4-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c3ef4-114">Requirements</span></span>  
 <span data-ttu-id="c3ef4-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3ef4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3ef4-116">**Nagłówek:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="c3ef4-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="c3ef4-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3ef4-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3ef4-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3ef4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3ef4-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c3ef4-119">See also</span></span>
- [<span data-ttu-id="c3ef4-120">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="c3ef4-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="c3ef4-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="c3ef4-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

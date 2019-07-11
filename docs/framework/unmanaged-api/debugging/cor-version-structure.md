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
ms.openlocfilehash: b1f0a36d186c6d9788d43b075bf9d67c36ed1acb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740566"
---
# <a name="corversion-structure"></a><span data-ttu-id="f214a-102">COR_VERSION — Struktura</span><span class="sxs-lookup"><span data-stu-id="f214a-102">COR_VERSION Structure</span></span>
<span data-ttu-id="f214a-103">Przechowuje standardowe Czteroczęściowy numer środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="f214a-103">Stores the standard four-part version number of the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f214a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f214a-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="f214a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="f214a-105">Members</span></span>  
  
|<span data-ttu-id="f214a-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="f214a-106">Member</span></span>|<span data-ttu-id="f214a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f214a-107">Description</span></span>|  
|------------|-----------------|  
|`dwMajor`|<span data-ttu-id="f214a-108">Główny numer wersji.</span><span class="sxs-lookup"><span data-stu-id="f214a-108">The major version number.</span></span>|  
|`dwMinor`|<span data-ttu-id="f214a-109">Pomocniczy numer wersji.</span><span class="sxs-lookup"><span data-stu-id="f214a-109">The minor version number.</span></span>|  
|`dwBuild`|<span data-ttu-id="f214a-110">Numer kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f214a-110">The build number.</span></span>|  
|`dwSubBuild`|<span data-ttu-id="f214a-111">Numer kompilacji podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="f214a-111">The sub-build number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f214a-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f214a-112">Remarks</span></span>  
 <span data-ttu-id="f214a-113">Jeśli numer wersji jest 1.0.3705.288, 1 to główny numer wersji, 0 to pomocniczy numer wersji, 3705 jest numerem kompilacji i 288 jest numer kompilackji podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="f214a-113">If the version number is 1.0.3705.288, 1 is the major version number, 0 is the minor version number, 3705 is the build number, and 288 is the sub-build number.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f214a-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f214a-114">Requirements</span></span>  
 <span data-ttu-id="f214a-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f214a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f214a-116">**Nagłówek:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="f214a-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="f214a-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f214a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f214a-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f214a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f214a-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f214a-119">See also</span></span>

- [<span data-ttu-id="f214a-120">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="f214a-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="f214a-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="f214a-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

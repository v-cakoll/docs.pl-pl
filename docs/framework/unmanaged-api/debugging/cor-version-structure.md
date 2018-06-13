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
ms.openlocfilehash: e2668e36debebb5ba71277912f37833eba584fde
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403282"
---
# <a name="corversion-structure"></a><span data-ttu-id="55b00-102">COR_VERSION — Struktura</span><span class="sxs-lookup"><span data-stu-id="55b00-102">COR_VERSION Structure</span></span>
<span data-ttu-id="55b00-103">Przechowuje numer wersji czteroczęściową standardowe środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="55b00-103">Stores the standard four-part version number of the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55b00-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="55b00-104">Syntax</span></span>  
  
```  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="55b00-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="55b00-105">Members</span></span>  
  
|<span data-ttu-id="55b00-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="55b00-106">Member</span></span>|<span data-ttu-id="55b00-107">Opis</span><span class="sxs-lookup"><span data-stu-id="55b00-107">Description</span></span>|  
|------------|-----------------|  
|`dwMajor`|<span data-ttu-id="55b00-108">Główny numer wersji.</span><span class="sxs-lookup"><span data-stu-id="55b00-108">The major version number.</span></span>|  
|`dwMinor`|<span data-ttu-id="55b00-109">Pomocniczy numer wersji.</span><span class="sxs-lookup"><span data-stu-id="55b00-109">The minor version number.</span></span>|  
|`dwBuild`|<span data-ttu-id="55b00-110">Numer kompilacji.</span><span class="sxs-lookup"><span data-stu-id="55b00-110">The build number.</span></span>|  
|`dwSubBuild`|<span data-ttu-id="55b00-111">Numer kompilacji podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="55b00-111">The sub-build number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55b00-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="55b00-112">Remarks</span></span>  
 <span data-ttu-id="55b00-113">Jeśli numer wersji jest 1.0.3705.288, główny numer wersji jest 1, 0 jest podrzędny numer wersji 3705 jest numer kompilacji i 288 jest numer kompilacji podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="55b00-113">If the version number is 1.0.3705.288, 1 is the major version number, 0 is the minor version number, 3705 is the build number, and 288 is the sub-build number.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55b00-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="55b00-114">Requirements</span></span>  
 <span data-ttu-id="55b00-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55b00-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55b00-116">**Nagłówek:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="55b00-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="55b00-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55b00-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55b00-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55b00-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55b00-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="55b00-119">See Also</span></span>  
 [<span data-ttu-id="55b00-120">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="55b00-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="55b00-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="55b00-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

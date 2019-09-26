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
ms.openlocfilehash: ffbe571ebc3d14c12e57b1f805d77e56e97d12e1
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274175"
---
# <a name="cor_version-structure"></a><span data-ttu-id="5d5b5-102">COR_VERSION — Struktura</span><span class="sxs-lookup"><span data-stu-id="5d5b5-102">COR_VERSION Structure</span></span>
<span data-ttu-id="5d5b5-103">Przechowuje numer standardowej wersji 4-częściowej środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="5d5b5-103">Stores the standard four-part version number of the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d5b5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5d5b5-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="5d5b5-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="5d5b5-105">Members</span></span>  
  
|<span data-ttu-id="5d5b5-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="5d5b5-106">Member</span></span>|<span data-ttu-id="5d5b5-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5d5b5-107">Description</span></span>|  
|------------|-----------------|  
|`dwMajor`|<span data-ttu-id="5d5b5-108">Główny numer wersji.</span><span class="sxs-lookup"><span data-stu-id="5d5b5-108">The major version number.</span></span>|  
|`dwMinor`|<span data-ttu-id="5d5b5-109">Pomocniczy numer wersji.</span><span class="sxs-lookup"><span data-stu-id="5d5b5-109">The minor version number.</span></span>|  
|`dwBuild`|<span data-ttu-id="5d5b5-110">Numer kompilacji.</span><span class="sxs-lookup"><span data-stu-id="5d5b5-110">The build number.</span></span>|  
|`dwSubBuild`|<span data-ttu-id="5d5b5-111">Numer kompilacji podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="5d5b5-111">The sub-build number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d5b5-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5d5b5-112">Remarks</span></span>  
 <span data-ttu-id="5d5b5-113">Jeśli numer wersji to 1.0.3705.288, 1 jest głównym numerem wersji, 0 jest numerem wersji pomocniczej, 3705 jest numerem kompilacji, a 288 jest numerem kompilacji podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="5d5b5-113">If the version number is 1.0.3705.288, 1 is the major version number, 0 is the minor version number, 3705 is the build number, and 288 is the sub-build number.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d5b5-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5d5b5-114">Requirements</span></span>  
 <span data-ttu-id="5d5b5-115">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d5b5-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d5b5-116">**Nagłówki** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="5d5b5-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="5d5b5-117">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d5b5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d5b5-118">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d5b5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d5b5-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d5b5-119">See also</span></span>

- [<span data-ttu-id="5d5b5-120">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="5d5b5-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="5d5b5-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="5d5b5-121">Debugging</span></span>](index.md)

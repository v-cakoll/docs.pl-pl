---
title: CorDebugCreateProcessFlags — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugCreateProcessFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugCreateProcessFlags
helpviewer_keywords:
- CorDebugCreateProcessFlags enumeration [.NET Framework debugging]
ms.assetid: e709acce-6a17-4346-b38a-467dba567358
topic_type:
- apiref
ms.openlocfilehash: c0e4c43ac18b5e214d38dd7a57452a3871e4b43d
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82796031"
---
# <a name="cordebugcreateprocessflags-enumeration"></a><span data-ttu-id="2249c-102">CorDebugCreateProcessFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2249c-102">CorDebugCreateProcessFlags Enumeration</span></span>
<span data-ttu-id="2249c-103">Zapewnia dodatkowe opcje debugowania, których można użyć w wywołaniu metody [ICorDebug:: CreateProcess](icordebug-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2249c-103">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](icordebug-createprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2249c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2249c-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCreateProcessFlags {  
    DEBUG_NO_SPECIAL_OPTIONS    = 0x0000  
} CorDebugCreateProcessFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="2249c-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="2249c-105">Members</span></span>  
  
|<span data-ttu-id="2249c-106">Członek</span><span class="sxs-lookup"><span data-stu-id="2249c-106">Member</span></span>|<span data-ttu-id="2249c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="2249c-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_NO_SPECIAL_OPTIONS`|<span data-ttu-id="2249c-108">Nie ustawiono żadnych specjalnych opcji.</span><span class="sxs-lookup"><span data-stu-id="2249c-108">No special options are set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2249c-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2249c-109">Requirements</span></span>  
 <span data-ttu-id="2249c-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2249c-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2249c-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2249c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2249c-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2249c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2249c-113">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2249c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2249c-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2249c-114">See also</span></span>

- [<span data-ttu-id="2249c-115">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="2249c-115">Debugging Enumerations</span></span>](debugging-enumerations.md)

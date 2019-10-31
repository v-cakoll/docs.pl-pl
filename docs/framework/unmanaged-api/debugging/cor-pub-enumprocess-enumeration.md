---
title: COR_PUB_ENUMPROCESS — Wyliczenie
ms.date: 03/30/2017
api_name:
- COR_PUB_ENUMPROCESS
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_PUB_ENUMPROCESS
helpviewer_keywords:
- COR_PUB_ENUMPROCESS enumeration [.NET Framework debugging]
ms.assetid: 5d3ada6e-feea-47da-a7ed-b664107c137f
topic_type:
- apiref
ms.openlocfilehash: f789105751ae2d498740ab60f326f9c0597483b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099210"
---
# <a name="cor_pub_enumprocess-enumeration"></a><span data-ttu-id="69196-102">COR_PUB_ENUMPROCESS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="69196-102">COR_PUB_ENUMPROCESS Enumeration</span></span>
<span data-ttu-id="69196-103">Identyfikuje typ procesu do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="69196-103">Identifies the type of process to be enumerated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69196-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="69196-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PUB_MANAGEDONLY    = 0x00000001  
} COR_PUB_ENUMPROCESS;  
```  
  
## <a name="members"></a><span data-ttu-id="69196-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="69196-105">Members</span></span>  
  
|<span data-ttu-id="69196-106">Nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="69196-106">Member name</span></span>|<span data-ttu-id="69196-107">Opis</span><span class="sxs-lookup"><span data-stu-id="69196-107">Description</span></span>|  
|-----------------|-----------------|  
|`COR_PUB_MANAGEDONLY`|<span data-ttu-id="69196-108">Proces zarządzany.</span><span class="sxs-lookup"><span data-stu-id="69196-108">A managed process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69196-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="69196-109">Remarks</span></span>  
 <span data-ttu-id="69196-110">Bieżąca wersja niezarządzanego interfejsu API debugowania wylicza tylko procesy zarządzane.</span><span class="sxs-lookup"><span data-stu-id="69196-110">The current version of the unmanaged debugging API enumerates only managed processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69196-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="69196-111">Requirements</span></span>  
 <span data-ttu-id="69196-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69196-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69196-113">**Nagłówek:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="69196-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="69196-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="69196-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69196-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69196-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69196-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="69196-116">See also</span></span>

- [<span data-ttu-id="69196-117">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="69196-117">Debugging Enumerations</span></span>](debugging-enumerations.md)

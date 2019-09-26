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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eab5fc13b74d8af4f0baaa3953c5c73ea255bfe6
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274019"
---
# <a name="cor_pub_enumprocess-enumeration"></a><span data-ttu-id="3b240-102">COR_PUB_ENUMPROCESS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="3b240-102">COR_PUB_ENUMPROCESS Enumeration</span></span>
<span data-ttu-id="3b240-103">Identyfikuje typ procesu do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="3b240-103">Identifies the type of process to be enumerated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b240-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3b240-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PUB_MANAGEDONLY    = 0x00000001  
} COR_PUB_ENUMPROCESS;  
```  
  
## <a name="members"></a><span data-ttu-id="3b240-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="3b240-105">Members</span></span>  
  
|<span data-ttu-id="3b240-106">Nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="3b240-106">Member name</span></span>|<span data-ttu-id="3b240-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3b240-107">Description</span></span>|  
|-----------------|-----------------|  
|`COR_PUB_MANAGEDONLY`|<span data-ttu-id="3b240-108">Proces zarządzany.</span><span class="sxs-lookup"><span data-stu-id="3b240-108">A managed process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b240-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3b240-109">Remarks</span></span>  
 <span data-ttu-id="3b240-110">Bieżąca wersja niezarządzanego interfejsu API debugowania wylicza tylko procesy zarządzane.</span><span class="sxs-lookup"><span data-stu-id="3b240-110">The current version of the unmanaged debugging API enumerates only managed processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b240-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3b240-111">Requirements</span></span>  
 <span data-ttu-id="3b240-112">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b240-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b240-113">**Nagłówki** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="3b240-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="3b240-114">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b240-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b240-115">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b240-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b240-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3b240-116">See also</span></span>

- [<span data-ttu-id="3b240-117">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="3b240-117">Debugging Enumerations</span></span>](debugging-enumerations.md)

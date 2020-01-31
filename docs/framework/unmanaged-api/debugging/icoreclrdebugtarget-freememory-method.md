---
title: ICoreClrDebugTarget::FreeMemory — Metoda
ms.date: 03/30/2017
api_name:
- ICoreDebugTarget.FreeMemory
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::FreeMemory
helpviewer_keywords:
- remote debugging API [Silverlight]
- FreeMemory method, ICoreClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::FreeMemory method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 98f2a0db-a6ec-4f9b-861d-f82485237d08
topic_type:
- apiref
ms.openlocfilehash: cfa313d286d0decad82f51bcedc582470549c8e1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790773"
---
# <a name="icoreclrdebugtargetfreememory-method"></a><span data-ttu-id="54532-102">ICoreClrDebugTarget::FreeMemory — Metoda</span><span class="sxs-lookup"><span data-stu-id="54532-102">ICoreClrDebugTarget::FreeMemory Method</span></span>
<span data-ttu-id="54532-103">Zwalnia pamięć przydzieloną przez metody [ICoreClrDebugTarget:: EnumProcesses —](icoreclrdebugtarget-enumprocesses-method.md) i [ICoreClrDebugTarget:: EnumRuntimes —](icoreclrdebugtarget-enumruntimes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="54532-103">Frees the memory allocated by the [ICoreClrDebugTarget::EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) and [ICoreClrDebugTarget::EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md) methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54532-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="54532-104">Syntax</span></span>  
  
```cpp  
void FreeMemory (  
     [in] void*pMemory);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54532-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="54532-105">Parameters</span></span>  
 `pMemory`  
 <span data-ttu-id="54532-106">podczas Wskaźnik do tablicy, który jest zwracany przez metodę [ICoreClrDebugTarget:: EnumProcesses —](icoreclrdebugtarget-enumprocesses-method.md) lub [ICoreClrDebugTarget:: EnumRuntimes —](icoreclrdebugtarget-enumruntimes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="54532-106">[in] A pointer to the array that is returned by either the [ICoreClrDebugTarget::EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) or the [ICoreClrDebugTarget::EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54532-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="54532-107">Requirements</span></span>  
 <span data-ttu-id="54532-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54532-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54532-109">**Nagłówek:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="54532-109">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="54532-110">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="54532-110">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="54532-111">**.NET Framework wersje:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="54532-111">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54532-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54532-112">See also</span></span>

- [<span data-ttu-id="54532-113">ICoreClrDebugTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="54532-113">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)

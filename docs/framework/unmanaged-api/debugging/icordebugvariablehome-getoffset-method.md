---
title: Metoda ICorDebugVariableHome::GetOffset
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetOffset
helpviewer_keywords:
- ICorDebugVariableHome::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: f025c2e5-3f6c-4be8-9ffe-c8b214617dfe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6880584fe407d651010fad885c2dd5983ad4dfcf
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492468"
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="fd58d-102">Metoda ICorDebugVariableHome::GetOffset</span><span class="sxs-lookup"><span data-stu-id="fd58d-102">ICorDebugVariableHome::GetOffset Method</span></span>
<span data-ttu-id="fd58d-103">Pobiera przesunięcie z podstawowej rejestru dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="fd58d-103">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd58d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fd58d-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd58d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fd58d-105">Parameters</span></span>  
 `pOffset`  
 <span data-ttu-id="fd58d-106">[out] Przesunięcie od podstawowej rejestru.</span><span class="sxs-lookup"><span data-stu-id="fd58d-106">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fd58d-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fd58d-107">Return Value</span></span>  
 <span data-ttu-id="fd58d-108">Metoda zwraca następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="fd58d-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="fd58d-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="fd58d-109">Value</span></span>|<span data-ttu-id="fd58d-110">Opis</span><span class="sxs-lookup"><span data-stu-id="fd58d-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="fd58d-111">Zmienna znajduje się w lokalizacji pamięci względem rejestru.</span><span class="sxs-lookup"><span data-stu-id="fd58d-111">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="fd58d-112">Zmienna nie jest w lokalizacji pamięci względem rejestru.</span><span class="sxs-lookup"><span data-stu-id="fd58d-112">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fd58d-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fd58d-113">Requirements</span></span>  
 <span data-ttu-id="fd58d-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd58d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd58d-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fd58d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fd58d-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd58d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd58d-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd58d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd58d-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fd58d-118">See also</span></span>
- [<span data-ttu-id="fd58d-119">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="fd58d-119">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)

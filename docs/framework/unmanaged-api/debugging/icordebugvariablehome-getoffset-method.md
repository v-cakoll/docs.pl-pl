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
ms.openlocfilehash: 864cb893511bceabd61ce0064065b3866ce01dfe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212599"
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="d83fd-102">Metoda ICorDebugVariableHome::GetOffset</span><span class="sxs-lookup"><span data-stu-id="d83fd-102">ICorDebugVariableHome::GetOffset Method</span></span>
<span data-ttu-id="d83fd-103">Pobiera przesunięcie z podstawowej rejestru dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="d83fd-103">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d83fd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d83fd-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d83fd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d83fd-105">Parameters</span></span>  
 `pOffset`  
 <span data-ttu-id="d83fd-106">[out] Przesunięcie od podstawowej rejestru.</span><span class="sxs-lookup"><span data-stu-id="d83fd-106">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d83fd-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d83fd-107">Return Value</span></span>  
 <span data-ttu-id="d83fd-108">Metoda zwraca następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="d83fd-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="d83fd-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="d83fd-109">Value</span></span>|<span data-ttu-id="d83fd-110">Opis</span><span class="sxs-lookup"><span data-stu-id="d83fd-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="d83fd-111">Zmienna znajduje się w lokalizacji pamięci względem rejestru.</span><span class="sxs-lookup"><span data-stu-id="d83fd-111">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="d83fd-112">Zmienna nie jest w lokalizacji pamięci względem rejestru.</span><span class="sxs-lookup"><span data-stu-id="d83fd-112">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d83fd-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d83fd-113">Requirements</span></span>  
 <span data-ttu-id="d83fd-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d83fd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d83fd-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d83fd-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d83fd-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d83fd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d83fd-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d83fd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d83fd-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d83fd-118">See also</span></span>

- [<span data-ttu-id="d83fd-119">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="d83fd-119">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)

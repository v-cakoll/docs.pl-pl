---
title: ICorDebugInternalFrame2::GetFrameAddress — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2.GetFrameAddress Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2::GetFrameAddress
helpviewer_keywords:
- GetFrameAddress method [.NET Framework debugging]
- ICorDebugInternalFrame2::GetFrameAddress method [.NET Framework debugging]
ms.assetid: 4ee8d058-ffc8-4967-9133-a5adfef4e518
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3062e636921ea959716a500dae689fbe07915006
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759999"
---
# <a name="icordebuginternalframe2getframeaddress-method"></a><span data-ttu-id="590b6-102">ICorDebugInternalFrame2::GetFrameAddress — Metoda</span><span class="sxs-lookup"><span data-stu-id="590b6-102">ICorDebugInternalFrame2::GetFrameAddress Method</span></span>
<span data-ttu-id="590b6-103">Zwraca adres stosu ramka wewnętrzna.</span><span class="sxs-lookup"><span data-stu-id="590b6-103">Returns the stack address of the internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="590b6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="590b6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="590b6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="590b6-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="590b6-106">[out] Wskaźnik do `CORDB_ADDRESS` wewnętrznego ramki.</span><span class="sxs-lookup"><span data-stu-id="590b6-106">[out] Pointer to the `CORDB_ADDRESS` for the internal frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="590b6-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="590b6-107">Return Value</span></span>  
 <span data-ttu-id="590b6-108">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="590b6-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="590b6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="590b6-109">HRESULT</span></span>|<span data-ttu-id="590b6-110">Opis</span><span class="sxs-lookup"><span data-stu-id="590b6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="590b6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="590b6-111">S_OK</span></span>|<span data-ttu-id="590b6-112">Pomyślnie zwrócono adres ramka wewnętrzna.</span><span class="sxs-lookup"><span data-stu-id="590b6-112">The address of the internal frame was successfully returned.</span></span>|  
|<span data-ttu-id="590b6-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="590b6-113">E_FAIL</span></span>|<span data-ttu-id="590b6-114">Nie można zwrócić adres ramka wewnętrzna.</span><span class="sxs-lookup"><span data-stu-id="590b6-114">The address of the internal frame could not be returned.</span></span>|  
|<span data-ttu-id="590b6-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="590b6-115">E_INVALIDARG</span></span>|<span data-ttu-id="590b6-116">`pAddress` jest `null`.</span><span class="sxs-lookup"><span data-stu-id="590b6-116">`pAddress` is `null`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="590b6-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="590b6-117">Remarks</span></span>  
 <span data-ttu-id="590b6-118">Wartość zwracana w `pAddress` może służyć do określenia lokalizacji ramka wewnętrzna względem innych ramek na stosie.</span><span class="sxs-lookup"><span data-stu-id="590b6-118">The value returned in `pAddress` can be used to determine the location of the internal frame relative to other frames on the stack.</span></span> <span data-ttu-id="590b6-119">Nawet na komputerach z procesorami IA-64 ramka wewnętrzna znajduje się na stosie tylko, a nie ma odpowiedniego wskaźnika w magazynie zapasowym.</span><span class="sxs-lookup"><span data-stu-id="590b6-119">Even on IA-64-based computers, the internal frame lives on the stack only, and there is no corresponding pointer to a backing store.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="590b6-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="590b6-120">Requirements</span></span>  
 <span data-ttu-id="590b6-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="590b6-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="590b6-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="590b6-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="590b6-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="590b6-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="590b6-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="590b6-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="590b6-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="590b6-125">See also</span></span>

- [<span data-ttu-id="590b6-126">ICorDebugInternalFrame2, interfejs</span><span class="sxs-lookup"><span data-stu-id="590b6-126">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)
- [<span data-ttu-id="590b6-127">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="590b6-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="590b6-128">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="590b6-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

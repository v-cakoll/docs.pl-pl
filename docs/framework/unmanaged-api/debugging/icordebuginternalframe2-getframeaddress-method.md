---
title: "ICorDebugInternalFrame2::GetFrameAddress — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugInternalFrame2.GetFrameAddress Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugInternalFrame2::GetFrameAddress
helpviewer_keywords:
- GetFrameAddress method [.NET Framework debugging]
- ICorDebugInternalFrame2::GetFrameAddress method [.NET Framework debugging]
ms.assetid: 4ee8d058-ffc8-4967-9133-a5adfef4e518
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9ee867afe99fc5d2f2eb27bb1e6888aef8341d71
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebuginternalframe2getframeaddress-method"></a><span data-ttu-id="f38d7-102">ICorDebugInternalFrame2::GetFrameAddress — Metoda</span><span class="sxs-lookup"><span data-stu-id="f38d7-102">ICorDebugInternalFrame2::GetFrameAddress Method</span></span>
<span data-ttu-id="f38d7-103">Zwraca adres stosu wewnętrznego ramki.</span><span class="sxs-lookup"><span data-stu-id="f38d7-103">Returns the stack address of the internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f38d7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f38d7-104">Syntax</span></span>  
  
```  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f38d7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f38d7-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="f38d7-106">[out] Wskaźnik do `CORDB_ADDRESS` wewnętrzny ramki.</span><span class="sxs-lookup"><span data-stu-id="f38d7-106">[out] Pointer to the `CORDB_ADDRESS` for the internal frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f38d7-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f38d7-107">Return Value</span></span>  
 <span data-ttu-id="f38d7-108">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="f38d7-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f38d7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f38d7-109">HRESULT</span></span>|<span data-ttu-id="f38d7-110">Opis</span><span class="sxs-lookup"><span data-stu-id="f38d7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f38d7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f38d7-111">S_OK</span></span>|<span data-ttu-id="f38d7-112">Pomyślnie zwrócono adres wewnętrzny ramki.</span><span class="sxs-lookup"><span data-stu-id="f38d7-112">The address of the internal frame was successfully returned.</span></span>|  
|<span data-ttu-id="f38d7-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f38d7-113">E_FAIL</span></span>|<span data-ttu-id="f38d7-114">Nie można zwrócić adres wewnętrzny ramki.</span><span class="sxs-lookup"><span data-stu-id="f38d7-114">The address of the internal frame could not be returned.</span></span>|  
|<span data-ttu-id="f38d7-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f38d7-115">E_INVALIDARG</span></span>|<span data-ttu-id="f38d7-116">`pAddress`jest `null`.</span><span class="sxs-lookup"><span data-stu-id="f38d7-116">`pAddress` is `null`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f38d7-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f38d7-117">Remarks</span></span>  
 <span data-ttu-id="f38d7-118">Wartość zwracana w `pAddress` może służyć do określenia lokalizacji wewnętrznych ramki względem innych ramek na stosie.</span><span class="sxs-lookup"><span data-stu-id="f38d7-118">The value returned in `pAddress` can be used to determine the location of the internal frame relative to other frames on the stack.</span></span> <span data-ttu-id="f38d7-119">Nawet w przypadku komputerów z procesorami IA-64 wewnętrzny ramki znajduje się na stosie tylko, a nie ma odpowiedniego wskaźnika do magazynu zapasowego.</span><span class="sxs-lookup"><span data-stu-id="f38d7-119">Even on IA-64-based computers, the internal frame lives on the stack only, and there is no corresponding pointer to a backing store.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f38d7-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f38d7-120">Requirements</span></span>  
 <span data-ttu-id="f38d7-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f38d7-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f38d7-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f38d7-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f38d7-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f38d7-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f38d7-124">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f38d7-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f38d7-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f38d7-125">See Also</span></span>  
 [<span data-ttu-id="f38d7-126">ICorDebugInternalFrame2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="f38d7-126">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 [<span data-ttu-id="f38d7-127">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="f38d7-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="f38d7-128">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="f38d7-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

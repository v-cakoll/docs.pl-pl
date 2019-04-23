---
title: ICorDebugCode::GetSize — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetSize method [.NET Framework debugging]
ms.assetid: 115bc6de-f5e2-4e8e-bb38-c7cf54045434
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 678b7fbd595b1238b7025c22b0ed80b02ed4becd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59085678"
---
# <a name="icordebugcodegetsize-method"></a><span data-ttu-id="b43e3-102">ICorDebugCode::GetSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="b43e3-102">ICorDebugCode::GetSize Method</span></span>
<span data-ttu-id="b43e3-103">Pobiera rozmiar w bajtach, reprezentowane przez ten icordebugcode "—" kod binarny.</span><span class="sxs-lookup"><span data-stu-id="b43e3-103">Gets the size, in bytes, of the binary code represented by this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b43e3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b43e3-104">Syntax</span></span>  
  
```  
HRESULT GetSize (  
    [out] ULONG32    *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b43e3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b43e3-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="b43e3-106">[out] Wskaźnik do rozmiaru, w bajtach pliku binarnego kod, że `ICorDebugCode` obiekt reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="b43e3-106">[out] A pointer to the size, in bytes, of the binary code that this `ICorDebugCode` object represents.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b43e3-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b43e3-107">Requirements</span></span>  
 <span data-ttu-id="b43e3-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b43e3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b43e3-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b43e3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b43e3-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b43e3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b43e3-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b43e3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b43e3-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b43e3-112">See also</span></span>

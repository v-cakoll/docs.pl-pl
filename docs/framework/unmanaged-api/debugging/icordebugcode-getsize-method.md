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
ms.openlocfilehash: 3a9a43735ec80821c2380b824bfced99113cf08f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651100"
---
# <a name="icordebugcodegetsize-method"></a><span data-ttu-id="c964b-102">ICorDebugCode::GetSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="c964b-102">ICorDebugCode::GetSize Method</span></span>
<span data-ttu-id="c964b-103">Pobiera rozmiar w bajtach, reprezentowane przez ten icordebugcode "—" kod binarny.</span><span class="sxs-lookup"><span data-stu-id="c964b-103">Gets the size, in bytes, of the binary code represented by this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c964b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c964b-104">Syntax</span></span>  
  
```  
HRESULT GetSize (  
    [out] ULONG32    *pcBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c964b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c964b-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="c964b-106">[out] Wskaźnik do rozmiaru, w bajtach pliku binarnego kod, że `ICorDebugCode` obiekt reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="c964b-106">[out] A pointer to the size, in bytes, of the binary code that this `ICorDebugCode` object represents.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c964b-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c964b-107">Requirements</span></span>  
 <span data-ttu-id="c964b-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c964b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c964b-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c964b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c964b-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c964b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c964b-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c964b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c964b-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c964b-112">See also</span></span>


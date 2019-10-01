---
title: ICorDebugCode::GetAddress — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetAddress
helpviewer_keywords:
- GetAddress method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetAddress method [.NET Framework debugging]
ms.assetid: cc507cb0-df2e-49c2-b32e-0c3271a8df9a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7df668487601e4278b56e196a43d1154b643fd29
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700746"
---
# <a name="icordebugcodegetaddress-method"></a><span data-ttu-id="ea4db-102">ICorDebugCode::GetAddress — Metoda</span><span class="sxs-lookup"><span data-stu-id="ea4db-102">ICorDebugCode::GetAddress Method</span></span>
<span data-ttu-id="ea4db-103">Pobiera względny adres wirtualny (RVA) segmentu kodu, który reprezentuje ten interfejs "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="ea4db-103">Gets the relative virtual address (RVA) of the code segment that this "ICorDebugCode" interface represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea4db-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ea4db-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS *pStart  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea4db-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ea4db-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="ea4db-106">określoną Wskaźnik do adresu RVA segmentu kodu.</span><span class="sxs-lookup"><span data-stu-id="ea4db-106">[out] A pointer to the RVA of the code segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea4db-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ea4db-107">Requirements</span></span>  
 <span data-ttu-id="ea4db-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea4db-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea4db-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ea4db-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea4db-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ea4db-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea4db-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea4db-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

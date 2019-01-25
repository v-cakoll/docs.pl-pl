---
title: ICorDebugCode::GetVersionNumber — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetVersionNumber
helpviewer_keywords:
- GetVersionNumber method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetVersionNumber method [.NET Framework debugging]
ms.assetid: c8e02518-679f-4e9f-8a28-ba4a89a3876f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b383c322f1119ff13ac4df9a8dc0563d26dcf895
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499724"
---
# <a name="icordebugcodegetversionnumber-method"></a><span data-ttu-id="73ce8-102">ICorDebugCode::GetVersionNumber — Metoda</span><span class="sxs-lookup"><span data-stu-id="73ce8-102">ICorDebugCode::GetVersionNumber Method</span></span>
<span data-ttu-id="73ce8-103">Pobiera numer liczonego od jednego, który identyfikuje wersję kodu, który reprezentuje to "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="73ce8-103">Gets the one-based number that identifies the version of the code that this "ICorDebugCode" represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73ce8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="73ce8-104">Syntax</span></span>  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32    *nVersion  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="73ce8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73ce8-105">Parameters</span></span>  
 `nVersion`  
 <span data-ttu-id="73ce8-106">[out] Wskaźnik do numer wersji kodu.</span><span class="sxs-lookup"><span data-stu-id="73ce8-106">[out] A pointer to the version number of the code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73ce8-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="73ce8-107">Remarks</span></span>  
 <span data-ttu-id="73ce8-108">Numer wersji jest zwiększany każdorazowo, gdy operacja edit-and-continue (EnC) odbywa się na kodzie.</span><span class="sxs-lookup"><span data-stu-id="73ce8-108">The version number is incremented each time an edit-and-continue (EnC) operation is performed on the code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73ce8-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="73ce8-109">Requirements</span></span>  
 <span data-ttu-id="73ce8-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73ce8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73ce8-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73ce8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73ce8-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73ce8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73ce8-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73ce8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73ce8-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73ce8-114">See also</span></span>


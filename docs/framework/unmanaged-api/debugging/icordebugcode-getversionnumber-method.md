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
ms.openlocfilehash: 003b29501e8f22ed9010a9f16a4f7ee67bce03a8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59098952"
---
# <a name="icordebugcodegetversionnumber-method"></a><span data-ttu-id="26d9d-102">ICorDebugCode::GetVersionNumber — Metoda</span><span class="sxs-lookup"><span data-stu-id="26d9d-102">ICorDebugCode::GetVersionNumber Method</span></span>
<span data-ttu-id="26d9d-103">Pobiera numer liczonego od jednego, który identyfikuje wersję kodu, który reprezentuje to "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="26d9d-103">Gets the one-based number that identifies the version of the code that this "ICorDebugCode" represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26d9d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="26d9d-104">Syntax</span></span>  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32    *nVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26d9d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="26d9d-105">Parameters</span></span>  
 `nVersion`  
 <span data-ttu-id="26d9d-106">[out] Wskaźnik do numer wersji kodu.</span><span class="sxs-lookup"><span data-stu-id="26d9d-106">[out] A pointer to the version number of the code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26d9d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="26d9d-107">Remarks</span></span>  
 <span data-ttu-id="26d9d-108">Numer wersji jest zwiększany każdorazowo, gdy operacja edit-and-continue (EnC) odbywa się na kodzie.</span><span class="sxs-lookup"><span data-stu-id="26d9d-108">The version number is incremented each time an edit-and-continue (EnC) operation is performed on the code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26d9d-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="26d9d-109">Requirements</span></span>  
 <span data-ttu-id="26d9d-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26d9d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26d9d-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="26d9d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26d9d-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26d9d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26d9d-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26d9d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26d9d-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26d9d-114">See also</span></span>

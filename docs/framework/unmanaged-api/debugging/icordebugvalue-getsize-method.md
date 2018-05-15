---
title: ICorDebugValue::GetSize — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugValue interface [.NET Framework debugging]
- ICorDebugValue::GetSize method [.NET Framework debugging]
ms.assetid: 445a9ee3-e050-4f3a-931a-96b0efb00110
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0023b8ad815b9204ed56791698c7242dfe90bec4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugvaluegetsize-method"></a><span data-ttu-id="75139-102">ICorDebugValue::GetSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="75139-102">ICorDebugValue::GetSize Method</span></span>
<span data-ttu-id="75139-103">Pobiera rozmiar w bajtach tego obiektu "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="75139-103">Gets the size, in bytes, of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75139-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="75139-104">Syntax</span></span>  
  
```  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="75139-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="75139-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="75139-106">[out] Rozmiar w bajtach, ta wartość obiektu.</span><span class="sxs-lookup"><span data-stu-id="75139-106">[out] The size, in bytes, of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75139-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="75139-107">Remarks</span></span>  
 <span data-ttu-id="75139-108">Jeśli typ wartości jest typem referencyjnym, ta metoda zwraca rozmiar wskaźnika niż rozmiar obiektu.</span><span class="sxs-lookup"><span data-stu-id="75139-108">If the value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="75139-109">`ICorDebugValue::GetSize` Metoda zwraca `COR_E_OVERFLOW` dla obiektów, które są większe niż 4 GB na platformach 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="75139-109">The `ICorDebugValue::GetSize` method returns `COR_E_OVERFLOW` for objects that are larger than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="75139-110">Użyj [ICorDebugValue3::GetSize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) metody zamiast tego dla obiektów, które są większe niż 4 GB.</span><span class="sxs-lookup"><span data-stu-id="75139-110">Use the [ICorDebugValue3::GetSize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) method instead for objects that are larger than 4 GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75139-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="75139-111">Requirements</span></span>  
 <span data-ttu-id="75139-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75139-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75139-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="75139-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="75139-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75139-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75139-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75139-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75139-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="75139-116">See Also</span></span>  
    
 [<span data-ttu-id="75139-117">GetSize64, metoda</span><span class="sxs-lookup"><span data-stu-id="75139-117">GetSize64 Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)

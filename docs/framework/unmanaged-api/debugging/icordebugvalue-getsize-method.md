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
ms.openlocfilehash: 3d26ddb6d89af60acf6dc1214b0423ba75e488ff
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791167"
---
# <a name="icordebugvaluegetsize-method"></a><span data-ttu-id="40909-102">ICorDebugValue::GetSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="40909-102">ICorDebugValue::GetSize Method</span></span>
<span data-ttu-id="40909-103">Pobiera rozmiar tego obiektu "ICorDebugValue" w bajtach.</span><span class="sxs-lookup"><span data-stu-id="40909-103">Gets the size, in bytes, of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40909-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="40909-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40909-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="40909-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="40909-106">określoną Rozmiar (w bajtach) tego obiektu wartości.</span><span class="sxs-lookup"><span data-stu-id="40909-106">[out] The size, in bytes, of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40909-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="40909-107">Remarks</span></span>  
 <span data-ttu-id="40909-108">Jeśli typ wartości jest typem referencyjnym, Metoda ta zwraca rozmiar wskaźnika, a nie rozmiar obiektu.</span><span class="sxs-lookup"><span data-stu-id="40909-108">If the value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="40909-109">Metoda `ICorDebugValue::GetSize` zwraca `COR_E_OVERFLOW` dla obiektów, które są większe niż 4 GB na platformach 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="40909-109">The `ICorDebugValue::GetSize` method returns `COR_E_OVERFLOW` for objects that are larger than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="40909-110">Zamiast obiektów, które są większe niż 4 GB, użyj metody [ICorDebugValue3:: GetSize64 —](icordebugvalue3-getsize64-method.md) .</span><span class="sxs-lookup"><span data-stu-id="40909-110">Use the [ICorDebugValue3::GetSize64](icordebugvalue3-getsize64-method.md) method instead for objects that are larger than 4 GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40909-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="40909-111">Requirements</span></span>  
 <span data-ttu-id="40909-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40909-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40909-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="40909-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40909-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="40909-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40909-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40909-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40909-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40909-116">See also</span></span>

- [<span data-ttu-id="40909-117">GetSize64, metoda</span><span class="sxs-lookup"><span data-stu-id="40909-117">GetSize64 Method</span></span>](icordebugvalue3-getsize64-method.md)

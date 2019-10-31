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
ms.openlocfilehash: 646c20ca1b78ff0ce513b8a3c9b578c3b1b9a696
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125603"
---
# <a name="icordebugcodegetversionnumber-method"></a><span data-ttu-id="9d5cc-102">ICorDebugCode::GetVersionNumber — Metoda</span><span class="sxs-lookup"><span data-stu-id="9d5cc-102">ICorDebugCode::GetVersionNumber Method</span></span>

<span data-ttu-id="9d5cc-103">Pobiera jednostronicowy numer identyfikujący wersję kodu, który reprezentuje ten "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="9d5cc-103">Gets the one-based number that identifies the version of the code that this "ICorDebugCode" represents.</span></span>

## <a name="syntax"></a><span data-ttu-id="9d5cc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d5cc-104">Syntax</span></span>

```cpp
HRESULT GetVersionNumber (
    [out] ULONG32    *nVersion
);
```

## <a name="parameters"></a><span data-ttu-id="9d5cc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d5cc-105">Parameters</span></span>

 `nVersion`  
 <span data-ttu-id="9d5cc-106">określoną Wskaźnik do numeru wersji kodu.</span><span class="sxs-lookup"><span data-stu-id="9d5cc-106">[out] A pointer to the version number of the code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9d5cc-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9d5cc-107">Remarks</span></span>

 <span data-ttu-id="9d5cc-108">Numer wersji jest zwiększany za każdym razem, gdy operacja Edit-and-Continue (EnC) jest wykonywana na kodzie.</span><span class="sxs-lookup"><span data-stu-id="9d5cc-108">The version number is incremented each time an edit-and-continue (EnC) operation is performed on the code.</span></span>

## <a name="requirements"></a><span data-ttu-id="9d5cc-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9d5cc-109">Requirements</span></span>

 <span data-ttu-id="9d5cc-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d5cc-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d5cc-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9d5cc-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d5cc-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9d5cc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d5cc-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d5cc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

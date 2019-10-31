---
title: ICorDebugInternalFrame::GetFrameType — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame.GetFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame::GetFrameType
helpviewer_keywords:
- GetFrameType method [.NET Framework debugging]
- ICorDebugInternalFrame::GetFrameType method [.NET Framework debugging]
ms.assetid: da278a29-dc2e-4bf7-96ce-801bdc4d7025
topic_type:
- apiref
ms.openlocfilehash: b7a33fd6e2178e0e9188b81f516b231702fb6460
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122713"
---
# <a name="icordebuginternalframegetframetype-method"></a><span data-ttu-id="f2a7d-102">ICorDebugInternalFrame::GetFrameType — Metoda</span><span class="sxs-lookup"><span data-stu-id="f2a7d-102">ICorDebugInternalFrame::GetFrameType Method</span></span>
<span data-ttu-id="f2a7d-103">Pobiera typ tej wewnętrznej ramki.</span><span class="sxs-lookup"><span data-stu-id="f2a7d-103">Gets the type of this internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2a7d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f2a7d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameType (  
    [out] CorDebugInternalFrameType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2a7d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f2a7d-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="f2a7d-106">określoną Wskaźnik do wartości wyliczenia CorDebugInternalFrameType —, który wskazuje typ wewnętrznej ramki reprezentowanej przez ten obiekt `ICorDebugInternalFrame`.</span><span class="sxs-lookup"><span data-stu-id="f2a7d-106">[out] A pointer to a value of the CorDebugInternalFrameType enumeration that indicates the type of internal frame represented by this `ICorDebugInternalFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2a7d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f2a7d-107">Remarks</span></span>  
 <span data-ttu-id="f2a7d-108">Wewnętrzny typ ramki nigdy nie będzie STUBFRAME_NONE.</span><span class="sxs-lookup"><span data-stu-id="f2a7d-108">The internal frame type will never be STUBFRAME_NONE.</span></span> <span data-ttu-id="f2a7d-109">Debugery powinny bezpiecznie ignorować nierozpoznane typy ramek wewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="f2a7d-109">Debuggers should gracefully ignore unrecognized internal frame types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2a7d-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f2a7d-110">Requirements</span></span>  
 <span data-ttu-id="f2a7d-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2a7d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2a7d-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f2a7d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2a7d-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f2a7d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2a7d-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2a7d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

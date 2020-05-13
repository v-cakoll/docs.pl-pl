---
title: ICorDebugNativeFrame::GetIP — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
- ICorDebugNativeFrame::GetIP method [.NET Framework debugging]
ms.assetid: 99f693f3-d3b9-4fd8-9d09-b8efd03f7b67
topic_type:
- apiref
ms.openlocfilehash: 53576ca938074fb7e5974a96bb53a84cb6ed67ab
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213598"
---
# <a name="icordebugnativeframegetip-method"></a><span data-ttu-id="f011e-102">ICorDebugNativeFrame::GetIP — Metoda</span><span class="sxs-lookup"><span data-stu-id="f011e-102">ICorDebugNativeFrame::GetIP Method</span></span>
<span data-ttu-id="f011e-103">Pobiera lokalizację natywnego przesunięcia kodu, w której wskaźnik instrukcji jest obecnie ustawiony.</span><span class="sxs-lookup"><span data-stu-id="f011e-103">Gets the native code offset location to which the instruction pointer is currently set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f011e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f011e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f011e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f011e-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="f011e-106">określoną Wskaźnik do lokalizacji przesunięcia w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="f011e-106">[out] A pointer to the offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f011e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f011e-107">Remarks</span></span>  
 <span data-ttu-id="f011e-108">Jeśli ramka stosu reprezentowana przez ten "ICorDebugNativeFrame" jest aktywna, przesunięcie jest adresem następnej instrukcji do wykonania.</span><span class="sxs-lookup"><span data-stu-id="f011e-108">If the stack frame that is represented by this "ICorDebugNativeFrame" is active, the offset is the address of the next instruction to be executed.</span></span> <span data-ttu-id="f011e-109">Jeśli ta ramka stosu nie jest aktywna, przesunięcie jest adresem następnej instrukcji, która ma zostać wykonana po ponownym uaktywnieniu ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="f011e-109">If this stack frame is not active, the offset is the address of the next instruction to be executed when the stack frame is reactivated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f011e-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f011e-110">Requirements</span></span>  
 <span data-ttu-id="f011e-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f011e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f011e-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f011e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f011e-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f011e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f011e-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f011e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f011e-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f011e-115">See also</span></span>

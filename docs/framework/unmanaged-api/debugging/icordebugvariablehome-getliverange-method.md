---
title: 'IcorDebugVariableHome:: GetLiveRange, Metoda'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetLiveRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetLiveRange
helpviewer_keywords:
- ICorDebugVariableHome::GetLiveRange method [.NET Framework debugging]
- GetLiveRange method, ICorDebugVariableFrame interface [.NET Framework debugging]
ms.assetid: 87277e1a-1595-4729-9e25-d1c3ac18ce5f
topic_type:
- apiref
ms.openlocfilehash: fb198782bb91a8301507fd6cadcffb0378230f0e
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396583"
---
# <a name="icordebugvariablehomegetliverange-method"></a><span data-ttu-id="f569a-102">IcorDebugVariableHome:: GetLiveRange, Metoda</span><span class="sxs-lookup"><span data-stu-id="f569a-102">IcorDebugVariableHome::GetLiveRange Method</span></span>
<span data-ttu-id="f569a-103">Pobiera natywny zakres, w którym znajduje się ta zmienna.</span><span class="sxs-lookup"><span data-stu-id="f569a-103">Gets the native range over which this variable is live.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f569a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f569a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLiveRange(  
    [out] ULONG32* pStartOffset,  
    [out] ULONG32 *pEndOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f569a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f569a-105">Parameters</span></span>  
 `pStartOffset`  
 <span data-ttu-id="f569a-106">określoną Przesunięcie logiczne, od którego zmienna jest najpierw aktywna.</span><span class="sxs-lookup"><span data-stu-id="f569a-106">[out] The logical offset at which the variable is first live.</span></span>  
  
 `pEndOffset`  
 <span data-ttu-id="f569a-107">określoną Logiczne przesunięcie bezpośrednio po punkcie, w którym zmienna jest Ostatnia na żywo.</span><span class="sxs-lookup"><span data-stu-id="f569a-107">[out] The logical offset immediately after the point at which the variable is last live.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f569a-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f569a-108">Requirements</span></span>  
 <span data-ttu-id="f569a-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f569a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f569a-110">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f569a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f569a-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f569a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f569a-112">**.NET Framework wersje:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f569a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f569a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f569a-113">See also</span></span>

- [<span data-ttu-id="f569a-114">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="f569a-114">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)

---
title: ICorDebugFrame::GetStackRange — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetStackRange
helpviewer_keywords:
- GetStackRange method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetStackRange method [.NET Framework debugging]
ms.assetid: fab037cb-fda6-40fb-9367-921e435dd5a0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c9f58e66286f5e3e169507efd2f87ce10e9d323b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754853"
---
# <a name="icordebugframegetstackrange-method"></a><span data-ttu-id="6b832-102">ICorDebugFrame::GetStackRange — Metoda</span><span class="sxs-lookup"><span data-stu-id="6b832-102">ICorDebugFrame::GetStackRange Method</span></span>
<span data-ttu-id="6b832-103">Pobiera bezwzględny zakres adresów tej ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="6b832-103">Gets the absolute address range of this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b832-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b832-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b832-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b832-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="6b832-106">[out] Wskaźnik do `CORDB_ADDRESS` , który określa adres początkowy ramki stosu, reprezentowane przez to `ICorDebugFrame` obiektu.</span><span class="sxs-lookup"><span data-stu-id="6b832-106">[out] A pointer to a `CORDB_ADDRESS` that specifies the starting address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="6b832-107">[out] Wskaźnik do `CORDB_ADDRESS` , który określa adres końcowy ramki stosu, reprezentowane przez to `ICorDebugFrame` obiektu.</span><span class="sxs-lookup"><span data-stu-id="6b832-107">[out] A pointer to a `CORDB_ADDRESS` that specifies the ending address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b832-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6b832-108">Remarks</span></span>  
 <span data-ttu-id="6b832-109">Zakres adresów stosu jest przydatna do zszywania przeplotem śladów stosu zebranych z wielu aparaty debugowania.</span><span class="sxs-lookup"><span data-stu-id="6b832-109">The address range of the stack is useful for piecing together interleaved stack traces gathered from multiple debugging engines.</span></span> <span data-ttu-id="6b832-110">Zakresu liczbowego nie dostarcza żadnych informacji o zawartości ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="6b832-110">The numeric range provides no information about the contents of the stack frame.</span></span> <span data-ttu-id="6b832-111">Jest to istotne tylko w przypadku porównywania lokalizacje ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="6b832-111">It is meaningful only for comparison of stack frame locations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b832-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6b832-112">Requirements</span></span>  
 <span data-ttu-id="6b832-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b832-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b832-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6b832-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b832-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b832-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b832-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b832-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

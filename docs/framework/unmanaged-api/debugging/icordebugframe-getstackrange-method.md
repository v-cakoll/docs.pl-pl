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
ms.openlocfilehash: cacdccf5c27cd1d115134d49e754b4ace2870b72
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205161"
---
# <a name="icordebugframegetstackrange-method"></a><span data-ttu-id="4e858-102">ICorDebugFrame::GetStackRange — Metoda</span><span class="sxs-lookup"><span data-stu-id="4e858-102">ICorDebugFrame::GetStackRange Method</span></span>
<span data-ttu-id="4e858-103">Pobiera bezwzględny zakres adresów tej ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="4e858-103">Gets the absolute address range of this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e858-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4e858-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e858-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4e858-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="4e858-106">określoną Wskaźnik do `CORDB_ADDRESS` obiektu, który określa adres początkowy ramki stosu reprezentowanej przez ten `ICorDebugFrame` obiekt.</span><span class="sxs-lookup"><span data-stu-id="4e858-106">[out] A pointer to a `CORDB_ADDRESS` that specifies the starting address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="4e858-107">określoną Wskaźnik do `CORDB_ADDRESS` obiektu, który określa adres końcowy ramki stosu reprezentowanej przez ten `ICorDebugFrame` obiekt.</span><span class="sxs-lookup"><span data-stu-id="4e858-107">[out] A pointer to a `CORDB_ADDRESS` that specifies the ending address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e858-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4e858-108">Remarks</span></span>  
 <span data-ttu-id="4e858-109">Zakres adresów stosu jest przydatny do zszywania razem z przeplotem śladów stosu zebranych z wielu aparatów debugowania.</span><span class="sxs-lookup"><span data-stu-id="4e858-109">The address range of the stack is useful for piecing together interleaved stack traces gathered from multiple debugging engines.</span></span> <span data-ttu-id="4e858-110">Zakres liczbowy nie zawiera żadnych informacji o zawartości ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="4e858-110">The numeric range provides no information about the contents of the stack frame.</span></span> <span data-ttu-id="4e858-111">Jest to zrozumiałe tylko dla porównania lokalizacji ramek stosu.</span><span class="sxs-lookup"><span data-stu-id="4e858-111">It is meaningful only for comparison of stack frame locations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e858-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4e858-112">Requirements</span></span>  
 <span data-ttu-id="4e858-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e858-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e858-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4e858-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e858-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4e858-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e858-116">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e858-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

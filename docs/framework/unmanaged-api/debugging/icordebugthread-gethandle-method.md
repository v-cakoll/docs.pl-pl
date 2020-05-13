---
title: ICorDebugThread::GetHandle — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetHandle method [.NET Framework debugging]
ms.assetid: 172ef8c4-2ead-4cfc-bd2e-dee4fb7191cd
topic_type:
- apiref
ms.openlocfilehash: 16aafa439fc81c3606f98ca2ba860316ec46e0db
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379737"
---
# <a name="icordebugthreadgethandle-method"></a><span data-ttu-id="85b8b-102">ICorDebugThread::GetHandle — Metoda</span><span class="sxs-lookup"><span data-stu-id="85b8b-102">ICorDebugThread::GetHandle Method</span></span>
<span data-ttu-id="85b8b-103">Pobiera bieżące dojście dla aktywnej części tego ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="85b8b-103">Gets the current handle for the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85b8b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="85b8b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85b8b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="85b8b-105">Parameters</span></span>  
 `phThreadHandle`  
 <span data-ttu-id="85b8b-106">określoną Wskaźnik do elementu HTHREAD, który jest uchwytem aktywnej części tego wątku.</span><span class="sxs-lookup"><span data-stu-id="85b8b-106">[out] A pointer to an HTHREAD that is the handle of the active part of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85b8b-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="85b8b-107">Remarks</span></span>  
 <span data-ttu-id="85b8b-108">Dojście może ulec zmianie, gdy proces jest wykonywany i może się różnić w różnych częściach wątku.</span><span class="sxs-lookup"><span data-stu-id="85b8b-108">The handle may change as the process executes, and may be different for different parts of the thread.</span></span>  
  
 <span data-ttu-id="85b8b-109">To dojście jest własnością interfejsu API debugowania.</span><span class="sxs-lookup"><span data-stu-id="85b8b-109">This handle is owned by the debugging API.</span></span> <span data-ttu-id="85b8b-110">Debuger powinien go zduplikować przed użyciem.</span><span class="sxs-lookup"><span data-stu-id="85b8b-110">The debugger should duplicate it before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85b8b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="85b8b-111">Requirements</span></span>  
 <span data-ttu-id="85b8b-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85b8b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85b8b-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="85b8b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85b8b-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="85b8b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85b8b-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85b8b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

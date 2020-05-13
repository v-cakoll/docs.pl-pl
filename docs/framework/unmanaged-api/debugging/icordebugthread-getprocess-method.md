---
title: ICorDebugThread::GetProcess — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetProcess
helpviewer_keywords:
- ICorDebugThread::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 163816e7-0739-4566-b3df-cd256be8b8a4
topic_type:
- apiref
ms.openlocfilehash: 76dfc10b9d9069f6d53cd292f241ae3080c6443a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379808"
---
# <a name="icordebugthreadgetprocess-method"></a><span data-ttu-id="b53d6-102">ICorDebugThread::GetProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="b53d6-102">ICorDebugThread::GetProcess Method</span></span>
<span data-ttu-id="b53d6-103">Pobiera wskaźnik interfejsu do procesu, którego częścią jest ten ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="b53d6-103">Gets an interface pointer to the process of which this ICorDebugThread forms a part.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b53d6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b53d6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b53d6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b53d6-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="b53d6-106">określoną Wskaźnik do adresu obiektu interfejsu ICorDebugProcess, który reprezentuje proces.</span><span class="sxs-lookup"><span data-stu-id="b53d6-106">[out] A pointer to the address of an ICorDebugProcess interface object that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b53d6-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b53d6-107">Requirements</span></span>  
 <span data-ttu-id="b53d6-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b53d6-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b53d6-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b53d6-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b53d6-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b53d6-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b53d6-111">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b53d6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

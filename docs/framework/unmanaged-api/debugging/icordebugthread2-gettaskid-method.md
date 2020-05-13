---
title: ICorDebugThread2::GetTaskID — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetTaskID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetTaskID
helpviewer_keywords:
- ICorDebugThread2::GetTaskID method [.NET Framework debugging]
- GetTaskID method [.NET Framework debugging]
ms.assetid: 6ba3c6ee-4ba1-4c98-bf1e-8531acd3da09
topic_type:
- apiref
ms.openlocfilehash: 841af546cc3586529fe290c69e686438f634b90d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83377784"
---
# <a name="icordebugthread2gettaskid-method"></a><span data-ttu-id="996bd-102">ICorDebugThread2::GetTaskID — Metoda</span><span class="sxs-lookup"><span data-stu-id="996bd-102">ICorDebugThread2::GetTaskID Method</span></span>
<span data-ttu-id="996bd-103">Pobiera identyfikator zadania uruchomionego w tym wątku.</span><span class="sxs-lookup"><span data-stu-id="996bd-103">Gets the identifier of the task running on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="996bd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="996bd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="996bd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="996bd-105">Parameters</span></span>  
 `pTaskId`  
 <span data-ttu-id="996bd-106">określoną Wskaźnik do identyfikatora zadania uruchomionego w wątku reprezentowanego przez ten obiekt ICorDebugThread2.</span><span class="sxs-lookup"><span data-stu-id="996bd-106">[out] A pointer to the identifier of the task running on the thread represented by this ICorDebugThread2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="996bd-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="996bd-107">Remarks</span></span>  
 <span data-ttu-id="996bd-108">Zadanie może być uruchomione tylko w wątku, jeśli wątek jest skojarzony z połączeniem.</span><span class="sxs-lookup"><span data-stu-id="996bd-108">A task can only be running on the thread if the thread is associated with a connection.</span></span> <span data-ttu-id="996bd-109">`GetTaskID`zwraca zero w `pTaskId` przypadku, gdy wątek nie jest skojarzony z połączeniem.</span><span class="sxs-lookup"><span data-stu-id="996bd-109">`GetTaskID` returns zero in `pTaskId` if the thread is not associated with a connection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="996bd-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="996bd-110">Requirements</span></span>  
 <span data-ttu-id="996bd-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="996bd-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="996bd-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="996bd-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="996bd-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="996bd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="996bd-114">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="996bd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

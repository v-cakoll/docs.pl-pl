---
title: ICorDebugThread::GetID — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetID
helpviewer_keywords:
- ICorDebugThread::GetID method [.NET Framework debugging]
- GetID method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: f1de4584-92df-42f3-9da4-fca03a1c6821
topic_type:
- apiref
ms.openlocfilehash: d01936481ec139757566d5b96cb95ea887cb8c20
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378056"
---
# <a name="icordebugthreadgetid-method"></a><span data-ttu-id="196d7-102">ICorDebugThread::GetID — Metoda</span><span class="sxs-lookup"><span data-stu-id="196d7-102">ICorDebugThread::GetID Method</span></span>
<span data-ttu-id="196d7-103">Pobiera bieżący identyfikator systemu operacyjnego aktywnej części tego ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="196d7-103">Gets the current operating system identifier of the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="196d7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="196d7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] DWORD *pdwThreadId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="196d7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="196d7-105">Parameters</span></span>  
 `pdwThreadId`  
 <span data-ttu-id="196d7-106">określoną Identyfikator wątku.</span><span class="sxs-lookup"><span data-stu-id="196d7-106">[out] The identifier of the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="196d7-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="196d7-107">Remarks</span></span>  
 <span data-ttu-id="196d7-108">Identyfikator systemu operacyjnego może ulec zmianie podczas wykonywania procesu i może być inną wartością dla różnych części wątku.</span><span class="sxs-lookup"><span data-stu-id="196d7-108">The operating system identifier can potentially change during execution of a process, and can be a different value for different parts of the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="196d7-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="196d7-109">Requirements</span></span>  
 <span data-ttu-id="196d7-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="196d7-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="196d7-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="196d7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="196d7-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="196d7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="196d7-113">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="196d7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

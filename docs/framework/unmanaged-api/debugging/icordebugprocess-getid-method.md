---
title: ICorDebugProcess::GetID — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetID
helpviewer_keywords:
- GetID method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetID method [.NET Framework debugging]
ms.assetid: b0ba8453-fa7e-4c14-93e5-335409cd4a47
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7d9239ccfe8ce08e5b50b762a6fede11ab8a439b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994500"
---
# <a name="icordebugprocessgetid-method"></a><span data-ttu-id="9bc6d-102">ICorDebugProcess::GetID — Metoda</span><span class="sxs-lookup"><span data-stu-id="9bc6d-102">ICorDebugProcess::GetID Method</span></span>
<span data-ttu-id="9bc6d-103">Pobiera identyfikator systemu operacyjnego (OS) procesu.</span><span class="sxs-lookup"><span data-stu-id="9bc6d-103">Gets the operating system (OS) ID of the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bc6d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9bc6d-104">Syntax</span></span>  
  
```  
HRESULT GetID([out] DWORD *pdwProcessId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9bc6d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9bc6d-105">Parameters</span></span>  
 `pdwProcessId`  
 <span data-ttu-id="9bc6d-106">[out] Unikatowy identyfikator procesu.</span><span class="sxs-lookup"><span data-stu-id="9bc6d-106">[out] The unique ID of the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bc6d-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9bc6d-107">Requirements</span></span>  
 <span data-ttu-id="9bc6d-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bc6d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bc6d-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9bc6d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9bc6d-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9bc6d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9bc6d-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bc6d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

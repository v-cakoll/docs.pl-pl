---
title: ICorDebugStepper2::SetJMC — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper2.SetJMC
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper2::SetJMC
helpviewer_keywords:
- ICorDebugStepper2::SetJMC method [.NET Framework debugging]
- SetJMC method [.NET Framework debugging]
ms.assetid: f5cdc135-6db4-4b32-9dd1-260ec58b774f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 129bf04a097b2019b080f813bf049d41b501f8fd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663872"
---
# <a name="icordebugstepper2setjmc-method"></a><span data-ttu-id="ddc95-102">ICorDebugStepper2::SetJMC — Metoda</span><span class="sxs-lookup"><span data-stu-id="ddc95-102">ICorDebugStepper2::SetJMC Method</span></span>
<span data-ttu-id="ddc95-103">Ustawia wartość określającą, czy ten ICorDebugStepper — przeprowadzi tylko kod, który został utworzony przez dewelopera aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ddc95-103">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span> <span data-ttu-id="ddc95-104">Ten proces jest również znane jako tylko mój kod (JMC) debugowania.</span><span class="sxs-lookup"><span data-stu-id="ddc95-104">This process is also known as just my code (JMC) debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddc95-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ddc95-105">Syntax</span></span>  
  
```  
HRESULT SetJMC (  
    [in] BOOL    fIsJMCStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ddc95-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ddc95-106">Parameters</span></span>  
 `fIsJMCStepper`  
 <span data-ttu-id="ddc95-107">[in] Ustaw `true` przechodzić jedynie przez kod, który jest utworzony przez dewelopera aplikacji; w przeciwnym wypadku ustaw `false`.</span><span class="sxs-lookup"><span data-stu-id="ddc95-107">[in] Set to `true` to step only through code that is authored by an application's developer; otherwise, set to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddc95-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ddc95-108">Requirements</span></span>  
 <span data-ttu-id="ddc95-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ddc95-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddc95-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ddc95-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ddc95-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ddc95-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ddc95-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddc95-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

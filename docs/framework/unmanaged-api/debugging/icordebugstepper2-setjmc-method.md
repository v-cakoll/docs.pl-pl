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
ms.openlocfilehash: 6c076dd2912a22e4f9492492a2d7a9fb73db88e8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139036"
---
# <a name="icordebugstepper2setjmc-method"></a><span data-ttu-id="2a010-102">ICorDebugStepper2::SetJMC — Metoda</span><span class="sxs-lookup"><span data-stu-id="2a010-102">ICorDebugStepper2::SetJMC Method</span></span>
<span data-ttu-id="2a010-103">Ustawia wartość określającą, czy ten ICorDebugStepper czynności tylko za pomocą kodu, który jest tworzony przez dewelopera aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2a010-103">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span> <span data-ttu-id="2a010-104">Ten proces jest również znany jako debugowanie tylko mój kod (JMC).</span><span class="sxs-lookup"><span data-stu-id="2a010-104">This process is also known as just my code (JMC) debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a010-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2a010-105">Syntax</span></span>  
  
```cpp  
HRESULT SetJMC (  
    [in] BOOL    fIsJMCStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a010-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2a010-106">Parameters</span></span>  
 `fIsJMCStepper`  
 <span data-ttu-id="2a010-107">podczas Ustaw, aby `true` tylko na krok za pomocą kodu, który jest tworzony przez dewelopera aplikacji; w przeciwnym razie ustaw wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="2a010-107">[in] Set to `true` to step only through code that is authored by an application's developer; otherwise, set to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a010-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2a010-108">Requirements</span></span>  
 <span data-ttu-id="2a010-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a010-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a010-110">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2a010-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a010-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2a010-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a010-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a010-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

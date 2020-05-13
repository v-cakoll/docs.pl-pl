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
ms.openlocfilehash: ab1351af042aba5042cc7a04614bc3cf14f7d7ae
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379458"
---
# <a name="icordebugstepper2setjmc-method"></a><span data-ttu-id="42cef-102">ICorDebugStepper2::SetJMC — Metoda</span><span class="sxs-lookup"><span data-stu-id="42cef-102">ICorDebugStepper2::SetJMC Method</span></span>
<span data-ttu-id="42cef-103">Ustawia wartość określającą, czy ten ICorDebugStepper czynności tylko za pomocą kodu, który jest tworzony przez dewelopera aplikacji.</span><span class="sxs-lookup"><span data-stu-id="42cef-103">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span> <span data-ttu-id="42cef-104">Ten proces jest również znany jako debugowanie tylko mój kod (JMC).</span><span class="sxs-lookup"><span data-stu-id="42cef-104">This process is also known as just my code (JMC) debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42cef-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="42cef-105">Syntax</span></span>  
  
```cpp  
HRESULT SetJMC (  
    [in] BOOL    fIsJMCStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42cef-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="42cef-106">Parameters</span></span>  
 `fIsJMCStepper`  
 <span data-ttu-id="42cef-107">podczas Ustaw na `true` krok tylko za pomocą kodu, który jest tworzony przez dewelopera aplikacji; w przeciwnym razie ustaw wartość `false` .</span><span class="sxs-lookup"><span data-stu-id="42cef-107">[in] Set to `true` to step only through code that is authored by an application's developer; otherwise, set to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42cef-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="42cef-108">Requirements</span></span>  
 <span data-ttu-id="42cef-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42cef-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42cef-110">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="42cef-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42cef-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="42cef-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42cef-112">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42cef-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

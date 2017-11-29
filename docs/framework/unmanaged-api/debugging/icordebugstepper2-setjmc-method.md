---
title: "ICorDebugStepper2::SetJMC — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper2.SetJMC
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper2::SetJMC
helpviewer_keywords:
- ICorDebugStepper2::SetJMC method [.NET Framework debugging]
- SetJMC method [.NET Framework debugging]
ms.assetid: f5cdc135-6db4-4b32-9dd1-260ec58b774f
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4b34e0d612957da1ec1ca3535bfa1a0d7a5bae5f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstepper2setjmc-method"></a><span data-ttu-id="3acd4-102">ICorDebugStepper2::SetJMC — Metoda</span><span class="sxs-lookup"><span data-stu-id="3acd4-102">ICorDebugStepper2::SetJMC Method</span></span>
<span data-ttu-id="3acd4-103">Ustawia wartość określającą, czy ten ICorDebugStepper — przeprowadza tylko przez kod, który został utworzony przez dewelopera aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3acd4-103">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span> <span data-ttu-id="3acd4-104">Ten proces jest również znane jako tylko mój kod (JMC) debugowania.</span><span class="sxs-lookup"><span data-stu-id="3acd4-104">This process is also known as just my code (JMC) debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3acd4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3acd4-105">Syntax</span></span>  
  
```  
HRESULT SetJMC (  
    [in] BOOL    fIsJMCStepper  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3acd4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3acd4-106">Parameters</span></span>  
 `fIsJMCStepper`  
 <span data-ttu-id="3acd4-107">[in] Ustaw `true` do kroku tylko za pośrednictwem kodu, który jest utworzony przez dewelopera aplikacji; w przeciwnym razie wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="3acd4-107">[in] Set to `true` to step only through code that is authored by an application's developer; otherwise, set to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3acd4-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3acd4-108">Requirements</span></span>  
 <span data-ttu-id="3acd4-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3acd4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3acd4-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3acd4-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3acd4-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3acd4-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3acd4-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3acd4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

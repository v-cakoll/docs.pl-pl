---
title: ICorDebugAssembly::GetProcess — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetProcess
helpviewer_keywords:
- ICorDebugAssembly::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: ea52be06-0a16-4f57-afca-4287d72e76c4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1c3bcc0ed22fa970d92e2384277d0786016db19
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugassemblygetprocess-method"></a><span data-ttu-id="1617f-102">ICorDebugAssembly::GetProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="1617f-102">ICorDebugAssembly::GetProcess Method</span></span>
<span data-ttu-id="1617f-103">Pobiera wskaźnika interfejsu do procesu, w którym jest uruchomione wystąpienie tego ICorDebugAssembly.</span><span class="sxs-lookup"><span data-stu-id="1617f-103">Gets an interface pointer to the process in which this ICorDebugAssembly instance is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1617f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1617f-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1617f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1617f-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="1617f-106">[out] Wskaźnik do ICorDebugProcess — interfejs reprezentujący procesu.</span><span class="sxs-lookup"><span data-stu-id="1617f-106">[out] A pointer to an ICorDebugProcess interface that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1617f-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1617f-107">Requirements</span></span>  
 <span data-ttu-id="1617f-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1617f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1617f-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1617f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1617f-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1617f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1617f-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1617f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

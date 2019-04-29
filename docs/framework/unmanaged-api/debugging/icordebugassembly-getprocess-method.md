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
ms.openlocfilehash: aeadcbd8f2d09320645c36fdc771cfb2cb976036
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645542"
---
# <a name="icordebugassemblygetprocess-method"></a><span data-ttu-id="f9913-102">ICorDebugAssembly::GetProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="f9913-102">ICorDebugAssembly::GetProcess Method</span></span>
<span data-ttu-id="f9913-103">Pobiera wskaźnik interfejsu do procesu, w którym jest uruchomione to wystąpienie ICorDebugAssembly.</span><span class="sxs-lookup"><span data-stu-id="f9913-103">Gets an interface pointer to the process in which this ICorDebugAssembly instance is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9913-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f9913-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9913-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9913-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="f9913-106">[out] Wskaźnik do icordebugprocess — interfejs, który reprezentuje proces.</span><span class="sxs-lookup"><span data-stu-id="f9913-106">[out] A pointer to an ICorDebugProcess interface that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9913-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f9913-107">Requirements</span></span>  
 <span data-ttu-id="f9913-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9913-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9913-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f9913-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9913-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9913-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9913-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9913-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

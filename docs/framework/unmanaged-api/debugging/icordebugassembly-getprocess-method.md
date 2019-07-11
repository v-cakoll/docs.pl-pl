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
ms.openlocfilehash: d0d5b6648fe6ce8a42f343d3cbdd77eb026b8f13
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744475"
---
# <a name="icordebugassemblygetprocess-method"></a><span data-ttu-id="ea831-102">ICorDebugAssembly::GetProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="ea831-102">ICorDebugAssembly::GetProcess Method</span></span>
<span data-ttu-id="ea831-103">Pobiera wskaźnik interfejsu do procesu, w którym jest uruchomione to wystąpienie ICorDebugAssembly.</span><span class="sxs-lookup"><span data-stu-id="ea831-103">Gets an interface pointer to the process in which this ICorDebugAssembly instance is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea831-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ea831-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea831-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ea831-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="ea831-106">[out] Wskaźnik do icordebugprocess — interfejs, który reprezentuje proces.</span><span class="sxs-lookup"><span data-stu-id="ea831-106">[out] A pointer to an ICorDebugProcess interface that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea831-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ea831-107">Requirements</span></span>  
 <span data-ttu-id="ea831-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea831-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea831-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ea831-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea831-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea831-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea831-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea831-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

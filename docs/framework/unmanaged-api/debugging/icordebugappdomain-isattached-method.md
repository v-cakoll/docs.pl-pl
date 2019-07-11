---
title: ICorDebugAppDomain::IsAttached — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.IsAttached
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::IsAttached
helpviewer_keywords:
- IsAttached method [.NET Framework debugging]
- ICorDebugAppDomain::IsAttached method [.NET Framework debugging]
ms.assetid: af0c67c7-f53e-47c9-b84b-be50bd04903e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a3f01edcd6ce1d16ab2c651a66d2fd9cd2eb0ba
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737820"
---
# <a name="icordebugappdomainisattached-method"></a><span data-ttu-id="c60c7-102">ICorDebugAppDomain::IsAttached — Metoda</span><span class="sxs-lookup"><span data-stu-id="c60c7-102">ICorDebugAppDomain::IsAttached Method</span></span>
<span data-ttu-id="c60c7-103">Pobiera wartość wskazującą, czy debuger jest dołączony do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c60c7-103">Gets a value that indicates whether the debugger is attached to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c60c7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c60c7-104">Syntax</span></span>  
  
```cpp  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c60c7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c60c7-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="c60c7-106">[out] `true` Jeśli Debuger jest dołączony do domeny aplikacji; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="c60c7-106">[out] `true` if the debugger is attached to the application domain; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c60c7-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c60c7-107">Remarks</span></span>  
 <span data-ttu-id="c60c7-108">Nie można używać metod icordebugcontroller —, dopóki debuger jest dołączany do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c60c7-108">The ICorDebugController methods cannot be used until the debugger attaches to the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c60c7-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c60c7-109">Requirements</span></span>  
 <span data-ttu-id="c60c7-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c60c7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c60c7-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c60c7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c60c7-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c60c7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c60c7-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c60c7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

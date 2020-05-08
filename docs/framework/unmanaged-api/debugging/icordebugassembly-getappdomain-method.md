---
title: ICorDebugAssembly::GetAppDomain — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetAppDomain
helpviewer_keywords:
- ICorDebugAssembly::GetAppDomain method [.NET Framework debugging]
- GetAppDomain method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 14e18510-23ac-4cba-9f96-c86147a2df9d
topic_type:
- apiref
ms.openlocfilehash: 81936052c3fa2ad4fb77b503341b8b4873b80695
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894932"
---
# <a name="icordebugassemblygetappdomain-method"></a><span data-ttu-id="8fb7f-102">ICorDebugAssembly::GetAppDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="8fb7f-102">ICorDebugAssembly::GetAppDomain Method</span></span>
<span data-ttu-id="8fb7f-103">Pobiera wskaźnik interfejsu do domeny aplikacji, która zawiera to `ICorDebugAssembly` wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="8fb7f-103">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fb7f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8fb7f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8fb7f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8fb7f-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="8fb7f-106">określoną Wskaźnik do adresu interfejsu ICorDebugAppDomain, który reprezentuje domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8fb7f-106">[out] A pointer to the address of an ICorDebugAppDomain interface that represents the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8fb7f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8fb7f-107">Remarks</span></span>  
 <span data-ttu-id="8fb7f-108">Jeśli ten zestaw jest zestawem systemowym `GetAppDomain` , zwraca wartość null.</span><span class="sxs-lookup"><span data-stu-id="8fb7f-108">If this assembly is the system assembly, `GetAppDomain` returns null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fb7f-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8fb7f-109">Requirements</span></span>  
 <span data-ttu-id="8fb7f-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fb7f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fb7f-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8fb7f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8fb7f-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8fb7f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8fb7f-113">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fb7f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

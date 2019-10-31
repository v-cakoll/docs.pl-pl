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
ms.openlocfilehash: 53042e722809a6574396648529c677d749154716
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132728"
---
# <a name="icordebugassemblygetappdomain-method"></a><span data-ttu-id="91fed-102">ICorDebugAssembly::GetAppDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="91fed-102">ICorDebugAssembly::GetAppDomain Method</span></span>
<span data-ttu-id="91fed-103">Pobiera wskaźnik interfejsu do domeny aplikacji, która zawiera to wystąpienie `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="91fed-103">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91fed-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="91fed-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91fed-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="91fed-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="91fed-106">określoną Wskaźnik do adresu interfejsu ICorDebugAppDomain, który reprezentuje domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="91fed-106">[out] A pointer to the address of an ICorDebugAppDomain interface that represents the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91fed-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="91fed-107">Remarks</span></span>  
 <span data-ttu-id="91fed-108">Jeśli ten zestaw jest zestawem systemowym, `GetAppDomain` zwraca wartość null.</span><span class="sxs-lookup"><span data-stu-id="91fed-108">If this assembly is the system assembly, `GetAppDomain` returns null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91fed-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="91fed-109">Requirements</span></span>  
 <span data-ttu-id="91fed-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91fed-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91fed-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="91fed-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91fed-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="91fed-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91fed-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91fed-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

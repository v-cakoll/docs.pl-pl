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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9ba09b80d7118b0ccd9b1647011a7fc7cd74e22
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645594"
---
# <a name="icordebugassemblygetappdomain-method"></a><span data-ttu-id="11a08-102">ICorDebugAssembly::GetAppDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="11a08-102">ICorDebugAssembly::GetAppDomain Method</span></span>
<span data-ttu-id="11a08-103">Pobiera wskaźnik interfejsu do domeny aplikacji, która zawiera to `ICorDebugAssembly` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="11a08-103">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11a08-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="11a08-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11a08-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="11a08-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="11a08-106">[out] Wskaźnik na adres icordebugappdomain — interfejs, który reprezentuje domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="11a08-106">[out] A pointer to the address of an ICorDebugAppDomain interface that represents the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11a08-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="11a08-107">Remarks</span></span>  
 <span data-ttu-id="11a08-108">Jeśli ten zestaw jest zestaw systemowy `GetAppDomain` zwraca wartość null.</span><span class="sxs-lookup"><span data-stu-id="11a08-108">If this assembly is the system assembly, `GetAppDomain` returns null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11a08-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="11a08-109">Requirements</span></span>  
 <span data-ttu-id="11a08-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11a08-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11a08-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="11a08-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="11a08-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11a08-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11a08-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11a08-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

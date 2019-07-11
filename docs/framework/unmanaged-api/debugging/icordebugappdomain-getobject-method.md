---
title: ICorDebugAppDomain::GetObject — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetObject
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetObject
helpviewer_keywords:
- ICorDebugAppDomain::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 78232e6f-ae18-4cfa-a6cd-e79471cf9d76
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1201ac0dca9cbd48c24b2621eba079ae672fd310
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737846"
---
# <a name="icordebugappdomaingetobject-method"></a><span data-ttu-id="ae872-102">ICorDebugAppDomain::GetObject — Metoda</span><span class="sxs-lookup"><span data-stu-id="ae872-102">ICorDebugAppDomain::GetObject Method</span></span>
<span data-ttu-id="ae872-103">Pobiera wskaźnik interfejsu do typowych domeny aplikacji języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="ae872-103">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae872-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ae872-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae872-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ae872-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="ae872-106">[out] Wskaźnik na adres obiektu interfejsu ICorDebugValue, który reprezentuje domenę aplikacji CLR.</span><span class="sxs-lookup"><span data-stu-id="ae872-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae872-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ae872-107">Return Value</span></span>  
 <span data-ttu-id="ae872-108">Jeśli jest to zarządzana <xref:System.AppDomain?displayProperty=nameWithType> obiekt nie został skonstruowany dla tej domeny aplikacji, Metoda ta zwraca `S_FALSE` i umieszcza `NULL` w `*ppObject`.</span><span class="sxs-lookup"><span data-stu-id="ae872-108">If a managed <xref:System.AppDomain?displayProperty=nameWithType> object hasn't been constructed for this application domain, the method returns `S_FALSE` and places `NULL` in `*ppObject`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae872-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ae872-109">Remarks</span></span>  
 <span data-ttu-id="ae872-110">Każda domena aplikacji, w ramach procesu może być zarządzany <xref:System.AppDomain?displayProperty=nameWithType> obiektu w czasie wykonywania, który go reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="ae872-110">Each application domain in a process may have a managed <xref:System.AppDomain?displayProperty=nameWithType> object in the runtime that represents it.</span></span> <span data-ttu-id="ae872-111">Ta funkcja pobiera obiekt interfejsu ICorDebugValue, który odpowiada to zarządzane <xref:System.AppDomain?displayProperty=nameWithType> obiektu.</span><span class="sxs-lookup"><span data-stu-id="ae872-111">This function gets an ICorDebugValue interface object that corresponds to this managed <xref:System.AppDomain?displayProperty=nameWithType> object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae872-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ae872-112">Requirements</span></span>  
 <span data-ttu-id="ae872-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae872-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae872-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ae872-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae872-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae872-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae872-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae872-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>

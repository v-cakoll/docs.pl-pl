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
ms.openlocfilehash: f2c881603cfa0e4b3d2dc8d1e996631b51d1e850
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134713"
---
# <a name="icordebugappdomaingetobject-method"></a><span data-ttu-id="ab268-102">ICorDebugAppDomain::GetObject — Metoda</span><span class="sxs-lookup"><span data-stu-id="ab268-102">ICorDebugAppDomain::GetObject Method</span></span>
<span data-ttu-id="ab268-103">Pobiera wskaźnik interfejsu do domeny aplikacji środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="ab268-103">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab268-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ab268-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab268-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ab268-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="ab268-106">określoną Wskaźnik do adresu obiektu interfejsu ICorDebugValue, który reprezentuje domenę aplikacji CLR.</span><span class="sxs-lookup"><span data-stu-id="ab268-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab268-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ab268-107">Return Value</span></span>  
 <span data-ttu-id="ab268-108">Jeśli obiekt zarządzany <xref:System.AppDomain?displayProperty=nameWithType> nie został skonstruowany dla tej domeny aplikacji, metoda zwróci `S_FALSE` i umieści `NULL` w `*ppObject`.</span><span class="sxs-lookup"><span data-stu-id="ab268-108">If a managed <xref:System.AppDomain?displayProperty=nameWithType> object hasn't been constructed for this application domain, the method returns `S_FALSE` and places `NULL` in `*ppObject`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab268-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ab268-109">Remarks</span></span>  
 <span data-ttu-id="ab268-110">Każda domena aplikacji w procesie może mieć zarządzany obiekt <xref:System.AppDomain?displayProperty=nameWithType> w czasie wykonywania, który go reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="ab268-110">Each application domain in a process may have a managed <xref:System.AppDomain?displayProperty=nameWithType> object in the runtime that represents it.</span></span> <span data-ttu-id="ab268-111">Ta funkcja pobiera obiekt interfejsu ICorDebugValue, który odpowiada obiektowi zarządzanemu <xref:System.AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ab268-111">This function gets an ICorDebugValue interface object that corresponds to this managed <xref:System.AppDomain?displayProperty=nameWithType> object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab268-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ab268-112">Requirements</span></span>  
 <span data-ttu-id="ab268-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab268-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab268-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ab268-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab268-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ab268-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab268-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab268-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>

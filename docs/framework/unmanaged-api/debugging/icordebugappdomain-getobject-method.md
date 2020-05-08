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
ms.openlocfilehash: a21f3b36e418bbde5dcb90f25a39dae03fde77c9
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895212"
---
# <a name="icordebugappdomaingetobject-method"></a><span data-ttu-id="2601e-102">ICorDebugAppDomain::GetObject — Metoda</span><span class="sxs-lookup"><span data-stu-id="2601e-102">ICorDebugAppDomain::GetObject Method</span></span>
<span data-ttu-id="2601e-103">Pobiera wskaźnik interfejsu do domeny aplikacji środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="2601e-103">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2601e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2601e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2601e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2601e-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="2601e-106">określoną Wskaźnik do adresu obiektu interfejsu ICorDebugValue, który reprezentuje domenę aplikacji CLR.</span><span class="sxs-lookup"><span data-stu-id="2601e-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2601e-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2601e-107">Return Value</span></span>  
 <span data-ttu-id="2601e-108">Jeśli obiekt zarządzany <xref:System.AppDomain?displayProperty=nameWithType> nie został skonstruowany dla tej domeny aplikacji, metoda zwraca `S_FALSE` i umieszcza `NULL` w. `*ppObject`</span><span class="sxs-lookup"><span data-stu-id="2601e-108">If a managed <xref:System.AppDomain?displayProperty=nameWithType> object hasn't been constructed for this application domain, the method returns `S_FALSE` and places `NULL` in `*ppObject`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2601e-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2601e-109">Remarks</span></span>  
 <span data-ttu-id="2601e-110">Każda domena aplikacji w procesie może mieć obiekt zarządzany <xref:System.AppDomain?displayProperty=nameWithType> w czasie wykonywania, który go reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="2601e-110">Each application domain in a process may have a managed <xref:System.AppDomain?displayProperty=nameWithType> object in the runtime that represents it.</span></span> <span data-ttu-id="2601e-111">Ta funkcja pobiera obiekt interfejsu ICorDebugValue, który odpowiada obiektowi zarządzanemu <xref:System.AppDomain?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="2601e-111">This function gets an ICorDebugValue interface object that corresponds to this managed <xref:System.AppDomain?displayProperty=nameWithType> object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2601e-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2601e-112">Requirements</span></span>  
 <span data-ttu-id="2601e-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2601e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2601e-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2601e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2601e-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2601e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2601e-116">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2601e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>

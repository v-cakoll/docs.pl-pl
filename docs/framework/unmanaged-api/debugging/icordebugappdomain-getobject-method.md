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
ms.openlocfilehash: a6f528bcef7d06b503b1ee9d7bd4a61d3d3e9672
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406523"
---
# <a name="icordebugappdomaingetobject-method"></a><span data-ttu-id="9ddfa-102">ICorDebugAppDomain::GetObject — Metoda</span><span class="sxs-lookup"><span data-stu-id="9ddfa-102">ICorDebugAppDomain::GetObject Method</span></span>
<span data-ttu-id="9ddfa-103">Pobiera wskaźnika interfejsu do typowych domeny aplikacji języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="9ddfa-103">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ddfa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9ddfa-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9ddfa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9ddfa-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="9ddfa-106">[out] Wskaźnik do adresu ICorDebugValue obiektu interfejsu, który reprezentuje CLR domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9ddfa-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ddfa-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9ddfa-107">Return Value</span></span>  
 <span data-ttu-id="9ddfa-108">Jeśli zarządzanego <xref:System.AppDomain?displayProperty=nameWithType> obiektu nie zostało utworzone dla tej domeny aplikacji, metoda zwraca `S_FALSE` i umieszcza `NULL` w `*ppObject`.</span><span class="sxs-lookup"><span data-stu-id="9ddfa-108">If a managed <xref:System.AppDomain?displayProperty=nameWithType> object hasn't been constructed for this application domain, the method returns `S_FALSE` and places `NULL` in `*ppObject`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ddfa-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9ddfa-109">Remarks</span></span>  
 <span data-ttu-id="9ddfa-110">Każda domena aplikacji w ramach procesu może mieć zarządzanego <xref:System.AppDomain?displayProperty=nameWithType> obiektu w czasie wykonywania, który reprezentuje on.</span><span class="sxs-lookup"><span data-stu-id="9ddfa-110">Each application domain in a process may have a managed <xref:System.AppDomain?displayProperty=nameWithType> object in the runtime that represents it.</span></span> <span data-ttu-id="9ddfa-111">Ta funkcja pobiera ICorDebugValue obiektu interfejsu, który odpowiada to zarządzany <xref:System.AppDomain?displayProperty=nameWithType> obiektu.</span><span class="sxs-lookup"><span data-stu-id="9ddfa-111">This function gets an ICorDebugValue interface object that corresponds to this managed <xref:System.AppDomain?displayProperty=nameWithType> object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ddfa-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9ddfa-112">Requirements</span></span>  
 <span data-ttu-id="9ddfa-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ddfa-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ddfa-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ddfa-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ddfa-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ddfa-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ddfa-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ddfa-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>

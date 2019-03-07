---
title: ICorDebugProcess2::GetReferenceValueFromGCHandle — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetReferenceValueFromGCHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetReferenceValueFromGCHandle
helpviewer_keywords:
- GetReferenceValueFromGCHandle method [.NET Framework debugging]
- ICorDebugProcess2::GetReferenceValueFromGCHandle method [.NET Framework debugging]
ms.assetid: 8bdd7f4c-19f2-4ede-875e-603773e8c128
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08bf4022f7cd7f85ffe7939c16fd47950e131a77
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471527"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a><span data-ttu-id="e4ceb-102">ICorDebugProcess2::GetReferenceValueFromGCHandle — Metoda</span><span class="sxs-lookup"><span data-stu-id="e4ceb-102">ICorDebugProcess2::GetReferenceValueFromGCHandle Method</span></span>
<span data-ttu-id="e4ceb-103">Pobiera wskaźnik odwołania do określonego obiektu zarządzanego, który ma obsługiwać wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e4ceb-103">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4ceb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e4ceb-104">Syntax</span></span>  
  
```  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4ceb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e4ceb-105">Parameters</span></span>  
 `handle`  
 <span data-ttu-id="e4ceb-106">[in] Wskaźnik do obiektu zarządzanego, który ma dojścia kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="e4ceb-106">[in] A pointer to a managed object that has a garbage collection handle.</span></span> <span data-ttu-id="e4ceb-107">Ta wartość jest <xref:System.IntPtr> obiektu i może zostać pobrana z <xref:System.Runtime.InteropServices.GCHandle> obiektu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="e4ceb-107">This value is a <xref:System.IntPtr> object and can be retrieved from the <xref:System.Runtime.InteropServices.GCHandle> for the managed object.</span></span>  
  
 `pOutValue`  
 <span data-ttu-id="e4ceb-108">[out] Wskaźnik na adres obiektu ICorDebugReferenceValue, który reprezentuje odwołanie do określonego obiektu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="e4ceb-108">[out] A pointer to the address of an ICorDebugReferenceValue object that represents a reference to the specified managed object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4ceb-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e4ceb-109">Remarks</span></span>  
 <span data-ttu-id="e4ceb-110">Nie należy mylić wartości zwracane odwołanie o wartości odniesienia kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="e4ceb-110">Do not confuse the returned reference value with a garbage collection reference value.</span></span>  
  
 <span data-ttu-id="e4ceb-111">Zwracane odwołanie zachowuje się jak normalne odwołania.</span><span class="sxs-lookup"><span data-stu-id="e4ceb-111">The returned reference behaves like a normal reference.</span></span> <span data-ttu-id="e4ceb-112">Jest ona wyłączona, gdy punkt przerwania jest kontynuowane wykonywanie kodu.</span><span class="sxs-lookup"><span data-stu-id="e4ceb-112">It is disabled when code execution continues after a breakpoint.</span></span> <span data-ttu-id="e4ceb-113">Okres istnienia wartość odwołania nie dotyczy okresu istnienia obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="e4ceb-113">The lifetime of the target object is not affected by the lifetime of the reference value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e4ceb-114">`GetReferenceValueFromGCHandle` Metoda nie sprawdza poprawności dojścia.</span><span class="sxs-lookup"><span data-stu-id="e4ceb-114">The `GetReferenceValueFromGCHandle` method does not validate the handle.</span></span> <span data-ttu-id="e4ceb-115">W związku z tym `GetReferenceValueFromGCHandle` metoda może potencjalnie uszkodzić debugera i kod debugowany, jeśli zostanie przekazana nieprawidłowego dojścia.</span><span class="sxs-lookup"><span data-stu-id="e4ceb-115">Therefore, the `GetReferenceValueFromGCHandle` method can potentially corrupt both the debugger and the code being debugged if an invalid handle is passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4ceb-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e4ceb-116">Requirements</span></span>  
 <span data-ttu-id="e4ceb-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4ceb-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4ceb-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e4ceb-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4ceb-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4ceb-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4ceb-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4ceb-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

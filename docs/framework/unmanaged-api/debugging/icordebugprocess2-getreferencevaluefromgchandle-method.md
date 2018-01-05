---
title: "ICorDebugProcess2::GetReferenceValueFromGCHandle — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2.GetReferenceValueFromGCHandle
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2::GetReferenceValueFromGCHandle
helpviewer_keywords:
- GetReferenceValueFromGCHandle method [.NET Framework debugging]
- ICorDebugProcess2::GetReferenceValueFromGCHandle method [.NET Framework debugging]
ms.assetid: 8bdd7f4c-19f2-4ede-875e-603773e8c128
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0ac4cc32be6914ea858d32b8699a695588f0a1e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a><span data-ttu-id="500c7-102">ICorDebugProcess2::GetReferenceValueFromGCHandle — Metoda</span><span class="sxs-lookup"><span data-stu-id="500c7-102">ICorDebugProcess2::GetReferenceValueFromGCHandle Method</span></span>
<span data-ttu-id="500c7-103">Pobiera wskaźnik odwołanie do określonego zarządzanego obiektu, który ma obsługiwać wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="500c7-103">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="500c7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="500c7-104">Syntax</span></span>  
  
```  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="500c7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="500c7-105">Parameters</span></span>  
 `handle`  
 <span data-ttu-id="500c7-106">[in] Wskaźnik do zarządzanego obiektu, który ma uchwyt kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="500c7-106">[in] A pointer to a managed object that has a garbage collection handle.</span></span> <span data-ttu-id="500c7-107">Ta wartość jest <xref:System.IntPtr> obiektu i mogą być pobierane z <xref:System.Runtime.InteropServices.GCHandle> dla obiekt zarządzany.</span><span class="sxs-lookup"><span data-stu-id="500c7-107">This value is a <xref:System.IntPtr> object and can be retrieved from the <xref:System.Runtime.InteropServices.GCHandle> for the managed object.</span></span>  
  
 `pOutValue`  
 <span data-ttu-id="500c7-108">[out] Wskaźnik do adresu ICorDebugReferenceValue obiekt, który reprezentuje odwołanie do określonego obiektu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="500c7-108">[out] A pointer to the address of an ICorDebugReferenceValue object that represents a reference to the specified managed object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="500c7-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="500c7-109">Remarks</span></span>  
 <span data-ttu-id="500c7-110">Nie należy mylić wartości zwracane odwołanie o wartości odwołania kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="500c7-110">Do not confuse the returned reference value with a garbage collection reference value.</span></span>  
  
 <span data-ttu-id="500c7-111">Zwracane odwołanie zachowuje się jak normalne odwołania.</span><span class="sxs-lookup"><span data-stu-id="500c7-111">The returned reference behaves like a normal reference.</span></span> <span data-ttu-id="500c7-112">Gdy kontynuuje wykonywanie kodu po punkt przerwania jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="500c7-112">It is disabled when code execution continues after a breakpoint.</span></span> <span data-ttu-id="500c7-113">Okres istnienia obiektu docelowego nie ma wpływu na okres istnienia wartości odwołania.</span><span class="sxs-lookup"><span data-stu-id="500c7-113">The lifetime of the target object is not affected by the lifetime of the reference value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="500c7-114">`GetReferenceValueFromGCHandle` Metody nie można zweryfikować dojście.</span><span class="sxs-lookup"><span data-stu-id="500c7-114">The `GetReferenceValueFromGCHandle` method does not validate the handle.</span></span> <span data-ttu-id="500c7-115">W związku z tym `GetReferenceValueFromGCHandle` metody może potencjalnie uszkodzić zarówno debugera i kod debugowany, jeżeli nie przekazano nieprawidłowe dojście.</span><span class="sxs-lookup"><span data-stu-id="500c7-115">Therefore, the `GetReferenceValueFromGCHandle` method can potentially corrupt both the debugger and the code being debugged if an invalid handle is passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="500c7-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="500c7-116">Requirements</span></span>  
 <span data-ttu-id="500c7-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="500c7-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="500c7-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="500c7-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="500c7-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="500c7-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="500c7-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="500c7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

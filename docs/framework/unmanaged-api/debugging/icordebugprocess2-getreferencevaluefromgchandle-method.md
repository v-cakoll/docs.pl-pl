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
ms.openlocfilehash: 21da325ee58df65ac449464f8292f2ba94d99338
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943296"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a><span data-ttu-id="43f36-102">ICorDebugProcess2::GetReferenceValueFromGCHandle — Metoda</span><span class="sxs-lookup"><span data-stu-id="43f36-102">ICorDebugProcess2::GetReferenceValueFromGCHandle Method</span></span>
<span data-ttu-id="43f36-103">Pobiera wskaźnik odwołania do określonego obiektu zarządzanego, który ma dojście do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="43f36-103">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43f36-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="43f36-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43f36-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="43f36-105">Parameters</span></span>  
 `handle`  
 <span data-ttu-id="43f36-106">podczas Wskaźnik do zarządzanego obiektu, który ma dojście do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="43f36-106">[in] A pointer to a managed object that has a garbage collection handle.</span></span> <span data-ttu-id="43f36-107">Ta wartość jest <xref:System.IntPtr> obiektem i można ją pobrać <xref:System.Runtime.InteropServices.GCHandle> z elementu dla obiektu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="43f36-107">This value is a <xref:System.IntPtr> object and can be retrieved from the <xref:System.Runtime.InteropServices.GCHandle> for the managed object.</span></span>  
  
 `pOutValue`  
 <span data-ttu-id="43f36-108">określoną Wskaźnik do adresu obiektu ICorDebugReferenceValue, który reprezentuje odwołanie do określonego obiektu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="43f36-108">[out] A pointer to the address of an ICorDebugReferenceValue object that represents a reference to the specified managed object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43f36-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="43f36-109">Remarks</span></span>  
 <span data-ttu-id="43f36-110">Nie należy mylić zwróconej wartości odniesienia z wartością referencyjną wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="43f36-110">Do not confuse the returned reference value with a garbage collection reference value.</span></span>  
  
 <span data-ttu-id="43f36-111">Zwrócone odwołanie zachowuje się jak normalne odwołanie.</span><span class="sxs-lookup"><span data-stu-id="43f36-111">The returned reference behaves like a normal reference.</span></span> <span data-ttu-id="43f36-112">Jest ono wyłączone, gdy wykonanie kodu jest kontynuowane po punkcie przerwania.</span><span class="sxs-lookup"><span data-stu-id="43f36-112">It is disabled when code execution continues after a breakpoint.</span></span> <span data-ttu-id="43f36-113">Okres istnienia obiektu docelowego nie ma wpływ na czas istnienia wartości referencyjnej.</span><span class="sxs-lookup"><span data-stu-id="43f36-113">The lifetime of the target object is not affected by the lifetime of the reference value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="43f36-114">`GetReferenceValueFromGCHandle` Metoda nie sprawdza poprawności dojścia.</span><span class="sxs-lookup"><span data-stu-id="43f36-114">The `GetReferenceValueFromGCHandle` method does not validate the handle.</span></span> <span data-ttu-id="43f36-115">W `GetReferenceValueFromGCHandle` związku z tym, Metoda może potencjalnie uszkodzić debuger i kod debugowany w przypadku przekazanie nieprawidłowego dojścia.</span><span class="sxs-lookup"><span data-stu-id="43f36-115">Therefore, the `GetReferenceValueFromGCHandle` method can potentially corrupt both the debugger and the code being debugged if an invalid handle is passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43f36-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="43f36-116">Requirements</span></span>  
 <span data-ttu-id="43f36-117">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43f36-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43f36-118">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="43f36-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="43f36-119">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43f36-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43f36-120">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43f36-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

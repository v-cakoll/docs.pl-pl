---
title: ICorDebugILFrame::GetIP — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::GetIP method [.NET Framework debugging]
ms.assetid: 18217ba1-1776-4297-a3b9-f77e64b0fead
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a7b8985e7580282d0e38205f9b1d6078f86cee6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479769"
---
# <a name="icordebugilframegetip-method"></a><span data-ttu-id="2815d-102">ICorDebugILFrame::GetIP — Metoda</span><span class="sxs-lookup"><span data-stu-id="2815d-102">ICorDebugILFrame::GetIP Method</span></span>
<span data-ttu-id="2815d-103">Pobiera wartość wskaźnika instrukcji i wartości bitowe połączenie, w tym artykule opisano, jak wartość wskaźnika instrukcji zostały pobrane.</span><span class="sxs-lookup"><span data-stu-id="2815d-103">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2815d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2815d-104">Syntax</span></span>  
  
```  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,   
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2815d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2815d-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="2815d-106">[out] Wartość wskaźnika instrukcji.</span><span class="sxs-lookup"><span data-stu-id="2815d-106">[out] The value of the instruction pointer.</span></span>  
  
 `pMappingResult`  
 <span data-ttu-id="2815d-107">[out] Wskaźnik do bitowa kombinacja wartości wyliczenia cordebugmappingresult —, które opisują, jak wartość wskaźnika instrukcji zostały pobrane.</span><span class="sxs-lookup"><span data-stu-id="2815d-107">[out] A pointer to a bitwise combination of the CorDebugMappingResult enumeration values that describe how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2815d-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2815d-108">Remarks</span></span>  
 <span data-ttu-id="2815d-109">Wartość wskaźnika instrukcji jest przesunięcie ramki stosu kod funkcji Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="2815d-109">The value of the instruction pointer is the stack frame's offset into the function's Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="2815d-110">Jeśli ramka stosu jest aktywna, ten adres jest następną instrukcję do wykonania.</span><span class="sxs-lookup"><span data-stu-id="2815d-110">If the stack frame is active, this address is the next instruction to execute.</span></span> <span data-ttu-id="2815d-111">Jeśli ramka stosu nie jest aktywny, ten adres jest następną instrukcję do wykonania podczas ponownego uaktywniania ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="2815d-111">If the stack frame is not active, this address is the next instruction to execute when the stack frame is reactivated.</span></span>  
  
 <span data-ttu-id="2815d-112">Jeśli ta ramka ramkę skompilowany just-in-time (JIT), wartość wskaźnika instrukcji będzie określana przez mapowanie wstecz od wskaźnika rzeczywiste natywnych instrukcji, co wartość może być tylko przybliżone.</span><span class="sxs-lookup"><span data-stu-id="2815d-112">If this frame is a just-in-time (JIT) compiled frame, the value of the instruction pointer will be determined by mapping backwards from the actual native instruction pointer, so the value may be only approximate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2815d-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2815d-113">Requirements</span></span>  
 <span data-ttu-id="2815d-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2815d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2815d-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2815d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2815d-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2815d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2815d-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2815d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

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
ms.openlocfilehash: f30516a8f59b90de9b4c052d92a8c88575ace3c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178822"
---
# <a name="icordebugilframegetip-method"></a><span data-ttu-id="5de75-102">ICorDebugILFrame::GetIP — Metoda</span><span class="sxs-lookup"><span data-stu-id="5de75-102">ICorDebugILFrame::GetIP Method</span></span>
<span data-ttu-id="5de75-103">Pobiera wartość wskaźnika instrukcji i bitowej wartości kombinacji, która opisuje, jak uzyskano wartość wskaźnika instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5de75-103">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5de75-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5de75-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5de75-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5de75-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="5de75-106">[na zewnątrz] Wartość wskaźnika instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5de75-106">[out] The value of the instruction pointer.</span></span>  
  
 `pMappingResult`  
 <span data-ttu-id="5de75-107">[na zewnątrz] Wskaźnik do bitowej kombinacji corDebugMappingResult wartości wyliczenia, które opisują, jak wartość wskaźnika instrukcji został uzyskany.</span><span class="sxs-lookup"><span data-stu-id="5de75-107">[out] A pointer to a bitwise combination of the CorDebugMappingResult enumeration values that describe how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5de75-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5de75-108">Remarks</span></span>  
 <span data-ttu-id="5de75-109">Wartość wskaźnika instrukcji jest przesunięcie ramki stosu do funkcji Microsoft pośredniego języka (MSIL) kod.</span><span class="sxs-lookup"><span data-stu-id="5de75-109">The value of the instruction pointer is the stack frame's offset into the function's Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="5de75-110">Jeśli ramka stosu jest aktywna, ten adres jest następną instrukcją do wykonania.</span><span class="sxs-lookup"><span data-stu-id="5de75-110">If the stack frame is active, this address is the next instruction to execute.</span></span> <span data-ttu-id="5de75-111">Jeśli ramka stosu nie jest aktywna, ten adres jest następną instrukcją do wykonania po ponownym uaktywnieniu ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="5de75-111">If the stack frame is not active, this address is the next instruction to execute when the stack frame is reactivated.</span></span>  
  
 <span data-ttu-id="5de75-112">Jeśli ta ramka jest klatką skompilowaną just-in-time (JIT), wartość wskaźnika instrukcji zostanie określona przez mapowanie wstecz z rzeczywistego wskaźnika instrukcji natywnej, więc wartość może być tylko przybliżona.</span><span class="sxs-lookup"><span data-stu-id="5de75-112">If this frame is a just-in-time (JIT) compiled frame, the value of the instruction pointer will be determined by mapping backwards from the actual native instruction pointer, so the value may be only approximate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5de75-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5de75-113">Requirements</span></span>  
 <span data-ttu-id="5de75-114">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5de75-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5de75-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5de75-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5de75-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5de75-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5de75-117">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5de75-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

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
ms.openlocfilehash: 7e1605eede55360e72d65da6744bc1dcce4f107f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130990"
---
# <a name="icordebugilframegetip-method"></a><span data-ttu-id="c13c3-102">ICorDebugILFrame::GetIP — Metoda</span><span class="sxs-lookup"><span data-stu-id="c13c3-102">ICorDebugILFrame::GetIP Method</span></span>
<span data-ttu-id="c13c3-103">Pobiera wartość wskaźnika instrukcji i wartość kombinacji bitowej opisującą sposób uzyskiwania wartości wskaźnika instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c13c3-103">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c13c3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c13c3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,   
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c13c3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c13c3-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="c13c3-106">określoną Wartość wskaźnika instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c13c3-106">[out] The value of the instruction pointer.</span></span>  
  
 `pMappingResult`  
 <span data-ttu-id="c13c3-107">określoną Wskaźnik do bitowej kombinacji wartości wyliczenia CorDebugMappingResult —, który opisuje sposób uzyskiwania wartości wskaźnika instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c13c3-107">[out] A pointer to a bitwise combination of the CorDebugMappingResult enumeration values that describe how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c13c3-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c13c3-108">Remarks</span></span>  
 <span data-ttu-id="c13c3-109">Wartość wskaźnika instrukcji to przesunięcie ramki stosu do kodu języka pośredniego firmy Microsoft (MSIL) funkcji.</span><span class="sxs-lookup"><span data-stu-id="c13c3-109">The value of the instruction pointer is the stack frame's offset into the function's Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="c13c3-110">Jeśli ramka stosu jest aktywna, ten adres jest następną instrukcją do wykonania.</span><span class="sxs-lookup"><span data-stu-id="c13c3-110">If the stack frame is active, this address is the next instruction to execute.</span></span> <span data-ttu-id="c13c3-111">Jeśli ramka stosu nie jest aktywna, ten adres jest następną instrukcją do wykonania po ponownym uaktywnieniu ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="c13c3-111">If the stack frame is not active, this address is the next instruction to execute when the stack frame is reactivated.</span></span>  
  
 <span data-ttu-id="c13c3-112">Jeśli ta ramka jest skompilowaną ramką just-in-Time (JIT), wartość wskaźnika instrukcji zostanie określona przez mapowanie wstecz od rzeczywistego wskaźnika instrukcji natywnych, więc wartość może być przybliżona.</span><span class="sxs-lookup"><span data-stu-id="c13c3-112">If this frame is a just-in-time (JIT) compiled frame, the value of the instruction pointer will be determined by mapping backwards from the actual native instruction pointer, so the value may be only approximate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c13c3-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c13c3-113">Requirements</span></span>  
 <span data-ttu-id="c13c3-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c13c3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c13c3-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c13c3-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c13c3-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c13c3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c13c3-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c13c3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

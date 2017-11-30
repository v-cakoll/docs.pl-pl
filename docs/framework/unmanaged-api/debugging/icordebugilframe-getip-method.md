---
title: "ICorDebugILFrame::GetIP — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.GetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::GetIP method [.NET Framework debugging]
ms.assetid: 18217ba1-1776-4297-a3b9-f77e64b0fead
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6f1ea9ad653deeaaa22944517ba5cbdb2f39c6d4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugilframegetip-method"></a><span data-ttu-id="7c333-102">ICorDebugILFrame::GetIP — Metoda</span><span class="sxs-lookup"><span data-stu-id="7c333-102">ICorDebugILFrame::GetIP Method</span></span>
<span data-ttu-id="7c333-103">Pobiera wartość wskaźnika instrukcji i wartości bitowe połączenie, opisujące, jak uzyskano wartość wskaźnika instrukcji.</span><span class="sxs-lookup"><span data-stu-id="7c333-103">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c333-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c333-104">Syntax</span></span>  
  
```  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,   
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7c333-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7c333-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="7c333-106">[out] Wartość wskaźnika instrukcji.</span><span class="sxs-lookup"><span data-stu-id="7c333-106">[out] The value of the instruction pointer.</span></span>  
  
 `pMappingResult`  
 <span data-ttu-id="7c333-107">[out] Wskaźnik do bitowe połączenie wartości wyliczenia CorDebugMappingResult, które opisują sposób uzyskano wartość wskaźnika instrukcji.</span><span class="sxs-lookup"><span data-stu-id="7c333-107">[out] A pointer to a bitwise combination of the CorDebugMappingResult enumeration values that describe how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c333-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7c333-108">Remarks</span></span>  
 <span data-ttu-id="7c333-109">Wartość wskaźnika instrukcji jest przesunięcie ramki stosu do kodu języka pośredniego (MSIL) firmy Microsoft przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="7c333-109">The value of the instruction pointer is the stack frame's offset into the function's Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="7c333-110">Jeśli ramka stosu jest aktywny, ten adres jest następną instrukcję do wykonania.</span><span class="sxs-lookup"><span data-stu-id="7c333-110">If the stack frame is active, this address is the next instruction to execute.</span></span> <span data-ttu-id="7c333-111">Jeśli ramka stosu nie jest aktywne, ten adres jest następną instrukcję do wykonania po ponownym uaktywnieniu ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="7c333-111">If the stack frame is not active, this address is the next instruction to execute when the stack frame is reactivated.</span></span>  
  
 <span data-ttu-id="7c333-112">Jeśli ta ramka jest ramki skompilowanych just in time (JIT), wartość wskaźnika instrukcji będzie określana przez mapowanie wstecz ze wskaźnika rzeczywiste instrukcji macierzystego, co wartość może być tylko przybliżonej.</span><span class="sxs-lookup"><span data-stu-id="7c333-112">If this frame is a just-in-time (JIT) compiled frame, the value of the instruction pointer will be determined by mapping backwards from the actual native instruction pointer, so the value may be only approximate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c333-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7c333-113">Requirements</span></span>  
 <span data-ttu-id="7c333-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c333-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c333-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7c333-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c333-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c333-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c333-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c333-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

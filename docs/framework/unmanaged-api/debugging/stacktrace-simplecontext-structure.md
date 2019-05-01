---
title: StackTrace_SimpleContext — Struktura
ms.date: 03/30/2017
api_name:
- StackTrace_SimpleContext
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SimpleContext
helpviewer_keywords:
- SimpleContext structure [.NET Framework debugging]
- StackTrace_SimpleContext structure [.NET Framework debugging]
ms.assetid: d4cef11f-a8ca-49bc-a1b8-6631f9e28f3e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0625dc72d44485dbb69b42cba5387085d1862bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986534"
---
# <a name="stacktracesimplecontext-structure"></a><span data-ttu-id="99445-102">StackTrace_SimpleContext — Struktura</span><span class="sxs-lookup"><span data-stu-id="99445-102">StackTrace_SimpleContext Structure</span></span>
<span data-ttu-id="99445-103">Udostępnia prosty kontekst, który można użyć zamiast pełnego `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="99445-103">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99445-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="99445-104">Syntax</span></span>  
  
```  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a><span data-ttu-id="99445-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="99445-105">Members</span></span>  
  
|<span data-ttu-id="99445-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="99445-106">Member</span></span>|<span data-ttu-id="99445-107">Opis</span><span class="sxs-lookup"><span data-stu-id="99445-107">Description</span></span>|  
|------------|-----------------|  
|`StackOffset`|<span data-ttu-id="99445-108">Wskaźnik stosu lub wskaźnik stosu enter (ESP) na x86 platform.</span><span class="sxs-lookup"><span data-stu-id="99445-108">The stack pointer, or the enter stack pointer (ESP) on x86 platforms.</span></span>|  
|`FrameOffset`|<span data-ttu-id="99445-109">Przesunięcie ramki lub zarejestruj EBP na x86 platform.</span><span class="sxs-lookup"><span data-stu-id="99445-109">The frame offset, or the EBP register on x86 platforms.</span></span>|  
|`InstructionOffset`|<span data-ttu-id="99445-110">Wskaźnik instrukcji lub enter wskaźnik instrukcji (EIP) na x86 platform.</span><span class="sxs-lookup"><span data-stu-id="99445-110">The instruction pointer, or the enter instruction pointer (EIP) on x86 platforms.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99445-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="99445-111">Remarks</span></span>  
 <span data-ttu-id="99445-112">Ponieważ funkcje śledzenia stosu zazwyczaj trzeba zwrócić tylko adres, przesunięcie ramki i adresu stosu, można opcjonalnie używać `SimpleContext` struktury zamiast dużą `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="99445-112">Because stack trace functions typically need to return only the address, frame offset, and stack address, you can optionally use the `SimpleContext` structure instead of a large `CONTEXT` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99445-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="99445-113">Requirements</span></span>  
 <span data-ttu-id="99445-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99445-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99445-115">**Nagłówek:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="99445-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="99445-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99445-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99445-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="99445-117">See also</span></span>

- [<span data-ttu-id="99445-118">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="99445-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="99445-119">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="99445-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

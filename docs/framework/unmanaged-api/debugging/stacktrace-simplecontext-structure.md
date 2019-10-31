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
ms.openlocfilehash: 1cd3c34fc292e4a050fa8a75078283e34425fc8f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139129"
---
# <a name="stacktrace_simplecontext-structure"></a><span data-ttu-id="f8f24-102">StackTrace_SimpleContext — Struktura</span><span class="sxs-lookup"><span data-stu-id="f8f24-102">StackTrace_SimpleContext Structure</span></span>
<span data-ttu-id="f8f24-103">Udostępnia prosty kontekst, który może być używany zamiast pełnej struktury `CONTEXT`.</span><span class="sxs-lookup"><span data-stu-id="f8f24-103">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8f24-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f8f24-104">Syntax</span></span>  
  
```cpp  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a><span data-ttu-id="f8f24-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="f8f24-105">Members</span></span>  
  
|<span data-ttu-id="f8f24-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="f8f24-106">Member</span></span>|<span data-ttu-id="f8f24-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f8f24-107">Description</span></span>|  
|------------|-----------------|  
|`StackOffset`|<span data-ttu-id="f8f24-108">Wskaźnik stosu lub wskaźnik wprowadzania stosu (ESP) na platformach x86.</span><span class="sxs-lookup"><span data-stu-id="f8f24-108">The stack pointer, or the enter stack pointer (ESP) on x86 platforms.</span></span>|  
|`FrameOffset`|<span data-ttu-id="f8f24-109">Przesunięcie ramki lub rejestrowanie EBP na platformach x86.</span><span class="sxs-lookup"><span data-stu-id="f8f24-109">The frame offset, or the EBP register on x86 platforms.</span></span>|  
|`InstructionOffset`|<span data-ttu-id="f8f24-110">Wskaźnik instrukcji lub wskaźnik wprowadzania instrukcji (EIP) na platformach x86.</span><span class="sxs-lookup"><span data-stu-id="f8f24-110">The instruction pointer, or the enter instruction pointer (EIP) on x86 platforms.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8f24-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f8f24-111">Remarks</span></span>  
 <span data-ttu-id="f8f24-112">Ponieważ funkcje śledzenia stosu zwykle muszą zwracać tylko adres, przesunięcie ramki i adres stosu, można opcjonalnie użyć struktury `SimpleContext` zamiast dużego `CONTEXT`j struktury.</span><span class="sxs-lookup"><span data-stu-id="f8f24-112">Because stack trace functions typically need to return only the address, frame offset, and stack address, you can optionally use the `SimpleContext` structure instead of a large `CONTEXT` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8f24-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f8f24-113">Requirements</span></span>  
 <span data-ttu-id="f8f24-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8f24-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8f24-115">**Nagłówek:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="f8f24-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="f8f24-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8f24-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8f24-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f8f24-117">See also</span></span>

- [<span data-ttu-id="f8f24-118">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="f8f24-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="f8f24-119">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="f8f24-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

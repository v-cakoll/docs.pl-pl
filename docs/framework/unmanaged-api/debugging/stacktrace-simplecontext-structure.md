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
ms.openlocfilehash: bc0fc18e31b89b22ffd30d99a8b079ed7b87fa1b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752503"
---
# <a name="stacktracesimplecontext-structure"></a><span data-ttu-id="d3d90-102">StackTrace_SimpleContext — Struktura</span><span class="sxs-lookup"><span data-stu-id="d3d90-102">StackTrace_SimpleContext Structure</span></span>
<span data-ttu-id="d3d90-103">Udostępnia prosty kontekst, który można użyć zamiast pełnego `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="d3d90-103">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3d90-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3d90-104">Syntax</span></span>  
  
```cpp  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a><span data-ttu-id="d3d90-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d3d90-105">Members</span></span>  
  
|<span data-ttu-id="d3d90-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="d3d90-106">Member</span></span>|<span data-ttu-id="d3d90-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d3d90-107">Description</span></span>|  
|------------|-----------------|  
|`StackOffset`|<span data-ttu-id="d3d90-108">Wskaźnik stosu lub wskaźnik stosu enter (ESP) na x86 platform.</span><span class="sxs-lookup"><span data-stu-id="d3d90-108">The stack pointer, or the enter stack pointer (ESP) on x86 platforms.</span></span>|  
|`FrameOffset`|<span data-ttu-id="d3d90-109">Przesunięcie ramki lub zarejestruj EBP na x86 platform.</span><span class="sxs-lookup"><span data-stu-id="d3d90-109">The frame offset, or the EBP register on x86 platforms.</span></span>|  
|`InstructionOffset`|<span data-ttu-id="d3d90-110">Wskaźnik instrukcji lub enter wskaźnik instrukcji (EIP) na x86 platform.</span><span class="sxs-lookup"><span data-stu-id="d3d90-110">The instruction pointer, or the enter instruction pointer (EIP) on x86 platforms.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3d90-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d3d90-111">Remarks</span></span>  
 <span data-ttu-id="d3d90-112">Ponieważ funkcje śledzenia stosu zazwyczaj trzeba zwrócić tylko adres, przesunięcie ramki i adresu stosu, można opcjonalnie używać `SimpleContext` struktury zamiast dużą `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="d3d90-112">Because stack trace functions typically need to return only the address, frame offset, and stack address, you can optionally use the `SimpleContext` structure instead of a large `CONTEXT` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3d90-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d3d90-113">Requirements</span></span>  
 <span data-ttu-id="d3d90-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3d90-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3d90-115">**Nagłówek:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="d3d90-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="d3d90-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3d90-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3d90-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d3d90-117">See also</span></span>

- [<span data-ttu-id="d3d90-118">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="d3d90-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="d3d90-119">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="d3d90-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

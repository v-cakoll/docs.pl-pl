---
title: CorDebugRegister — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugRegister
helpviewer_keywords:
- CorDebugRegister enumeration [.NET Framework debugging]
ms.assetid: 003bb138-7960-4291-ac88-0d87e470ff70
topic_type:
- apiref
ms.openlocfilehash: 9af265144c9e38ffe132c16a318c374b08a920e3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778253"
---
# <a name="cordebugregister-enumeration"></a><span data-ttu-id="16aca-102">CorDebugRegister — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="16aca-102">CorDebugRegister Enumeration</span></span>
<span data-ttu-id="16aca-103">Określa rejestry skojarzone z daną architekturą procesora.</span><span class="sxs-lookup"><span data-stu-id="16aca-103">Specifies the registers associated with a given processor architecture.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16aca-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="16aca-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugRegister {  
  
    REGISTER_INSTRUCTION_POINTER = 0,  
    REGISTER_STACK_POINTER,  
    REGISTER_FRAME_POINTER,  
  
    REGISTER_X86_EIP = 0,  
    REGISTER_X86_ESP,  
    REGISTER_X86_EBP,  
  
    REGISTER_X86_EAX,  
    REGISTER_X86_ECX,  
    REGISTER_X86_EDX,  
    REGISTER_X86_EBX,  
  
    REGISTER_X86_ESI,  
    REGISTER_X86_EDI,  
  
    REGISTER_X86_FPSTACK_0,  
    REGISTER_X86_FPSTACK_1,  
    REGISTER_X86_FPSTACK_2,  
    REGISTER_X86_FPSTACK_3,  
    REGISTER_X86_FPSTACK_4,  
    REGISTER_X86_FPSTACK_5,  
    REGISTER_X86_FPSTACK_6,  
    REGISTER_X86_FPSTACK_7,  
  
    REGISTER_AMD64_RIP = 0,  
    REGISTER_AMD64_RSP,  
    REGISTER_AMD64_RBP,  
    REGISTER_AMD64_RAX,  
    REGISTER_AMD64_RCX,  
    REGISTER_AMD64_RDX,  
    REGISTER_AMD64_RBX,  
    REGISTER_AMD64_RSI,  
    REGISTER_AMD64_RDI,  
    REGISTER_AMD64_R8,  
    REGISTER_AMD64_R9,  
    REGISTER_AMD64_R10,  
    REGISTER_AMD64_R11,  
    REGISTER_AMD64_R12,  
    REGISTER_AMD64_R13,  
    REGISTER_AMD64_R14,  
    REGISTER_AMD64_R15,  
  
    REGISTER_AMD64_XMM0,  
    REGISTER_AMD64_XMM1,  
    REGISTER_AMD64_XMM2,  
    REGISTER_AMD64_XMM3,  
    REGISTER_AMD64_XMM4,  
    REGISTER_AMD64_XMM5,  
    REGISTER_AMD64_XMM6,  
    REGISTER_AMD64_XMM7,  
    REGISTER_AMD64_XMM8,  
    REGISTER_AMD64_XMM9,  
    REGISTER_AMD64_XMM10,  
    REGISTER_AMD64_XMM11,  
    REGISTER_AMD64_XMM12,  
    REGISTER_AMD64_XMM13,  
    REGISTER_AMD64_XMM14,  
    REGISTER_AMD64_XMM15,  
  
    REGISTER_IA64_BSP = REGISTER_FRAME_POINTER,  
    REGISTER_IA64_R0  = REGISTER_IA64_BSP + 1,  
    REGISTER_IA64_F0  = REGISTER_IA64_R0  + 128,  
    REGISTER_ARM_PC = 0,  
    REGISTER_ARM_SP,  
    REGISTER_ARM_R0,  
    REGISTER_ARM_R1,  
    REGISTER_ARM_R2,  
    REGISTER_ARM_R3,  
    REGISTER_ARM_R4,  
    REGISTER_ARM_R5,  
    REGISTER_ARM_R6,  
    REGISTER_ARM_R7,  
    REGISTER_ARM_R8,  
    REGISTER_ARM_R9,  
    REGISTER_ARM_R10,  
    REGISTER_ARM_R11,  
    REGISTER_ARM_R12,  
    REGISTER_ARM_LR,  
  
} CorDebugRegister;  
```  
  
## <a name="members"></a><span data-ttu-id="16aca-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="16aca-105">Members</span></span>  
  
|<span data-ttu-id="16aca-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="16aca-106">Member</span></span>|<span data-ttu-id="16aca-107">Opis</span><span class="sxs-lookup"><span data-stu-id="16aca-107">Description</span></span>|  
|------------|-----------------|  
|`REGISTER_INSTRUCTION_POINTER`|<span data-ttu-id="16aca-108">Zarejestrowano wskaźnik instrukcji na dowolnym procesorze.</span><span class="sxs-lookup"><span data-stu-id="16aca-108">An instruction pointer register on any processor.</span></span>|  
|`REGISTER_STACK_POINTER`|<span data-ttu-id="16aca-109">Zarejestrowano Wskaźnik stosu na dowolnym procesorze.</span><span class="sxs-lookup"><span data-stu-id="16aca-109">A stack pointer register on any processor.</span></span>|  
|`REGISTER_FRAME_POINTER`|<span data-ttu-id="16aca-110">Rejestr wskaźnika ramki na dowolnym procesorze.</span><span class="sxs-lookup"><span data-stu-id="16aca-110">A frame pointer register on any processor.</span></span>|  
|`REGISTER_X86_EIP`|<span data-ttu-id="16aca-111">Wskaźnik instrukcji jest rejestrowany na procesorze x86.</span><span class="sxs-lookup"><span data-stu-id="16aca-111">The instruction pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_ESP`|<span data-ttu-id="16aca-112">Wskaźnik stosu jest rejestrowany na procesorze x86.</span><span class="sxs-lookup"><span data-stu-id="16aca-112">The stack pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_EBP`|<span data-ttu-id="16aca-113">Podstawowy wskaźnik rejestracji na procesorze x86.</span><span class="sxs-lookup"><span data-stu-id="16aca-113">The base pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_EAX`|<span data-ttu-id="16aca-114">Rejestr danych na procesorze x86.</span><span class="sxs-lookup"><span data-stu-id="16aca-114">The A data register on the x86 processor.</span></span>|  
|`REGISTER_X86_ECX`|<span data-ttu-id="16aca-115">Rejestr danych języka C na procesorze x86.</span><span class="sxs-lookup"><span data-stu-id="16aca-115">The C data register on the x86 processor.</span></span>|  
|`REGISTER_X86_EDX`|<span data-ttu-id="16aca-116">Rejestr danych D na procesorze x86.</span><span class="sxs-lookup"><span data-stu-id="16aca-116">The D data register on the x86 processor.</span></span>|  
|`REGISTER_X86_EBX`|<span data-ttu-id="16aca-117">Rejestr danych B na procesorze x86.</span><span class="sxs-lookup"><span data-stu-id="16aca-117">The B data register on the x86 processor.</span></span>|  
|`REGISTER_X86_ESI`|<span data-ttu-id="16aca-118">Indeks źródła jest rejestrowany na procesorze x86.</span><span class="sxs-lookup"><span data-stu-id="16aca-118">The source index register on the x86 processor.</span></span>|  
|`REGISTER_X86_EDI`|<span data-ttu-id="16aca-119">Indeks docelowy jest rejestrowany na procesorze x86.</span><span class="sxs-lookup"><span data-stu-id="16aca-119">The destination index register on the x86 processor.</span></span>|  
|`REGISTER_X86_FPSTACK_0`|<span data-ttu-id="16aca-120">Stos rejestruje 0 na procesorze zmiennoprzecinkowym x86 (FP).</span><span class="sxs-lookup"><span data-stu-id="16aca-120">The stack register 0 on the x86 floating-point (FP) processor.</span></span>|  
|`REGISTER_X86_FPSTACK_1`|<span data-ttu-id="16aca-121">#1 zarejestrować stos na procesorze x86 FP.</span><span class="sxs-lookup"><span data-stu-id="16aca-121">The #1 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_2`|<span data-ttu-id="16aca-122">#2 zarejestrować stos na procesorze x86 FP.</span><span class="sxs-lookup"><span data-stu-id="16aca-122">The #2 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_3`|<span data-ttu-id="16aca-123">#3 zarejestrować stos na procesorze x86 FP.</span><span class="sxs-lookup"><span data-stu-id="16aca-123">The #3 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_4`|<span data-ttu-id="16aca-124">#4 zarejestrować stos na procesorze x86 FP.</span><span class="sxs-lookup"><span data-stu-id="16aca-124">The #4 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_5`|<span data-ttu-id="16aca-125">#5 zarejestrować stos na procesorze x86 FP.</span><span class="sxs-lookup"><span data-stu-id="16aca-125">The #5 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_6`|<span data-ttu-id="16aca-126">#6 zarejestrować stos na procesorze x86 FP.</span><span class="sxs-lookup"><span data-stu-id="16aca-126">The #6 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_7`|<span data-ttu-id="16aca-127">#7 zarejestrować stos na procesorze x86 FP.</span><span class="sxs-lookup"><span data-stu-id="16aca-127">The #7 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_AMD64_RIP`|<span data-ttu-id="16aca-128">Wskaźnik instrukcji jest rejestrowany na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-128">The instruction pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RSP`|<span data-ttu-id="16aca-129">Wskaźnik stosu jest rejestrowany na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-129">The stack pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RBP`|<span data-ttu-id="16aca-130">Podstawowy wskaźnik rejestru na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-130">The base pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RAX`|<span data-ttu-id="16aca-131">Rejestr danych na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-131">The A data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RCX`|<span data-ttu-id="16aca-132">Rejestr danych języka C na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-132">The C data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RDX`|<span data-ttu-id="16aca-133">Rejestr D na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-133">The D data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RBX`|<span data-ttu-id="16aca-134">Rejestr danych B na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-134">The B data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RSI`|<span data-ttu-id="16aca-135">Indeks źródła jest rejestrowany na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-135">The source index register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RDI`|<span data-ttu-id="16aca-136">Indeks docelowy rejestruje się w procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-136">The destination index register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R8`|<span data-ttu-id="16aca-137">Rejestr danych #8 na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-137">The #8 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R9`|<span data-ttu-id="16aca-138">Rejestr danych #9 na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-138">The #9 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R10`|<span data-ttu-id="16aca-139">Rejestr danych #10 na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-139">The #10 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R11`|<span data-ttu-id="16aca-140">Rejestr danych #11 na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-140">The #11 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R12`|<span data-ttu-id="16aca-141">Rejestr danych #12 na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-141">The #12 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R13`|<span data-ttu-id="16aca-142">Rejestr danych #13 na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-142">The #13 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R14`|<span data-ttu-id="16aca-143">Rejestr danych #14 na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-143">The #14 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R15`|<span data-ttu-id="16aca-144">Rejestr danych #15 na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-144">The #15 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM0`|<span data-ttu-id="16aca-145">#0 rejestr multimedialny na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-145">The #0 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM1`|<span data-ttu-id="16aca-146">#1 Rejestr multimedialny na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-146">The #1 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM2`|<span data-ttu-id="16aca-147">#2 rejestr multimedialny na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-147">The #2 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM3`|<span data-ttu-id="16aca-148">#3 rejestr multimedialny na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-148">The #3 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM4`|<span data-ttu-id="16aca-149">#4 rejestr multimedialny na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-149">The #4 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM5`|<span data-ttu-id="16aca-150">#5 rejestr multimedialny na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-150">The #5 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM6`|<span data-ttu-id="16aca-151">#6 rejestr multimedialny na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-151">The #6 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM7`|<span data-ttu-id="16aca-152">#7 rejestr multimedialny na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-152">The #7 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM8`|<span data-ttu-id="16aca-153">#8 rejestr multimedialny na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-153">The #8 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM9`|<span data-ttu-id="16aca-154">#9 rejestr multimedialny na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-154">The #9 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM10`|<span data-ttu-id="16aca-155">#10 rejestr multimedialny na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-155">The #10 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM11`|<span data-ttu-id="16aca-156">#11 rejestr multimedialny na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-156">The #11 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM12`|<span data-ttu-id="16aca-157">#12 rejestr multimedialny na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-157">The #12 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM13`|<span data-ttu-id="16aca-158">#13 rejestr multimedialny na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-158">The #13 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM14`|<span data-ttu-id="16aca-159">#14 rejestr multimedialny na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-159">The #14 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM15`|<span data-ttu-id="16aca-160">#15 rejestr multimedialny na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="16aca-160">The #15 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_IA64_BSP`|<span data-ttu-id="16aca-161">Wskaźnik stosu jest rejestrowany w procesorze IA-64.</span><span class="sxs-lookup"><span data-stu-id="16aca-161">The stack pointer register on the IA-64 processor.</span></span>|  
|`REGISTER_IA64_R0`|<span data-ttu-id="16aca-162">#0 zarejestrować dane w procesorze IA-64.</span><span class="sxs-lookup"><span data-stu-id="16aca-162">The #0 data register on the IA-64 processor.</span></span>|  
|`REGISTER_IA64_F0`|<span data-ttu-id="16aca-163">Rejestr danych FP #0 w procesorze IA-64.</span><span class="sxs-lookup"><span data-stu-id="16aca-163">The #0 FP data register on the IA-64 processor.</span></span>|  
|`REGISTER_ARM_PC`|<span data-ttu-id="16aca-164">Rejestr licznika programu (R15) na procesorze ARM.</span><span class="sxs-lookup"><span data-stu-id="16aca-164">The program counter register (R15) on the ARM processor.</span></span>|  
|`REGISTER_ARM_SP`|<span data-ttu-id="16aca-165">Rejestr wskaźnika stosu (R13) na procesorze ARM.</span><span class="sxs-lookup"><span data-stu-id="16aca-165">The stack pointer register (R13) on the ARM processor.</span></span>|  
|`REGISTER_ARM_R0`|<span data-ttu-id="16aca-166">R0 rejestru danych w procesorze ARM.</span><span class="sxs-lookup"><span data-stu-id="16aca-166">Data register R0 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R1`|<span data-ttu-id="16aca-167">Rejestr danych R1 w procesorze ARM.</span><span class="sxs-lookup"><span data-stu-id="16aca-167">Data register R1 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R2`|<span data-ttu-id="16aca-168">Rejestr danych R2 w procesorze ARM.</span><span class="sxs-lookup"><span data-stu-id="16aca-168">Data register R2 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R3`|<span data-ttu-id="16aca-169">Zarejestruj dane R3 na procesorze ARM.</span><span class="sxs-lookup"><span data-stu-id="16aca-169">Data register R3 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R4`|<span data-ttu-id="16aca-170">Zarejestruj R4 na procesorze ARM.</span><span class="sxs-lookup"><span data-stu-id="16aca-170">Register R4 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R5`|<span data-ttu-id="16aca-171">Zarejestruj R5 na procesorze ARM.</span><span class="sxs-lookup"><span data-stu-id="16aca-171">Register R5 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R6`|<span data-ttu-id="16aca-172">Zarejestruj R6 na procesorze ARM.</span><span class="sxs-lookup"><span data-stu-id="16aca-172">Register R6 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R7`|<span data-ttu-id="16aca-173">Zarejestruj R7 (wskaźnik ramki KCIUKa) na procesorze ARM.</span><span class="sxs-lookup"><span data-stu-id="16aca-173">Register R7 (the THUMB frame pointer) on the ARM processor.</span></span>|  
|`REGISTER_ARM_R8`|<span data-ttu-id="16aca-174">Zarejestruj R8 na procesorze ARM.</span><span class="sxs-lookup"><span data-stu-id="16aca-174">Register R8 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R9`|<span data-ttu-id="16aca-175">Zarejestruj R9 na procesorze ARM.</span><span class="sxs-lookup"><span data-stu-id="16aca-175">Register R9 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R10`|<span data-ttu-id="16aca-176">Zarejestruj R10 na procesorze ARM.</span><span class="sxs-lookup"><span data-stu-id="16aca-176">Register R10 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R11`|<span data-ttu-id="16aca-177">Wskaźnik ramki na procesorze ARM.</span><span class="sxs-lookup"><span data-stu-id="16aca-177">The frame pointer on the ARM processor.</span></span>|  
|`REGISTER_ARM_R12`|<span data-ttu-id="16aca-178">Zarejestruj R12 na procesorze ARM.</span><span class="sxs-lookup"><span data-stu-id="16aca-178">Register R12 on the ARM processor.</span></span>|  
|`REGISTER_ARM_LR`|<span data-ttu-id="16aca-179">Rejestracja linku (R14) na procesorze ARM.</span><span class="sxs-lookup"><span data-stu-id="16aca-179">The link register (R14) on the ARM processor.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16aca-180">Uwagi</span><span class="sxs-lookup"><span data-stu-id="16aca-180">Remarks</span></span>  
 <span data-ttu-id="16aca-181">Istnieją 128 rejestrów danych ogólnego przeznaczenia i 128 rejestrów danych zmiennoprzecinkowych w procesorze IA-64, ale podano tylko wartości `REGISTER_IA64_R0` i `REGISTER_IA64_F0`.</span><span class="sxs-lookup"><span data-stu-id="16aca-181">There are 128 general-purpose data registers and 128 floating-point data registers on the IA-64 processor, but only values `REGISTER_IA64_R0` and `REGISTER_IA64_F0` are provided.</span></span> <span data-ttu-id="16aca-182">Inne wartości można określić w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="16aca-182">The other values can be determined as follows:</span></span>  
  
- <span data-ttu-id="16aca-183">Dodaj numer rejestru do `REGISTER_IA64_R0` wartości `REGISTER_IA64_R1` za pomocą `REGISTER_IA64_R127`, który odpowiada #1 rejestru danych przez #127 rejestru danych w procesorze IA-64.</span><span class="sxs-lookup"><span data-stu-id="16aca-183">Add the register number to `REGISTER_IA64_R0` for values `REGISTER_IA64_R1` through `REGISTER_IA64_R127`, which correspond to the #1 data register through the #127 data register on the IA-64 processor.</span></span>  
  
- <span data-ttu-id="16aca-184">Dodaj numer rejestru do `REGISTER_IA64_F0` dla wartości `REGISTER_IA64_F1` za pomocą `REGISTER_IA64_F127`, który odpowiada rejestrowi danych z #1 FP za pomocą rejestru #127 FP w ramach procesora IA-64.</span><span class="sxs-lookup"><span data-stu-id="16aca-184">Add the register number to `REGISTER_IA64_F0` for values `REGISTER_IA64_F1` through `REGISTER_IA64_F127`, which correspond to the #1 FP data register through the #127 FP data register on the IA-64 processor.</span></span>  
  
 <span data-ttu-id="16aca-185">Na przykład, jeśli konieczne jest określenie #83 rejestru danych w procesorze IA-64, należy użyć `REGISTER_IA64_R0` + 83.</span><span class="sxs-lookup"><span data-stu-id="16aca-185">For example, if you need to specify the #83 data register on the IA-64 processor, use `REGISTER_IA64_R0` + 83.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16aca-186">Wymagania</span><span class="sxs-lookup"><span data-stu-id="16aca-186">Requirements</span></span>  
 <span data-ttu-id="16aca-187">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16aca-187">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16aca-188">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="16aca-188">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16aca-189">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="16aca-189">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16aca-190">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16aca-190">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16aca-191">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="16aca-191">See also</span></span>

- [<span data-ttu-id="16aca-192">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="16aca-192">Debugging Enumerations</span></span>](debugging-enumerations.md)

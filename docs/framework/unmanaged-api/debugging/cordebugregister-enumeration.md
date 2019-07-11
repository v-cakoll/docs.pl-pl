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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bed3c461935c5a2bc912ed9ed16d147fddaf8a1a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739655"
---
# <a name="cordebugregister-enumeration"></a><span data-ttu-id="fc76d-102">CorDebugRegister — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fc76d-102">CorDebugRegister Enumeration</span></span>
<span data-ttu-id="fc76d-103">Określa rejestrów związane z architekturą procesora w danym.</span><span class="sxs-lookup"><span data-stu-id="fc76d-103">Specifies the registers associated with a given processor architecture.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc76d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc76d-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="fc76d-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="fc76d-105">Members</span></span>  
  
|<span data-ttu-id="fc76d-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="fc76d-106">Member</span></span>|<span data-ttu-id="fc76d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="fc76d-107">Description</span></span>|  
|------------|-----------------|  
|`REGISTER_INSTRUCTION_POINTER`|<span data-ttu-id="fc76d-108">Wskaźnik instrukcji rejestrowania na każdy procesor.</span><span class="sxs-lookup"><span data-stu-id="fc76d-108">An instruction pointer register on any processor.</span></span>|  
|`REGISTER_STACK_POINTER`|<span data-ttu-id="fc76d-109">Wskaźnik stosu, zarejestruj się na każdy procesor.</span><span class="sxs-lookup"><span data-stu-id="fc76d-109">A stack pointer register on any processor.</span></span>|  
|`REGISTER_FRAME_POINTER`|<span data-ttu-id="fc76d-110">Wskaźnik ramki, zarejestruj się na każdy procesor.</span><span class="sxs-lookup"><span data-stu-id="fc76d-110">A frame pointer register on any processor.</span></span>|  
|`REGISTER_X86_EIP`|<span data-ttu-id="fc76d-111">Rejestr wskaźnika instrukcji na x86 procesora.</span><span class="sxs-lookup"><span data-stu-id="fc76d-111">The instruction pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_ESP`|<span data-ttu-id="fc76d-112">Rejestr wskaźnika stosu na x86 procesora.</span><span class="sxs-lookup"><span data-stu-id="fc76d-112">The stack pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_EBP`|<span data-ttu-id="fc76d-113">Podstawowy wskaźnik, zarejestruj się na x86 procesora.</span><span class="sxs-lookup"><span data-stu-id="fc76d-113">The base pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_EAX`|<span data-ttu-id="fc76d-114">Rejestr danych A na x86 procesora.</span><span class="sxs-lookup"><span data-stu-id="fc76d-114">The A data register on the x86 processor.</span></span>|  
|`REGISTER_X86_ECX`|<span data-ttu-id="fc76d-115">Rejestr danych C na x86 procesora.</span><span class="sxs-lookup"><span data-stu-id="fc76d-115">The C data register on the x86 processor.</span></span>|  
|`REGISTER_X86_EDX`|<span data-ttu-id="fc76d-116">D dane rejestrują się x86 procesora.</span><span class="sxs-lookup"><span data-stu-id="fc76d-116">The D data register on the x86 processor.</span></span>|  
|`REGISTER_X86_EBX`|<span data-ttu-id="fc76d-117">Rejestr danych B na x86 procesora.</span><span class="sxs-lookup"><span data-stu-id="fc76d-117">The B data register on the x86 processor.</span></span>|  
|`REGISTER_X86_ESI`|<span data-ttu-id="fc76d-118">Źródło indeks rejestru w x86 procesora.</span><span class="sxs-lookup"><span data-stu-id="fc76d-118">The source index register on the x86 processor.</span></span>|  
|`REGISTER_X86_EDI`|<span data-ttu-id="fc76d-119">Rejestr indeksu docelowego na x86 procesora.</span><span class="sxs-lookup"><span data-stu-id="fc76d-119">The destination index register on the x86 processor.</span></span>|  
|`REGISTER_X86_FPSTACK_0`|<span data-ttu-id="fc76d-120">Procesor rejestru 0 na x86 zmiennoprzecinkowych (FP) stosu.</span><span class="sxs-lookup"><span data-stu-id="fc76d-120">The stack register 0 on the x86 floating-point (FP) processor.</span></span>|  
|`REGISTER_X86_FPSTACK_1`|<span data-ttu-id="fc76d-121">Stos #1 rejestrują się x86 FP procesora.</span><span class="sxs-lookup"><span data-stu-id="fc76d-121">The #1 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_2`|<span data-ttu-id="fc76d-122">Stos #2 rejestrują się x86 FP procesora.</span><span class="sxs-lookup"><span data-stu-id="fc76d-122">The #2 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_3`|<span data-ttu-id="fc76d-123">Stos #3 rejestrują się x86 FP procesora.</span><span class="sxs-lookup"><span data-stu-id="fc76d-123">The #3 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_4`|<span data-ttu-id="fc76d-124">Stos #4 rejestrują się x86 FP procesora.</span><span class="sxs-lookup"><span data-stu-id="fc76d-124">The #4 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_5`|<span data-ttu-id="fc76d-125">Stos #5 rejestrują się x86 FP procesora.</span><span class="sxs-lookup"><span data-stu-id="fc76d-125">The #5 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_6`|<span data-ttu-id="fc76d-126">Stos #6 rejestrują się x86 FP procesora.</span><span class="sxs-lookup"><span data-stu-id="fc76d-126">The #6 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_7`|<span data-ttu-id="fc76d-127">Stos #7 rejestrują się x86 FP procesora.</span><span class="sxs-lookup"><span data-stu-id="fc76d-127">The #7 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_AMD64_RIP`|<span data-ttu-id="fc76d-128">Zarejestruj wskaźnik instrukcji w procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-128">The instruction pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RSP`|<span data-ttu-id="fc76d-129">Wskaźnik stosu, zarejestruj się na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-129">The stack pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RBP`|<span data-ttu-id="fc76d-130">Podstawowy wskaźnik, zarejestruj się na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-130">The base pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RAX`|<span data-ttu-id="fc76d-131">Rejestr danych A na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-131">The A data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RCX`|<span data-ttu-id="fc76d-132">Zarejestruj dane C na systemów z procesorem AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-132">The C data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RDX`|<span data-ttu-id="fc76d-133">Zarejestruj D dane na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-133">The D data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RBX`|<span data-ttu-id="fc76d-134">Rejestrowanie danych B na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-134">The B data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RSI`|<span data-ttu-id="fc76d-135">Indeks źródła, zarejestruj się na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-135">The source index register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RDI`|<span data-ttu-id="fc76d-136">Indeksu docelowego, zarejestruj się na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-136">The destination index register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R8`|<span data-ttu-id="fc76d-137">Zarejestruj dane #8 na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-137">The #8 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R9`|<span data-ttu-id="fc76d-138">Zarejestruj dane #9 na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-138">The #9 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R10`|<span data-ttu-id="fc76d-139">Zarejestruj dane #10 na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-139">The #10 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R11`|<span data-ttu-id="fc76d-140">Zarejestruj dane #11 na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-140">The #11 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R12`|<span data-ttu-id="fc76d-141">Zarejestruj dane #12 na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-141">The #12 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R13`|<span data-ttu-id="fc76d-142">Zarejestruj dane #13 na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-142">The #13 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R14`|<span data-ttu-id="fc76d-143">Zarejestruj dane #14 na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-143">The #14 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R15`|<span data-ttu-id="fc76d-144">Zarejestruj dane #15 na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-144">The #15 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM0`|<span data-ttu-id="fc76d-145">#0 multimedialnych zarejestrować na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-145">The #0 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM1`|<span data-ttu-id="fc76d-146">Zarejestruj #1 multimedialnych na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-146">The #1 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM2`|<span data-ttu-id="fc76d-147">Zarejestruj #2 multimedialnych na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-147">The #2 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM3`|<span data-ttu-id="fc76d-148">Zarejestruj #3 multimedialnych na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-148">The #3 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM4`|<span data-ttu-id="fc76d-149">Zarejestruj #4 multimedialnych na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-149">The #4 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM5`|<span data-ttu-id="fc76d-150">Zarejestruj #5 multimedialnych na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-150">The #5 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM6`|<span data-ttu-id="fc76d-151">Zarejestruj #6 multimedialnych na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-151">The #6 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM7`|<span data-ttu-id="fc76d-152">Zarejestruj #7 multimedialnych na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-152">The #7 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM8`|<span data-ttu-id="fc76d-153">Zarejestruj #8 multimedialnych na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-153">The #8 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM9`|<span data-ttu-id="fc76d-154">Zarejestruj #9 multimedialnych na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-154">The #9 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM10`|<span data-ttu-id="fc76d-155">Zarejestruj #10 multimedialnych na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-155">The #10 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM11`|<span data-ttu-id="fc76d-156">Zarejestruj #11 multimedialnych na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-156">The #11 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM12`|<span data-ttu-id="fc76d-157">Zarejestruj #12 multimedialnych na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-157">The #12 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM13`|<span data-ttu-id="fc76d-158">Zarejestruj #13 multimedialnych na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-158">The #13 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM14`|<span data-ttu-id="fc76d-159">Zarejestruj #14 multimedialnych na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-159">The #14 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM15`|<span data-ttu-id="fc76d-160">Zarejestruj #15 multimedialnych na procesorze AMD64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-160">The #15 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_IA64_BSP`|<span data-ttu-id="fc76d-161">Wskaźnik stosu, zarejestruj się na procesorze IA-64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-161">The stack pointer register on the IA-64 processor.</span></span>|  
|`REGISTER_IA64_R0`|<span data-ttu-id="fc76d-162">Zarejestruj dane #0 na procesorze IA-64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-162">The #0 data register on the IA-64 processor.</span></span>|  
|`REGISTER_IA64_F0`|<span data-ttu-id="fc76d-163">Zarejestruj dane FP #0 na procesorze IA-64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-163">The #0 FP data register on the IA-64 processor.</span></span>|  
|`REGISTER_ARM_PC`|<span data-ttu-id="fc76d-164">Licznik programu Zarejestruj (R15) w procesorze ARM.</span><span class="sxs-lookup"><span data-stu-id="fc76d-164">The program counter register (R15) on the ARM processor.</span></span>|  
|`REGISTER_ARM_SP`|<span data-ttu-id="fc76d-165">Wskaźnik stosu Zarejestruj (R13) w procesorze ARM.</span><span class="sxs-lookup"><span data-stu-id="fc76d-165">The stack pointer register (R13) on the ARM processor.</span></span>|  
|`REGISTER_ARM_R0`|<span data-ttu-id="fc76d-166">Data zarejestrowania R0 procesora ARM.</span><span class="sxs-lookup"><span data-stu-id="fc76d-166">Data register R0 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R1`|<span data-ttu-id="fc76d-167">Data zarejestrowania R1 procesora ARM.</span><span class="sxs-lookup"><span data-stu-id="fc76d-167">Data register R1 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R2`|<span data-ttu-id="fc76d-168">Data zarejestrowania R2 procesora ARM.</span><span class="sxs-lookup"><span data-stu-id="fc76d-168">Data register R2 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R3`|<span data-ttu-id="fc76d-169">Data zarejestrowania R3 procesora ARM.</span><span class="sxs-lookup"><span data-stu-id="fc76d-169">Data register R3 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R4`|<span data-ttu-id="fc76d-170">Zarejestruj R4 procesora ARM.</span><span class="sxs-lookup"><span data-stu-id="fc76d-170">Register R4 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R5`|<span data-ttu-id="fc76d-171">Zarejestruj R5 procesora ARM.</span><span class="sxs-lookup"><span data-stu-id="fc76d-171">Register R5 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R6`|<span data-ttu-id="fc76d-172">Zarejestruj R6 procesora ARM.</span><span class="sxs-lookup"><span data-stu-id="fc76d-172">Register R6 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R7`|<span data-ttu-id="fc76d-173">Zarejestruj R7 (THUMB wskaźnika ramki) na procesorze ARM.</span><span class="sxs-lookup"><span data-stu-id="fc76d-173">Register R7 (the THUMB frame pointer) on the ARM processor.</span></span>|  
|`REGISTER_ARM_R8`|<span data-ttu-id="fc76d-174">Zarejestruj R8 procesora ARM.</span><span class="sxs-lookup"><span data-stu-id="fc76d-174">Register R8 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R9`|<span data-ttu-id="fc76d-175">Zarejestruj R9 procesora ARM.</span><span class="sxs-lookup"><span data-stu-id="fc76d-175">Register R9 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R10`|<span data-ttu-id="fc76d-176">Zarejestruj R10 procesora ARM.</span><span class="sxs-lookup"><span data-stu-id="fc76d-176">Register R10 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R11`|<span data-ttu-id="fc76d-177">Wskaźnik ramki procesora ARM.</span><span class="sxs-lookup"><span data-stu-id="fc76d-177">The frame pointer on the ARM processor.</span></span>|  
|`REGISTER_ARM_R12`|<span data-ttu-id="fc76d-178">Zarejestruj R12 procesora ARM.</span><span class="sxs-lookup"><span data-stu-id="fc76d-178">Register R12 on the ARM processor.</span></span>|  
|`REGISTER_ARM_LR`|<span data-ttu-id="fc76d-179">Rejestr link (R14) w procesorze ARM.</span><span class="sxs-lookup"><span data-stu-id="fc76d-179">The link register (R14) on the ARM processor.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc76d-180">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fc76d-180">Remarks</span></span>  
 <span data-ttu-id="fc76d-181">Brak rejestrów 128 danych ogólnego przeznaczenia i 128 rejestrów zmiennoprzecinkowych danych na procesorach IA-64 procesora, ale tylko wartości `REGISTER_IA64_R0` i `REGISTER_IA64_F0` są dostarczane.</span><span class="sxs-lookup"><span data-stu-id="fc76d-181">There are 128 general-purpose data registers and 128 floating-point data registers on the IA-64 processor, but only values `REGISTER_IA64_R0` and `REGISTER_IA64_F0` are provided.</span></span> <span data-ttu-id="fc76d-182">Inne wartości mogą być określane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="fc76d-182">The other values can be determined as follows:</span></span>  
  
- <span data-ttu-id="fc76d-183">Dodaj numer rejestru w celu `REGISTER_IA64_R0` wartości `REGISTER_IA64_R1` za pośrednictwem `REGISTER_IA64_R127`, które odpowiadają rejestru #1 danych za pośrednictwem rejestru #127 danych w procesorze IA-64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-183">Add the register number to `REGISTER_IA64_R0` for values `REGISTER_IA64_R1` through `REGISTER_IA64_R127`, which correspond to the #1 data register through the #127 data register on the IA-64 processor.</span></span>  
  
- <span data-ttu-id="fc76d-184">Dodaj numer rejestru w celu `REGISTER_IA64_F0` wartości `REGISTER_IA64_F1` za pośrednictwem `REGISTER_IA64_F127`, które są zgodne Rejestr danych FP #1 do #127 Rejestr danych FP na procesorze IA-64.</span><span class="sxs-lookup"><span data-stu-id="fc76d-184">Add the register number to `REGISTER_IA64_F0` for values `REGISTER_IA64_F1` through `REGISTER_IA64_F127`, which correspond to the #1 FP data register through the #127 FP data register on the IA-64 processor.</span></span>  
  
 <span data-ttu-id="fc76d-185">Na przykład, jeśli zachodzi potrzeba Określ rejestr #83 danych w procesorze IA-64, użyj `REGISTER_IA64_R0` + 83.</span><span class="sxs-lookup"><span data-stu-id="fc76d-185">For example, if you need to specify the #83 data register on the IA-64 processor, use `REGISTER_IA64_R0` + 83.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc76d-186">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fc76d-186">Requirements</span></span>  
 <span data-ttu-id="fc76d-187">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc76d-187">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc76d-188">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc76d-188">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc76d-189">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc76d-189">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc76d-190">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc76d-190">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc76d-191">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc76d-191">See also</span></span>

- [<span data-ttu-id="fc76d-192">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="fc76d-192">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

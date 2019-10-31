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
ms.openlocfilehash: d182476130e611e57df232c9652cda4bec002c31
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132777"
---
# <a name="cordebugregister-enumeration"></a>CorDebugRegister — Wyliczenie
Określa rejestry skojarzone z daną architekturą procesora.  
  
## <a name="syntax"></a>Składnia  
  
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
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`REGISTER_INSTRUCTION_POINTER`|Zarejestrowano wskaźnik instrukcji na dowolnym procesorze.|  
|`REGISTER_STACK_POINTER`|Zarejestrowano Wskaźnik stosu na dowolnym procesorze.|  
|`REGISTER_FRAME_POINTER`|Rejestr wskaźnika ramki na dowolnym procesorze.|  
|`REGISTER_X86_EIP`|Wskaźnik instrukcji jest rejestrowany na procesorze x86.|  
|`REGISTER_X86_ESP`|Wskaźnik stosu jest rejestrowany na procesorze x86.|  
|`REGISTER_X86_EBP`|Podstawowy wskaźnik rejestracji na procesorze x86.|  
|`REGISTER_X86_EAX`|Rejestr danych na procesorze x86.|  
|`REGISTER_X86_ECX`|Rejestr danych języka C na procesorze x86.|  
|`REGISTER_X86_EDX`|Rejestr danych D na procesorze x86.|  
|`REGISTER_X86_EBX`|Rejestr danych B na procesorze x86.|  
|`REGISTER_X86_ESI`|Indeks źródła jest rejestrowany na procesorze x86.|  
|`REGISTER_X86_EDI`|Indeks docelowy jest rejestrowany na procesorze x86.|  
|`REGISTER_X86_FPSTACK_0`|Stos rejestruje 0 na procesorze zmiennoprzecinkowym x86 (FP).|  
|`REGISTER_X86_FPSTACK_1`|#1 zarejestrować stos na procesorze x86 FP.|  
|`REGISTER_X86_FPSTACK_2`|#2 zarejestrować stos na procesorze x86 FP.|  
|`REGISTER_X86_FPSTACK_3`|#3 zarejestrować stos na procesorze x86 FP.|  
|`REGISTER_X86_FPSTACK_4`|#4 zarejestrować stos na procesorze x86 FP.|  
|`REGISTER_X86_FPSTACK_5`|#5 zarejestrować stos na procesorze x86 FP.|  
|`REGISTER_X86_FPSTACK_6`|#6 zarejestrować stos na procesorze x86 FP.|  
|`REGISTER_X86_FPSTACK_7`|#7 zarejestrować stos na procesorze x86 FP.|  
|`REGISTER_AMD64_RIP`|Wskaźnik instrukcji jest rejestrowany na procesorze AMD64.|  
|`REGISTER_AMD64_RSP`|Wskaźnik stosu jest rejestrowany na procesorze AMD64.|  
|`REGISTER_AMD64_RBP`|Podstawowy wskaźnik rejestru na procesorze AMD64.|  
|`REGISTER_AMD64_RAX`|Rejestr danych na procesorze AMD64.|  
|`REGISTER_AMD64_RCX`|Rejestr danych języka C na procesorze AMD64.|  
|`REGISTER_AMD64_RDX`|Rejestr D na procesorze AMD64.|  
|`REGISTER_AMD64_RBX`|Rejestr danych B na procesorze AMD64.|  
|`REGISTER_AMD64_RSI`|Indeks źródła jest rejestrowany na procesorze AMD64.|  
|`REGISTER_AMD64_RDI`|Indeks docelowy rejestruje się w procesorze AMD64.|  
|`REGISTER_AMD64_R8`|Rejestr danych #8 na procesorze AMD64.|  
|`REGISTER_AMD64_R9`|Rejestr danych #9 na procesorze AMD64.|  
|`REGISTER_AMD64_R10`|Rejestr danych #10 na procesorze AMD64.|  
|`REGISTER_AMD64_R11`|Rejestr danych #11 na procesorze AMD64.|  
|`REGISTER_AMD64_R12`|Rejestr danych #12 na procesorze AMD64.|  
|`REGISTER_AMD64_R13`|Rejestr danych #13 na procesorze AMD64.|  
|`REGISTER_AMD64_R14`|Rejestr danych #14 na procesorze AMD64.|  
|`REGISTER_AMD64_R15`|Rejestr danych #15 na procesorze AMD64.|  
|`REGISTER_AMD64_XMM0`|#0 rejestr multimedialny na procesorze AMD64.|  
|`REGISTER_AMD64_XMM1`|#1 Rejestr multimedialny na procesorze AMD64.|  
|`REGISTER_AMD64_XMM2`|#2 rejestr multimedialny na procesorze AMD64.|  
|`REGISTER_AMD64_XMM3`|#3 rejestr multimedialny na procesorze AMD64.|  
|`REGISTER_AMD64_XMM4`|#4 rejestr multimedialny na procesorze AMD64.|  
|`REGISTER_AMD64_XMM5`|#5 rejestr multimedialny na procesorze AMD64.|  
|`REGISTER_AMD64_XMM6`|#6 rejestr multimedialny na procesorze AMD64.|  
|`REGISTER_AMD64_XMM7`|#7 rejestr multimedialny na procesorze AMD64.|  
|`REGISTER_AMD64_XMM8`|#8 rejestr multimedialny na procesorze AMD64.|  
|`REGISTER_AMD64_XMM9`|#9 rejestr multimedialny na procesorze AMD64.|  
|`REGISTER_AMD64_XMM10`|#10 rejestr multimedialny na procesorze AMD64.|  
|`REGISTER_AMD64_XMM11`|#11 rejestr multimedialny na procesorze AMD64.|  
|`REGISTER_AMD64_XMM12`|#12 rejestr multimedialny na procesorze AMD64.|  
|`REGISTER_AMD64_XMM13`|#13 rejestr multimedialny na procesorze AMD64.|  
|`REGISTER_AMD64_XMM14`|#14 rejestr multimedialny na procesorze AMD64.|  
|`REGISTER_AMD64_XMM15`|#15 rejestr multimedialny na procesorze AMD64.|  
|`REGISTER_IA64_BSP`|Wskaźnik stosu jest rejestrowany w procesorze IA-64.|  
|`REGISTER_IA64_R0`|#0 zarejestrować dane w procesorze IA-64.|  
|`REGISTER_IA64_F0`|Rejestr danych FP #0 w procesorze IA-64.|  
|`REGISTER_ARM_PC`|Rejestr licznika programu (R15) na procesorze ARM.|  
|`REGISTER_ARM_SP`|Rejestr wskaźnika stosu (R13) na procesorze ARM.|  
|`REGISTER_ARM_R0`|R0 rejestru danych w procesorze ARM.|  
|`REGISTER_ARM_R1`|Rejestr danych R1 w procesorze ARM.|  
|`REGISTER_ARM_R2`|Rejestr danych R2 w procesorze ARM.|  
|`REGISTER_ARM_R3`|Zarejestruj dane R3 na procesorze ARM.|  
|`REGISTER_ARM_R4`|Zarejestruj R4 na procesorze ARM.|  
|`REGISTER_ARM_R5`|Zarejestruj R5 na procesorze ARM.|  
|`REGISTER_ARM_R6`|Zarejestruj R6 na procesorze ARM.|  
|`REGISTER_ARM_R7`|Zarejestruj R7 (wskaźnik ramki KCIUKa) na procesorze ARM.|  
|`REGISTER_ARM_R8`|Zarejestruj R8 na procesorze ARM.|  
|`REGISTER_ARM_R9`|Zarejestruj R9 na procesorze ARM.|  
|`REGISTER_ARM_R10`|Zarejestruj R10 na procesorze ARM.|  
|`REGISTER_ARM_R11`|Wskaźnik ramki na procesorze ARM.|  
|`REGISTER_ARM_R12`|Zarejestruj R12 na procesorze ARM.|  
|`REGISTER_ARM_LR`|Rejestracja linku (R14) na procesorze ARM.|  
  
## <a name="remarks"></a>Uwagi  
 Istnieją 128 rejestrów danych ogólnego przeznaczenia i 128 rejestrów danych zmiennoprzecinkowych w procesorze IA-64, ale podano tylko wartości `REGISTER_IA64_R0` i `REGISTER_IA64_F0`. Inne wartości można określić w następujący sposób:  
  
- Dodaj numer rejestru do `REGISTER_IA64_R0` wartości `REGISTER_IA64_R1` za pomocą `REGISTER_IA64_R127`, który odpowiada #1 rejestru danych przez #127 rejestru danych w procesorze IA-64.  
  
- Dodaj numer rejestru do `REGISTER_IA64_F0` dla wartości `REGISTER_IA64_F1` za pomocą `REGISTER_IA64_F127`, który odpowiada rejestrowi danych z #1 FP za pomocą rejestru #127 FP w ramach procesora IA-64.  
  
 Na przykład, jeśli konieczne jest określenie #83 rejestru danych w procesorze IA-64, należy użyć `REGISTER_IA64_R0` + 83.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

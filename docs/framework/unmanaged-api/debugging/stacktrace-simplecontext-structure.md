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
ms.openlocfilehash: c81a5787eb06971e3d52aff5d1c1154a72564daf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790335"
---
# <a name="stacktrace_simplecontext-structure"></a>StackTrace_SimpleContext — Struktura
Udostępnia prosty kontekst, który może być używany zamiast pełnej struktury `CONTEXT`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`StackOffset`|Wskaźnik stosu lub wskaźnik wprowadzania stosu (ESP) na platformach x86.|  
|`FrameOffset`|Przesunięcie ramki lub rejestrowanie EBP na platformach x86.|  
|`InstructionOffset`|Wskaźnik instrukcji lub wskaźnik wprowadzania instrukcji (EIP) na platformach x86.|  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ funkcje śledzenia stosu zwykle muszą zwracać tylko adres, przesunięcie ramki i adres stosu, można opcjonalnie użyć struktury `SimpleContext` zamiast dużego `CONTEXT`j struktury.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** SOS_Stacktrace. h  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury debugowania](debugging-structures.md)
- [Debugowanie](index.md)

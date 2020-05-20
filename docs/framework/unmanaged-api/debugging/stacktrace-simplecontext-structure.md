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
ms.openlocfilehash: 45ae947cda5b4ddadfb10f5b2bdc78a95f031703
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420694"
---
# <a name="stacktrace_simplecontext-structure"></a>StackTrace_SimpleContext — Struktura
Udostępnia prosty kontekst, który może być używany zamiast pełnej `CONTEXT` struktury.  
  
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
  
|Członek|Opis|  
|------------|-----------------|  
|`StackOffset`|Wskaźnik stosu lub wskaźnik wprowadzania stosu (ESP) na platformach x86.|  
|`FrameOffset`|Przesunięcie ramki lub rejestrowanie EBP na platformach x86.|  
|`InstructionOffset`|Wskaźnik instrukcji lub wskaźnik wprowadzania instrukcji (EIP) na platformach x86.|  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ funkcje śledzenia stosu zwykle muszą zwracać tylko adres, przesunięcie ramki i adres stosu, można opcjonalnie użyć `SimpleContext` struktury zamiast dużej `CONTEXT` struktury.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** SOS_Stacktrace. h  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury debugowania](debugging-structures.md)
- [Debugowanie](index.md)

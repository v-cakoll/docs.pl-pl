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
ms.openlocfilehash: acf2ba752ace49ae288857dc22819a8e7e429a34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424056"
---
# <a name="stacktracesimplecontext-structure"></a>StackTrace_SimpleContext — Struktura
Udostępnia prosty kontekstu, którego można użyć zamiast pełnej `CONTEXT` struktury.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|`StackOffset`|Wskaźnik stosu lub wskaźnik stosu enter (ESP) na x86 platform.|  
|`FrameOffset`|Przesunięcie ramki lub rejestru EBP na x86 platform.|  
|`InstructionOffset`|Wskaźnik instrukcji lub wprowadź wskaźnika instrukcji (EIP) na x86 platform.|  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ funkcji śledzenia stosu zwykle musi zwracać tylko adres, przesunięcie ramki i adres stosu, można opcjonalnie użyć `SimpleContext` struktury zamiast dużej `CONTEXT` struktury.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** SOS_Stacktrace.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)

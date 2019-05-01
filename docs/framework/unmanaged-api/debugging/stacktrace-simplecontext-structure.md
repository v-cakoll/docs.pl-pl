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
# <a name="stacktracesimplecontext-structure"></a>StackTrace_SimpleContext — Struktura
Udostępnia prosty kontekst, który można użyć zamiast pełnego `CONTEXT` struktury.  
  
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
|`FrameOffset`|Przesunięcie ramki lub zarejestruj EBP na x86 platform.|  
|`InstructionOffset`|Wskaźnik instrukcji lub enter wskaźnik instrukcji (EIP) na x86 platform.|  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ funkcje śledzenia stosu zazwyczaj trzeba zwrócić tylko adres, przesunięcie ramki i adresu stosu, można opcjonalnie używać `SimpleContext` struktury zamiast dużą `CONTEXT` struktury.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** SOS_Stacktrace.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)

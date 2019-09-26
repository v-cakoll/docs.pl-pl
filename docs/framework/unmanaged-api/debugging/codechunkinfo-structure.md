---
title: CodeChunkInfo — Struktura
ms.date: 03/30/2017
api_name:
- CodeChunkInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CodeChunkInfo
helpviewer_keywords:
- CodeChunkInfo structure [.NET Framework debugging]
ms.assetid: 0f482454-8517-48de-ba7a-d7aedab13bb5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36afee8af3de046683c55215a677a529b0837c77
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274256"
---
# <a name="codechunkinfo-structure"></a>CodeChunkInfo — Struktura

Reprezentuje pojedynczy fragment kodu w pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`startAddr`|`CORDB_ADDRESS` Wartość określająca początkowy adres fragmentu.|  
|`length`|Rozmiar fragmentu, w bajtach.|  
  
## <a name="remarks"></a>Uwagi  
 Pojedynczy fragment kodu jest regionem kodu natywnego, który jest częścią obiektu kodu, takiego jak funkcja.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetCodeChunks, metoda](icordebugcode2-getcodechunks-method.md)
- [Struktury debugowania](debugging-structures.md)
- [Debugowanie](index.md)

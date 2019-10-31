---
title: ESymbolReadingPolicy — Wyliczenie
ms.date: 03/30/2017
api_name:
- ESymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ESymbolReadingPolicy
helpviewer_keywords:
- ESymbolReadingPolicy enumeration [.NET Framework hosting]
ms.assetid: 4dc6c80d-b694-480b-a378-d5b18420ce17
topic_type:
- apiref
ms.openlocfilehash: 786ff6895383fc18dcfedb26fab344f80f04c1df
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138205"
---
# <a name="esymbolreadingpolicy-enumeration"></a>ESymbolReadingPolicy — Wyliczenie
Zawiera wartości, które ustawiają zasady odczytujące pliki bazy danych (PDB) programu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`eSymbolReadingAlways`|Określa, że debuger powinien zawsze odczytywać pliki PDB.|  
|`eSymbolReadingFullTrustOnly`|Określa, że debuger powinien odczytać tylko pliki PDB, które są skojarzone z zestawami pełnego zaufania.|  
|`eSymbolReadingNever`|Określa, że debuger nie powinien odczytywać plików PDB.|  
  
## <a name="remarks"></a>Uwagi  
 Wyliczenie `ESymbolReadingPolicy` jest używane z metodą [ICLRDebugManager:: SetSymbolReadingPolicy —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

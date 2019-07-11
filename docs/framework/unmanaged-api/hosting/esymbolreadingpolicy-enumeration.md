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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45b6b8593331801dd237d0a730afbd5a6a714bbf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774183"
---
# <a name="esymbolreadingpolicy-enumeration"></a>ESymbolReadingPolicy — Wyliczenie
Zawiera wartości, które ustawić zasady do odczytywania plików bazy danych (PDB) programu.  
  
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
|`eSymbolReadingAlways`|Określa, że debuger zawsze powinni przeczytać pliki PDB.|  
|`eSymbolReadingFullTrustOnly`|Określa, czy debuger powinien pliki tylko do odczytu pliku PDB, które są skojarzone z zestawów pełnego zaufania.|  
|`eSymbolReadingNever`|Określa, że debuger nigdy nie powinni przeczytać pliki PDB.|  
  
## <a name="remarks"></a>Uwagi  
 `ESymbolReadingPolicy` Wyliczenie jest używane z [iclrdebugmanager::setsymbolreadingpolicy —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

---
title: CorDebugMDAFlags — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugMDAFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMDAFlags
helpviewer_keywords:
- CorDebugMDAFlags enumeration [.NET Framework debugging]
ms.assetid: 7c0c92fe-8bd2-477f-b307-aca0143732ca
topic_type:
- apiref
ms.openlocfilehash: 34a66a8afa118ecaaaeea0b7b78daaadf1da7509
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778263"
---
# <a name="cordebugmdaflags-enumeration"></a>CorDebugMDAFlags — Wyliczenie
Określa stan wątku, w którym jest uruchamiany Asystent debugowania zarządzanego (MDA).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|Wątek, w którym zostało wywołane zdarzenie MDA, został wywołany od momentu uruchomienia MDA.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy stos wywołań nie opisuje już, gdzie zdarzenie MDA zostało pierwotnie zgłoszone, wątek jest traktowany jako *poślizg*. Jest to nietypowe działanie związane z wykonywaniem przez wątek nieprawidłowej operacji przy zamykaniu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](debugging-enumerations.md)

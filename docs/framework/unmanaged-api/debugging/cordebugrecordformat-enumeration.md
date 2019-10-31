---
title: Wyliczenie CorDebugRecordFormat
ms.date: 03/30/2017
api_name:
- CorDebugRecordFormat
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: d680c1c0-16ab-4ccc-9444-39cf8e0e05ee
topic_type:
- apiref
ms.openlocfilehash: 239b1a9f258f435e6dcca6e00cc20df5b5c01188
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097453"
---
# <a name="cordebugrecordformat-enumeration"></a>Wyliczenie CorDebugRecordFormat
Opisuje format danych w tablicy bajtów, który zawiera informacje na temat natywnego zdarzenia debugowania wyjątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum CorDebugRecordFormat {  
    FORMAT_WINDOWS_EXCEPTIONRECORD32 = 1,  
    FORMAT_WINDOWS_EXCEPTIONRECORD64 = 2,  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD32`|Dane to 32-bitowy rekord wyjątku systemu Windows.|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD64`|Dane to 64-bitowy rekord wyjątku systemu Windows.|  
  
## <a name="remarks"></a>Uwagi  
 Element członkowski wyliczenia `CorDebugRecordFormat` jest przenoszona do metody [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) , aby wskazać format tablicy bajtowej w argumencie `pRecord`.  
  
> [!NOTE]
> To wyliczenie jest przeznaczone do użycia tylko w scenariuszach debugowania .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

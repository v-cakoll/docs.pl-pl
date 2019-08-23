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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e6ed7d25593f9dd5d5d01f8c06024dcf8acfcfea
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916473"
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
 Element członkowski `CorDebugRecordFormat` wyliczenia jest przesyłany do metody [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) w celu wskazania formatu tablicy `pRecord` bajtów w argumencie.  
  
> [!NOTE]
> To wyliczenie jest przeznaczone do użycia tylko w scenariuszach debugowania .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

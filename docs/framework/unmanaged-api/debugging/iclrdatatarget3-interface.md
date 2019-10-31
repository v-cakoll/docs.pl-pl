---
title: ICLRDataTarget3 — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRDataTarget3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: d2711bdf-64b3-404c-a0c3-01ba4907f703
topic_type:
- apiref
ms.openlocfilehash: a6591f7d7b632bcdbdabb1633f7431d79da7ff6e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111813"
---
# <a name="iclrdatatarget3-interface"></a>ICLRDataTarget3 — Interfejs
Podklasa elementu [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) , która zapewnia dostęp do informacji o wyjątku.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetExceptionRecord, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)|Wywoływana przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR) w celu pobrania rekordu wyjątku skojarzonego z procesem docelowym.|  
|[GetExceptionContextRecord, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)|Wywoływana przez usługi dostępu do danych CLR w celu pobrania rekordu kontekstu skojarzonego z procesem docelowym.|  
|[GetExceptionThreadID, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)|Wywoływane przez usługi dostępu do danych środowiska CLR w celu uzyskania identyfikatora wątku, który wywołał wyjątek.|  
  
## <a name="remarks"></a>Uwagi  
 Klient API (tzn. debuger) musi implementować ten interfejs stosownie do określonego procesu docelowego. Na przykład żywy proces miałby inną implementację od tej ze zrzutu pamięci. Cel może nie obsługiwać modyfikacji regionów pamięci.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData. idl, ClrData. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRDataTarget, interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
- [ICLRDataTarget2, interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

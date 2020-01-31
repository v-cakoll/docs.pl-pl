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
ms.openlocfilehash: f7635dc3fad9b3de30fa052c7d2e67a7e6953fb3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789045"
---
# <a name="iclrdatatarget3-interface"></a>ICLRDataTarget3 — Interfejs
Podklasa elementu [ICLRDataTarget2](iclrdatatarget2-interface.md) , która zapewnia dostęp do informacji o wyjątku.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetExceptionRecord, metoda](iclrdatatarget3-getexceptionrecord-method.md)|Wywoływana przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR) w celu pobrania rekordu wyjątku skojarzonego z procesem docelowym.|  
|[GetExceptionContextRecord, metoda](iclrdatatarget3-getexceptioncontextrecord-method.md)|Wywoływana przez usługi dostępu do danych CLR w celu pobrania rekordu kontekstu skojarzonego z procesem docelowym.|  
|[GetExceptionThreadID, metoda](iclrdatatarget3-getexceptionthreadid-method.md)|Wywoływane przez usługi dostępu do danych środowiska CLR w celu uzyskania identyfikatora wątku, który wywołał wyjątek.|  
  
## <a name="remarks"></a>Uwagi  
 Klient API (tzn. debuger) musi implementować ten interfejs stosownie do określonego procesu docelowego. Na przykład żywy proces miałby inną implementację od tej ze zrzutu pamięci. Cel może nie obsługiwać modyfikacji regionów pamięci.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData. idl, ClrData. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRDataTarget, interfejs](iclrdatatarget-interface.md)
- [ICLRDataTarget2, interfejs](iclrdatatarget2-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)

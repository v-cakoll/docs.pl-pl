---
title: ICLRDataTarget — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget
helpviewer_keywords:
- ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: e2f05155-9bef-4e11-b703-7f05890665ca
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ed3cb62b56e80a7fe4ea54b43ac9f4a28b8d102
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100252"
---
# <a name="iclrdatatarget-interface"></a>ICLRDataTarget — Interfejs
Zapewnia metody interakcji z elementem docelowym środowiska uruchomieniowego języka wspólnego (CLR).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetCurrentThreadID, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getcurrentthreadid-method.md)|Pobiera identyfikator systemu operacyjnego dla bieżącego wątku.|  
|[GetImageBase, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getimagebase-method.md)|Pobiera adres podstawowy pamięci dla określonego obrazu.|  
|[GetMachineType, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getmachinetype-method.md)|Pobiera identyfikator dla rodzaju — zestaw instrukcji używanej przez proces docelowy.|  
|[GetPointerSize, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getpointersize-method.md)|Pobiera rozmiar w bajtach, wskaźnik do bieżącego elementu docelowego.|  
|[GetThreadContext, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getthreadcontext-method.md)|Pobiera wskaźnik do kontekstu wątku z określonym identyfikatorem.|  
|[GetTLSValue, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-gettlsvalue-method.md)|Pobiera wartość w pamięci lokalnej wątku (TLS) dla podanego indeksu dla określonego wątku.|  
|[ReadVirtual, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-readvirtual-method.md)|Odczytuje dane z adresu określonego pamięci wirtualnej do określonego bufora.|  
|[Request, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-request-method.md)|Metoda wywoływana przez wspólnego języka wspólnego (CLR) usługi dostępu do danych do żądania operacji, zgodnie z definicją przez implementację.|  
|[SetThreadContext, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-setthreadcontext-method.md)|Ustawia bieżący kontekst określony wątek w procesie docelowym.|  
|[SetTLSValue, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-settlsvalue-method.md)|Ustawia wartość w pamięci lokalnej wątku (TLS) określony wątek w procesie docelowym.|  
|[WriteVirtual, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-writevirtual-method.md)|Zapisuje dane z określonego bufora do adresu określonego pamięci wirtualnej.|  
  
## <a name="remarks"></a>Uwagi  
 Klient interfejsu API (tzn debuger) musi implementować ten interfejs stosownie dla elementu określonego celu. Na przykład żywy proces miałby inną implementację od tej ze zrzutu pamięci.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData.idl, ClrData.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRDataTarget2 — Interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [Debugowanie — Interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

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
ms.openlocfilehash: 51b246e45b8bbdf809f5e90ac2bc29ca724751fc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73113489"
---
# <a name="iclrdatatarget-interface"></a>ICLRDataTarget — Interfejs
Zapewnia metody interakcji z elementem docelowym środowiska uruchomieniowego języka wspólnego (CLR).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetCurrentThreadID, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getcurrentthreadid-method.md)|Pobiera identyfikator systemu operacyjnego dla bieżącego wątku.|  
|[GetImageBase, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getimagebase-method.md)|Pobiera adres pamięci bazowej dla określonego obrazu.|  
|[GetMachineType, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getmachinetype-method.md)|Pobiera identyfikator rodzaju instrukcji, która jest używana przez proces docelowy.|  
|[GetPointerSize, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getpointersize-method.md)|Pobiera rozmiar wskaźnika do bieżącego elementu docelowego w bajtach.|  
|[GetThreadContext, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getthreadcontext-method.md)|Pobiera wskaźnik do kontekstu wątku o określonym identyfikatorze.|  
|[GetTLSValue, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-gettlsvalue-method.md)|Pobiera wartość w magazynie lokalnym wątku (TLS) o określonym indeksie dla określonego wątku.|  
|[ReadVirtual, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-readvirtual-method.md)|Odczytuje dane z określonego adresu pamięci wirtualnej do określonego buforu.|  
|[Request, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-request-method.md)|Wywoływane przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR) do żądania operacji zgodnie z definicją w implementacji.|  
|[SetThreadContext, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-setthreadcontext-method.md)|Ustawia bieżący kontekst określonego wątku w procesie docelowym.|  
|[SetTLSValue, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-settlsvalue-method.md)|Ustawia wartość w ramach wątku lokalnego magazynu (TLS) określonego wątku w procesie docelowym.|  
|[WriteVirtual, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-writevirtual-method.md)|Zapisuje dane z określonego buforu na określonym adresie pamięci wirtualnej.|  
  
## <a name="remarks"></a>Uwagi  
 Klient interfejsu API (czyli debuger) musi zaimplementować ten interfejs zgodnie z potrzebami dla określonego elementu docelowego. Na przykład żywy proces miałby inną implementację od tej ze zrzutu pamięci.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData. idl, ClrData. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRDataTarget2, interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

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
ms.openlocfilehash: b0a5abe8877c8414443fadc00e223df240721132
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33410445"
---
# <a name="iclrdatatarget-interface"></a>ICLRDataTarget — Interfejs
Udostępnia metody do interakcji z elementem docelowym o środowisko uruchomieniowe języka wspólnego (CLR).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetCurrentThreadID, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getcurrentthreadid-method.md)|Pobiera identyfikator systemu operacyjnego dla bieżącego wątku.|  
|[GetImageBase, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getimagebase-method.md)|Pobiera adres podstawowy pamięci dla określonego obrazu.|  
|[GetMachineType, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getmachinetype-method.md)|Pobiera identyfikator dla rodzaju zestaw instrukcji, który używa procesu docelowego.|  
|[GetPointerSize, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getpointersize-method.md)|Pobiera rozmiar w bajtach wskaźnik do bieżącą lokalizację docelową.|  
|[GetThreadContext, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getthreadcontext-method.md)|Pobiera wskaźnik w kontekście wątku o podanym identyfikatorze.|  
|[GetTLSValue, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-gettlsvalue-method.md)|Pobiera wartość w lokalny magazyn wątków (TLS) w określonym indeksie dla określonego wątku.|  
|[ReadVirtual, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-readvirtual-method.md)|Odczytuje dane z adresów pamięci wirtualnej określony w buforze określona.|  
|[Request, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-request-method.md)|Metoda wywoływana przez wspólne języka wspólnego (CLR) danych dostęp do usługi do żądania operacji zdefiniowanej przez implementację.|  
|[SetThreadContext, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-setthreadcontext-method.md)|Ustawia bieżący kontekst określonego wątku w procesie docelowym.|  
|[SetTLSValue, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-settlsvalue-method.md)|Ustawia wartość w lokalny magazyn wątków (TLS) z określonego wątku w procesie docelowym.|  
|[WriteVirtual, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-writevirtual-method.md)|Zapisuje dane z określonego bufora na adres określony pamięci wirtualnej.|  
  
## <a name="remarks"></a>Uwagi  
 Klienta interfejsu API (debuger) musi implementować ten interfejs na potrzeby elementu określonego elementu docelowego. Na przykład żywy proces miałby inną implementację od tej ze zrzutu pamięci.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData.idl, ClrData.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRDataTarget2, interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

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
ms.openlocfilehash: 30806394a8895084068acaec6f7d03c6b67bb14b
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860567"
---
# <a name="iclrdatatarget-interface"></a>ICLRDataTarget — Interfejs
Zapewnia metody interakcji z elementem docelowym środowiska uruchomieniowego języka wspólnego (CLR).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetCurrentThreadID — Metoda](iclrdatatarget-getcurrentthreadid-method.md)|Pobiera identyfikator systemu operacyjnego dla bieżącego wątku.|  
|[GetImageBase, metoda](iclrdatatarget-getimagebase-method.md)|Pobiera adres pamięci bazowej dla określonego obrazu.|  
|[GetMachineType, metoda](iclrdatatarget-getmachinetype-method.md)|Pobiera identyfikator rodzaju instrukcji, która jest używana przez proces docelowy.|  
|[GetPointerSize, metoda](iclrdatatarget-getpointersize-method.md)|Pobiera rozmiar wskaźnika do bieżącego elementu docelowego w bajtach.|  
|[GetThreadContext — Metoda](iclrdatatarget-getthreadcontext-method.md)|Pobiera wskaźnik do kontekstu wątku o określonym identyfikatorze.|  
|[GetTLSValue, metoda](iclrdatatarget-gettlsvalue-method.md)|Pobiera wartość w magazynie lokalnym wątku (TLS) o określonym indeksie dla określonego wątku.|  
|[ReadVirtual, metoda](iclrdatatarget-readvirtual-method.md)|Odczytuje dane z określonego adresu pamięci wirtualnej do określonego buforu.|  
|[Request, metoda](iclrdatatarget-request-method.md)|Wywoływane przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR) do żądania operacji zgodnie z definicją w implementacji.|  
|[SetThreadContext, metoda](iclrdatatarget-setthreadcontext-method.md)|Ustawia bieżący kontekst określonego wątku w procesie docelowym.|  
|[SetTLSValue, metoda](iclrdatatarget-settlsvalue-method.md)|Ustawia wartość w ramach wątku lokalnego magazynu (TLS) określonego wątku w procesie docelowym.|  
|[WriteVirtual, metoda](iclrdatatarget-writevirtual-method.md)|Zapisuje dane z określonego buforu na określonym adresie pamięci wirtualnej.|  
  
## <a name="remarks"></a>Uwagi  
 Klient interfejsu API (czyli debuger) musi zaimplementować ten interfejs zgodnie z potrzebami dla określonego elementu docelowego. Na przykład żywy proces miałby inną implementację od tej ze zrzutu pamięci.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData. idl, ClrData. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICLRDataTarget2 — Interfejs](iclrdatatarget2-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)

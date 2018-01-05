---
title: Metoda ICLRDataTarget3::GetExceptionContextRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICLRDataTarget3.GetContextRecord
api_location: mscordbi.dll
api_type: COM
ms.assetid: 66076ed5-f05c-4114-9788-94cb143abb8a
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 517e2a692c3b67a85bc24437dd5fbaedd5fc7254
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a>Metoda ICLRDataTarget3::GetExceptionContextRecord
Metoda wywoływana przez wspólne języka wspólnego (CLR) danych dostęp do usługi można pobrać rekordu kontekstu skojarzonych z procesem docelowym. Na przykład dla elementu docelowego zrzutu to równoważne rekordu kontekstu przekazano za pośrednictwem `ExceptionParam` argument [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360\(v=vs.85\).aspx) funkcji w bibliotece systemu Windows debugowania pomocy (DbgHelp).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bufferSize`  
 [in] Rozmiar buforu wejściowego w bajtach. Musi to być wystarczająco duży, aby pomieścić rekordu kontekstu.  
  
 `bufferUsed`  
 [out] Wskaźnik do `ULONG32` typu, który odbiera liczba bajtów zapisana w buforze.  
  
 `buffer`  
 [out] Wskaźnik do buforu pamięci, który otrzyma kopię rekordu kontekstu. Rekordu wyjątku jest zwracana jako [KONTEKSTU](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) typu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość zwracana jest `S_OK` na powodzenie lub niepowodzenie `HRESULT` kod błędu. `HRESULT` Mogą obejmować kody, ale nie są ograniczone do następujących:  
  
|Kod powrotu|Opis|  
|-----------------|-----------------|  
|`S_OK`|Metoda zakończyło się pomyślnie. Rekordu kontekstu został skopiowany do buforu wyjściowego.|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|Nie rekordu kontekstu jest skojarzony z elementem docelowym.|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|Rozmiar buforu wejściowego nie jest wystarczająco duży, aby pomieścić rekordu kontekstu.|  
  
## <a name="remarks"></a>Uwagi  
 [KONTEKST](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) jest strukturą specyficzne dla platformy zdefiniowane w nagłówki udostępnione przez zestaw Windows SDK.  
  
 Ta metoda jest implementowany przez twórcę debugowania aplikacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData.idl, ClrData.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRDataTarget3, interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [GetExceptionRecord, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)  
 [GetExceptionThreadID, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)

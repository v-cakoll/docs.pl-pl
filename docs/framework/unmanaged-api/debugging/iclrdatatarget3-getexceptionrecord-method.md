---
title: "ICLRDataTarget3::GetExceptionRecord — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICLRDataTarget3.GetExceptionRecord
api_location: mscordbi.dll
api_type: COM
ms.assetid: 6643c2af-2ee6-4789-aa25-1d8eaf500c94
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f8c9ac4ecc0cffda4038129b1244b81501e9a1f7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a>ICLRDataTarget3::GetExceptionRecord — Metoda
Wywoływana przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR) w celu pobrania rekordu wyjątku skojarzonego z procesem docelowym. Na przykład dla elementu docelowego zrzutu to równoważne rekordu wyjątku przekazano za pośrednictwem `ExceptionParam` argument [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360.aspx) funkcji w bibliotece systemu Windows debugowania pomocy (DbgHelp).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetExceptionRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize] BYTE* buffer  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bufferSize`  
 [in] Rozmiar buforu wejściowego w bajtach. To musi być równa `sizeof(` [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx)`)`.  
  
 `bufferUsed`  
 [out] Wskaźnik do `ULONG32` typu, który odbiera liczba bajtów zapisana w buforze.  
  
 `buffer`  
 [out] Wskaźnik do buforu pamięci, który otrzyma kopię rekordu wyjątku. Rekordu wyjątku jest zwracana jako [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx) typu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość zwracana jest `S_OK` na powodzenie lub niepowodzenie `HRESULT` kod błędu. `HRESULT` Mogą obejmować kody, ale nie są ograniczone do następujących:  
  
|Kod powrotu|Opis|  
|-----------------|-----------------|  
|`S_OK`|Metoda zakończyło się pomyślnie. Rekord wyjątek został skopiowany do buforu wyjściowego.|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|Nie rekordu wyjątku jest skojarzony z elementem docelowym.|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|Rozmiar buforu wejściowego nie jest równa `sizeof(MINIDUMP_EXCEPTION)`.|  
  
## <a name="remarks"></a>Uwagi  
 [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx) jest strukturą zdefiniowany w dbghelp.h i imagehlp.h w zestawie Windows SDK.  
  
 Ta metoda jest implementowany przez twórcę debugowania aplikacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData.idl, ClrData.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Iclrdatatarget3 — interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [Metoda GetExceptionContextRecord](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)  
 [Metoda GetExceptionThreadID](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)

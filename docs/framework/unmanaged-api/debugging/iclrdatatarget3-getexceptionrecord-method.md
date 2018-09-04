---
title: ICLRDataTarget3::GetExceptionRecord — Metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetExceptionRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6643c2af-2ee6-4789-aa25-1d8eaf500c94
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a43863477e902f6f02007ba291a25d2469283e91
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525633"
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a>ICLRDataTarget3::GetExceptionRecord — Metoda
Wywoływana przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR) w celu pobrania rekordu wyjątku skojarzonego z procesem docelowym. Na przykład dla elementu docelowego zrzutu jest to równoważne z rekordu wyjątku przekazaną za pomocą `ExceptionParam` argument [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) funkcji w Windows debugowania pomóc w bibliotece (DbgHelp).  
  
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
 [in] Rozmiar buforu wejściowego w bajtach. To musi być równa `sizeof(` [MINIDUMP_EXCEPTION](/windows/desktop/api/minidumpapiset/ns-minidumpapiset-_minidump_exception)`)`.  
  
 `bufferUsed`  
 [out] Wskaźnik do `ULONG32` typu, który odbiera liczbę bajtów, które rzeczywiście zapisanych w buforze.  
  
 `buffer`  
 [out] Wskaźnik do buforu pamięci, który otrzymuje kopię rekordu wyjątku. Rekordu wyjątku jest zwracana jako [MINIDUMP_EXCEPTION](/windows/desktop/api/minidumpapiset/ns-minidumpapiset-_minidump_exception) typu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość zwracana jest `S_OK` na powodzenie lub niepowodzenie `HRESULT` kod błędu. `HRESULT` Mogą obejmować kody, ale nie są ograniczone do następujących:  
  
|Kod powrotu|Opis|  
|-----------------|-----------------|  
|`S_OK`|Metody powiodło się. Rekordu wyjątku został skopiowany do buforu danych wyjściowych.|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|Nie rekordu wyjątku jest skojarzony z obiektem docelowym.|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|Rozmiar buforu wejściowego nie jest równa `sizeof(MINIDUMP_EXCEPTION)`.|  
  
## <a name="remarks"></a>Uwagi  
 [MINIDUMP_EXCEPTION](/windows/desktop/api/minidumpapiset/ns-minidumpapiset-_minidump_exception) jest strukturą, który został zdefiniowany w dbghelp.h i imagehlp.h w zestawie Windows SDK.  
  
 Ta metoda jest implementowana przez moduł zapisujący debugowania aplikacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData.idl, ClrData.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRDataTarget3, interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [GetExceptionContextRecord, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)  
 [GetExceptionThreadID, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)

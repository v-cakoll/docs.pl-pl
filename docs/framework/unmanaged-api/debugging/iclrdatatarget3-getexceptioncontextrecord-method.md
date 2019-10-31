---
title: Metoda ICLRDataTarget3::GetExceptionContextRecord
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetContextRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 66076ed5-f05c-4114-9788-94cb143abb8a
topic_type:
- apiref
ms.openlocfilehash: 5a090b7c4801e6b2baf56f1d80e7e52f2aaa9293
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73112303"
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a>Metoda ICLRDataTarget3::GetExceptionContextRecord
Wywoływane przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR) do pobierania rekordu kontekstu skojarzonego z procesem docelowym. Na przykład dla elementu docelowego zrzutu będzie to odpowiednik rekordu kontekstu przekazanego za pośrednictwem argumentu `ExceptionParam` do funkcji [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) w bibliotece pomocy debugowania systemu Windows (dbghelp).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `bufferSize`  
 podczas Rozmiar buforu wejściowego w bajtach. Musi być wystarczająco duży, aby pomieścić rekord kontekstu.  
  
 `bufferUsed`  
 określoną Wskaźnik do typu `ULONG32`, który odbiera liczbę bajtów rzeczywiście zapisywanych w buforze.  
  
 `buffer`  
 określoną Wskaźnik do bufora pamięci, który otrzymuje kopię rekordu kontekstu. Rekord wyjątku jest zwracany jako typ [kontekstu](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) .  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość zwracana jest `S_OK` w przypadku sukcesu lub niepowodzenie `HRESULT` kod w przypadku niepowodzenia. Kody `HRESULT` mogą zawierać, ale nie są ograniczone do następujących:  
  
|Kod powrotu|Opis|  
|-----------------|-----------------|  
|`S_OK`|Metoda powiodła się. Rekord kontekstu został skopiowany do buforu wyjściowego.|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|Żaden rekord kontekstu nie jest skojarzony z elementem docelowym.|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|Rozmiar buforu wejściowego nie jest wystarczająco duży, aby pomieścić rekord kontekstu.|  
  
## <a name="remarks"></a>Uwagi  
 [Kontekst](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) jest strukturą specyficzną dla platformy zdefiniowaną w nagłówkach dostarczonych przez Windows SDK.  
  
 Ta metoda jest implementowana przez moduł zapisujący aplikacji debugowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData. idl, ClrData. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRDataTarget3, interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)
- [GetExceptionRecord, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)
- [GetExceptionThreadID, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)

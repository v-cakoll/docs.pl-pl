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
ms.openlocfilehash: aed301fa136ff3d45269c82b46e4cad699074874
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785240"
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
  
## <a name="return-value"></a>Wartość zwrócona  
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

- [ICLRDataTarget3, interfejs](iclrdatatarget3-interface.md)
- [GetExceptionRecord, metoda](iclrdatatarget3-getexceptionrecord-method.md)
- [GetExceptionThreadID, metoda](iclrdatatarget3-getexceptionthreadid-method.md)

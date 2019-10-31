---
title: Metoda ICLRDataTarget3::GetExceptionThreadID
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetExceptionThreadID
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 307d6ac7-4a86-45f3-999d-6b47004a68f2
topic_type:
- apiref
ms.openlocfilehash: 5e7fd2f277a9c3d8410020a53d348456ef9deffb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111905"
---
# <a name="iclrdatatarget3getexceptionthreadid-method"></a>Metoda ICLRDataTarget3::GetExceptionThreadID
Wywoływane przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR), aby uzyskać identyfikator wątku, który wywołał wyjątek.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetExceptionThreadID(  
    [out] ULONG32* threadID  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `threadID`  
 określoną Identyfikator wątku, który wywołał wyjątek.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość zwracana jest `S_OK` w przypadku sukcesu lub niepowodzenie `HRESULT` kod w przypadku niepowodzenia. Kody `HRESULT` mogą zawierać, ale nie są ograniczone do następujących:  
  
|Kod powrotu|Opis|  
|-----------------|-----------------|  
|`S_OK`|Metoda powiodła się.|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|Nie można znaleźć prawidłowego identyfikatora wątku dla wyjątku.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest implementowana przez moduł zapisujący aplikacji debugowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData. idl, ClrData. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRDataTarget3, interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)
- [GetExceptionContextRecord, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)
- [GetExceptionRecord, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)

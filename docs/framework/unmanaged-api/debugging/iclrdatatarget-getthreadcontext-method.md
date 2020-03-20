---
title: ICLRDataTarget::GetThreadContext — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetThreadContext
helpviewer_keywords:
- ICLRDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: b9d8c3b5-3a2e-4225-95d4-dd052c4532c3
topic_type:
- apiref
ms.openlocfilehash: 3777ad4b12c7d0593c095c470aba81088137a859
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179178"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a>ICLRDataTarget::GetThreadContext — Metoda
Pobiera bieżącego kontekstu wykonywania dla danego wątku w procesie docelowym. Ta metoda jest wywoływana przez usługi dostępu do danych środowiska wykonawczego języka wspólnego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `threadID`  
 [w] Identyfikator systemu operacyjnego wątku w procesie docelowym.  
  
 `contextFlags`  
 [w] Flagi, które określają, które części kontekstu do zwrócenia. Wdrożenie zwróci co najmniej te części kontekstu.  
  
 `contextSize`  
 [w] Rozmiar kontekstu.  
  
 `context`  
 [na zewnątrz] Wskaźnik do buforu, w którym można umieścić kontekst.  
  
 Dane w `context` buforze muszą być w formacie `CONTEXT` struktury Win32. Kontekst określa dane rejestru specyficzne dla procesora, więc `CONTEXT` definicja struktury Win32 zależy od architektury procesora. Definicję struktury Win32 `CONTEXT` można znaleźć w pliku nagłówka WinNT.h.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest implementowana przez moduł zapisujący aplikacji debugowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData.idl, ClrData.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICLRDataTarget, interfejs](iclrdatatarget-interface.md)

---
title: ICLRDataTarget::SetThreadContext — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::SetThreadContext
helpviewer_keywords:
- SetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::SetThreadContext method [.NET Framework debugging]
ms.assetid: 103c8502-81fe-40d7-9c1e-9008d8fb19e1
topic_type:
- apiref
ms.openlocfilehash: d76a907434b12b85aaedeef169390ec6f0df724a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179129"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a>ICLRDataTarget::SetThreadContext — Metoda
Ustawia bieżący kontekst określonego wątku w procesie docelowym. Ta metoda jest wywoływana przez usługi dostępu do danych wspólnego środowiska wykonawczego języka (CLR).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]
         BYTE               *context  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `threadID`  
 [w] Identyfikator systemu operacyjnego wątku w procesie docelowym.  
  
 `contextSize`  
 [w] Rozmiar kontekstu.  
  
 `context`  
 [w] Wskaźnik do buforu zawierającego kontekst.  
  
 Dane w `context` buforze będą w formacie struktury `CONTEXT` Win32. Kontekst określa dane rejestru specyficzne dla procesora, więc `CONTEXT` definicja struktury Win32 zależy od architektury procesora. Definicję struktury Win32 `CONTEXT` można znaleźć w pliku nagłówka WinNT.h.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest implementowana przez moduł zapisujący aplikacji debugowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData.idl, ClrData.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICLRDataTarget, interfejs](iclrdatatarget-interface.md)

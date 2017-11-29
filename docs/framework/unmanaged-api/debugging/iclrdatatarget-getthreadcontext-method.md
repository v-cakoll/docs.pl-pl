---
title: "ICLRDataTarget::GetThreadContext — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.GetThreadContext
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::GetThreadContext
helpviewer_keywords:
- ICLRDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: b9d8c3b5-3a2e-4225-95d4-dd052c4532c3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 480b65b279dbc0359b078f3f1d543f63a0bfd0f6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdatatargetgetthreadcontext-method"></a>ICLRDataTarget::GetThreadContext — Metoda
Pobiera bieżącego kontekstu wykonywania dla danego wątku w procesie docelowym. Ta metoda jest wywoływana przez usługi dostępu danych środowiska uruchomieniowego języka wspólnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]   
        BYTE                *context  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `threadID`  
 [in] System operacyjny identyfikator wątku w procesie docelowym.  
  
 `contextFlags`  
 [in] Flagi określające, które części kontekstu do zwrócenia. Implementacja zwróci co najmniej tych elementów kontekstu.  
  
 `contextSize`  
 [in] Rozmiar kontekstu.  
  
 `context`  
 [out] Wskaźnik do buforu, w której ma zostać umieszczony w kontekście.  
  
 Dane w `context` buforu musi być w formacie Win32 `CONTEXT` struktury. Kontekst określa dane rejestru specyficznych dla procesora, więc definicji Win32 `CONTEXT` struktury jest zależna od architektury procesora. Zajrzyj do pliku nagłówka pliku WinNT.h definicji Win32 `CONTEXT` struktury.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest implementowany przez twórcę debugowania aplikacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData.idl, ClrData.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRDataTarget — interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)

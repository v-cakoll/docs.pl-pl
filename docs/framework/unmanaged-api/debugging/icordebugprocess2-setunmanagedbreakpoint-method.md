---
title: ICorDebugProcess2::SetUnmanagedBreakpoint — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint
helpviewer_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint method [.NET Framework debugging]
- SetUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 93829d15-d942-4e2d-b7a4-dfc9d7fb96be
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b374720bd7bdad48222da006b809702de6462a62
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472788"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a>ICorDebugProcess2::SetUnmanagedBreakpoint — Metoda
Ustawia niezarządzany punkt przerwania w przesunięciu określonego obrazu natywnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]   
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `address`  
 [in] A `CORDB_ADDRESS` obiekt, który określa przesunięcie obrazu natywnego.  
  
 `bufsize`  
 [in] Rozmiar w bajtach z `buffer` tablicy.  
  
 `buffer`  
 [out] Tablica, która zawiera kod operacji, który jest zastępowany przez punkt przerwania.  
  
 `bufLen`  
 [out] Wskaźnik do liczby bajtów zwróconych w `buffer` tablicy.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli przesunięcie obrazów natywnych w środowisko uruchomieniowe języka wspólnego (CLR), punkt przerwania zostanie zignorowany. Dzięki temu środowisko CLR uniknąć przerwania out-of-band wysyłki, gdy punkt przerwania jest ustawiony przez debuger.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

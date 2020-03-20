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
ms.openlocfilehash: fb8b8f3e29c141e91587a4d0cdc81cdabccdbc9e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178650"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a>ICorDebugProcess2::SetUnmanagedBreakpoint — Metoda
Ustawia niezarządzany punkt przerwania przy określonym przesunięciu obrazu macierzystego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
 [w] Obiekt `CORDB_ADDRESS` określający przesunięcie obrazu macierzystego.  
  
 `bufsize`  
 [w] Rozmiar tablicy w bajtach. `buffer`  
  
 `buffer`  
 [na zewnątrz] Tablica zawierająca opcode, który jest zastępowany przez punkt przerwania.  
  
 `bufLen`  
 [na zewnątrz] Wskaźnik do liczby bajtów zwróconych w tablicy. `buffer`  
  
## <a name="remarks"></a>Uwagi  
 Jeśli przesunięcie obrazu macierzystego znajduje się w środowisku uruchomieniowym języka wspólnego (CLR), punkt przerwania zostanie zignorowany. Dzięki temu CLR uniknąć wysyłania pozapasmowego punktu przerwania, gdy punkt przerwania jest ustawiany przez debugera.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

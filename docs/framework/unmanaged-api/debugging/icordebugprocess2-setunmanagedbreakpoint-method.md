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
ms.openlocfilehash: 6b9396d03892f29e3698af90856d0c0023dc628a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213468"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a>ICorDebugProcess2::SetUnmanagedBreakpoint — Metoda
Ustawia niezarządzany punkt przerwania w określonym przesunięciu obrazu natywnego.  
  
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
 podczas `CORDB_ADDRESS`Obiekt, który określa przesunięcie obrazu natywnego.  
  
 `bufsize`  
 podczas Rozmiar tablicy w bajtach `buffer` .  
  
 `buffer`  
 określoną Tablica zawierająca kod operacji, który jest zastępowany przez punkt przerwania.  
  
 `bufLen`  
 określoną Wskaźnik do liczby bajtów zwróconych w `buffer` tablicy.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli przesunięcie obrazu natywnego znajduje się w środowisku uruchomieniowym języka wspólnego (CLR), punkt przerwania zostanie zignorowany. Pozwala to na uniknięcie wysyłania przez środowisko uruchomieniowe punktu przerwania poza pasmem, gdy punkt przerwania jest ustawiony przez debuger.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

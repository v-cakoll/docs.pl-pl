---
title: ICorDebugProcess::ReadMemory — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ReadMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ReadMemory
helpviewer_keywords:
- ReadMemory method [.NET Framework debugging]
- ICorDebugProcess::ReadMemory method [.NET Framework debugging]
ms.assetid: 28e4b2f6-9589-445c-be24-24a3306795e7
topic_type:
- apiref
ms.openlocfilehash: 383e3f8990a1f355c94ff5e9f9daa69bdbdd97bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178661"
---
# <a name="icordebugprocessreadmemory-method"></a>ICorDebugProcess::ReadMemory — Metoda
Odczytuje określony obszar pamięci dla tego procesu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
## <a name="parameters"></a>Parametry  
 `address`  
 [w] Wartość `CORDB_ADDRESS` określająca adres podstawowy pamięci do odczytu.  
  
 `size`  
 [w] Liczba bajtów do odczytania z pamięci.  
  
 `buffer`  
 [na zewnątrz] Bufor, który odbiera zawartość pamięci.  
  
 `read`  
 [na zewnątrz] Wskaźnik do liczby bajtów przeniesionych do określonego buforu.  
  
## <a name="remarks"></a>Uwagi  
 Metoda `ReadMemory` jest przeznaczona głównie do użycia przez debugowanie międzyoperacyjne do inspekcji regionów pamięci, które są używane przez niezarządzaną część debuggee. Ta metoda może również służyć do odczytywania kodu języka pośredniego firmy Microsoft (MSIL) i natywnego kodu skompilowanego przez JIT.  
  
 Wszystkie zarządzane punkty przerwania zostaną usunięte z danych, które są zwracane w parametrze. `buffer` Nie zostaną wprowadzone żadne zmiany dla natywnych punktów przerwania ustawionych przez [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md).  
  
 Nie jest wykonywane buforowanie pamięci procesowej.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

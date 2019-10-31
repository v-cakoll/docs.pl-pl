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
ms.openlocfilehash: ef9e339c74b2d2785d758ed9c4adfc1901073253
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139360"
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
 podczas Wartość `CORDB_ADDRESS`, która określa podstawowy adres pamięci, która ma zostać odczytana.  
  
 `size`  
 podczas Liczba bajtów do odczytu z pamięci.  
  
 `buffer`  
 określoną Bufor, który odbiera zawartość pamięci.  
  
 `read`  
 określoną Wskaźnik do liczby bajtów transferowanych do określonego buforu.  
  
## <a name="remarks"></a>Uwagi  
 Metoda `ReadMemory` jest przeznaczona głównie do użycia przez debugowanie międzyoperacyjną do inspekcji regionów pamięci, które są używane przez niezarządzaną część debugowanego obiektu. Ta metoda może być również używana do odczytywania kodu języka pośredniego firmy Microsoft (MSIL) i natywnego kodu skompilowanego JIT.  
  
 Wszystkie zarządzane punkty przerwania zostaną usunięte z danych, które są zwracane w parametrze `buffer`. Nie będą wprowadzane żadne korekty dla natywnych punktów przerwania ustawionych przez [ICorDebugProcess2:: SetUnmanagedBreakpoint —](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).  
  
 Nie jest wykonywane buforowanie pamięci procesu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

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
ms.openlocfilehash: dca2a4e5ee869346108137a8ba01ab8855756725
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792558"
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
  
 Wszystkie zarządzane punkty przerwania zostaną usunięte z danych, które są zwracane w parametrze `buffer`. Nie będą wprowadzane żadne korekty dla natywnych punktów przerwania ustawionych przez [ICorDebugProcess2:: SetUnmanagedBreakpoint —](icordebugprocess2-setunmanagedbreakpoint-method.md).  
  
 Nie jest wykonywane buforowanie pamięci procesu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 218279684304b766a9bf009f5891ac4910254a3c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994386"
---
# <a name="icordebugprocessreadmemory-method"></a>ICorDebugProcess::ReadMemory — Metoda
Odczytuje określony obszar pamięci dla tego procesu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,   
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
## <a name="parameters"></a>Parametry  
 `address`  
 [in] A `CORDB_ADDRESS` wartość, która określa adres bazowy pamięci do odczytu.  
  
 `size`  
 [in] Liczba bajtów, które mają zostać odczytana z pamięci.  
  
 `buffer`  
 [out] Bufor, który odbiera zawartość pamięci.  
  
 `read`  
 [out] Wskaźnik do liczby bajtów przesłanych do określonego bufora.  
  
## <a name="remarks"></a>Uwagi  
 `ReadMemory` Metoda jest przeznaczona głównie do użycia przez debugowania międzyoperacyjnego, aby sprawdzić regiony pamięci, które są używane przez niezarządzane część debugowany program. Tę metodę można również odczytywać kod intermediate language (MSIL) firmy Microsoft i natywnego kodu kompilowanego dokładnie na czas.  
  
 Wszelkie zarządzane punkty przerwania zostaną usunięte z danych, które są zwracane w `buffer` parametru. Nie zmiany zostaną wprowadzone dla natywnych punkty przerwania ustawione [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).  
  
 Brak buforowania pamięci procesu jest wykonywane.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

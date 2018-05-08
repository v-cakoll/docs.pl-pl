---
title: ICorDebugProcess::WriteMemory — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.WriteMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::WriteMemory
helpviewer_keywords:
- ICorDebugProcess::WriteMemory method [.NET Framework debugging]
- WriteMemory method [.NET Framework debugging]
ms.assetid: d5c07d86-045d-4391-893b-0bcd2959f90e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6da4c282c7f969a406a657d1e30dd6120a32b4e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocesswritememory-method"></a>ICorDebugProcess::WriteMemory — Metoda
Zapisuje dane do to obszar pamięci w tym procesie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 [in] A `CORDB_ADDRESS` wartość, która jest adresem podstawowym obszaru pamięci dane są zapisywane. Przed wystąpieniem transferu danych, system sprawdza, czy obszar pamięci o określonym rozmiarze, rozpoczynając od adres podstawowy jest dostępny do zapisu. Jeśli nie jest dostępny, metoda kończy się niepowodzeniem.  
  
 `size`  
 [in] Liczba bajtów do zapisania w obszarze pamięci.  
  
 `buffer`  
 [in] Buforu, który zawiera dane do zapisania.  
  
 `written`  
 [out] Wskaźnik do zmiennej, która odbiera liczba bajtów zapisanych do obszaru pamięci w tym procesie. Jeśli `written` ma wartość NULL, ten parametr jest ignorowany.  
  
## <a name="remarks"></a>Uwagi  
 Dane są automatycznie zapisywane za wszystkie punkty przerwania. W programie .NET Framework w wersji 2.0 natywnego debugery nie należy używać tej metody można wstawić punktów przerwania do strumienia instrukcji. Użyj [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) zamiast tego.  
  
 `WriteMemory` Metoda powinna być używana tylko poza kodu zarządzanego. Ta metoda może uszkodzić środowiska uruchomieniowego, użycie nieprawidłowo.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

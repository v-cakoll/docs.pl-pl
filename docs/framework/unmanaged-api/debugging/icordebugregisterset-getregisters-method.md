---
title: ICorDebugRegisterSet::GetRegisters — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type:
- apiref
ms.openlocfilehash: 32e899622b9c649a08e3bca1b6645f70dcbcbb19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178543"
---
# <a name="icordebugregistersetgetregisters-method"></a>ICorDebugRegisterSet::GetRegisters — Metoda
Pobiera wartość każdego rejestru (na komputerze, który jest aktualnie wykonywany kod), który jest określony przez maskę bitową.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG64       mask,
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `mask`  
 [w] Maska bitowa określająca, które wartości rejestru mają zostać pobrane. Każdy bit odpowiada rejestrowi. Jeśli bit jest ustawiony na jeden, wartość rejestru jest pobierana; w przeciwnym razie wartość rejestru nie jest pobierana.  
  
 `regCount`  
 [w] Liczba wartości rejestru do pobrania.  
  
 `regBuffer`  
 [na zewnątrz] Tablica `CORDB_REGISTER` obiektów, z których każdy otrzymuje wartość rejestru.  
  
## <a name="remarks"></a>Uwagi  
 Rozmiar tablicy powinien być równy liczbie bitów ustawionych na jeden w masce bitowej. Parametr `regCount` określa liczbę elementów w buforze, które otrzymają wartości rejestru. Jeśli `regCount` wartość jest zbyt mała dla liczby rejestrów wskazanych przez maskę, wyższe numerowane rejestry zostaną obcięty z zestawu. Jeśli `regCount` wartość jest zbyt duża, `regBuffer` nieużywane elementy będą niezmodyfikowane.  
  
 Jeśli maska bitowa określa rejestr, `GetRegisters` który jest niedostępny, zwraca nieokreśloną wartość dla tego rejestru.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugRegisterSet — Interfejs](icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2 — Interfejs](icordebugregisterset2-interface.md)

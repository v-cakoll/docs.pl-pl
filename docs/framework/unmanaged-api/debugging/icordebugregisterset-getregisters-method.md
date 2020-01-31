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
ms.openlocfilehash: 737993ac80b26d490915af3e97fd6a9552246aee
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792117"
---
# <a name="icordebugregistersetgetregisters-method"></a>ICorDebugRegisterSet::GetRegisters — Metoda
Pobiera wartość każdego rejestru (na komputerze, który aktualnie wykonuje kod), który jest określony przez maskę bitową.  
  
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
 podczas Maska bitów określająca, które wartości rejestru mają być pobierane. Każdy bit odnosi się do rejestru. Jeśli bit jest ustawiony na jeden, zostanie pobrana wartość rejestru. w przeciwnym razie wartość rejestru nie zostanie pobrana.  
  
 `regCount`  
 podczas Liczba wartości rejestru do pobrania.  
  
 `regBuffer`  
 określoną Tablica obiektów `CORDB_REGISTER`, z których każdy otrzymuje wartość rejestru.  
  
## <a name="remarks"></a>Uwagi  
 Rozmiar tablicy musi być równy liczbie bitów ustawionych dla jednej w masce bitów. `regCount` parametr określa liczbę elementów w buforze, które będą otrzymywać wartości rejestru. Jeśli wartość `regCount` jest za mała dla liczby rejestrów wskazanych przez maskę, te rejestry o wyższych numerach zostaną obcięte z zestawu. Jeśli wartość `regCount` jest zbyt duża, nieużywane elementy `regBuffer` będą niemodyfikowane.  
  
 Jeśli Maska bitów określa rejestr, który jest niedostępny, `GetRegisters` zwraca nieokreśloną wartość dla tego rejestru.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugRegisterSet, interfejs](icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2, interfejs](icordebugregisterset2-interface.md)

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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b417685361126951470571e2440cc842ab1c94fb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59153910"
---
# <a name="icordebugregistersetgetregisters-method"></a>ICorDebugRegisterSet::GetRegisters — Metoda
Pobiera wartość każdego rejestru (na komputerze, który aktualnie wykonuje kod) określonej przez Maska bitów.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `mask`  
 [in] Maska bitów, określający które rejestr wartości, które mają być pobierane. Każdy bit odnosi się do rejestru. Jeśli bit jest ustawiony na jedną, wartość rejestru jest pobierana; w przeciwnym razie wartości rejestru nie są pobierane.  
  
 `regCount`  
 [in] Liczba wartości rejestru, które mają zostać pobrane.  
  
 `regBuffer`  
 [out] Tablica `CORDB_REGISTER` obiektów, z których każdy otrzymuje wartość rejestru.  
  
## <a name="remarks"></a>Uwagi  
 Rozmiar tablicy powinna być równa liczbie bitów w masce bitowej. `regCount` Parametr określa liczbę elementów w buforze, który będzie otrzymywał wartości rejestru. Jeśli `regCount` wartość jest zbyt mały dla liczby rejestrów wskazywanym przez maskę, wyższe rejestrów numerowane zostanie obcięta z zestawu. Jeśli `regCount` jest zbyt duża, nieużywane `regBuffer` elementy zostaną zostały zmodyfikowane.  
  
 Jeśli maska bitowa, określa rejestru, który jest niedostępny, `GetRegisters` zwraca wartość nieokreśloną dla tego rejestru.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugRegisterSet, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)

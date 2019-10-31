---
title: ICorDebugRegisterSet2::GetRegisters — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegisters method [.NET Framework debugging]
ms.assetid: dbc498a8-ba3f-42f2-bdd9-b623c77a1019
topic_type:
- apiref
ms.openlocfilehash: 8e5583acfe338c185200c0b8e41b7d6e051fa146
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131358"
---
# <a name="icordebugregisterset2getregisters-method"></a>ICorDebugRegisterSet2::GetRegisters — Metoda
Pobiera wartość każdego rejestru (dla platformy, w której kod jest aktualnie wykonywany), która jest określona przez daną maskę bitową.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `maskCount`  
 podczas Rozmiar (w bajtach) tablicy `mask`.  
  
 `mask`  
 podczas Tablica bajtów, z których każdy bit odnosi się do rejestru. Jeśli bit wynosi 1, zostanie pobrana odpowiednia wartość rejestru.  
  
 `regCount`  
 podczas Liczba wartości rejestru do pobrania.  
  
 `regBuffer`  
 określoną Tablica obiektów `CORDB_REGISTER`, z których każdy otrzymuje wartość rejestru.  
  
## <a name="remarks"></a>Uwagi  
 Metoda `GetRegisters` zwraca tablicę wartości z rejestrów, które są określone przez maskę. Tablica nie zawiera wartości rejestrów, których bit maski nie jest ustawiony. W ten sposób rozmiar tablicy `regBuffer` musi być równy liczbie 1 w masce. Jeśli wartość `regCount` jest za mała dla liczby rejestrów wskazywanych przez maskę, wartości wyższych numerowanych rejestrów zostaną obcięte z zestawu. Jeśli `regCount` jest zbyt duży, nieużywane elementy `regBuffer` będą niemodyfikowane.  
  
 Jeśli niedostępna Rejestracja jest wskazywana przez maskę, zostanie zwrócona wartość nieokreślona dla tego rejestru.  
  
 Metoda `ICorDebugRegisterSet2::GetRegisters` jest niezbędna dla platform, które mają więcej niż 64 rejestrów. Na przykład IA64 ma 128 rejestry ogólnego przeznaczenia i 128 rejestry zmiennoprzecinkowe, więc potrzebujesz więcej niż 64-bitów w masce bitowej.  
  
 Jeśli nie ma więcej niż 64 rejestrów, tak jak w przypadku platform, takich jak x86, Metoda `GetRegisters` faktycznie tłumaczy bajty w tablicy `mask` bajtów na `ULONG64`, a następnie wywołuje metodę [ICorDebugRegisterSet:: GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) , która przyjmuje maskę `ULONG64`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugRegisterSet2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [ICorDebugRegisterSet, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)

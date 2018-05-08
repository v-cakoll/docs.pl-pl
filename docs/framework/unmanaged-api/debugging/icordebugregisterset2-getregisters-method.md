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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aca83a66520531074f376a47a7f2994cda237f9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugregisterset2getregisters-method"></a>ICorDebugRegisterSet2::GetRegisters — Metoda
Pobiera wartość każdego rejestru (dla platformy, na którym kod jest aktualnie wykonywany) określonym przez dany bitowej maski.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `maskCount`  
 [in] Rozmiar w bajtach z `mask` tablicy.  
  
 `mask`  
 [in] Tablica bajtów, każdy bit odpowiada rejestru. Jeśli bit ma wartość 1, będzie można pobrać wartości rejestru odpowiednich.  
  
 `regCount`  
 [in] Liczba wartości rejestru, które mają zostać pobrane.  
  
 `regBuffer`  
 [out] Tablica `CORDB_REGISTER` obiektów, z których każdy otrzymuje wartość rejestru.  
  
## <a name="remarks"></a>Uwagi  
 `GetRegisters` Metoda zwraca tablicę wartości z rejestrów, które są określone przez maskę. Tablica nie zawiera wartości rejestrów bit maski, których nie jest ustawiony. W związku z tym rozmiar `regBuffer` tablicy musi być równa liczbie 1 maski. Jeśli wartość `regCount` jest za mały dla liczby rejestrów wskazanych przez maskę wartości wyższej rejestrów numerowane zostanie obcięty z zestawu. Jeśli `regCount` jest zbyt duży, nieużywane `regBuffer` elementy zostaną zmodyfikowane.  
  
 Jeśli niedostępny rejestru jest określane przez maski, zostanie zwrócony nieokreśloną wartość do rejestru.  
  
 `ICorDebugRegisterSet2::GetRegisters` Metoda jest niezbędne dla platform, które mają ponad 64 rejestrów. Na przykład IA64 ma 128 rejestrów ogólnego przeznaczenia i 128 rejestrów zmiennoprzecinkowych, więc należy więcej niż 64-bitowej maski bitowej.  
  
 Jeśli nie masz więcej niż 64 rejestrów, tak jak w przypadku na platformach, na przykład x86, `GetRegisters` metody rzeczywista właśnie tłumaczy bajtów w `mask` tablica bajtów do `ULONG64` , a następnie wywołuje [ICorDebugRegisterSet:: GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) metodę, która przyjmuje `ULONG64` maski.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugRegisterSet2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 [ICorDebugRegisterSet, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)

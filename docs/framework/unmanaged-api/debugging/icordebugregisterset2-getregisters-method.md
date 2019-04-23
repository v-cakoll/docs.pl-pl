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
ms.openlocfilehash: e2dc1064656f3493db78d858cf1e86db0cb83d6c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136698"
---
# <a name="icordebugregisterset2getregisters-method"></a>ICorDebugRegisterSet2::GetRegisters — Metoda
Pobiera wartość każdego rejestru (dla platformy, na którym aktualnie wykonuje kod) określonej przez dany bitowej maski.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `maskCount`  
 [in] Rozmiar w bajtach z `mask` tablicy.  
  
 `mask`  
 [in] Tablica bajtów, każdy bit odnosi się do rejestru. Jeśli bit ma wartość 1, zostanie pobrana wartość w odpowiednim rejestrze.  
  
 `regCount`  
 [in] Liczba wartości rejestru, które mają zostać pobrane.  
  
 `regBuffer`  
 [out] Tablica `CORDB_REGISTER` obiektów, z których każdy otrzymuje wartość rejestru.  
  
## <a name="remarks"></a>Uwagi  
 `GetRegisters` Metoda zwraca tablicę wartości z rejestrów, określonych przez maskę. Tablica nie zawiera wartości rejestrów, w których bit maski nie jest ustawiony. Dlatego rozmiar `regBuffer` tablicy musi być równa liczbie 1 maski. Jeśli wartość `regCount` jest zbyt mały dla liczby rejestrów wskazywanym przez maskę wartości wyższej rejestrów numerowane zostanie obcięta z zestawu. Jeśli `regCount` jest zbyt duży, nieużywane `regBuffer` elementy zostaną zostały zmodyfikowane.  
  
 Jeśli rejestrowanie niedostępne jest wskazywany przez maskę, nieokreślona wartość zwracaną dla tego rejestru.  
  
 `ICorDebugRegisterSet2::GetRegisters` Metoda jest niezbędna dla platform, które mają więcej niż 64 rejestrów. Na przykład IA64 ma 128 rejestrów ogólnego przeznaczenia i 128 rejestrów zmiennoprzecinkowych, dlatego potrzebujesz więcej niż 64-bitowej maski bitowej.  
  
 Jeśli nie masz więcej niż 64 rejestry, tak jak w przypadku na platformach takich jak x86, `GetRegisters` metody w rzeczywistości po prostu tłumaczy bajtów w `mask` tablicy typu byte do `ULONG64` , a następnie wywołuje [ICorDebugRegisterSet:: Getregisters —](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) metody, która przyjmuje `ULONG64` maski.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugRegisterSet2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [ICorDebugRegisterSet, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)

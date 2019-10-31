---
title: ICorDebugNativeFrame::GetLocalRegisterValue — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalRegisterValue
helpviewer_keywords:
- GetLocalRegisterValue method [.NET Framework debugging]
- ICorDebugNativeFrame::GetLocalRegisterValue method [.NET Framework debugging]
ms.assetid: 5ccb74f3-f891-430c-b70a-e370624edde2
topic_type:
- apiref
ms.openlocfilehash: 132e0868426670ba61d8ee12ba7007be1a8a52de
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139395"
---
# <a name="icordebugnativeframegetlocalregistervalue-method"></a>ICorDebugNativeFrame::GetLocalRegisterValue — Metoda
Pobiera wartość argumentu lub zmiennej lokalnej przechowywanej w określonym rejestrze dla tej ramki natywnej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetLocalRegisterValue (  
    [in]  CorDebugRegister   reg,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `reg`  
 podczas Wartość wyliczenia "CorDebugRegister —", która określa rejestr zawierający wartość.  
  
 `cbSigBlob`  
 podczas Liczba całkowita określająca rozmiar podpisu metadanych binarnych, do którego odwołuje się parametr `pvSigBlob`.  
  
 `pvSigBlob`  
 podczas Wartość `PCCOR_SIGNATURE`, która wskazuje na podpis metadanych binarnych typu wartości.  
  
 `ppValue`  
 określoną Wskaźnik do adresu obiektu "ICorDebugValue" reprezentującego pobraną wartość, która jest przechowywana w określonym rejestrze.  
  
## <a name="remarks"></a>Uwagi  
 Metody `GetLocalRegisterValue` można użyć w ramce natywnej lub w ramce skompilowanej just-in-Time (JIT).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

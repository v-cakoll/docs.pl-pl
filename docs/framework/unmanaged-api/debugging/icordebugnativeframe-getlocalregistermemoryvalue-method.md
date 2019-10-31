---
title: ICorDebugNativeFrame::GetLocalRegisterMemoryValue — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalRegisterMemoryValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalRegisterMemoryValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalRegisterMemoryValue method [.NET Framework debugging]
- GetLocalRegisterMemoryValue method [.NET Framework debugging]
ms.assetid: d350f69d-9aff-4f5a-8301-daea22dee2da
topic_type:
- apiref
ms.openlocfilehash: d44d7c23f88f5ea93f608d06b69f69b2c3637b5e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096847"
---
# <a name="icordebugnativeframegetlocalregistermemoryvalue-method"></a>ICorDebugNativeFrame::GetLocalRegisterMemoryValue — Metoda
Pobiera wartość argumentu lub zmiennej lokalnej, w której dolny wyraz i duże słowo są przechowywane w lokalizacji pamięci i określone zarejestrowane odpowiednio dla tej ramki natywnej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetLocalRegisterMemoryValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CORDB_ADDRESS      lowWordAddress,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `highWordReg`  
 podczas Wartość wyliczenia "CorDebugRegister —", która określa rejestr zawierający wysokie słowo wartości.  
  
 `lowWordAddress`  
 podczas Wartość `CORDB_ADDRESS`, która określa lokalizację pamięci zawierającą dolny wyraz wartości.  
  
 `cbSigBlob`  
 podczas Liczba całkowita określająca rozmiar podpisu metadanych binarnych, do którego odwołuje się parametr `pvSigBlob`.  
  
 `pvSigBlob`  
 podczas Wartość `PCCOR_SIGNATURE`, która wskazuje na podpis metadanych binarnych typu wartości.  
  
 `ppValue`  
 określoną Wskaźnik do adresu obiektu "ICorDebugValue" reprezentującego pobraną wartość, która jest przechowywana w określonym rejestrze i lokalizacji pamięci.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

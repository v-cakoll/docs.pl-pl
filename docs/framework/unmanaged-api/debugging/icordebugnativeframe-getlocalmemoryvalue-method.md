---
title: ICorDebugNativeFrame::GetLocalMemoryValue — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalMemoryValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalMemoryValue
helpviewer_keywords:
- GetLocalMemoryValue method [.NET Framework debugging]
- ICorDebugNativeFrame::GetLocalMemoryValue method [.NET Framework debugging]
ms.assetid: b600b3a2-9908-42d8-8093-ab6f39e9a2c9
topic_type:
- apiref
ms.openlocfilehash: cee095003c136142052b8f946fa8227927c80ee2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096865"
---
# <a name="icordebugnativeframegetlocalmemoryvalue-method"></a>ICorDebugNativeFrame::GetLocalMemoryValue — Metoda
Pobiera wartość argumentu lub zmiennej lokalnej przechowywanej w określonej lokalizacji pamięci dla tej ramki natywnej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetLocalMemoryValue (  
    [in]  CORDB_ADDRESS      address,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `address`  
 podczas Wartość `CORDB_ADDRESS`, która określa lokalizację pamięci zawierającą wartość.  
  
 `cbSigBlob`  
 podczas Liczba całkowita określająca rozmiar podpisu metadanych binarnych, do którego odwołuje się parametr `pvSigBlob`.  
  
 `pvSigBlob`  
 podczas Wartość `PCCOR_SIGNATURE`, która wskazuje na podpis metadanych binarnych typu wartości.  
  
 `ppValue`  
 określoną Wskaźnik do adresu obiektu "ICorDebugValue" reprezentującego pobraną wartość przechowywaną w określonej lokalizacji pamięci.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

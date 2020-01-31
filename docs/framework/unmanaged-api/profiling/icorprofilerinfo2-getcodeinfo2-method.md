---
title: ICorProfilerInfo2::GetCodeInfo2 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetCodeInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetCodeInfo2
helpviewer_keywords:
- ICorProfilerInfo2::GetCodeInfo2 method [.NET Framework profiling]
- GetCodeInfo2 method [.NET Framework profiling]
ms.assetid: 532da6ee-7f0a-401b-a61e-fc47ec235d2e
topic_type:
- apiref
ms.openlocfilehash: 9295ea8b22f72529f55cbe13f6a79a0aa34d2fa0
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868799"
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a>ICorProfilerInfo2::GetCodeInfo2 — Metoda
Pobiera zakresy kodu natywnego powiązane z określonym `FunctionID`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetCodeInfo2(  
    [in]  FunctionID functionID,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionID`  
 podczas Identyfikator funkcji, z którą jest skojarzony kod natywny.  
  
 `cCodeInfos`  
 podczas Rozmiar tablicy `codeInfos`.  
  
 `pcCodeInfos`  
 określoną Wskaźnik do łącznej liczby dostępnych struktur [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) .  
  
 `codeInfos`  
 określoną Bufor dostarczony przez wywołującego. Po powrocie metody zawiera tablicę struktur `COR_PRF_CODE_INFO`, z których każdy opisuje blok kodu natywnego.  
  
## <a name="remarks"></a>Uwagi  
 Zakresy są sortowane w kolejności rosnącego przesunięcia języka pośredniego firmy Microsoft (MSIL).  
  
 Po powrocie `GetCodeInfo2` należy sprawdzić, czy bufor `codeInfos` był wystarczająco duży, aby zawierał wszystkie struktury `COR_PRF_CODE_INFO`. W tym celu należy porównać wartość `cCodeInfos` z wartością parametru `cchName`. Jeśli `cCodeInfos` podzielona przez rozmiar struktury `COR_PRF_CODE_INFO` jest mniejsza niż `pcCodeInfos`, Przydziel większy bufor `codeInfos`, zaktualizuj `cCodeInfos` z nowym, większym rozmiarem i ponownie wywołaj `GetCodeInfo2`.  
  
 Alternatywnie można najpierw wywołać `GetCodeInfo2` z buforem `codeInfos` o zerowej długości, aby uzyskać prawidłowy rozmiar buforu. Następnie można ustawić `codeInfos` rozmiar buforu na wartość zwróconą w `pcCodeInfos`, pomnożoną przez rozmiar struktury `COR_PRF_CODE_INFO` i ponownie wywołać `GetCodeInfo2`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetCodeInfo3, metoda](icorprofilerinfo4-getcodeinfo3-method.md)
- [ICorProfilerInfo2, interfejs](icorprofilerinfo2-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowanie](index.md)

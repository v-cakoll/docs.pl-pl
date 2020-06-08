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
ms.openlocfilehash: 04ce9ebded4be7ac3b20a4ceb78dd02294bbff4a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502902"
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a>ICorProfilerInfo2::GetCodeInfo2 — Metoda
Pobiera zakresy kodu natywnego skojarzonego z określonym `FunctionID` .  
  
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
 podczas Rozmiar `codeInfos` tablicy.  
  
 `pcCodeInfos`  
 określoną Wskaźnik do łącznej liczby dostępnych struktur [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) .  
  
 `codeInfos`  
 określoną Bufor dostarczony przez wywołującego. Po powrocie metody zawiera tablicę `COR_PRF_CODE_INFO` struktur, z których każdy opisuje blok kodu natywnego.  
  
## <a name="remarks"></a>Uwagi  
 Zakresy są sortowane w kolejności rosnącego przesunięcia języka pośredniego firmy Microsoft (MSIL).  
  
 Po `GetCodeInfo2` powrocie należy sprawdzić, czy `codeInfos` bufor jest wystarczająco duży, aby można było zawierać wszystkie `COR_PRF_CODE_INFO` struktury. W tym celu należy porównać wartość `cCodeInfos` z wartością `cchName` parametru. Jeśli `cCodeInfos` podzielona przez rozmiar `COR_PRF_CODE_INFO` struktury jest mniejsza niż `pcCodeInfos` , Przydziel większy `codeInfos` bufor, zaktualizuj `cCodeInfos` przy użyciu nowego, większego rozmiaru i ponownie wywołaj `GetCodeInfo2` .  
  
 Alternatywnie, można najpierw wywołać `GetCodeInfo2` z buforem o zerowej długości, `codeInfos` Aby uzyskać prawidłowy rozmiar buforu. Następnie można ustawić `codeInfos` rozmiar buforu na wartość zwróconą w `pcCodeInfos` , pomnożoną przez rozmiar `COR_PRF_CODE_INFO` struktury i `GetCodeInfo2` ponownie wywołać.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetCodeInfo3, metoda](icorprofilerinfo4-getcodeinfo3-method.md)
- [ICorProfilerInfo2, interfejs](icorprofilerinfo2-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowanie](index.md)

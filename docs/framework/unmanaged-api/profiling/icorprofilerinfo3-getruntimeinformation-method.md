---
title: ICorProfilerInfo3::GetRuntimeInformation — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetRuntimeInformation Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetRuntimeInformation
helpviewer_keywords:
- GetRuntimeInformation method [.NET Framework profiling]
- ICorProfilerInfo3::GetRuntimeInformation method [.NET Framework profiling]
ms.assetid: 4400fb8c-0407-4791-8557-f011fd2aee51
topic_type:
- apiref
ms.openlocfilehash: b8e503af11fa1d02aac2ec83edde0ffbd562d8e5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496402"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a>ICorProfilerInfo3::GetRuntimeInformation — Metoda
Zawiera informacje o wersji dotyczące PROFILOWANEGO środowiska uruchomieniowego języka wspólnego (CLR).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetRuntimeInformation(  
       [out] USHORT *pClrInstanceId,  
       [out] COR_PRF_RUNTIME_TYPE *pRuntimeType,  
       [out] USHORT *pMajorVersion,  
       [out] USHORT *pMinorVersion,  
       [out] USHORT *pBuildNumber,  
       [out] USHORT *pQFEVersion,  
       [in]  ULONG  cchVersionString,  
       [out] ULONG  *pcchVersionString,  
       [out, size_is(cchVersionString), length_is(*pcchVersionString)]  
                   WCHAR  szVersionString[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `pClrInstanceId`  
 określoną Identyfikator reprezentatywny uruchomionego wystąpienia środowiska CLR w procesie. Jest to takie samo, jak `ClrInstanceID` raport zdarzenia uruchamiania śledzenie zdarzeń systemu Windows (ETW).  
  
 `pRuntimeType`  
 określoną Typ środowiska uruchomieniowego. Ten parametr zwraca `COR_PRF_DESKTOP_CLR` dla wersji klasycznej środowiska CLR lub `COR_PRF_CORE_CLR` dla podstawowej wersji środowiska CLR używanej w technologii Silverlight.  
  
 `pMajorVersion`  
 określoną Numer wersji głównej środowiska CLR.  
  
 `pMinorVersion`  
 określoną Numer wersji pomocniczej środowiska CLR.  
  
 `pBuildVersion`  
 określoną Numer wersji kompilacji środowiska CLR.  
  
 `pQFEVersion`  
 określoną Numer wersji środowiska CLR skojarzonego z aktualizacją oprogramowania.  
  
 `cchVersionString`  
 podczas Długość (w znakach) bufora, który `szVersionString` wskazuje.  
  
 `pcchVersionString`  
 określoną Długość, w znakach, z `szVersionString` .  
  
 `szVersionString`  
 określoną Ciąg wersji środowiska CLR.  
  
## <a name="remarks"></a>Uwagi  
 Dla dowolnego parametru można przekazać wartość null. Jednak `pcchVersionString` nie może mieć wartości null, chyba że `szVersionString` ma również wartość null.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo3, interfejs](icorprofilerinfo3-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowanie](index.md)

---
title: "ICorProfilerInfo3::GetRuntimeInformation — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.GetRuntimeInformation Method
api_location: Mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::GetRuntimeInformation
helpviewer_keywords:
- GetRuntimeInformation method [.NET Framework profiling]
- ICorProfilerInfo3::GetRuntimeInformation method [.NET Framework profiling]
ms.assetid: 4400fb8c-0407-4791-8557-f011fd2aee51
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5eadd9970d29cc65d8411692407dcae5471e51c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a>ICorProfilerInfo3::GetRuntimeInformation — Metoda
Zawiera informacje o wersji dotyczące środowisko uruchomieniowe języka wspólnego (CLR), który jest poddawany profilowaniu.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `pClrInstanceId`  
 [out] Identyfikator pracownika uruchomionego wystąpienia CLR w procesie. To jest taka sama jak `ClrInstanceID` czy raporty śledzenie zdarzeń dla zdarzenia uruchamiania systemu Windows (ETW).  
  
 `pRuntimeType`  
 [out] Typ środowiska uruchomieniowego. Ten parametr zwraca `COR_PRF_DESKTOP_CLR` dla tej wersji środowiska CLR, lub `COR_PRF_CORE_CLR` dla wersji core CLR używane w programie Silverlight.  
  
 `pMajorVersion`  
 [out] Główny numer wersji środowiska CLR.  
  
 `pMinorVersion`  
 [out] Podrzędny numer wersji środowiska CLR.  
  
 `pBuildVersion`  
 [out] Numer wersji kompilacji środowiska CLR.  
  
 `pQFEVersion`  
 [out] Numer wersji środowiska CLR, która jest skojarzona z aktualizacji oprogramowania.  
  
 `cchVersionString`  
 [in] Długość w znakach buforu który `szVersionString` wskazuje.  
  
 `pcchVersionString`  
 [out] Długość w znakach, z `szVersionString`.  
  
 `szVersionString`  
 [out] Ciąg wersji aparatu CLR.  
  
## <a name="remarks"></a>Uwagi  
 Użytkownik może przekazać wartości null dla żadnego parametru. Jednak `pcchVersionString` nie może mieć wartości null chyba że `szVersionString` również ma wartość null.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo3, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)

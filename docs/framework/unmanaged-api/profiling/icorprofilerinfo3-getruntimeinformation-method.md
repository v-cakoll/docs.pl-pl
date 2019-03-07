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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: da116de6bde01ea7fd17f7ab27605501ae723f30
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473011"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a>ICorProfilerInfo3::GetRuntimeInformation — Metoda
Zawiera informacje o wersji dotyczące wspólne środowisko uruchomieniowe języka (wspólnego CLR), która jest profilowana.  
  
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
  
## <a name="parameters"></a>Parametry  
 `pClrInstanceId`  
 [out] Identyfikator przedstawiciel uruchomionego wystąpienia CLR w procesie. To jest taka sama jak `ClrInstanceID` czy raportów śledzenia zdarzeń dla zdarzenia uruchamiania Windows (ETW).  
  
 `pRuntimeType`  
 [out] Typ środowiska uruchomieniowego. Ten parametr zwraca `COR_PRF_DESKTOP_CLR` w przypadku klasycznej wersji środowiska CLR, lub `COR_PRF_CORE_CLR` core wersję środowiska CLR używanego w technologii Silverlight.  
  
 `pMajorVersion`  
 [out] Główny numer wersji środowiska CLR.  
  
 `pMinorVersion`  
 [out] Pomocniczy numer wersji środowiska CLR.  
  
 `pBuildVersion`  
 [out] Numer wersji kompilacji środowiska CLR.  
  
 `pQFEVersion`  
 [out] Numer wersji środowiska CLR, który jest skojarzony z aktualizacji oprogramowania.  
  
 `cchVersionString`  
 [in] Długość w znakach buforu, który `szVersionString` wskazuje.  
  
 `pcchVersionString`  
 [out] Długość w znakach, z `szVersionString`.  
  
 `szVersionString`  
 [out] Ciąg wersji środowiska CLR.  
  
## <a name="remarks"></a>Uwagi  
 Możesz przekazać wartości null dla każdego parametru. Jednak `pcchVersionString` nie może mieć wartości null Jeśli nie `szVersionString` również ma wartość null.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorProfilerInfo3, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)

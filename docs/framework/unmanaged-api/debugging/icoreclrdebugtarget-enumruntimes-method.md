---
title: ICoreClrDebugTarget::EnumRuntimes — Metoda
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumRuntimes
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumRuntimes
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget::EnumRuntimes method [Silverlight debugging]
- EnumRuntimes method, ICoreClrDebugTarget interface [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 316df866-442d-40cc-b049-45e8adcb65d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: afb31646d21ec7e15f79601f5fe83ea6ce44fa90
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134683"
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a>ICoreClrDebugTarget::EnumRuntimes — Metoda
Wylicza środowiska uruchomieniowego języka wspólnego (CLRs) w określonym procesie, który jest uruchomiona na komputerze zdalnym.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
## <a name="parameters"></a>Parametry  
 `dwInternalProcessID`  
 [in] Wewnętrzny proces identyfikator procesu, dla którego chcesz wyliczyć środowisk uruchomieniowych. Będzie to `m_dwInternalID` od odpowiadających im [coreclrdebugprocinfo —](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md).  
  
 `pcRuntimes`  
 [out] Liczba środowisk uruchomieniowych zwracane w `ppRuntimes`. Ta wartość może być 0 (zero).  
  
 `ppRuntimes`  
 [out] Tablica [CoreClrDebugRuntimeInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md) struktur, które reprezentują środowiska uruchomieniowego załadowany w procesie docelowym zdalnego.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 Powodzenie.  
  
 S_FALSE  
 `dwInternalProcessID` nie pasuje żaden proces, który jest uruchomiony na komputerze, prawdopodobnie ponieważ proces został zakończony. `pcRuntimes` i `ppRuntimes` będzie miał wartość null.  
  
 E_OUTOFMEMORY  
 Nie można przydzielić wystarczającej ilości pamięci do `ppRuntimes`.  
  
 E_FAIL (lub inne kody powrotne e_)  
 Inne błędy.  
  
## <a name="remarks"></a>Uwagi  
 Aby zwolnić pamięć, która została przydzielona przez tę metodę, należy wywołać [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Library:** mscordbi_macx86.dll  
  
 **Wersje programu .NET framework:** 3.5 z dodatkiem SP1  
  
## <a name="see-also"></a>Zobacz także

- [ICoreClrDebugTarget, interfejs](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)

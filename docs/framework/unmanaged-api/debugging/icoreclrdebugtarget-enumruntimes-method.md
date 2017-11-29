---
title: "ICoreClrDebugTarget::EnumRuntimes — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICoreClrDebugTarget.EnumRuntimes
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: ICoreClrDebugTarget::EnumRuntimes
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget::EnumRuntimes method [Silverlight debugging]
- EnumRuntimes method, ICoreClrDebugTarget interface [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 316df866-442d-40cc-b049-45e8adcb65d1
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d28e5f3f529f72607e2ddd84789e89f82dcdaba0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a>ICoreClrDebugTarget::EnumRuntimes — Metoda
Wylicza wspólnej obsługi language (CLRs) określonego procesu uruchomionego na komputerze zdalnym.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwInternalProcessID`  
 [in] Wewnętrzny proces identyfikator procesu, który ma wyliczyć środowisk uruchomieniowych. Są to `m_dwInternalID` z odpowiadającego [coreclrdebugprocinfo —](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md).  
  
 `pcRuntimes`  
 [out] Liczba zwracanych w środowiskach uruchomieniowych `ppRuntimes`. Ta wartość może być 0 (zero).  
  
 `ppRuntimes`  
 [out] Tablica [coreclrdebugruntimeinfo —](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md) struktur reprezentujących środowisk uruchomieniowych załadowany w procesie docelowym zdalnego.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 Powodzenie.  
  
 WARTOŚCI S_FALSE  
 `dwInternalProcessID`nie odpowiada żaden proces, który jest uruchomiony na komputerze, prawdopodobnie, ponieważ proces został zakończony. `pcRuntimes`i `ppRuntimes` będzie mieć wartość null.  
  
 E_OUTOFMEMORY  
 Nie można przydzielić wystarczającej ilości pamięci do `ppRuntimes`.  
  
 E_FAIL (lub inne kody powrotu E_)  
 Inne błędy.  
  
## <a name="remarks"></a>Uwagi  
 Aby zwolnić pamięć, która została przydzielona przez tę metodę, należy wywołać [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Biblioteka:** mscordbi_macx86.dll  
  
 **Wersje programu .NET framework:** 3.5 z dodatkiem SP1  
  
## <a name="see-also"></a>Zobacz też  
 [Icoreclrdebugtarget — interfejs](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)

---
title: ICoreClrDebugTarget::EnumProcesses — Metoda
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumProcesses
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumProcesses
helpviewer_keywords:
- remote debugging API [Silverlight]
- EnumProcesses method, ICorClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::EnumProcesses method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: e00fd477-4f49-43d3-bd0e-3094824b1136
topic_type:
- apiref
ms.openlocfilehash: 0c1b18f24fd30b5f6d5e85633fc0c25839aba6df
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396410"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a>ICoreClrDebugTarget::EnumProcesses — Metoda
Wylicza procesy, które są uruchomione na komputerze zdalnym.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pcProcs`  
 określoną Liczba procesów zwróconych w `ppProcs` . Ta wartość może być równa 0 (zero).  
  
 `ppProcs`  
 określoną Tablica struktur [CoreClrDebugProcInfo —](coreclrdebugprocinfo-structure.md) , które reprezentują procesy uruchomione na komputerze zdalnym.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 Powodzenie.  
  
 E_OUTOFMEMORY  
 Nie można przydzielić wystarczającej ilości pamięci dla `ppProcs` .  
  
 E_FAIL (lub inne kody powrotne E_)  
 Inne błędy.  
  
## <a name="remarks"></a>Uwagi  
 Aby zwolnić pamięć, która została przypisana przez tę metodę, wywołaj metodę [ICoreClrDebugTarget:: freememory —](icoreclrdebugtarget-freememory-method.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Biblioteka:** mscordbi_macx86. dll  
  
 **.NET Framework wersje:** 3,5 SP1  
  
## <a name="see-also"></a>Zobacz także

- [ICoreClrDebugTarget — Interfejs](icoreclrdebugtarget-interface.md)

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
ms.openlocfilehash: 6484832e8e737b9a0d0b3eaf3ede4078729f7a4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178438"
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
 [na zewnątrz] Liczba procesów zwróconych w `ppProcs`pliku . Ta wartość może wynosić 0 (zero).  
  
 `ppProcs`  
 [na zewnątrz] Tablica [struktur CoreClrDebugProcInfo,](coreclrdebugprocinfo-structure.md) które reprezentują procesy uruchomione na komputerze zdalnym.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 Powodzenie.  
  
 E_outofmemory  
 Nie można przydzielić `ppProcs`wystarczającej ilości pamięci dla pliku .  
  
 E_FAIL (lub inne E_ kody zwrotne)  
 Inne awarie.  
  
## <a name="remarks"></a>Uwagi  
 Aby zwolnić pamięć, która została przydzielona przez tę metodę, wywołaj [metodę ICoreClrDebugTarget::FreeMemory.](icoreclrdebugtarget-freememory-method.md)  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Biblioteka:** mscordbi_macx86.dll  
  
 **Wersje .NET Framework:** 3.5 SP1  
  
## <a name="see-also"></a>Zobacz też

- [ICoreClrDebugTarget, interfejs](icoreclrdebugtarget-interface.md)

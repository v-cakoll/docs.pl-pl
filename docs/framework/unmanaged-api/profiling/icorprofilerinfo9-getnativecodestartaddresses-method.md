---
title: ICorProfilerInfo9::GetNativeCodeStartAddresses
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetNativeCodeStartAddresses
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: f5c7f11a322e4cf3ed38608e0f380dd632bc8fb6
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973691"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a>ICorProfilerInfo9:: GetNativeCodeStartAddresses, Metoda
  
 Mając functionId i rejitId, wylicza natywny adres początkowy kodu dla wszystkich wersji trybie JIT tego kodu, który już istnieje.   
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 podczas Identyfikator funkcji, której powinny zostać zwrócone adresy początkowe kodu natywnego.  
  
 `reJitId`  
 podczas Tożsamość funkcji ponownie skompilowanej JIT. 
  
 `cCodeStartAddresses` \
 podczas Maksymalny rozmiar `codeStartAddresses` tablicy.

 `pcCodeStartAddresses` \
 określoną Liczba dostępnych adresów.

 `codeStartAddresses` \
 określoną Tablica, z `UINT_PTR`której każdy jest adresem początkowym dla określonej funkcji. 

## <a name="remarks"></a>Uwagi  
 Gdy kompilacja warstwowa jest włączona, funkcja może mieć więcej niż jedną treść kodu natywnego. 

## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).  
  
 **Nagłówki** CorProf. idl, CorProf. h  
  
 **Biblioteki** CorGuids.lib  
  
 **Wersje .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)] 
  
## <a name="see-also"></a>Zobacz także
- [ICorProfilerInfo9, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md)


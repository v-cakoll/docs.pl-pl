---
title: 'ICorDebugMergedAssemblyRecord:: getIndex — Metoda'
ms.date: 03/30/2017
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
ms.openlocfilehash: c8fb5ace27fbf7fbebdaca5822af99cd6673e8cf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793125"
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a>ICorDebugMergedAssemblyRecord:: getIndex — Metoda
Pobiera indeks prefiksu zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pIndex`  
 określoną Wskaźnik do indeksu prefiksu.  
  
## <a name="remarks"></a>Uwagi  
 Indeks prefiksu służy do zapobiegania kolizjom nazw w scalonych nazwach typów metadanych.  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugMergedAssemblyRecord, interfejs](icordebugmergedassemblyrecord-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)

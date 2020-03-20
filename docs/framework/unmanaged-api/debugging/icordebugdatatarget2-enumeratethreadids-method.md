---
title: Metoda ICorDebugDataTarget2::EnumerateThreadIDs
ms.date: 03/30/2017
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
ms.openlocfilehash: 120a970aac33b1ab06ae47335a959d2791f893ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178979"
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a>Metoda ICorDebugDataTarget2::EnumerateThreadIDs
Zwraca listę aktywnych identyfikatorów wątków.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,
    [out] ULONG32 *pcThreadIds,
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 cThreadIDs  
 [w] Maksymalna liczba wątków, których identyfikatory mogą być zwracane.  
  
 pcThreadIds (Nieujmi.  
 [na zewnątrz] Wskaźnik `ULONG32` do, który wskazuje rzeczywistą liczbę identyfikatorów wątku `pThreadIds` zapisane w tablicy.  
  
 pThreadIDs (Psż.  
 Tablica identyfikatorów wątków.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ta metoda jest dostępna tylko w przypadku platformy .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md). **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugDataTarget2, interfejs](icordebugdatatarget2-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)

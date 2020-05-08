---
title: Metoda ICorDebugDataTarget2::EnumerateThreadIDs
ms.date: 03/30/2017
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
ms.openlocfilehash: 4a65b76f384cdad68cba75af524dbe672c309624
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976489"
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
 podczas Maksymalna liczba wątków, których identyfikatory można zwrócić.  
  
 pcThreadIds  
 określoną Wskaźnik `ULONG32` wskazujący rzeczywistą liczbę identyfikatorów wątków zapisaną w `pThreadIds` tablicy.  
  
 pThreadIDs  
 Tablica identyfikatorów wątków.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md). **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Interfejs ICorDebugDataTarget2](icordebugdatatarget2-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)

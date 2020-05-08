---
title: ICorDebugDataTarget3::GetLoadedModules — metoda
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
ms.openlocfilehash: c3565f4f9284bc121b0e2d3b0885cbea927acfdd
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976424"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a>ICorDebugDataTarget3::GetLoadedModules — metoda
Pobiera listę modułów, które zostały wcześniej załadowane.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cRequestedModules`  
 podczas Liczba modułów, dla których żądane są informacje.  
  
 `pcFetchedModules`  
 określoną Wskaźnik do liczby modułów, na których zwrócono informacje.  
  
 `pLoadedModules`  
 określoną Wskaźnik do tablicy obiektów [ICorDebugLoadedModule](icordebugloadedmodule-interface.md) , które zawierają informacje o załadowanych modułach.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugDataTarget3 — interfejs](icordebugdatatarget3-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)

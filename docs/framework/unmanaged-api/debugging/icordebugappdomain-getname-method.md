---
title: ICorDebugAppDomain::GetName — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetName
helpviewer_keywords:
- ICorDebugAppDomain::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 02c596d7-00b0-4e2c-856b-5425158fcefd
topic_type:
- apiref
ms.openlocfilehash: 45d27fca888bdabedf197525c63dbd03af7ba1ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179088"
---
# <a name="icordebugappdomaingetname-method"></a>ICorDebugAppDomain::GetName — Metoda
Pobiera nazwę domeny aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
         WCHAR              szName[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cchName`  
 [w] Rozmiar tablicy. `szName` Ustaw tę wartość na zero, aby umieścić tę metodę w trybie kwerendy.  
  
 `pcchName`  
 [na zewnątrz] Wskaźnik do rozmiaru nazwy lub liczby znaków faktycznie `szName`zwróconych w . W trybie kwerendy ta wartość pozwala wywołującemu wiedzieć, jak duży bufor do przydzielenia dla nazwy.  
  
 `szName`  
 [na zewnątrz] Tablica, która przechowuje nazwę domeny aplikacji.  
  
## <a name="remarks"></a>Uwagi  
 Debuger wywołuje `GetName` metodę raz, aby uzyskać rozmiar buforu wymaganego dla nazwy. Debuger przydziela bufor, a następnie wywołuje metodę po raz drugi, aby wypełnić bufor. Pierwsze wywołanie, aby uzyskać rozmiar nazwy, jest określany jako *tryb kwerendy*.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

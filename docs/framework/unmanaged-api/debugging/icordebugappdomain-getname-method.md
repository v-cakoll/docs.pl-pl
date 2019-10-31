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
ms.openlocfilehash: 2c9aa6792885c685195049948a540453b1f5235e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73110307"
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
 podczas Rozmiar tablicy `szName`. Ustaw tę wartość na zero, aby ustawić tę metodę w trybie zapytania.  
  
 `pcchName`  
 określoną Wskaźnik do rozmiaru nazwy lub liczby znaków faktycznie zwracanych w `szName`. W trybie zapytania ta wartość umożliwia obiektowi wywołującemu określenie, jak duży bufor ma zostać przydzielony do nazwy.  
  
 `szName`  
 określoną Tablica, w której jest przechowywana nazwa domeny aplikacji.  
  
## <a name="remarks"></a>Uwagi  
 Debuger wywołuje metodę `GetName` raz, aby uzyskać rozmiar buforu wymaganego dla nazwy. Debuger przydziela bufor, a następnie wywołuje metodę przy drugim czasie, aby wypełnić bufor. Pierwsze wywołanie, aby uzyskać rozmiar nazwy, jest określany jako *tryb zapytania*.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

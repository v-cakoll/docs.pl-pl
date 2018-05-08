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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84f895e749fc8f2520dbce3caf9e6c11fda78a7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugappdomaingetname-method"></a>ICorDebugAppDomain::GetName — Metoda
Pobiera nazwę domeny aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
         WCHAR              szName[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cchName`  
 [in] Rozmiar `szName` tablicy. Ta wartość zero, aby umieścić tę metodę w trybie zapytania.  
  
 `pcchName`  
 [out] Wskaźnik do rozmiaru nazwę lub liczbę znaków, które faktycznie zwracane w `szName`. W trybie zapytania, ta wartość umożliwia wywołującego wiedzieć, jak duży buforu do przydzielenia dla nazwy.  
  
 `szName`  
 [out] Tablica, która przechowuje nazwę domeny aplikacji.  
  
## <a name="remarks"></a>Uwagi  
 Wywołuje debugera `GetName` metodę raz, aby pobrać rozmiaru buforu potrzebne dla nazwy. Debuger przydziela buforu, a następnie wywołuje metodę po raz drugi do wypełnienia buforu. Pierwsze wywołanie, aby uzyskać nazwę, rozmiar jest określany jako *tryb zapytania*.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

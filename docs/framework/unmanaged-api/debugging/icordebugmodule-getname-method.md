---
title: ICorDebugModule::GetName — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetName
helpviewer_keywords:
- ICorDebugModule::GetName method [.NET Framework debugging]
- GetName method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: db499637-7ba9-421e-b8b1-35856995e80b
topic_type:
- apiref
ms.openlocfilehash: 55342c803756aa10c2e7c835d9e1d58b439bb36c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212545"
---
# <a name="icordebugmodulegetname-method"></a>ICorDebugModule::GetName — Metoda
Pobiera nazwę pliku modułu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cchname`  
 podczas Rozmiar `szName` tablicy.  
  
 `pcchName`  
 podczas Wskaźnik do długości zwracanej nazwy.  
  
 `szName`  
 określoną Tablica przechowująca zwróconą nazwę.  
  
## <a name="remarks"></a>Uwagi  
 `GetName`Metoda zwraca S_OK HRESULT, jeśli nazwa pliku modułu jest zgodna z nazwą na dysku. `GetName`Zwraca S_FALSE HRESULT, jeśli nazwa jest wypełniania, na przykład w module dynamicznym lub w pamięci.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

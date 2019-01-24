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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ae9bc5925634f8bba71731a0c51eb19cf9eec04
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663956"
---
# <a name="icordebugmodulegetname-method"></a>ICorDebugModule::GetName — Metoda
Pobiera nazwę pliku modułu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cchname`  
 [in] Rozmiar `szName` tablicy.  
  
 `pcchName`  
 [in] Wskaźnik do długości nazwy zwrócone.  
  
 `szName`  
 [out] Tablica, która przechowuje nazwę zwracanego.  
  
## <a name="remarks"></a>Uwagi  
 `GetName` Metoda zwraca wartość HRESULT S_OK, jeśli nazwa pliku modułu jest zgodna z nazwą, na dysku. `GetName` Zwraca wartość HRESULT S_FALSE, jeśli nazwa jest metalowych, tak samo jak w przypadku modułu dynamicznego lub w pamięci.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także



---
title: ICorDebugNativeFrame2::IsMatchingParentFrame — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.IsMatchingParentFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::IsMatchingParentFrame
helpviewer_keywords:
- IsMatchingParentFrame method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsMatchingParentFrame method [.NET Framework debugging]
ms.assetid: d2ca20db-df22-4528-a0dd-a09ea62c8998
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 39c0ea69a0922f5e0d25c98c21ec17a872b2f421
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418873"
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a>ICorDebugNativeFrame2::IsMatchingParentFrame — Metoda
Określa, czy określonej ramce nadrzędny bieżącej ramki.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pPotentialParentFrame`  
 [in] Wskaźnik do obiektu ramki, który chcesz ocenić stan nadrzędnej.  
  
 `pIsParent`  
 [out] `true` Jeśli `pPotentialParentFrame` jest elementem nadrzędnym bieżącej ramki; w przeciwnym razie `false`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Pomyślnie zwrócono stan nadrzędnej.|  
|E_FAIL|Nie można zwrócić stan nadrzędnej.|  
|E_INVALIDARG|`pPotentialParentFrame` lub `pIsParent` ma wartość null.|  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
 `IsMatchingParentFrame` Zwraca `true` Jeśli obiekt ramki przekazać do metody jest elementem nadrzędnym obiektu ramki, wywołania tej metody. Jeśli należy wywołać metodę ramki, który nie jest elementem podrzędnym określonej ramce zwraca błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugNativeFrame2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)

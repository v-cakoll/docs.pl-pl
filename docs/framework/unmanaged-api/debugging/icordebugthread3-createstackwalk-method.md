---
title: ICorDebugThread3::CreateStackWalk — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.CreateStackWalk Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::CreateStackWalk
helpviewer_keywords:
- CreateStackWalk method [.NET Framework debugging]
- ICorDebugThread3::CreateStackWalk method [.NET Framework debugging]
ms.assetid: c55e35d9-f9aa-4268-94b5-dce44c61acf2
topic_type:
- apiref
ms.openlocfilehash: 64f6bc9abb8105cdfa942c2aaca71994e8a91765
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791416"
---
# <a name="icordebugthread3createstackwalk-method"></a>ICorDebugThread3::CreateStackWalk — Metoda
Tworzy obiekt [ICorDebugStackWalk](icordebugstackwalk-interface.md) dla wątku, którego stos ma zostać rozwinięcia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppStackWalk`  
 określoną Wskaźnik do adresu obiektu [ICorDebugStackWalk](icordebugstackwalk-interface.md) dla wątku, którego stos ma zostać rozwinięcia.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Obiekt `ICorDebugStackWalk` został pomyślnie utworzony.|  
|E_FAIL|Obiekt `ICorDebugStackWalk` nie został utworzony.|  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
 Jeśli metoda `CreateStackWalk` powiedzie się, zostanie ustawiony kontekst zwróconego obiektu `ICorDebugStackWalk` dla bieżącego kontekstu wątku.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)

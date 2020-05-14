---
title: 'ICorDebugVariableSymbol:: GetSize — metoda'
ms.date: 03/30/2017
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
ms.openlocfilehash: d924de33c8ec49501be0ee7700b2eee8c79bb950
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397115"
---
# <a name="icordebugvariablesymbolgetsize-method"></a>ICorDebugVariableSymbol:: GetSize — metoda
Pobiera rozmiar zmiennej w bajtach.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pcbValue`  
 Wskaźnik do 32-bitowej liczby całkowitej bez znaku zawierającego rozmiar zmiennej.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugVariableSymbol, interfejs](icordebugvariablesymbol-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)

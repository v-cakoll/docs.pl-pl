---
title: ICorDebugVariableSymbol::GetSize Method
ms.date: 03/30/2017
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a41ec4a556ca26404b5f76ddb35d9f73d7307a7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659059"
---
# <a name="icordebugvariablesymbolgetsize-method"></a>ICorDebugVariableSymbol::GetSize Method
Pobiera rozmiar zmiennej elementu w bajtach.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcbValue`  
 Wskaźnik 32-bitowa liczba całkowita bez znaku zawierający rozmiar zmiennej.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z architekturą .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorDebugVariableSymbol, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

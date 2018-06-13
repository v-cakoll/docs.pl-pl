---
title: ICorDebugVariableSymbol::GetSlotIndex — metoda
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1657ed4d8326b573fe081b98c1fc414e231ac465
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420625"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a>ICorDebugVariableSymbol::GetSlotIndex — metoda
Pobiera indeks gniazda zarządzanych zmiennej lokalnej.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pSlotIndex`  
 [out] Wskaźnik do zmiennej lokalnej miejsca indeksu.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK` w przypadku powodzenia. `E_FAIL` Jeśli zmienna jest argumentu funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Indeks gniazda zarządzanych zmiennej lokalnej może służyć do pobierania informacji o metadanych zmiennej  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z platformą .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugVariableSymbol, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

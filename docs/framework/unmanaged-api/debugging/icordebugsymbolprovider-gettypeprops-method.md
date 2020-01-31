---
title: 'ICorDebugSymbolProvider:: GetTypeProps, Metoda'
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
ms.openlocfilehash: 5fa091eaf2cf93b0c645effeec3c959d42665fc9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791547"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a>ICorDebugSymbolProvider:: GetTypeProps, Metoda
Zwraca informacje o właściwościach typu, takich jak liczba podpisów jego parametrów ogólnych, z uwzględnieniem względnego adresu wirtualnego (RVA) w tabeli jednoelementowej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tableRva`  
 podczas Względny adres wirtualny (RVA) w tabeli jednoelementowej.  
  
 `cbSignature`  
 podczas Rozmiar tablicy `signature`. Zobacz sekcję Uwagi.  
  
 `pcbSignature`  
 określoną określoną Wskaźnik do rozmiaru zwróconej tablicy `signature`.  
  
 `signature`  
 określoną Bufor, który przechowuje sygnatury elementu TypeSpec wszystkich parametrów ogólnych.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać wymagany rozmiar tablicy `signature` typu, ustaw dla argumentu `cbSignature` wartość 0, a `signature` na **wartość null**. Gdy metoda zwraca, `pcbSignature` będzie zawierać liczbę bajtów wymaganą dla `signature` tablicy.  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetMethodProps, metoda](icordebugsymbolprovider-getmethodprops-method.md)
- [ICorDebugSymbolProvider, interfejs](icordebugsymbolprovider-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)

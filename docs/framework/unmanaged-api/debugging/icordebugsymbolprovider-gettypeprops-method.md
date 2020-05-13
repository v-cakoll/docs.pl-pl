---
title: 'ICorDebugSymbolProvider:: GetTypeProps, Metoda'
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
ms.openlocfilehash: e116716284bb2081edb669e7fc9083cde10f6457
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379362"
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
 podczas Rozmiar `signature` tablicy. Zobacz sekcję Uwagi.  
  
 `pcbSignature`  
 określoną określoną Wskaźnik do rozmiaru zwróconej `signature` tablicy.  
  
 `signature`  
 określoną Bufor, który przechowuje sygnatury elementu TypeSpec wszystkich parametrów ogólnych.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać wymagany rozmiar `signature` tablicy typu, należy ustawić `cbSignature` argument na 0 i `signature` na **wartość null**. Gdy metoda zwraca, `pcbSignature` będzie zawierać liczbę bajtów wymaganych przez `signature` tablicę.  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [GetMethodProps, metoda](icordebugsymbolprovider-getmethodprops-method.md)
- [ICorDebugSymbolProvider, interfejs](icordebugsymbolprovider-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)

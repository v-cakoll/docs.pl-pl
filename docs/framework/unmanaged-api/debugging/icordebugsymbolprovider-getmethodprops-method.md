---
title: 'ICorDebugSymbolProvider:: GetMethodProps —, Metoda'
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
ms.openlocfilehash: 811106216e1e454ddf342af1578f74c80ba2acc9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138832"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a>ICorDebugSymbolProvider:: GetMethodProps —, Metoda
Zwraca informacje o właściwościach metody, takich jak token metadanych metody i informacje o jego ogólnych parametrach, w którym znajduje się względny adres wirtualny (RVA) w tej metodzie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetMethodProps(  
   [in]  ULONG32 codeRva,  
   [out] mdToken *pMethodToken,  
   [out] ULONG32 *pcGenericParams,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `codeRVA`  
 podczas Względny adres wirtualny w metodzie, o które informacje mają być pobierane.  
  
 `pMethodToken`  
 określoną Wskaźnik do tokenu metadanych metody.  
  
 `pcGenericParams`  
 określoną Wskaźnik do liczby parametrów ogólnych skojarzonych z tą metodą.  
  
 `cbSignature`  
 podczas Rozmiar tablicy `signature`. Zobacz sekcję Uwagi.  
  
 `pcbSignature`  
 określoną Wskaźnik do rozmiaru zwróconej tablicy `signature`.  
  
 `signature`  
 określoną Bufor, który przechowuje sygnatury elementu TypeSpec wszystkich parametrów ogólnych.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać wymagany rozmiar tablicy `signature` metody, ustaw argument `cbSignature` na wartość 0, a `signature` na **wartość null**. Gdy metoda zwraca, `pcbSignature` będzie zawierać liczbę bajtów wymaganą dla `signature` tablicy.  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetTypeProps, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)
- [ICorDebugSymbolProvider, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

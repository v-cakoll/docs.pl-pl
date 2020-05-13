---
title: 'ICorDebugSymbolProvider:: GetMethodProps —, Metoda'
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
ms.openlocfilehash: c9e73c4de7389405d9e4b643036709ff2dbb82e6
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379562"
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
 podczas Rozmiar `signature` tablicy. Zobacz sekcję Uwagi.  
  
 `pcbSignature`  
 określoną Wskaźnik do rozmiaru zwróconej `signature` tablicy.  
  
 `signature`  
 określoną Bufor, który przechowuje sygnatury elementu TypeSpec wszystkich parametrów ogólnych.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać wymagany rozmiar `signature` tablicy metody, należy ustawić `cbSignature` argument na 0 i `signature` na **wartość null**. Gdy metoda zwraca, `pcbSignature` będzie zawierać liczbę bajtów wymaganych przez `signature` tablicę.  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [GetTypeProps, metoda](icordebugsymbolprovider-gettypeprops-method.md)
- [ICorDebugSymbolProvider, interfejs](icordebugsymbolprovider-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)

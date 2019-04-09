---
title: Metoda ICorDebugSymbolProvider::GetMethodProps
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 784fcb10e9c0c3c6ff50c25d47bb4fb3fd5762ba
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59161112"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a>Metoda ICorDebugSymbolProvider::GetMethodProps
Zwraca informacje o właściwości metody, takie jak metody token metadanych oraz informacje o jego parametrów ogólnych, biorąc pod uwagę względnych adresów wirtualnych (RVA) w tej metodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 [in] Względny adres wirtualny w metodzie o tym, jakie informacje są do pobrania.  
  
 `pMethodToken`  
 [out] Wskaźnik do metody token metadanych.  
  
 `pcGenericParams`  
 [out] Wskaźnik do liczby parametrów ogólnych skojarzone z tą metodą.  
  
 `cbSignature`  
 [in] Rozmiar `signature` tablicy. Zobacz sekcję Uwagi.  
  
 `pcbSignature`  
 [out] Wskaźnik do rozmiaru zwracanego `signature` tablicy.  
  
 `signature`  
 [out] Buforu, który zawiera sygnatury elementu typespec wszystkich parametrów ogólnych.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać wymagany rozmiar metody `signature` tablicy, należy ustawić `cbSignature` argument 0 i `signature` do **null**. Po powrocie z metody `pcbSignature` będzie zawierać liczbę bajtów wymaganą dla `signature` tablicy.  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z architekturą .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetTypeProps, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)
- [ICorDebugSymbolProvider, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [Debugowanie — Interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

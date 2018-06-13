---
title: ICorDebugSymbolProvider::GetMethodProps — metoda
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f52d20b9cb717d72d660bb19a0474c3e5b293ab4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422194"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a>ICorDebugSymbolProvider::GetMethodProps — metoda
Zwraca informacje o właściwości metody, takie jak token metadanych oraz informacje o jego parametrów ogólnych — metoda podany wirtualny adres względny (RVA) w tej metody.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `codeRVA`  
 [in] Wirtualny adres względny w metodzie o tym, które ma być pobrana informacji.  
  
 `pMethodToken`  
 [out] Wskaźnik do metody token metadanych.  
  
 `pcGenericParams`  
 [out] Wskaźnik do liczby parametrów ogólnych skojarzonych z tą metodą.  
  
 `cbSignature`  
 [in] Rozmiar `signature` tablicy. W sekcji uwag.  
  
 `pcbSignature`  
 [out] Wskaźnik do rozmiaru zwracana `signature` tablicy.  
  
 `signature`  
 [out] Buforu, który zawiera podpisy elementu typespec wszystkich parametrów ogólnych.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać wymagany rozmiar metody `signature` tablicy, ustaw `cbSignature` argument 0 i `signature` do **null**. Gdy metoda zwróci wartość, `pcbSignature` będzie zawierać liczbę bajtów wymaganą dla `signature` tablicy.  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z platformą .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [GetTypeProps, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)  
 [ICorDebugSymbolProvider, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

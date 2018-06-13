---
title: ICorDebugSymbolProvider::GetTypeProps — metoda
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3398e01912309c057cd1e01e8fc0af6c62f976bf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421603"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a>ICorDebugSymbolProvider::GetTypeProps — metoda
Zwraca informacje dotyczące typu właściwości, takie jak liczba podpisu jego parametry ogólne, podany wirtualny adres względny (RVA) w vtable.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `tableRva`  
 [in] Wirtualny adres względny (RVA) w vtable.  
  
 `cbSignature`  
 [in] Rozmiar `signature` tablicy. W sekcji uwag.  
  
 `pcbSignature`  
 [out] [out] Wskaźnik do rozmiaru zwracana `signature` tablicy.  
  
 `signature`  
 [out] Buforu, który zawiera podpisy elementu typespec wszystkich parametrów ogólnych.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać wymagany rozmiar typu `signature` tablicy, ustaw `cbSignature` argument 0 i `signature` do **null**. Gdy metoda zwróci wartość, `pcbSignature` będzie zawierać liczbę bajtów wymaganą dla `signature` tablicy.  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z platformą .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [GetMethodProps, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)  
 [ICorDebugSymbolProvider, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

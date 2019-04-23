---
title: Metoda ICorDebugSymbolProvider::GetMethodParameterSymbols
ms.date: 03/30/2017
ms.assetid: 58b7c0b9-f6ad-4b49-b92d-0e421cfd0ec6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98efd1446c88c3a6c004b5a3254c9db835a43804
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197376"
---
# <a name="icordebugsymbolprovidergetmethodparametersymbols-method"></a>Metoda ICorDebugSymbolProvider::GetMethodParameterSymbols
Pobiera symbole parametru metody podany wirtualny adres względny (RVA) tej metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetMethodParameterSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `nativeRVA`  
 [in] Natywne wirtualny adres względny metody.  
  
 `cRequestedSymbols`  
 [in] Liczba symbole lokalne żądanie.  
  
 `pcFetchedSymbols`  
 [out] Wskaźnik do liczby symboli pobierane przez metodę.  
  
 `pcFetchedSymbols`  
 [out] Wskaźnik do [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) tablicę, która zawiera symbole lokalne metody.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z architekturą .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetMethodLocalSymbols, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)
- [ICorDebugSymbolProvider, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

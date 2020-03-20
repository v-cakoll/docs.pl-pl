---
title: ICorDebugSymbolProvider::Metoda GetCodeRange
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
ms.openlocfilehash: 81babade2ba499ce9326c664e83fa582abbd216f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178478"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a>ICorDebugSymbolProvider::Metoda GetCodeRange
Pobiera adres początkowy metody i rozmiar, biorąc pod uwagę względny adres wirtualny (RVA) w metodzie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,
   [out] ULONG32* pCodeStartAddress,
   [out] ULONG32* pCodeSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `codeRva`  
 [w] Względny adres wirtualny (RVA) w metodzie.  
  
 `pCodeStartAddress`  
 [na zewnątrz] Wskaźnik do adresu początkowego metody.  
  
 `pCodeSize`  
 Wskaźnik do rozmiaru kodu metody (liczba bajtów kodu metody).  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ta metoda jest dostępna tylko w przypadku platformy .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugSymbolProvider, interfejs](icordebugsymbolprovider-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)

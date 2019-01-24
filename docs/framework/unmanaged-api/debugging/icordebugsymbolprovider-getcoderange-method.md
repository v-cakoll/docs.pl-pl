---
title: ICorDebugSymbolProvider::GetCodeRange Method
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bfaa8ce16a3874d28e06bdb77f1e903548c0a03b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684791"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a>ICorDebugSymbolProvider::GetCodeRange Method
Pobiera adres początkowy metody i biorąc względnych adresów wirtualnych (RVA) w metodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,   
   [out] ULONG32* pCodeStartAddress,   
   [out] ULONG32* pCodeSize  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `codeRva`  
 [in] Wirtualny adres względny (RVA) w metodzie.  
  
 `pCodeStartAddress`  
 [out] Wskaźnik do adres początkowy metody.  
  
 `pCodeSize`  
 Wskaźnik do rozmiaru kodu — metoda (liczba bajtów kodu metody).  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z architekturą .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorDebugSymbolProvider, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

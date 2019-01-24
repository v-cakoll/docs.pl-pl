---
title: Metoda ICorDebugSymbolProvider2::GetFrameProps
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd8cc461519b01a9bf62a28610386e51630060d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646204"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a>Metoda ICorDebugSymbolProvider2::GetFrameProps
Zwraca metodę uruchamiania względny adres wirtualny, metody i podany kod względny adres wirtualny nadrzędnej ramki.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `codeRva`  
 [in] Względny adres wirtualny kodu.  
  
 `pCodeStartRva`  
 [out] Wskaźnik do metody uruchamiania względny adres wirtualny.  
  
 `pParentFrameStartRva`  
 [out] Wskaźnik do ramki uruchamianie względny adres wirtualny.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z architekturą .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorDebugSymbolProvider2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

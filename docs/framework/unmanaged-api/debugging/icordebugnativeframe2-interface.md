---
title: ICorDebugNativeFrame2 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2
helpviewer_keywords:
- ICorDebugNativeFrame2 interface [.NET Framework debugging]
ms.assetid: 52a80838-af36-4399-bc97-d8a4c6d76df2
topic_type:
- apiref
ms.openlocfilehash: bff6dea0e870cf62734fa583eefa481c594481b1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096521"
---
# <a name="icordebugnativeframe2-interface"></a>ICorDebugNativeFrame2 — Interfejs
Dostarcza metody testowania relacji podrzędnych i nadrzędnych ramek.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IsChild, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ischild-method.md)|Określa, czy bieżąca ramka jest ramką podrzędną.|  
|[IsMatchingParentFrame, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md)|Określa, czy określona ramka jest elementem nadrzędnym bieżącej ramki.|  
|[GetStackParameterSize, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-getstackparametersize-method.md)|Zwraca skumulowany rozmiar parametrów na stosie w systemach operacyjnych x86.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs logicznie rozszerza interfejs "ICorDebugNativeFrame".  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)

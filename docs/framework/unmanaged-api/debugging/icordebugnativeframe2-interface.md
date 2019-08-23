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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 638ce7933ededf2ff7b03b1c5aed7f6bdbfebc6c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912791"
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
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)

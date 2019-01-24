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
ms.openlocfilehash: cc664d308d4db3e97597d785eda159e32255fa54
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520376"
---
# <a name="icordebugnativeframe2-interface"></a>ICorDebugNativeFrame2 — Interfejs
Dostarcza metody testowania relacji podrzędnych i nadrzędnych ramek.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IsChild, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ischild-method.md)|Określa, czy bieżące ramce ramki podrzędnej.|  
|[IsMatchingParentFrame, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md)|Określa, czy ramki o określonym nadrzędny bieżącej ramki.|  
|[GetStackParameterSize, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-getstackparametersize-method.md)|Zwraca całkowity rozmiar wszystkich parametrów na stosie na x86 systemów operacyjnych.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs rozszerza logicznie interfejsu "icordebugnativeframe —".  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)

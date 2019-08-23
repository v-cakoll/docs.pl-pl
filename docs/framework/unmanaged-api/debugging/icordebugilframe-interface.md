---
title: ICorDebugILFrame, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame
helpviewer_keywords:
- ICorDebugILFrame interface [.NET Framework debugging]
ms.assetid: d5cf5056-da4d-4629-914d-afe42a5393df
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0a40436fcf1485c5d08d175b0396af2b6870c19a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917021"
---
# <a name="icordebugilframe-interface"></a>ICorDebugILFrame, interfejs

Przedstawia ramkę stosu kodu języka pośredniego firmy Microsoft (MSIL). Ten interfejs jest podklasą interfejsu ICorDebugFrame.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CanSetIP, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|Pobiera wartość wskazującą, czy jest bezpieczna, aby ustawić wskaźnik instrukcji na określoną lokalizację przesunięcia.|  
|[EnumerateArguments, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|Pobiera moduł wyliczający dla argumentów w tej ramce.|  
|[EnumerateLocalVariables, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|Pobiera moduł wyliczający dla zmiennych lokalnych w tej ramce.|  
|[GetArgument, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|Pobiera wartość określonego argumentu w tej ramce stosu MSIL.|  
|[GetIP, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|Pobiera wartość wskaźnika instrukcji i wartość kombinacji bitowej opisującą sposób uzyskiwania wartości wskaźnika instrukcji.|  
|[GetLocalVariable, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|Pobiera wartość określonej zmiennej lokalnej w tej ramce stosu MSIL.|  
|[GetStackDepth, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|Nie zaimplementowane.|  
|[GetStackValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|Nie zaimplementowane.|  
|[SetIP, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|Ustawia wskaźnik instrukcji na określoną lokalizację przesunięcia w kodzie MSIL.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugILFrame` Interfejs jest wyspecjalizowanym interfejsem ICorDebugFrame. Jest używana w przypadku ramek kodu MSIL lub dla ramek skompilowanych w trybie just-in-Time (JIT). Ramki skompilowane JIT implementują `ICorDebugILFrame` interfejs i interfejs ICorDebugNativeFrame.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

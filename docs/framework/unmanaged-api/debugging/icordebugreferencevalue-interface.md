---
title: ICorDebugReferenceValue — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue
helpviewer_keywords:
- ICorDebugReferenceValue interface [.NET Framework debugging]
ms.assetid: 2040e2be-119a-4cfb-ae52-b0b6f052665c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4709d1b8126436d4400c788891960100915cd1bc
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971440"
---
# <a name="icordebugreferencevalue-interface"></a>ICorDebugReferenceValue — Interfejs
Udostępnia metody zarządzające wartość, która jest odwołanie do obiektu. (Czyli ten interfejs udostępnia metody zarządzające wskaźnik). Ten interfejs implementuje "ICorDebugValue".  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Dereference, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|Pobiera obiekt, do którego istnieje odwołanie.|  
|[DereferenceStrong, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|Nie zaimplementowano. Nie wywołuj tej metody.|  
|[GetValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|Pobiera bieżący adres pamięci przywoływanego obiektu.|  
|[IsNull, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|Pobiera wartość wskazującą, czy to `ICorDebugReferenceValue` jest wartość null, w którym to przypadku `ICorDebugReferenceValue` nie wskazuje na obiekt.|  
|[SetValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|Ustawia bieżący adres pamięci. Oznacza to, że ta metoda Określa `ICorDebugReferenceValue` wskaż obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe języka wspólnego (CLR) może wykonać wyrzucania elementów bezużytecznych na obiektach, gdy debugowany proces jest kontynuowany. Wyrzucanie elementów bezużytecznych może poruszanie się obiekty w pamięci. `ICorDebugReferenceValue` Albo współpracują z wyrzucania elementów bezużytecznych tak, aby pobierał informacje o jest aktualizowany po wyrzucania elementów bezużytecznych lub go zostaną unieważnione niejawnie przed wyrzucania elementów bezużytecznych.  
  
 `ICorDebugReferenceValue` Obiekt może być niejawnie unieważniony po ciąg dalszy debugowanego procesu. Pochodne icordebughandlevalue "—" nie zostaje unieważniony, dopóki zostanie jawnie wydane lub ujawnione.  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także


- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

---
title: ICorDebugClass2, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugClass2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2
helpviewer_keywords:
- ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 5416de70-43f2-4cdf-a11f-d570759c9c0c
topic_type:
- apiref
ms.openlocfilehash: 795e9f4862992d95eeef98a986545cca47d828c6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784141"
---
# <a name="icordebugclass2-interface"></a>ICorDebugClass2, interfejs

Reprezentuje klasę generyczną lub klasę z parametrem metody typu <xref:System.Type>. Ten interfejs rozszerza [ICorDebugClass](icordebugclass-interface.md).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetParameterizedType, metoda](icordebugclass2-getparameterizedtype-method.md)|Pobiera deklarację typu dla tej klasy.|  
|[SetJMCStatus, metoda](icordebugclass2-setjmcstatus-method.md)|Dla każdej metody tej klasy ustawia wartość wskazującą, czy metoda jest kodem zdefiniowanym przez użytkownika.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugClass, interfejs](icordebugclass-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)

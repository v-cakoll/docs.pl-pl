---
title: ICorDebugAppDomainEnum, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomainEnum
helpviewer_keywords:
- ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: e9226e6e-ca2c-428e-bb38-0c099210f507
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da1fc949109455cf50767191a99a8a727116f77c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59155197"
---
# <a name="icordebugappdomainenum-interface"></a>ICorDebugAppDomainEnum, interfejs

Udostępnia `Next` metody, która zwraca określoną liczbę `ICorDebugAppDomainEnum` wartości, zaczynając od następnej pozycji w wyliczeniu. Ten interfejs jest podklasą "ICorDebugEnum".  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Next, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-next-method.md)|Pobiera określoną liczbę domen aplikacji z kolekcji, począwszy od bieżącej pozycji kursora.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebug — Interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [Debugowanie — Interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

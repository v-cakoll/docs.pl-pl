---
title: ICorDebugDataTarget::GetPlatform — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetPlatform Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetPlatform
helpviewer_keywords:
- GetPlatform method [.NET Framework debugging]
- ICorDebugDataTarget::GetPlatform method [.NET Framework debugging]
ms.assetid: 9ee96c9d-7a3d-4129-a6cc-7675c7f2dda4
topic_type:
- apiref
ms.openlocfilehash: 3654c94975d16e35d5c3d8e762730d17509a2c6d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788878"
---
# <a name="icordebugdatatargetgetplatform-method"></a>ICorDebugDataTarget::GetPlatform — Metoda
Zawiera informacje na temat platformy, w tym architektury procesora i systemu operacyjnego, na których jest uruchomiony proces docelowy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
## <a name="parameters"></a>Parametry  
 `pTargetPlatform`  
 określoną Wskaźnik do wyliczenia [CorDebugPlatformEnum —](cordebugplatform-enumeration.md) , który opisuje platformę docelową.  
  
## <a name="remarks"></a>Uwagi  
 Wartość zwracana `CorDebugPlatformEnum` wyliczeniem jest używana przez interfejs [ICorDebug](icordebug-interface.md) , aby określić szczegóły procesu docelowego, takie jak rozmiar wskaźnika, układ przestrzeni adresowej, zestaw rejestru, format instrukcji, układ kontekstu i konwencje wywoływania.  
  
 Wartość `pTargetPlatform` może odwoływać się do platformy, która jest emulowana dla elementu docelowego zamiast określania rzeczywistego sprzętu w użyciu. Na przykład proces uruchomiony w środowisku systemu Windows w systemie Windows (WOW) w 64-bitowej wersji systemu operacyjnego Windows powinien używać wartości `CORDB_PLATFORM_WINDOWS_X86` wyliczenia [CorDebugPlatformEnum —](cordebugplatform-enumeration.md) .  
  
 Ta metoda musi zakończyć się pomyślnie. Jeśli to się nie powiedzie, platforma docelowa będzie bezużyteczny. Metoda może zakończyć się niepowodzeniem z następujących powodów:  
  
- Platforma, która jest emulowana dla elementu docelowego, nie nadaje się do użytku.  
  
- Rzeczywisty sprzęt na platformie docelowej nie nadaje się do użytku.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugDataTarget, interfejs](icordebugdatatarget-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)

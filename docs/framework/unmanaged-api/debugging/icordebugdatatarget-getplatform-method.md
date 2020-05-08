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
ms.openlocfilehash: 3df35d52a4e5209b282ccef653b065bdcf1f8fe4
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976541"
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
 Wartość `CorDebugPlatformEnum` zwracana Wyliczenie jest używana przez interfejs [ICorDebug](icordebug-interface.md) do określenia szczegółów procesu docelowego, takich jak rozmiar wskaźnika, układ przestrzeni adresowej, zestaw rejestru, format instrukcji, układ kontekstu i konwencje wywoływania.  
  
 `pTargetPlatform` Wartość może odnosić się do platformy, która jest emulowana dla elementu docelowego zamiast określania rzeczywistego sprzętu w użyciu. Na przykład proces uruchomiony w środowisku systemu Windows w systemie Windows (WOW) w 64-bitowej wersji systemu operacyjnego Windows powinien używać `CORDB_PLATFORM_WINDOWS_X86` wartości wyliczenia [CorDebugPlatformEnum —](cordebugplatform-enumeration.md) .  
  
 Ta metoda musi zakończyć się pomyślnie. Jeśli to się nie powiedzie, platforma docelowa będzie bezużyteczny. Metoda może zakończyć się niepowodzeniem z następujących powodów:  
  
- Platforma, która jest emulowana dla elementu docelowego, nie nadaje się do użytku.  
  
- Rzeczywisty sprzęt na platformie docelowej nie nadaje się do użytku.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugDataTarget — Interfejs](icordebugdatatarget-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)

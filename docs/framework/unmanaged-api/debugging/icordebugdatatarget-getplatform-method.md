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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 17ae761b2d48552aded8191ddbea26552d8da277
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411021"
---
# <a name="icordebugdatatargetgetplatform-method"></a>ICorDebugDataTarget::GetPlatform — Metoda
Zawiera informacje o platformie, w tym architektury procesora i systemu operacyjnego, na którym jest uruchomiony proces docelowy.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pTargetPlatform`  
 [out] Wskaźnik do [cordebugplatformenum —](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) wyliczenie opisujące platformy docelowej.  
  
## <a name="remarks"></a>Uwagi  
 `CorDebugPlatformEnum` Zwracana wartość wyliczenia jest używany przez [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interfejsu, aby określić szczegóły procesu docelowego, na przykład jego rozmiar wskaźnika, układ przestrzeni adresów, zestaw rejestru, format instrukcji, układ kontekstu i Konwencje wywoływania.  
  
 `pTargetPlatform` Wartość może odwoływać się do platformy, która jest emulowane dla elementu docelowego zamiast określania rzeczywistego sprzętu w użyciu. Na przykład, należy użyć procesu, który jest uruchomiony w systemie Windows w środowisku Windows (WOW) w 64-bitowej wersji systemu operacyjnego Windows `CORDB_PLATFORM_WINDOWS_X86` wartość [cordebugplatformenum —](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) wyliczenia.  
  
 Ta metoda musi zakończyć się pomyślnie. W przypadku niepowodzenia platformy docelowej jest korzystanie z niej. Metoda może się nie powieść z następujących powodów:  
  
-   Platforma, która jest emulowane dla obiekt docelowy jest korzystanie z niej.  
  
-   Nadaje się sprzętem na platformie docelowej.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugDataTarget, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)

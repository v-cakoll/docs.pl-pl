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
ms.openlocfilehash: 309c31dacd801f1c46a2d37932124638bc157cd6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214030"
---
# <a name="icordebugdatatargetgetplatform-method"></a>ICorDebugDataTarget::GetPlatform — Metoda
Zawiera informacje dotyczące platformy, w tym architektury procesora i systemu operacyjnego, na którym jest uruchomiony proces docelowy.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
## <a name="parameters"></a>Parametry  
 `pTargetPlatform`  
 [out] Wskaźnik do [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) wyliczenie opisujące platformę docelową.  
  
## <a name="remarks"></a>Uwagi  
 `CorDebugPlatformEnum` Zwracana wartość wyliczenia jest używany przez [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interfejsu, aby określić szczegóły procesu docelowego, takie jak rozmiar wskaźnika, układ przestrzeni adresowej, zarejestrować zestaw, format instrukcji, układ kontekstu i Konwencje wywoływania.  
  
 `pTargetPlatform` Wartość może odwoływać się do platformy, która jest emulowane dla elementu docelowego zamiast określania sprzęt rzeczywisty w użyciu. Na przykład, należy użyć procesu, który jest uruchomiony w Windows w środowisku Windows (WOW) w 64-bitowej wersji systemu operacyjnego Windows `CORDB_PLATFORM_WINDOWS_X86` wartość [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) wyliczenia.  
  
 Ta metoda musi zakończyć się pomyślnie. Jeśli nie powiedzie się, platformą docelową jest bezużyteczny. Metoda może się nie powieść z następujących powodów:  
  
-   Platforma, która jest emulowane dla obiektu docelowego jest bezużyteczny.  
  
-   Nadaje się sprzętem na platformie docelowej.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugDataTarget — Interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [Debugowanie — Interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)

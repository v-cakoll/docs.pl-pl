---
title: ICorDebugProcess4::ProcessStateChanged Method
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4::ProcessStateChanged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4::ProcessStateChanged
helpviewer_keywords:
- ICorDebugProcess4::ProcessStateChanged method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: b77dd1277e7d23729f30d9d495c5417055a22759
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948811"
---
# <a name="icordebugprocess4processstatechanged-method"></a>ICorDebugProcess4::ProcessStateChanged Method

Powiadamia potoku ICorDebug, poza debugera proces kontynuuje wykonywanie debugee.

## <a name="syntax"></a>Składnia

```
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a>Parametry

 `eChange`\
[in] Członek [wyliczenie CorDebugStateChange](cordebugstatechange-enumeration.md) opisujące zmianę stanu wykonywania procesu.

## <a name="remarks"></a>Uwagi

Podana metoda jest częścią `ICorDebugProcess4` interfejs i odpowiada czwarte miejsce tabeli wirtualnej metody.

## <a name="requirements"></a>Wymagania

 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

 **Nagłówek:** Brak

 **Biblioteka:** Brak
 
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [ICorDebugProcess4 Interface](icordebugprocess4-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)
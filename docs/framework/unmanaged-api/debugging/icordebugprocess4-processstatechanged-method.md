---
title: ICorDebugProcess4::PproessStateChanged Method
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
ms.openlocfilehash: a6f36f5b86b4fa58ce2a4ef4aa23d527f797a5a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178631"
---
# <a name="icordebugprocess4processstatechanged-method"></a>ICorDebugProcess4::PproessStateChanged Method

Powiadamia potokU ICorDebug, że debuger poza procesem kontynuuje wykonanie debugee.

## <a name="syntax"></a>Składnia

```cpp
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a>Parametry

 `eChange`\
[w] Członek [wyliczenia CorDebugStateChange](cordebugstatechange-enumeration.md) opisujące zmiany w stanie wykonywania procesu.

## <a name="remarks"></a>Uwagi

Podana metoda jest `ICorDebugProcess4` częścią interfejsu i odpowiada czwartemu slotowi tabeli metod wirtualnych.

## <a name="requirements"></a>Wymagania

 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

 **Nagłówek:** Brak

 **Biblioteka:** Brak

 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Zobacz też

- [ICorDebugProcess4, interfejs](icordebugprocess4-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
- [Debugging](index.md)

---
title: ICorDebugProcess4::P rocessStateChanged Metoda
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
ms.openlocfilehash: 910c411d2c63ce2c6cf262e28e08546657dc2a4c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213572"
---
# <a name="icordebugprocess4processstatechanged-method"></a>ICorDebugProcess4::P rocessStateChanged Metoda

Powiadamia potok ICorDebug, że debuger out of process kontynuuje wykonywanie operacji debugee.

## <a name="syntax"></a>Składnia

```cpp
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a>Parametry

 `eChange`\
podczas Składowa [wyliczenia CorDebugStateChange](cordebugstatechange-enumeration.md) opisującego zmianę stanu wykonywania procesu.

## <a name="remarks"></a>Uwagi

Podana metoda jest częścią `ICorDebugProcess4` interfejsu i odpowiada czwartemu gnieździe tabeli metody wirtualnej.

## <a name="requirements"></a>Wymagania

 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

 **Nagłówek:** Dawaj

 **Biblioteka:** Dawaj

 **.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Zobacz też

- [ICorDebugProcess4, interfejs](icordebugprocess4-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)

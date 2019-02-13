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
ms.openlocfilehash: b434f30fc187af8b118ac926fec96d28182b0bfc
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221378"
---
# <a name="icordebugprocess4processstatechanged-method"></a>ICorDebugProcess4::ProcessStateChanged Method

Powiadamia potoku ICorDebug, poza debugera proces kontynuuje wykonywanie debugee.

## <a name="syntax"></a>Składnia

```
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

#### <a name="parameters"></a>Parametry

 `eChange`

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

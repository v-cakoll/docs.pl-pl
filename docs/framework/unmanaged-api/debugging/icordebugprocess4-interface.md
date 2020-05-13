---
title: ICorDebugProcess4, interfejs
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4
helpviewer_keywords:
- ICorDebugProcess4 interface [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: fcf725ea98fa4351e72cf592f92968ee2233ecb0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213585"
---
# <a name="icordebugprocess4-interface"></a>ICorDebugProcess4, interfejs

Zapewnia obsługę kontroli wykonywania poza procesem.

## <a name="methods"></a>Metody

| Metoda                                                                 | Opis                                                                                             |
| ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| [ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) | Powiadamia potok ICorDebug, że debuger out of process kontynuuje wykonywanie operacji debugee. |

## <a name="remarks"></a>Uwagi

Ten interfejs jest wewnątrz środowiska uruchomieniowego i nie jest udostępniany przez żadne nagłówki lub pliki bibliotek. Jest to jednak interfejs COM pochodzący z `IUnknown` identyfikatora GUID `E930C679-78AF-4953-8AB7-B0AABF0F9F80` , który można uzyskać za pomocą zwykłych mechanizmów com.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówek:** Dawaj

**Biblioteka:** Dawaj

**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Zobacz też

- [Debugowanie — Interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)

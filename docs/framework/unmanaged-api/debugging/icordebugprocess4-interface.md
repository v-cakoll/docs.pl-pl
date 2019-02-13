---
title: ICorDebugProcess4 Interface
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
ms.openlocfilehash: 1bdc958f2516bcd7c2eb74312fbf478e6d49535a
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221377"
---
# <a name="icordebugprocess4-interface"></a>ICorDebugProcess4 Interface

Zapewnia obsługę poza Kontrola wykonywania procesu.

## <a name="methods"></a>Metody

| Metoda                                                                 | Opis                                                                                             |
| ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| [ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) | Powiadamia potoku ICorDebug, poza debugera proces kontynuuje wykonywanie debugee. |

## <a name="remarks"></a>Uwagi

Ten interfejs znajduje się wewnątrz środowiska uruchomieniowego i nie jest dostępna za pośrednictwem wszystkich nagłówków lub pliki biblioteki. Jednak jest interfejsem COM, która pochodzi od klasy `IUnknown` o identyfikatorze GUID `E930C679-78AF-4953-8AB7-B0AABF0F9F80` , można uzyskać za pośrednictwem zwykłych mechanizmów COM.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

**Nagłówek:** Brak

**Biblioteka:** Brak

**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)

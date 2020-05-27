---
title: CorThreadSafetyOptions — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorThreadSafetyOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorThreadSafetyOptions
helpviewer_keywords:
- CorThreadSafetyOptions enumeration [.NET Framework metadata]
ms.assetid: dae07d9b-df51-488c-b17e-52d6e48217bd
topic_type:
- apiref
ms.openlocfilehash: 8c0527a7bc3cde7344bf809dc8e6f5a3fac04852
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007510"
---
# <a name="corthreadsafetyoptions-enumeration"></a>CorThreadSafetyOptions — Wyliczenie

Określa flagi, aby wybrać opcje bezpieczeństwa wątku.

## <a name="syntax"></a>Składnia

```cpp
typedef enum CorThreadSafetyOptions {
    MDThreadSafetyDefault       = 0x00000000,
    MDThreadSafetyOff           = 0x00000000,
    MDThreadSafetyOn            = 0x00000001,
} CorThreadSafetyOptions;
```

## <a name="members"></a>Elementy członkowskie

|Członek|Opis|
|------------|-----------------|
|`MDThreadSafetyDefault`|Wartość domyślna. Analogicznie jak `MDThreadSafetyOff` .|
|`MDThreadSafetyOff`|Wskazuje, że nie można ustawić blokady czytnika/składnika zapisywania.|
|`MDThreadSafetyOn`|Wskazuje, że można ustawić blokadę czytnika/składnika zapisywania.|

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówek:** CorHdr. h

**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Zobacz też

- [Wyliczenia metadanych](metadata-enumerations.md)

---
title: COR_VERSION — Struktura
ms.date: 03/30/2017
api_name:
- COR_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_VERSION
helpviewer_keywords:
- COR_VERSION structure [.NET Framework debugging]
ms.assetid: 5efaee1c-a001-4c73-9525-4160f4c71567
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ffbe571ebc3d14c12e57b1f805d77e56e97d12e1
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274175"
---
# <a name="cor_version-structure"></a>COR_VERSION — Struktura
Przechowuje numer standardowej wersji 4-częściowej środowiska uruchomieniowego języka wspólnego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`dwMajor`|Główny numer wersji.|  
|`dwMinor`|Pomocniczy numer wersji.|  
|`dwBuild`|Numer kompilacji.|  
|`dwSubBuild`|Numer kompilacji podrzędnej.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli numer wersji to 1.0.3705.288, 1 jest głównym numerem wersji, 0 jest numerem wersji pomocniczej, 3705 jest numerem kompilacji, a 288 jest numerem kompilacji podrzędnej.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury debugowania](debugging-structures.md)
- [Debugowanie](index.md)

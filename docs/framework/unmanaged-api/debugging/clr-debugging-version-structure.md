---
title: CLR_DEBUGGING_VERSION — Struktura
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_VERSION
helpviewer_keywords:
- CLR_DEBUGGING_VERSION structure [.NET Framework debugging]
ms.assetid: 4d821186-3ddf-405a-ac44-d79438a9f7f3
topic_type:
- apiref
ms.openlocfilehash: 651b916a0e3ca178432094428611f9bcc8f0fd17
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132417"
---
# <a name="clr_debugging_version-structure"></a>CLR_DEBUGGING_VERSION — Struktura
Definiuje wersję produktu środowiska uruchomieniowego języka wspólnego (CLR) do celów debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _CLR_DEBUGGING_VERSION  
{  
    WORD wStructVersion;
    WORD wMajor;
    WORD wMinor;
    WORD wBuild;
    WORD wRevision;
} CLR_DEBUGGING_VERSION;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`wStructVersion`|Numer wersji struktury|  
|`wMajor`|Główny numer wersji.|  
|`wMinor`|Pomocniczy numer wersji.|  
|`wBuild`|Numer kompilacji.|  
|`wRevision`|Numer poprawki.|  
  
## <a name="remarks"></a>Uwagi  
 Struktura `CLR_DEBUGGING_VERSION` jest taka sama jak struktura COR_VERSION, jednak struktura `CLR_DEBUGGING_VERSION` zawiera dodatkowe pole wersji struktury (`wStructVersion`). Obecnie to pole musi mieć wartość zero.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury debugowania](debugging-structures.md)
- [Debugowanie](index.md)

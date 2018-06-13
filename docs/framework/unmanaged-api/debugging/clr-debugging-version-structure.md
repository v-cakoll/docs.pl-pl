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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4be232ab557d582f3521b8775108c004b5a3dd78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403308"
---
# <a name="clrdebuggingversion-structure"></a>CLR_DEBUGGING_VERSION — Struktura
Określa wersję produktu środowisko uruchomieniowe języka wspólnego (CLR) na potrzeby debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
Typedef struct _CLR_DEBUGGING_VERSION  
{  
WORD wStructVersion;  
WORD wMajor;   
WORD wMinor;  
WORD wBuild;  
WORD wRevision;  
}  CLR_DEBUGGING_VERSION;  
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
 `CLR_DEBUGGING_VERSION` Struktura jest taka sama jak cor_version — struktura, jednak, `CLR_DEBUGGING_VERSION` struktura zawiera pola wersji struktury dodatkowe (`wStructVersion`). Obecnie to pole musi mieć ustawioną wartość zero.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)

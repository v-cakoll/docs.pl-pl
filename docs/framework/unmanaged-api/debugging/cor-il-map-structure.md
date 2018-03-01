---
title: "COR_IL_MAP — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- COR_IL_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_IL_MAP
helpviewer_keywords:
- COR_IL_MAP structure [.NET Framework debugging]
ms.assetid: 534ebc17-963d-4b26-8375-8cd940281db3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2e2772833d75ced2209896ca37cf6cf37fb965f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corilmap-structure"></a>COR_IL_MAP — Struktura
Określa przesunięcie względną funkcji zmiany.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;   
    ULONG32 newOffset;   
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`oldOffset`|Stary Microsoft język pośredni (MSIL) przesuwane względem początku funkcji.|  
|`newOffset`|Nowe MSIL przesunięcie względem początku funkcji.|  
|`fAccurate`|`true`Jeśli mapowanie jest znany jako dokładne; w przeciwnym razie `false`.|  
  
## <a name="remarks"></a>Uwagi  
 Format mapy jest następujący: debuger zakłada, że `oldOffset` odwołuje się do MSIL przesunięcie w oryginalnym niezmodyfikowanego kodu MSIL. `newOffset` Parametr odwołuje się do odpowiedniego przesunięcie MSIL kodem nowy, instrumentacją.  
  
 Dla wykonywanie krok po kroku, aby działała poprawnie, powinny być spełnione następujące wymagania:  
  
-   Mapy mają być sortowane w kolejności rosnącej.  
  
-   Nie wymagają zmiany kolejności instrumentowanych kod MSIL.  
  
-   Oryginalny kod MSIL nie powinien zostać usunięty.  
  
-   Mapy powinny zawierać wpisy do wszystkich punktów sekwencji z programu (PDB) pliku mapowania.  
  
 Mapa nie interpolować Brak wpisów. W poniższym przykładzie przedstawiono mapy, a jego wyniki.  
  
 Mapa:  
  
-   Przesunięcie starego 0, 0 przesunięcie nowy  
  
-   Przesunięcie starego 5, 10 nowych przesunięcie  
  
-   Przesunięcie starego 9, 20 przesunięcie nowy  
  
 Wyniki:  
  
-   Stary przesunięciem równym 0, 1, 2, 3 lub 4 zostaną zmapowane do nowego przesunięciem równym 0.  
  
-   Stary przesunięcie 5, 6, 7 lub 8 zostaną zmapowane do nowego przesunięcie 10.  
  
-   Przesunięcie starego 9 lub nowszą zostaną zmapowane do nowego przesunięcie 20.  
  
-   Nowe przesunięcie 0, 1, 2, 3, 4, 5, 6, 7, 8 lub 9 zostaną zmapowane do starego przesunięciu 0.  
  
-   Nowe przesunięcie 10, 11, 12, 13, 14, 15, 16, 17, 18 lub 19 zostaną zmapowane do starego przesunięcie 5.  
  
-   Nowe przesunięcie 20 lub wyższe zostaną zmapowane do starego przesunięcie 9.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorProf.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)

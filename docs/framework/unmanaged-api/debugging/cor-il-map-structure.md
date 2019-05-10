---
title: COR_IL_MAP — Struktura
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 02a7bff021387f615c823b2df96615c1284cb82b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64617714"
---
# <a name="corilmap-structure"></a>COR_IL_MAP — Struktura
Określa przesunięcie względne funkcji zmiany.  
  
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
|`oldOffset`|Stary języka Microsoft intermediate language (MSIL) przesunięcie względem początku funkcji.|  
|`newOffset`|Nowe MSIL przesunięcie względem początku funkcji.|  
|`fAccurate`|`true` Jeśli wiadomo, że mapowanie jest dokładne; w przeciwnym razie `false`.|  
  
## <a name="remarks"></a>Uwagi  
 Format mapy jest w następujący sposób: Debuger będzie przyjęto założenie, że `oldOffset` odwołuje się do przesunięcia MSIL w kodzie MSIL oryginalne, niezmodyfikowanego. `newOffset` Parametr odnosi się do odpowiedniego przesunięcia MSIL kodem nowe, instrumentowaną.  
  
 Przechodzenie krok po kroku, aby zapewnić prawidłowe działanie, aby uzyskać być spełnione następujące wymagania:  
  
- Mapa powinny być sortowane w kolejności rosnącej.  
  
- Instrumentowane kod MSIL nie wymagają zmiany kolejności.  
  
- Oryginalny kod MSIL nie powinny być usuwane.  
  
- Mapa powinny zawierać wpisy, aby zamapować wszystkie punkty sekwencji z plik bazy danych (PDB) programu.  
  
 Mapa nie interpolacji Brak wpisów. Poniższy przykład pokazuje, mapy i jego wyniki.  
  
 Mapy:  
  
- Przesunięcie stare 0, 0 nowe przesunięcie  
  
- Przesunięcie stare 5, 10 nowych przesunięcie  
  
- Przesunięcie stare 9, 20 nowych przesunięcie  
  
 Liczba wyników:  
  
- Stary przesunięcia 0, 1, 2, 3 lub 4 zostanie zamapowane do nowego przesunięcia 0.  
  
- Przesunięcie stare 5, 6, 7 lub 8 zostaną odwzorowane na nowe przesunięcie 10.  
  
- Stary przesunięcie 9 lub nowszą zostaną odwzorowane na nowe przesunięcie 20.  
  
- Nowe przesunięcie 0, 1, 2, 3, 4, 5, 6, 7, 8 lub 9 zostaną zmapowane do starego przesunięciu 0.  
  
- Nowe przesunięcie 10, 11, 12, 13, 14, 15, 16, 17, 18 lub 19 zostanie zamapowane do starego przesunięcia 5.  
  
- Nowe przesunięcie 20 lub nowszej zostanie zamapowane do starego przesunięcia 9.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorProf.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)

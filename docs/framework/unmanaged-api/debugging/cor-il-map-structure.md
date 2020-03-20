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
ms.openlocfilehash: 4c79d0e4e37f3f884651e49c8fff6db72fac4f50
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179289"
---
# <a name="cor_il_map-structure"></a>COR_IL_MAP — Struktura
Określa zmiany względnego odsunięcia funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;
    ULONG32 newOffset;
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`oldOffset`|Stare przesunięcie języka pośredniego firmy Microsoft (MSIL) względem początku funkcji.|  
|`newOffset`|Nowe przesunięcie MSIL względem początku funkcji.|  
|`fAccurate`|`true`jeśli wiadomo, że mapowanie jest dokładne; w `false`przeciwnym razie , .|  
  
## <a name="remarks"></a>Uwagi  
 Format mapy jest następujący: Debuger przyjmie, `oldOffset` że odnosi się do przesunięcia MSIL w oryginalnym, niezmodyfikowanym kodzie MSIL. Parametr `newOffset` odnosi się do odpowiedniego przesunięcia MSIL w nowym, oprzyrządowanym kodzie.  
  
 W celu prawidłowego przechodzenia do pracy należy spełnić następujące wymagania:  
  
- Mapa powinna być sortowana w porządku rosnącym.  
  
- Instrumentowany kod MSIL nie powinien być ponownie zamówiony.  
  
- Oryginalny kod MSIL nie powinien zostać usunięty.  
  
- Mapa powinna zawierać wpisy do mapowania wszystkich punktów sekwencji z pliku bazy danych programu (PDB).  
  
 Mapa nie interpoluje brakujących wpisów. Poniższy przykład pokazuje mapę i jej wyniki.  
  
 Mapę:  
  
- 0 stare przesunięcie, 0 nowe przesunięcie  
  
- 5 stare przesunięcie, 10 nowych offset  
  
- 9 stare przesunięcie, 20 nowych offset  
  
 Wyniki:  
  
- Stare przesunięcie 0, 1, 2, 3 lub 4 zostanie odwzorowane na nowe przesunięcie 0.  
  
- Stare przesunięcie 5, 6, 7 lub 8 zostanie odwzorowane na nowe przesunięcie 10.  
  
- Stare przesunięcie 9 lub wyższe zostanie zmapowane na nowe przesunięcie 20.  
  
- Nowe przesunięcie 0, 1, 2, 3, 4, 5, 6, 7, 8 lub 9 zostanie odwzorowane na stare przesunięcie 0.  
  
- Nowe przesunięcie 10, 11, 12, 13, 14, 15, 16, 17, 18 lub 19 zostanie odwzorowane na stare przesunięcie 5.  
  
- Nowe przesunięcie 20 lub wyższe zostanie odwzorowane na stare przesunięcie 9.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorProf.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Struktury debugowania](debugging-structures.md)
- [Debugging](index.md)

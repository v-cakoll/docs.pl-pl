---
title: IMetaDataDispenser — Interfejs
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser
helpviewer_keywords:
- IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 989840b3-9822-4ce5-a6c5-b375d3340a7a
topic_type:
- apiref
ms.openlocfilehash: 2bdfe65dbf923ec61d91a259b5257d892fef53da
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007341"
---
# <a name="imetadatadispenser-interface"></a>IMetaDataDispenser — Interfejs
Zawiera metody tworzenia nowego zakresu metadanych lub otwierania istniejącego.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[DefineScope — Metoda](imetadatadispenser-definescope-method.md)|Tworzy nowy obszar w pamięci, w którym można tworzyć nowe metadane.|  
|[OpenScope — Metoda](imetadatadispenser-openscope-method.md)|Otwiera istniejący plik na dysku i mapuje jego metadane do pamięci.|  
|[OpenScopeOnMemory — Metoda](imetadatadispenser-openscopeonmemory-method.md)|Otwiera obszar pamięci, który zawiera istniejące metadane. Oznacza to, że ta metoda otwiera określony obszar pamięci, w której istniejące dane są traktowane jako metadane.|  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataDispenserEx, interfejs](imetadatadispenserex-interface.md)
- [Interfejsy metadanych](metadata-interfaces.md)

---
title: "IMetaDataDispenser — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenser
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenser
helpviewer_keywords: IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 989840b3-9822-4ce5-a6c5-b375d3340a7a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c5a0464f2fb7b81d98fcbb4b04bc465cf57b1b0f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenser-interface"></a>IMetaDataDispenser — Interfejs
Udostępnia metody, aby utworzyć nowy zakres metadanych lub Otwórz istniejący.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[DefineScope — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-definescope-method.md)|Tworzy nowy obszar w pamięci, w którym można utworzyć nowe metadane.|  
|[OpenScope — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)|Otwiera istniejący plik na dysku, a następnie mapuje metadanych do pamięci.|  
|[OpenScopeOnMemory — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)|Otwiera to obszar pamięci, która zawiera istniejące metadane. Oznacza to ta metoda powoduje otwarcie określonego obszaru pamięci, w którym istniejących danych jest traktowany jak metadanych.|  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataDispenserEx — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [Interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)

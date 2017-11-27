---
title: "IMetaDataTables::GetNextGuid — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetNextGuid
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetNextGuid
helpviewer_keywords:
- GetNextGuid method [.NET Framework metadata]
- IMetaDataTables::GetNextGuid method [.NET Framework metadata]
ms.assetid: 68f6ea4d-9112-4d6b-93d9-e34f1e2f2496
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 015bf62bdca1c7437afb26a5d08d21bd276cd3db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgetnextguid-method"></a>IMetaDataTables::GetNextGuid — Metoda
Pobiera indeks następnego wartości identyfikatora GUID w bieżącej kolumny tabeli.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetNextGuid (  
    [in]  ULONG   ixGuid,  
    [out] ULONG   *pNext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ixGuid`  
 [in] Wartość indeksu z kolumną tabeli identyfikatora GUID.  
  
 `pNext`  
 [out] Wskaźnik do indeksu następnej wartości identyfikatora GUID.  
  
## <a name="remarks"></a>Uwagi  
 Zaleca się korzystanie z tej metody, ponieważ nie zwraca spójne wyniki. Informacje o tabeli identyfikatora GUID w dokumentacji infrastruktury języka wspólnego (CLI), szczególnie "partycji II: metadane definicji i semantyki". Dokumentacja jest dostępna w trybie online; zobacz [ECMA C# i wspólne normy infrastruktury języka](http://go.microsoft.com/fwlink/?LinkID=99212) w witrynie MSDN i [standardowe ECMA-335 - infrastruktury języka wspólnego (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) w witrynie sieci Web międzynarodowej Ecma.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataTables — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [IMetaDataTables2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

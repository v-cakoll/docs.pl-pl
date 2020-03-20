---
title: IMetaDataTables::GetGuid — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuid
helpviewer_keywords:
- GetGuid method [.NET Framework metadata]
- IMetaDataTables::GetGuid method [.NET Framework metadata]
ms.assetid: a3546316-e24d-417f-9909-e45d42c9d471
topic_type:
- apiref
ms.openlocfilehash: 57df124f15f78daad053d9634e1baa969a65cc35
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175281"
---
# <a name="imetadatatablesgetguid-method"></a>IMetaDataTables::GetGuid — Metoda
Pobiera identyfikator GUID z wiersza w określonym indeksie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetGuid (
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ixGuid`  
 [w] Indeks wiersza, z którego można uzyskać identyfikator GUID.  
  
 `ppGuid`  
 [na zewnątrz] Wskaźnik do wskaźnika do identyfikatora GUID.  
  
## <a name="remarks"></a>Uwagi  

  Nie zaleca się stosowania tej metody, ponieważ nie zwraca spójne wyniki. Aby uzyskać informacje na temat tabeli GUID, zobacz dokumentację wspólnej infrastruktury języka (CLI), w szczególności "Partycja II: Definicja metadanych i semantyka". Dokumentacja jest dostępna online; zobacz [ECMA C# i common language infrastructure standards](../../../standard/components.md#applicable-standards) and standard [ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataTables, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2 — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

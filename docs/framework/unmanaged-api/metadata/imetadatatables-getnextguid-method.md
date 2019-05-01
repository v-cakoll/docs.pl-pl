---
title: IMetaDataTables::GetNextGuid — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextGuid
helpviewer_keywords:
- GetNextGuid method [.NET Framework metadata]
- IMetaDataTables::GetNextGuid method [.NET Framework metadata]
ms.assetid: 68f6ea4d-9112-4d6b-93d9-e34f1e2f2496
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b23e1d26d62012efe338eeb179db0e7ee17cd658
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042370"
---
# <a name="imetadatatablesgetnextguid-method"></a>IMetaDataTables::GetNextGuid — Metoda
Pobiera indeks następnego wartość identyfikatora GUID w bieżącej kolumnie tabeli.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetNextGuid (  
    [in]  ULONG   ixGuid,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ixGuid`  
 [in] Wartość indeksu z kolumną tabeli identyfikatora GUID.  
  
 `pNext`  
 [out] Wskaźnik do indeksu następną wartość identyfikatora GUID.  
  
## <a name="remarks"></a>Uwagi  
 Firma Microsoft nie zaleca się użycie tej metody, ponieważ zwraca spójne wyniki. Informacje o tabeli identyfikatora GUID, w dokumentacji Common Language Infrastructure (CLI), szczególnie "partycja II: Definicja metadanych i semantyka". Dokumentacja jest dostępna w trybie online; zobacz [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) w witrynie MSDN i [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) w witrynie Ecma International w sieci Web.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataTables, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

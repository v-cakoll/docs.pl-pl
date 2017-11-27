---
title: "IMetaDataTables::GetTableInfo — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetTableInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetTableInfo
helpviewer_keywords:
- IMetaDataTables::GetTableInfo method [.NET Framework metadata]
- GetTableInfo method [.NET Framework metadata]
ms.assetid: 50cbe557-2322-41aa-8e0d-f967602eaa0f
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0f4ccd9bbd1c7caa9bbeb548176d834dc8844213
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgettableinfo-method"></a>IMetaDataTables::GetTableInfo — Metoda
Pobiera nazwę, rozmiar wiersza, liczbę wierszy, liczby kolumn oraz kolumny klucza indeksu określonej tabeli.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetTableInfo (  
    [in]  ULONG       ixTbl,  
    [out] ULONG       *pcbRow,  
    [out] ULONG       *pcRows,  
    [out] ULONG       *pcCols,  
    [out] ULONG       *piKey,  
    [out] const char  **ppName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ixTbl`  
 [in] Identyfikator tabeli, którego właściwości do zwrócenia.  
  
 `pcbRow`  
 [out] Wskaźnik do, w bajtach rozmiar wiersza tabeli.  
  
 `pcRows`  
 [out] Wskaźnik do liczby wierszy w tabeli.  
  
 `pcCols`  
 [out] Wskaźnik do liczby kolumn w tabeli.  
  
 `piKey`  
 [out] Wskaźnik do indeks kolumny klucza, lub wartość -1, jeśli tabela nie ma kolumny klucza.  
  
 `ppName`  
 [out] Wskaźnik na wskaźnik do nazwy tabeli.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataTables — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [IMetaDataTables2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

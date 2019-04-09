---
title: IMetaDataTables::GetTableInfo — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetTableInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetTableInfo
helpviewer_keywords:
- IMetaDataTables::GetTableInfo method [.NET Framework metadata]
- GetTableInfo method [.NET Framework metadata]
ms.assetid: 50cbe557-2322-41aa-8e0d-f967602eaa0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82c88c75d5799134d8c683c91e28f956743b84ba
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194516"
---
# <a name="imetadatatablesgettableinfo-method"></a>IMetaDataTables::GetTableInfo — Metoda
Pobiera nazwę, rozmiar wiersza, liczba wierszy, liczba kolumn, a kolumny klucza indeksu w określonej tabeli.  
  
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
  
## <a name="parameters"></a>Parametry  
 `ixTbl`  
 [in] Identyfikator tabeli, którego właściwości do zwrócenia.  
  
 `pcbRow`  
 [out] Wskaźnik do rozmiaru, w bajtach wiersza tabeli.  
  
 `pcRows`  
 [out] Wskaźnik do liczby wierszy w tabeli.  
  
 `pcCols`  
 [out] Wskaźnik do liczby kolumn w tabeli.  
  
 `piKey`  
 [out] Wskaźnik do indeksu kolumny klucza lub wartość -1, jeśli tabela nie ma kolumny klucza.  
  
 `ppName`  
 [out] Wskaźnik do wskaźnika do nazwy tabeli.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataTables — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2 — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

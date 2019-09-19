---
title: IMetaDataTables::GetColumn — Metoda
ms.date: 02/25/2019
api_name:
- IMetaDataTables.GetColumn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumn
helpviewer_keywords:
- IMetaDataTables::GetColumn method [.NET Framework metadata]
- GetColumn method [.NET Framework metadata]
ms.assetid: 1032055b-cabb-45c5-a50e-7e853201b175
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 853f137d91e1b3eb4f3f65a06522618f8441dcb3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053673"
---
# <a name="imetadatatablesgetcolumn-method"></a>IMetaDataTables::GetColumn — Metoda
Pobiera wskaźnik do wartości zawartej w komórce określonej kolumny i wiersza w danej tabeli.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetColumn (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a>Parametry

 `ixTbl`  
 podczas Indeks tabeli.  
  
 `ixCol`  
 podczas Indeks kolumny w tabeli.  
  
 `rid`  
 podczas Indeks wiersza w tabeli.  
  
 `pVal`  
 określoną Wskaźnik do wartości w komórce.  
 
## <a name="remarks"></a>Uwagi

Interpretacja wartości zwracanej przez `pVal` jest zależna od typu kolumny. Typ kolumny można określić przez wywołanie metody [IMetaDataTables. GetColumnInfo](imetadatatables-getcolumninfo-method.md).

- Metoda **GetColumn** automatycznie konwertuje kolumny typu **RID** lub **CodedToken** na pełne wartości 32-bitowe `mdToken` .
- Automatycznie konwertuje wartości 8-bitowe lub 16-bitowe na pełne wartości 32-bitowe. 
- W przypadku kolumn typu *sterty* zwracany *Pval* będzie indeksem do odpowiedniej sterty.

| Typ kolumny              | pVal zawiera | Komentarz                          |
|--------------------------|---------------|-----------------------------------|
| `0`..`iRidMax`<br>(0.. 63)  | mdToken     | *Pval* będzie zawierać pełny token. Funkcja automatycznie konwertuje identyfikator RID na pełny token. |
| `iCodedToken`..`iCodedTokenMax`<br>(64.. 95) | mdToken | Po powrocie *Pval* będzie zawierać pełny token. Funkcja automatycznie dekompresuje CodedToken do pełnego tokenu. |
| `iSHORT`(96)            | Int16         | Automatycznie Podpisz do 32-bitowego.  |
| `iUSHORT`(97)           | UInt16        | Automatycznie Podpisz do 32-bitowego.  |
| `iLONG`(98)             | Int32         |                                        | 
| `iULONG`(99)            | UInt32        |                                        |
| `iBYTE`(100)            | Byte          | Automatycznie Podpisz do 32-bitowego.  |
| `iSTRING`(101)          | Indeks sterty ciągu | *Pval* jest indeksem do sterty ciągu. Użyj [IMetadataTables:: GetString](imetadatatables-getstring-method.md) , aby uzyskać rzeczywistą wartość ciągu kolumny. |
| `iGUID`(102)            | Indeks sterty identyfikatora GUID | *Pval* jest indeksem do sterty identyfikatora GUID. Użyj [IMetadataTables:: GetGuid](imetadatatables-getguid-method.md) , aby uzyskać rzeczywistą wartość identyfikatora GUID kolumny. |
| `iBLOB`(103)            | Indeks sterty obiektu BLOB | *Pval* jest indeksem do sterty obiektu BLOB. Użyj [IMetadataTables:: GetBlob](imetadatatables-getblob-method.md) , aby uzyskać rzeczywistą wartość obiektu BLOB kolumny. |
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** Cor. h  
  
 **Biblioteki** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataTables, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

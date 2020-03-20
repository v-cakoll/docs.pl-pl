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
ms.openlocfilehash: f43d4d1547cbe92f325950e1697dada83b42c4f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177138"
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
 [w] Indeks tabeli.  
  
 `ixCol`  
 [w] Indeks kolumny w tabeli.  
  
 `rid`  
 [w] Indeks wiersza w tabeli.  
  
 `pVal`  
 [na zewnątrz] Wskaźnik do wartości w komórce.  

## <a name="remarks"></a>Uwagi

Interpretacja wartości zwracanej `pVal` za pośrednictwem zależy od typu kolumny. Typ kolumny można określić, wywołując [IMetaDataTables.GetColumnInfo](imetadatatables-getcolumninfo-method.md).

- **Metoda GetColumn** automatycznie konwertuje kolumny typu **Rid** lub **CodedToken** na `mdToken` pełne wartości 32-bitowe.
- Automatycznie konwertuje również wartości 8-bitowe lub 16-bitowe na pełne wartości 32-bitowe.
- Dla kolumn typu *sterty* zwrócony *pVal* będzie indeksem do odpowiedniego stosu.

| Typ kolumny              | pVal zawiera | Komentarz                          |
|--------------------------|---------------|-----------------------------------|
| `0`..`iRidMax`<br>(0..63)  | mdToken (mdToken)     | *pVal* będzie zawierać pełny token. Funkcja automatycznie konwertuje Rid do pełnego tokenu. |
| `iCodedToken`..`iCodedTokenMax`<br>(64..95) | mdToken (mdToken) | Po zwrocie *pVal* będzie zawierał pełny Token. Funkcja automatycznie dekompresuje CodedToken do pełnego tokenu. |
| `iSHORT`(96)            | Int16         | Automatycznie podpisuj rozszerzony do 32-bitowego.  |
| `iUSHORT`(97)           | UInt16        | Automatycznie podpisuj rozszerzony do 32-bitowego.  |
| `iLONG`(98)             | Int32         |                                        |
| `iULONG`(99)            | UInt32        |                                        |
| `iBYTE`(100)            | Byte          | Automatycznie podpisuj rozszerzony do 32-bitowego.  |
| `iSTRING`(101)          | Indeks sterty ciągów | *pVal* jest indeksem do stosu String. Użyj [IMetadataTables::GetString,](imetadatatables-getstring-method.md) aby uzyskać rzeczywistą wartość ciągu kolumny. |
| `iGUID`(102)            | Wskaźnik sterty guid | *pVal* jest indeksem do sterty Guid. Użyj [IMetadataTables::GetGuid,](imetadatatables-getguid-method.md) aby uzyskać rzeczywistą wartość Guid kolumny. |
| `iBLOB`(103)            | Indeks sterty obiektów blob | *pVal* jest indeksem do sterty obiektów Blob. Użyj [IMetadataTables::GetBlob,](imetadatatables-getblob-method.md) aby uzyskać rzeczywistą wartość obiektu blob kolumny. |
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataTables, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2 — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

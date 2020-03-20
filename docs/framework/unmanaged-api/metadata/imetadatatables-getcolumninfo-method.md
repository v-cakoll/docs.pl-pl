---
title: IMetaDataTables::GetColumnInfo — Metoda
ms.date: 10/10/2019
api_name:
- IMetaDataTables.GetColumnInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumnInfo
helpviewer_keywords:
- IMetaDataTables::GetColumnInfo method [.NET Framework metadata]
- GetColumnInfo method [.NET Framework metadata]
ms.assetid: 68c160ea-ae7d-4750-985d-a038b2c8e7d9
topic_type:
- apiref
ms.openlocfilehash: cc8aac32149fed952737d928e16a8f6efc448c79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177123"
---
# <a name="imetadatatablesgetcolumninfo-method"></a>IMetaDataTables::GetColumnInfo — Metoda
Pobiera dane dotyczące określonej kolumny w określonej tabeli.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetColumnInfo (
    [in]  ULONG        ixTbl,  
    [in]  ULONG        ixCol,  
    [out] ULONG        *poCol,  
    [out] ULONG        *pcbCol,  
    [out] ULONG        *pType,  
    [out] const char   **ppName  
);  
```  
  
## <a name="parameters"></a>Parametry
=======

 `ixTbl`  
 [w] Indeks żądanej tabeli.  
  
 `ixCol`  
 [w] Indeks żądanej kolumny.  
  
 `poCol`  
 [na zewnątrz] Wskaźnik do odsunięcia kolumny w wierszu.  
  
 `pcbCol`  
 [na zewnątrz] Wskaźnik do rozmiaru w bajtach kolumny.  
  
 `pType`  
 [na zewnątrz] Wskaźnik do typu wartości w kolumnie.  
  
 `ppName`  
 [na zewnątrz] Wskaźnik do wskaźnika do nazwy kolumny.  

## <a name="remarks"></a>Uwagi

Zwracany typ kolumny mieści się w zakresie wartości:

| pTyp                    | Opis   | Funkcja pomocnika                   |
|--------------------------|---------------|-----------------------------------|
| `0`..`iRidMax`<br>(0..63)   | Rid           | **Typ IsRid**<br>**IsRidOrToken (IsRidOrToken)** |
| `iCodedToken`..`iCodedTokenMax`<br>(64..95) | Token kodowany | **Typ IsCodedToken** <br>**IsRidOrToken (IsRidOrToken)** |
| `iSHORT`(96)            | Int16         | **IsFixedType (Typ isfixedtype)**                   |
| `iUSHORT`(97)           | UInt16        | **IsFixedType (Typ isfixedtype)**                   |
| `iLONG`(98)             | Int32         | **IsFixedType (Typ isfixedtype)**                   |
| `iULONG`(99)            | UInt32        | **IsFixedType (Typ isfixedtype)**                   |
| `iBYTE`(100)            | Byte          | **IsFixedType (Typ isfixedtype)**                   |
| `iSTRING`(101)          | Ciąg        | **Typ IsHeapType**                    |
| `iGUID`(102)            | Guid (identyfikator GUID)          | **Typ IsHeapType**                    |
| `iBLOB`(103)            | Obiekt blob          | **Typ IsHeapType**                    |

Wartości, które są przechowywane w *stercie* `IsHeapType == true`(czyli) można odczytać za pomocą:

- `iSTRING`: **IMetadataTables.GetString**
- `iGUID`: **IMetadataTables.GetGUID**
- `iBLOB`: **IMetadataTables.GetBlob**

> [!IMPORTANT]
> Aby użyć stałych zdefiniowanych w powyższej `#define _DEFINE_META_DATA_META_CONSTANTS` tabeli, należy dołączyć dyrektywę dostarczoną przez plik nagłówka *cor.h.*

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataTables, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2 — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

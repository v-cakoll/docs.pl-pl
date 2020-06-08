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
ms.openlocfilehash: a044924810016eea60682b8765aeee448b552f0d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501199"
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
 podczas Indeks żądanej tabeli.  
  
 `ixCol`  
 podczas Indeks żądanej kolumny.  
  
 `poCol`  
 określoną Wskaźnik do przesunięcia kolumny w wierszu.  
  
 `pcbCol`  
 określoną Wskaźnik do rozmiaru, w bajtach, kolumny.  
  
 `pType`  
 określoną Wskaźnik do typu wartości w kolumnie.  
  
 `ppName`  
 określoną Wskaźnik do wskaźnika do nazwy kolumny.  

## <a name="remarks"></a>Uwagi

Zwracany typ kolumny znajduje się w zakresie wartości:

| pType                    | Opis   | Funkcja pomocnika                   |
|--------------------------|---------------|-----------------------------------|
| `0`..`iRidMax`<br>(0.. 63)   | Objęte           | **IsRidType**<br>**IsRidOrToken** |
| `iCodedToken`..`iCodedTokenMax`<br>(64.. 95) | Zakodowany token | **IsCodedTokenType** <br>**IsRidOrToken** |
| `iSHORT`(96)            | Int16         | **Isfixedtype**                   |
| `iUSHORT`(97)           | UInt16        | **Isfixedtype**                   |
| `iLONG`(98)             | Int32         | **Isfixedtype**                   |
| `iULONG`(99)            | UInt32        | **Isfixedtype**                   |
| `iBYTE`(100)            | Byte          | **Isfixedtype**                   |
| `iSTRING`(101)          | String        | **Issterta**                    |
| `iGUID`(102)            | Guid (identyfikator GUID)          | **Issterta**                    |
| `iBLOB`(103)            | Obiekt blob          | **Issterta**                    |

Wartości, które są przechowywane w *stercie* (czyli `IsHeapType == true` ), można odczytać przy użyciu:

- `iSTRING`: **IMetadataTables. GetString**
- `iGUID`: **IMetadataTables. GETguid**
- `iBLOB`: **IMetadataTables. GetBlob**

> [!IMPORTANT]
> Aby użyć stałych zdefiniowanych w powyższej tabeli, należy uwzględnić dyrektywę `#define _DEFINE_META_DATA_META_CONSTANTS` dostarczoną przez plik nagłówkowy *cor. h* .

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataTables, interfejs](imetadatatables-interface.md)
- [IMetaDataTables2 — Interfejs](imetadatatables2-interface.md)

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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dd67d9faafedf4fb92c69618d4464ebb2ce47dcc
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774255"
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
| `0`.. `iRidMax`<br>(0.. 63)   | Objęte           | **IsRidType**<br>**IsRidOrToken** |
| `iCodedToken`.. `iCodedTokenMax`<br>(64.. 95) | Zakodowany token | **IsCodedTokenType** <br>**IsRidOrToken** |
| `iSHORT` (96)            | Int16         | **Isfixedtype**                   |
| `iUSHORT` (97)           | UInt16        | **Isfixedtype**                   |
| `iLONG` (98)             | Int32         | **Isfixedtype**                   |
| `iULONG` (99)            | UInt32        | **Isfixedtype**                   |
| `iBYTE` (100)            | Byte          | **Isfixedtype**                   |
| `iSTRING` (101)          | String        | **Issterta**                    |
| `iGUID` (102)            | Ident          | **Issterta**                    |
| `iBLOB` (103)            | Tworzenia          | **Issterta**                    |

Wartości, które są przechowywane w *stercie* (`IsHeapType == true`) można odczytać przy użyciu:

- `iSTRING`: **IMetadataTables. GetString**
- `iGUID`: **IMetadataTables. GETguid**
- `iBLOB`: **IMetadataTables. GetBlob**

> [!IMPORTANT]
> Aby użyć stałych zdefiniowanych w powyższej tabeli, należy uwzględnić dyrektywę `#define _DEFINE_META_DATA_META_CONSTANTS` dostarczoną przez plik nagłówkowy *cor. h* .

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataTables, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

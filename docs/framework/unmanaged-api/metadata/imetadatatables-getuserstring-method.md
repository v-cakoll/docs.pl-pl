---
title: IMetaDataTables::GetUserString — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserString
helpviewer_keywords:
- IMetaDataTables::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 35b8f0d6-9aba-4714-adb2-62020a38fb7e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0fefbab6b2ea9fbbfd90e03c41578a924f99c7a0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645204"
---
# <a name="imetadatatablesgetuserstring-method"></a>IMetaDataTables::GetUserString — Metoda

Pobiera ciąg ustaloną dla podanego indeksu w kolumnie ciągu w bieżącym zakresie.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetUserString (
    [in]  ULONG       ixUserString,
    [out] ULONG       *pcbData,
    [out] const void  **ppData
);
```

## <a name="parameters"></a>Parametry

`ixUserString`\
[in] Wartość indeksu, z którego będą pobierane ciągu ustalonych.

`pcbData`\
[out] Wskaźnik do rozmiaru `ppData`.

`ppData`\
[out] Wskaźnik do wskaźnika do zwracanego ciągu.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

**Nagłówek:** COR.h

**Biblioteka:** Używany jako zasób w MsCorEE.dll

**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [IMetaDataTables, interfejs](imetadatatables-interface.md)
- [IMetaDataTables2, interfejs](imetadatatables2-interface.md)
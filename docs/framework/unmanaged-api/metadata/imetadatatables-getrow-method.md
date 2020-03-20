---
title: IMetaDataTables::GetRow — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetRow
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetRow
helpviewer_keywords:
- IMetaDataTables::GetRow method [.NET Framework metadata]
- GetRow method [.NET Framework metadata]
ms.assetid: a7408d51-0bce-45a2-b58f-da4660bbc039
topic_type:
- apiref
ms.openlocfilehash: 71f6c496816fec1a7537f5ccdfdc1b47d17da871
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177114"
---
# <a name="imetadatatablesgetrow-method"></a>IMetaDataTables::GetRow — Metoda
Pobiera wiersz w określonym indeksie wiersza, w tabeli w określonym indeksie tabeli.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetRow (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ixTbl`  
 [w] Indeks tabeli, z której wiersz zostanie pobrany.  
  
 `rid`  
 [w] Indeks wiersza, aby uzyskać.  
  
 `ppRow`  
 [na zewnątrz] Wskaźnik do wskaźnika do wiersza.  
  
## <a name="remarks"></a>Uwagi  

  Nie zaleca się stosowania tej metody, ponieważ nie zwraca spójne wyniki. Aby uzyskać informacje na temat tabeli GUID, zobacz dokumentację wspólnej infrastruktury języka (CLI), w szczególności "Partycja II: Definicja metadanych i semantyka". Dokumentacja jest dostępna online; zobacz [ECMA C# i common language infrastructure standards](../../../standard/components.md#applicable-standards) and standard [ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataTables, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2 — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

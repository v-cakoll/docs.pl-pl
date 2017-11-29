---
title: "ISymUnmanagedBinder::GetReaderFromStream — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder.GetReaderFromStream
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder::GetReaderFromStream
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderFromStream method [.NET Framework debugging]
- GetReaderFromStream method [.NET Framework debugging]
ms.assetid: aa38efd4-de7e-4482-a5d3-adc152093460
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 96bd12b69b84537415ddf2e0ae992ec179f32493
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a>ISymUnmanagedBinder::GetReaderFromStream — Metoda
Podany interfejs metadanych i strumienia, który zawiera magazyn symbol zwraca poprawny <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> Struktura, która będzie odczytywać debugowanie symboli z magazynu podanego symbolu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
#### <a name="parameters"></a>Parametry  
 `importer`  
 [in] Wskaźnik do interfejsu importu metadanych.  
  
 `pstream`  
 [in] Wskaźnik do strumienia, który zawiera magazynu symboli.  
  
 `pRetVal`  
 [out] Wskaźnik, który jest ustawiony na zwracana <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interfejsu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [ISymUnmanagedBinder — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)

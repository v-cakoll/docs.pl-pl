---
title: "ISymUnmanagedReader2::GetSymAttributePreRemap — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader2.GetSymAttributePreRemap
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader2::GetSymAttributePreRemap
helpviewer_keywords:
- GetSymAttributePreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetSymAttributePreRemap method [.NET Framework debugging]
ms.assetid: 7580d546-a709-40c5-ad02-aa70d774fd0b
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 75608d89b6fd34570166718de824150b0621c84e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a>ISymUnmanagedReader2::GetSymAttributePreRemap — Metoda
Pobiera atrybut niestandardowy ustalane na podstawie jego nazwy. W przeciwieństwie do niestandardowych atrybutów metadanych te atrybuty są przechowywane w magazynie symboli.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetSymAttributePreRemap(  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is(cBuffer),  
        length_is(*pcBuffer)] BYTE buffer[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `parent`  
 [in] Token metadanych elementu nadrzędnego.  
  
 `name`  
 [in] Wskaźnik do `WCHAR` zawierający nazwę.  
  
 `cBuffer`  
 [in] A `ULONG32` wskazuje, że rozmiar `buffer` tablicy.  
  
 `pcBuffer`  
 [out] Wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać atrybut bajtów.  
  
 `buffer`  
 [out] Wskaźnik do buforu, który odbiera bajtów atrybutu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [ISymUnmanagedReader2 — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)

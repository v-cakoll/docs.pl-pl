---
title: ISymUnmanagedReader2::GetSymAttributePreRemap — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetSymAttributePreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetSymAttributePreRemap
helpviewer_keywords:
- GetSymAttributePreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetSymAttributePreRemap method [.NET Framework debugging]
ms.assetid: 7580d546-a709-40c5-ad02-aa70d774fd0b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 543a8015e944333942b619060059273577902a74
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986339"
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a>ISymUnmanagedReader2::GetSymAttributePreRemap — Metoda
Pobiera atrybut niestandardowy na podstawie jego nazwy. W przeciwieństwie do metadanych atrybutów niestandardowych te atrybuty są przechowywane w magazynie symboli.  
  
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
  
## <a name="parameters"></a>Parametry  
 `parent`  
 [in] Token metadanych elementu nadrzędnego.  
  
 `name`  
 [in] Wskaźnik do `WCHAR` zawierający nazwę.  
  
 `cBuffer`  
 [in] A `ULONG32` oznacza rozmiar `buffer` tablicy.  
  
 `pcBuffer`  
 [out] Wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać bajtów atrybutu.  
  
 `buffer`  
 [out] Wskaźnik do buforu, który otrzymuje bajtów atrybutu.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedReader2, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)

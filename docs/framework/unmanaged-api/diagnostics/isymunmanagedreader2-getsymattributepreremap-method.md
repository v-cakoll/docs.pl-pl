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
ms.openlocfilehash: 46c608a644619c28709de135d7c062175b012d80
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777379"
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a>ISymUnmanagedReader2::GetSymAttributePreRemap — Metoda
Pobiera atrybut niestandardowy na podstawie jego nazwy. W przeciwieństwie do metadanych atrybutów niestandardowych te atrybuty są przechowywane w magazynie symboli.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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

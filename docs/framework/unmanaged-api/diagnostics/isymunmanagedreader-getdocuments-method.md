---
title: ISymUnmanagedReader::GetDocuments — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocuments
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocuments
helpviewer_keywords:
- GetDocuments method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocuments method [.NET Framework debugging]
ms.assetid: e3b73a3f-d089-4101-a9a9-5e0765d05b61
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 629f9a62364729984a7eec86090876c3eaebb881
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57464558"
---
# <a name="isymunmanagedreadergetdocuments-method"></a>ISymUnmanagedReader::GetDocuments — Metoda
Zwraca tablicę wszystkich dokumentów, które są zdefiniowane w magazynie symboli.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetDocuments (  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,  
    [out, size_is (cDocs),  
        length_is (*pcDocs)] ISymUnmanagedDocument *pDocs[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cDocs`  
 [in] Rozmiar `pDocs` tablicy.  
  
 `pcDocs`  
 [out] Wskaźnik do zmiennej, która odbiera długość tablicy.  
  
 `pDocs`  
 [out] Wskaźnik do zmiennej, która odbiera tablicy dokumentu.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także
- [ISymUnmanagedReader, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

---
title: ISymUnmanagedReader::GetDocumentVersion — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocumentVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocumentVersion
helpviewer_keywords:
- GetDocumentVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocumentVersion method [.NET Framework debugging]
ms.assetid: a51f1f64-e084-44c5-830c-2222da5a6bbf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: efe4d28d207625f00634087b862d76c001518c8d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777025"
---
# <a name="isymunmanagedreadergetdocumentversion-method"></a>ISymUnmanagedReader::GetDocumentVersion — Metoda
Pobiera określoną wersję określonego dokumentu. Wersja dokumentu rozpoczyna się od 1 i jest zwiększana za każdym razem, dokument jest aktualizowany za pomocą [updatesymbolstore —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) metody. Jeśli `pbCurrent` parametr jest `true`, to jest najnowsza wersja dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetDocumentVersion (  
    [in]  ISymUnmanagedDocument *pDoc,  
    [out] int* version,  
    [out] BOOL* pbCurrent);  
```  
  
## <a name="parameters"></a>Parametry  
 `pDoc`  
 [in] Określony dokument.  
  
 `version`  
 [out] Wskaźnik do zmiennej, która odbiera wersję określonego dokumentu.  
  
 `pbCurrent`  
 [out] Wskaźnik do zmiennej, która odbiera `true` Jeśli to jest najnowsza wersja dokumentu, lub `false` Jeśli nie jest najnowsza wersja.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedReader, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

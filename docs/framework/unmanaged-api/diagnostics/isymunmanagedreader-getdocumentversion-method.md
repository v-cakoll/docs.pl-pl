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
ms.openlocfilehash: c2cc541b2a78f16d5ca6b19405794faa825a9d72
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615036"
---
# <a name="isymunmanagedreadergetdocumentversion-method"></a>ISymUnmanagedReader::GetDocumentVersion — Metoda
Pobiera określoną wersję określonego dokumentu. Wersja dokumentu zaczyna się od 1 i jest zwiększana za każdym razem, gdy dokument zostanie zaktualizowany przy użyciu metody [UpdateSymbolStore —](isymunmanagedreader-updatesymbolstore-method.md) . Jeśli `pbCurrent` parametr jest `true` , jest to Najnowsza wersja dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetDocumentVersion (  
    [in]  ISymUnmanagedDocument *pDoc,  
    [out] int* version,  
    [out] BOOL* pbCurrent);  
```  
  
## <a name="parameters"></a>Parametry  
 `pDoc`  
 podczas Określony dokument.  
  
 `version`  
 określoną Wskaźnik do zmiennej, która otrzymuje wersję określonego dokumentu.  
  
 `pbCurrent`  
 określoną Wskaźnik do zmiennej, która otrzymuje `true` , jeśli jest to Najnowsza wersja dokumentu lub jeśli nie jest to `false` Najnowsza wersja.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedReader — Interfejs](isymunmanagedreader-interface.md)

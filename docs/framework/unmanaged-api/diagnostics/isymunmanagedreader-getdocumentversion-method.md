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
ms.openlocfilehash: 31b550c7b3cec999b0420fbdc06582a24f420abe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425987"
---
# <a name="isymunmanagedreadergetdocumentversion-method"></a>ISymUnmanagedReader::GetDocumentVersion — Metoda
Pobiera określoną wersję określonego dokumentu. Wersja dokumentu rozpoczyna się od 1 i jest zwiększany po każdej dokumentu jest aktualizowany przy użyciu [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) metody. Jeśli `pbCurrent` parametr jest `true`, jest to najnowsza wersja dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetDocumentVersion (  
    [in]  ISymUnmanagedDocument *pDoc,  
    [out] int* version,  
    [out] BOOL* pbCurrent);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pDoc`  
 [in] Określony dokument.  
  
 `version`  
 [out] Wskaźnik do zmiennej, która odbiera wersji określonego dokumentu.  
  
 `pbCurrent`  
 [out] Wskaźnik do zmiennej, która odbiera `true` , jeśli jest to najnowsza wersja dokumentu lub `false` Jeśli nie jest najnowsza wersja.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [ISymUnmanagedReader, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

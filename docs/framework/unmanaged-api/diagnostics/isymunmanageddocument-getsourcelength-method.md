---
title: ISymUnmanagedDocument::GetSourceLength — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetSourceLength
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceLength
helpviewer_keywords:
- GetSourceLength method [.NET Framework debugging]
- ISymUnmanagedDocument::GetSourceLength method [.NET Framework debugging]
ms.assetid: e087dbbb-f4fb-4fbe-8292-e4f1a14d0df2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3341159600c85915cd3c1a138265dc386edbb766
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424121"
---
# <a name="isymunmanageddocumentgetsourcelength-method"></a>ISymUnmanagedDocument::GetSourceLength — Metoda
Pobiera długość w bajtach osadzonego źródła.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetSourceLength(  
    [out, retval]  ULONG32*  pRetVal);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Wskaźnik do zmiennej, która wskazuje długość w bajtach osadzone źródło.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli metoda zakończy się powodzeniem.  
  
## <a name="see-also"></a>Zobacz też  
 [ISymUnmanagedDocument, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)

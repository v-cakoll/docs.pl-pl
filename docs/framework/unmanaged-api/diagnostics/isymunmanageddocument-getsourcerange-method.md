---
title: ISymUnmanagedDocument::GetSourceRange — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceRange
helpviewer_keywords:
- ISymUnmanagedDocument::GetSourceRange method [.NET Framework debugging]
- GetSourceRange method [.NET Framework debugging]
ms.assetid: 20fefee7-1040-41ba-93dc-bd42f68b90c2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 00baed93bd9ab48c92de83dac76931c3149afc2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424641"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a>ISymUnmanagedDocument::GetSourceRange — Metoda
Zwraca określony zakres osadzone źródło do danego buforu. Rozmiar buforu musi być wystarczająco duży, aby pomieścić źródła.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetSourceRange(  
    [in]  ULONG32  startLine,  
    [in]  ULONG32  startColumn,  
    [in]  ULONG32  endLine,  
    [in]  ULONG32  endColumn,  
    [in]  ULONG32  cSourceBytes,  
    [out] ULONG32  *pcSourceBytes,  
    [out, size_is(cSourceBytes),  
        length_is(*pcSourceBytes)] BYTE source[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `startLine`  
 [in] Linia początkowa w bieżącym dokumencie.  
  
 `startColumn`  
 [in] Kolumna początkowa w bieżącym dokumencie.  
  
 `endLine`  
 [in] Końcowego wiersza w bieżącym dokumencie.  
  
 `endColumn`  
 [in] Ostatniej kolumny w bieżącym dokumencie.  
  
 `cSourceBytes`  
 [in] Rozmiar źródła, w bajtach.  
  
 `pcSourceBytes`  
 [out] Wskaźnik do zmiennej, która odbiera rozmiar źródła.  
  
 `source`  
 [out] Rozmiar i długość zakresu określonego dokumentu źródłowego w bajtach.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli metoda zakończy się powodzeniem.  
  
## <a name="see-also"></a>Zobacz też  
 [ISymUnmanagedDocument, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)

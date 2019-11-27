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
ms.openlocfilehash: 64ecbb56ab32ac8381a4864acd5fd40741786d30
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449132"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a>ISymUnmanagedDocument::GetSourceRange — Metoda
Zwraca określony zakres osadzonego źródła do podanego buforu. Bufor musi być wystarczająco duży, aby pomieścić źródło.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
  
## <a name="parameters"></a>Parametry  
 `startLine`  
 podczas Wiersz początkowy w bieżącym dokumencie.  
  
 `startColumn`  
 podczas Kolumna początkowa w bieżącym dokumencie.  
  
 `endLine`  
 podczas Ostatni wiersz w bieżącym dokumencie.  
  
 `endColumn`  
 podczas Końcowa kolumna w bieżącym dokumencie.  
  
 `cSourceBytes`  
 podczas Rozmiar źródła w bajtach.  
  
 `pcSourceBytes`  
 określoną Wskaźnik do zmiennej, która otrzymuje rozmiar źródła.  
  
 `source`  
 określoną Rozmiar i długość określonego zakresu dokumentu źródłowego w bajtach.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda zakończy się pomyślnie.  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedDocument, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)

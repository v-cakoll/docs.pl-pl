---
title: ISymUnmanagedWriter::SetMethodSourceRange — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetMethodSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetMethodSourceRange
helpviewer_keywords:
- SetMethodSourceRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetMethodSourceRange method [.NET Framework debugging]
ms.assetid: c698b86e-ace7-4b21-9549-f52d6a034959
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 40d05ee60d0183337e67b1f36722dff29ae9beaf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663547"
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a>ISymUnmanagedWriter::SetMethodSourceRange — Metoda
Określa wartość true, początek i koniec okresu metody w pliku źródłowym. Ta metoda umożliwia określenie stopnia metody, niezależnie od punktów sekwencji, które istnieją w metodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
#### <a name="parameters"></a>Parametry  
 `startDoc`  
 [in] Wskaźnik do dokumentu zawierającego pozycja początkowa.  
  
 `startLine`  
 [in] Numer wiersza początkowego.  
  
 `startColumn`  
 [in] Kolumna początkowa.  
  
 `endDoc`  
 [in] Wskaźnik do dokumentu zawierającego pozycji końcowej.  
  
 `endLine`  
 [in] Końcowy numer wiersza.  
  
 `endColumn`  
 [in] Numer kolumny końcowej.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także
- [ISymUnmanagedWriter, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

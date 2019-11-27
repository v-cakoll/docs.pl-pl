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
ms.openlocfilehash: 85e65f6a3ec13c2acc31b8f87dbe4b4476ffc2a5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427866"
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a>ISymUnmanagedWriter::SetMethodSourceRange — Metoda
Określa wartość rzeczywistą początkową i końcową metody w pliku źródłowym. Użyj tej metody, aby określić zakres metody niezależnie od punktów sekwencji istniejących w metodzie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
## <a name="parameters"></a>Parametry  
 `startDoc`  
 podczas Wskaźnik do dokumentu zawierającego pozycję początkową.  
  
 `startLine`  
 podczas Numer wiersza początkowego.  
  
 `startColumn`  
 podczas Kolumna początkowa.  
  
 `endDoc`  
 podczas Wskaźnik do dokumentu zawierającego pozycję końcową.  
  
 `endLine`  
 podczas Numer wiersza końcowego.  
  
 `endColumn`  
 podczas Numer kolumny końcowej.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedWriter, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

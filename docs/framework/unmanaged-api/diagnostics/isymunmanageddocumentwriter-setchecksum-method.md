---
title: ISymUnmanagedDocumentWriter::SetCheckSum — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocumentWriter.SetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum method [.NET Framework debugging]
- SetCheckSum method [.NET Framework debugging]
ms.assetid: c7e99879-421f-43ce-b193-34733cf30085
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ac3daccfade4f5ae10fe2ebbf83a7a11af34b89b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59196986"
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a>ISymUnmanagedDocumentWriter::SetCheckSum — Metoda
Ustawia informacji o sumie kontrolnej.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `algorithmId`  
 [in] Identyfikator GUID, który reprezentuje identyfikator algorytmu.  
  
 `checkSumSize`  
 [in] A `ULONG32` rozmiar w bajtach, który wskazuje z `checkSum` buforu.  
  
 `checkSum`  
 [in] Bufor, który przechowuje informacji o sumie kontrolnej.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedDocumentWriter, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)

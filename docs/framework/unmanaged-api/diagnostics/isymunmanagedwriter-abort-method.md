---
title: ISymUnmanagedWriter::Abort — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Abort
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Abort
helpviewer_keywords:
- ISymUnmanagedWriter::Abort method [.NET Framework debugging]
- Abort method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 416b220f-38d4-48e0-bb49-d2faa7366702
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b4c79cb3df37a9ed10e46567be63aad29fee37c4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550191"
---
# <a name="isymunmanagedwriterabort-method"></a>ISymUnmanagedWriter::Abort — Metoda
Zamyka moduł zapisujący symboli nie poświęcając symbole do magazynu symboli. Po tym wywołaniu moduł zapisujący symbol staje się nieprawidłowy dalsze aktualizacje. Aby zatwierdzić symboli i zamknąć Edytor symboli, należy użyć [ISymUnmanagedWriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) metody zamiast tego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Abort();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także
- [ISymUnmanagedWriter, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

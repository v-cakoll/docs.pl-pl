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
ms.openlocfilehash: 09f39d3b6486e2ec3c04c5d1858a85ce56895527
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610161"
---
# <a name="isymunmanagedwriterabort-method"></a>ISymUnmanagedWriter::Abort — Metoda
Zamyka moduł zapisujący symboli bez przekazywania symboli do magazynu symboli. Po tym wywołaniu moduł zapisujący symboli jest nieprawidłowy dla dalszych aktualizacji. Aby zatwierdzić symbole i zamknąć moduł zapisujący symboli, należy zamiast tego użyć metody [ISymUnmanagedWriter:: Close](isymunmanagedwriter-close-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Abort();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedWriter — Interfejs](isymunmanagedwriter-interface.md)

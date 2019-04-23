---
title: ISymUnmanagedWriter::Close — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Close
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Close
helpviewer_keywords:
- Close method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::Close method [.NET Framework debugging]
ms.assetid: 4cce59e1-80b9-4fc4-b3aa-126f1c5876bc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4d3497d3167715d3e8a04f10a6687260949e4a36
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104705"
---
# <a name="isymunmanagedwriterclose-method"></a>ISymUnmanagedWriter::Close — Metoda
Zamyka moduł zapisujący symbol po zatwierdzeniu symbole do magazynu symboli.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Close();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="remarks"></a>Uwagi  
 Po tym wywołaniu moduł zapisujący symbol staje się nieprawidłowy dalsze aktualizacje. Aby zamknąć Edytor symboli nie poświęcając symbole, należy użyć [ISymUnmanagedWriter::Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) metody zamiast tego.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedWriter, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

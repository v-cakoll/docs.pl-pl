---
title: ISymUnmanagedMethod::GetSourceStartEnd — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSourceStartEnd
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSourceStartEnd
helpviewer_keywords:
- GetSourceStartEnd method [.NET Framework debugging]
- ISymUnmanagedMethod::GetSourceStartEnd method [.NET Framework debugging]
ms.assetid: 2a420900-01f1-4461-8777-3a34a6dc1426
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0d9a02ea338dd2c1366256434eacda51327b7d5f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479470"
---
# <a name="isymunmanagedmethodgetsourcestartend-method"></a>ISymUnmanagedMethod::GetSourceStartEnd — Metoda
Pobiera położenie dokumentu rozpoczęcia i zakończenia dla źródłowej, tej metody. Na pierwszym miejscu tablicy jest początek, a na drugim miejscu tablicy jest zakończenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetSourceStartEnd(  
    [in]  ISymUnmanagedDocument  *docs[2],  
    [in]  ULONG32                lines[2],  
    [in]  ULONG32                columns[2],  
    [out] BOOL                   *pRetVal);  
```  
  
## <a name="parameters"></a>Parametry  
 `docs`  
 [in] Początkowe i końcowe dokumentu źródłowego.  
  
 `lines`  
 [in] Początkowe i końcowe wiersze w odpowiednich źródła dokumentów.  
  
 `columns`  
 [in] Początkowy i końcowy kolumn w odpowiednich źródła dokumentów.  
  
 `pRetVal`  
 [out] `true` gdyby położenia zdefiniowanych; w przeciwnym razie `false`.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także
- [ISymUnmanagedMethod, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)

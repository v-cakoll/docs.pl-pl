---
title: ISymUnmanagedReader2::GetMethodsInDocument — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetMethodsInDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetMethodsInDocument
helpviewer_keywords:
- ISymUnmanagedReader2::GetMethodsInDocument method [.NET Framework debugging]
- GetMethodsInDocument method [.NET Framework debugging]
ms.assetid: c7ae84d6-81e8-4cb7-a1f9-d48b6cde5d79
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 26e6efff403f7fa10e1d96ffb3bf0f4b9ab3a96d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465858"
---
# <a name="isymunmanagedreader2getmethodsindocument-method"></a>ISymUnmanagedReader2::GetMethodsInDocument — Metoda
Pobiera każdej metody, która ma informacje wiersza w podany dokument.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetMethodsInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is(cMethod),  
        length_is(*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `document`  
 [in] Wskaźnik do dokumentu.  
  
 `cMethod`  
 [in] A `ULONG32` oznacza rozmiar `pRetVal` tablicy.  
  
 `pcMethod`  
 [out] Wskaźnik do `ULONG32` rozmiar buforu, muszą zawierać metody, która otrzymuje.  
  
 `pRetVal`  
 [out] Wskaźnik do buforu, który otrzymuje te metody.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także
- [ISymUnmanagedReader2, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)

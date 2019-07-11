---
title: ISymUnmanagedMethod::GetSequencePoints — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePoints
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePoints method [.NET Framework debugging]
- GetSequencePoints method [.NET Framework debugging]
ms.assetid: f909ac48-3d8f-49fb-a369-e3d9959151cd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d8cfde8f0eb14919c12d261c3f9f7209365829c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759449"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a>ISymUnmanagedMethod::GetSequencePoints — Metoda
Pobiera wszystkie punkty sekwencji w ramach tej metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetSequencePoints(  
    [in]  ULONG32  cPoints,  
    [out] ULONG32  *pcPoints,  
    [in, size_is(cPoints)] ULONG32  offsets[],  
    [in, size_is(cPoints)] ISymUnmanagedDocument* documents[],  
    [in, size_is(cPoints)] ULONG32  lines[],  
    [in, size_is(cPoints)] ULONG32  columns[],  
    [in, size_is(cPoints)] ULONG32  endLines[],  
    [in, size_is(cPoints)] ULONG32  endColumns[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cPoints`  
 [in] A `ULONG32` wielkości, która otrzymuje `offsets`, `documents`, `lines`, `columns`, `endLines`, i `endColumns` tablic.  
  
 `pcPoints`  
 [out] Wskaźnik do `ULONG32` odbierająca długość buforu, muszą zawierać punktów sekwencji.  
  
 `offsets`  
 [in] Tablica, w którym będą przechowywane przez firmę Microsoft intermediate language (MSIL) powoduje przesunięcie od początku metody punktów sekwencji.  
  
 `documents`  
 [in] Tablica do przechowywania dokumentów, w których znajdują się punkty sekwencji.  
  
 `lines`  
 [in] Tablica do przechowywania wierszy w dokumentach, w których znajdują się punkty sekwencji.  
  
 `columns`  
 [in] Tablica, w którym będą przechowywane w kolumnach w dokumentach, w których znajdują się punkty sekwencji.  
  
 `endLines`  
 [in] Tablica wiersze w dokumentach, w których sekwencji punktów końcowych.  
  
 `endColumns`  
 [in] Tablica kolumn w dokumentach, w których sekwencji punktów końcowych.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedMethod, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)

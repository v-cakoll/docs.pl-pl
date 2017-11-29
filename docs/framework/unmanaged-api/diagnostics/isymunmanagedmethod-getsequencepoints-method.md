---
title: "ISymUnmanagedMethod::GetSequencePoints — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetSequencePoints
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetSequencePoints
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePoints method [.NET Framework debugging]
- GetSequencePoints method [.NET Framework debugging]
ms.assetid: f909ac48-3d8f-49fb-a369-e3d9959151cd
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3cde9de634534acdeafa40bd7a94c46624e49604
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a>ISymUnmanagedMethod::GetSequencePoints — Metoda
Pobiera wszystkie punkty sekwencji w ramach tej metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `cPoints`  
 [in] A `ULONG32` odbierająca rozmiar `offsets`, `documents`, `lines`, `columns`, `endLines`, i `endColumns` tablic.  
  
 `pcPoints`  
 [out] Wskaźnik do `ULONG32` odbierająca długość buforu, muszą zawierać punkty sekwencji.  
  
 `offsets`  
 [in] Tablica do przechowywania Microsoft pośredniego language (MSIL) powoduje przesunięcie od początku metodę punkty sekwencji.  
  
 `documents`  
 [in] Tablica do przechowywania dokumentów, w których znajdują się punkty sekwencji.  
  
 `lines`  
 [in] Tablica do przechowywania dokumentów, w których znajdują się punkty sekwencji wierszy.  
  
 `columns`  
 [in] Tablica do przechowywania kolumny w dokumentach, w których znajdują się punkty sekwencji.  
  
 `endLines`  
 [in] Tablica wiersze w dokumentach, w których sekwencja punktów końcowych.  
  
 `endColumns`  
 [in] Tablica kolumn w dokumentach, w których sekwencja punktów końcowych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [ISymUnmanagedMethod — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)

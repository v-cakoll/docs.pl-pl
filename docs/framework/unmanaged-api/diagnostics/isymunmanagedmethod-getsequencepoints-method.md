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
ms.openlocfilehash: 451cfecde7e14fad9d3fed3367112e1fb59796e5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615148"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a>ISymUnmanagedMethod::GetSequencePoints — Metoda
Pobiera wszystkie punkty sekwencji w tej metodzie.  
  
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
 podczas A, `ULONG32` który otrzymuje wielkość tablic,,,, `offsets` `documents` `lines` `columns` `endLines` i `endColumns` .  
  
 `pcPoints`  
 określoną Wskaźnik do obiektu `ULONG32` , który otrzymuje długość buforu wymaganego do zawierania punktów sekwencji.  
  
 `offsets`  
 podczas Tablica, w której mają być przechowywane przesunięcia języka pośredniego firmy Microsoft (MSIL) od początku metody dla punktów sekwencji.  
  
 `documents`  
 podczas Tablica, w której mają być przechowywane dokumenty, w których znajdują się punkty sekwencji.  
  
 `lines`  
 podczas Tablica, w której mają być przechowywane wiersze w dokumentach, w których znajdują się punkty sekwencji.  
  
 `columns`  
 podczas Tablica, w której mają być przechowywane kolumny w dokumentach, w których znajdują się punkty sekwencji.  
  
 `endLines`  
 podczas Tablica wierszy w dokumentach, w których kończy się punkty sekwencji.  
  
 `endColumns`  
 podczas Tablica kolumn w dokumentach, w których kończy się punkty sekwencji.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedMethod — Interfejs](isymunmanagedmethod-interface.md)

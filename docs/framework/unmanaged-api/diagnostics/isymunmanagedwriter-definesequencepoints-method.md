---
title: ISymUnmanagedWriter::DefineSequencePoints — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineSequencePoints
helpviewer_keywords:
- DefineSequencePoints method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineSequencePoints method [.NET Framework debugging]
ms.assetid: 64202baf-be6b-40ba-8162-8cc6c0c9b8e1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5825f0425947f109ed834879684357fef7b70959
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123777"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a>ISymUnmanagedWriter::DefineSequencePoints — Metoda
Definiuje grupę punktów sekwencji w bieżącej metodzie. Każda linia początkowa i kolumnę początkową definiują rozpoczęcia instrukcji wewnątrz metody. Zakończenie każdego wiersza i zakończenie kolumnę zdefiniuj końca instrukcji wewnątrz metody. Tablice powinny być sortowane rosnąco przesunięcia. Przesunięcie zawsze jest mierzony od początku metody, w bajtach.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `document`  
 [in] Obiekt dokumentu, dla której są zdefiniowane punktów sekwencji.  
  
 `spCount`  
 [in] A `ULONG32` oznacza to rozmiar wszystkich `offsets`, `lines`, `columns`, `endLines`, i `endColumns` buforów.  
  
 `offsets`  
 [in] Przesunięcie punktów sekwencji jest mierzony od początku metody.  
  
 `lines`  
 [in] Linia początkowa liczby punktów sekwencji.  
  
 `columns`  
 [in] Począwszy od liczby kolumn punktów sekwencji.  
  
 `endLines`  
 [in] Końcowy numery wierszy punktów sekwencji. Ten parametr jest opcjonalny.  
  
 `endColumns`  
 [in] Końcowej kolumny liczby punktów sekwencji. Ten parametr jest opcjonalny.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [ISymUnmanagedWriter, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

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
ms.openlocfilehash: 63ba108bc234e566450bb019afc63acb4e75ad1f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427985"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a>ISymUnmanagedWriter::DefineSequencePoints — Metoda
Definiuje grupę punktów sekwencji w bieżącej metodzie. Każda linia początkowa i początkowa kolumna definiują początek instrukcji w ramach metody. Każdy wiersz końcowy i kolumna końcowa definiują koniec instrukcji w ramach metody. Tablice powinny być sortowane w kolejności rosnącej. Przesunięcie jest zawsze mierzone od początku metody, w bajtach.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `document`  
 podczas Obiekt dokumentu, dla którego są definiowane punkty sekwencji.  
  
 `spCount`  
 podczas `ULONG32`, który wskazuje rozmiar każdego z `offsets`, `lines`, `columns`, `endLines`i `endColumns` buforów.  
  
 `offsets`  
 podczas Przesunięcie punktów sekwencji mierzone od początku metody.  
  
 `lines`  
 podczas Numery wierszy początkowych punktów sekwencji.  
  
 `columns`  
 podczas Numery kolumn początkowych punktów sekwencji.  
  
 `endLines`  
 podczas Numery wierszy zakończenia punktów sekwencji. Ten parametr jest opcjonalny.  
  
 `endColumns`  
 podczas Numery kolumn końcowych punktów sekwencji. Ten parametr jest opcjonalny.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedWriter, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

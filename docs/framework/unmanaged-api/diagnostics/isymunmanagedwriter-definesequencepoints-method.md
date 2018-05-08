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
ms.openlocfilehash: 1dc87b201638bab974c59722a69300977b14cf08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a>ISymUnmanagedWriter::DefineSequencePoints — Metoda
Definiuje grupę punkty sekwencji w bieżącej metodzie. Każdego wiersza początkowego i kolumna początkowa definiują rozpoczęcia instrukcji w metodzie. Każdy zakończenia wiersza i kończąc na kolumnie zdefiniuj końca instrukcji w metodzie. Tablice mają być sortowane w rosnącej kolejności przesunięcia. Przesunięcie jest zawsze mierzona od początku metody, w bajtach.  
  
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
 [in] Obiekt dokumentu, dla której są zdefiniowane punkty sekwencji.  
  
 `spCount`  
 [in] A `ULONG32` czy wskazuje rozmiar poszczególnych `offsets`, `lines`, `columns`, `endLines`, i `endColumns` buforów.  
  
 `offsets`  
 [in] Przesunięcie punkty sekwencji zmierzony od początku metody.  
  
 `lines`  
 [in] Numery wiersza początkowego punkty sekwencji.  
  
 `columns`  
 [in] Początkowy numery kolumn punkty sekwencji.  
  
 `endLines`  
 [in] Końcowy numery wierszy punkty sekwencji. Ten parametr jest opcjonalny.  
  
 `endColumns`  
 [in] Końcowy numery kolumn punkty sekwencji. Ten parametr jest opcjonalny.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [ISymUnmanagedWriter, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

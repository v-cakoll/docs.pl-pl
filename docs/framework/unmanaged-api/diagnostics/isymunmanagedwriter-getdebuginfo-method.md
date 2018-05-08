---
title: ISymUnmanagedWriter::GetDebugInfo — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.GetDebugInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::GetDebugInfo
helpviewer_keywords:
- ISymUnmanagedWriter::GetDebugInfo method [.NET Framework debugging]
- GetDebugInfo method [.NET Framework debugging]
ms.assetid: dd31c210-6829-45eb-927e-cc53932638b7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c1e9a2261ab5fd06e0514efdddf8a8e952a6e3d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a>ISymUnmanagedWriter::GetDebugInfo — Metoda
Zwraca informacje niezbędne do kompilatora, aby zapisać wpis katalogu debugowania w przenośnych nagłówka pliku wykonywalnego (PE). Moduł zapisujący symbol wypełnia wszystkie pola z wyjątkiem `TimeDateStamp` i `PointerToRawData`. (Kompilator jest odpowiedzialny za odpowiednie ustawienie tych dwóch pól).  
  
 Kompilator powinien wywołać tę metodę, Emituj danych obiektu blob do pliku PE, ustaw `PointerToRawData` w IMAGE_DEBUG_DIRECTORY polecenie emitowany dane i zapis IMAGE_DEBUG_DIRECTORY pliku PE. Kompilator należy również ustawić `TimeDateStamp` równą `TimeDateStamp` Trwa generowanie pliku PE.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pIDD`  
 [w, out] Wskaźnik do IMAGE_DEBUG_DIRECTORY, który wypełnia twórcę symbolu.  
  
 `cData`  
 [in] A `DWORD` zawierający rozmiar danych debugowania.  
  
 `pcData`  
 [out] Wskaźnik do `DWORD` odbierająca rozmiar buforu, muszą zawierać dane debugowania.  
  
 `data`  
 [out] Wskaźnik do buforu, który jest wystarczająco duży, aby pomieścić dane magazynu symboli debugowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [ISymUnmanagedWriter, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

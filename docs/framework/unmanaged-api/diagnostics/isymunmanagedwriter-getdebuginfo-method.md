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
ms.openlocfilehash: f8eb4cb6bad95295e10a72812fa8dbb0adfcc898
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614789"
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a>ISymUnmanagedWriter::GetDebugInfo — Metoda
Zwraca informacje niezbędne do zapisania przez kompilator wpisu katalogu debugowania w nagłówku przenośnego pliku wykonywalnego (PE). Moduł zapisywania symboli wypełnia wszystkie pola z wyjątkiem `TimeDateStamp` i `PointerToRawData` . (Kompilator jest odpowiedzialny za odpowiednie ustawienie tych dwóch pól).  
  
 Kompilator powinien wywołać tę metodę, emitować obiekt BLOB danych do pliku PE, ustawić `PointerToRawData` pole w IMAGE_DEBUG_DIRECTORY, aby wskazywało emitowane dane, i zapisać IMAGE_DEBUG_DIRECTORY do pliku PE. Kompilator powinien również ustawić pole tak `TimeDateStamp` , aby było równe `TimeDateStamp` wygenerowanego pliku PE.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `pIDD`  
 [in. out] Wskaźnik do IMAGE_DEBUG_DIRECTORY wypełniania przez moduł zapisujący symboli.  
  
 `cData`  
 podczas A `DWORD` , który zawiera rozmiar danych debugowania.  
  
 `pcData`  
 określoną Wskaźnik do obiektu `DWORD` , który odbiera rozmiar buforu wymaganego do przechowywania danych debugowania.  
  
 `data`  
 określoną Wskaźnik do buforu, który jest wystarczająco duży, aby pomieścić dane debugowania dla magazynu symboli.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedWriter — Interfejs](isymunmanagedwriter-interface.md)

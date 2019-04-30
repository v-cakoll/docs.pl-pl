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
ms.openlocfilehash: 41d96c6d2024dbc3cab669f2dba2f99faef89f4b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701297"
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a>ISymUnmanagedWriter::GetDebugInfo — Metoda
Zwraca informacje niezbędne do kompilatora zapisać wpis katalogu debugowania w przenośnych nagłówka pliku wykonywalnego (PE). Moduł zapisujący symbol wypełni wszystkie pola z wyjątkiem `TimeDateStamp` i `PointerToRawData`. (Kompilator jest odpowiedzialny za odpowiednie ustawienie tych dwóch pól).  
  
 Kompilatora powinna wywołać tę metodę, emisji obiektu blob danych do pliku PE, ustawianie `PointerToRawData` pole IMAGE_DEBUG_DIRECTORY polecenie emitowany dane i zapisać IMAGE_DEBUG_DIRECTORY do pliku PE. Kompilator należy również ustawić `TimeDateStamp` równą `TimeDateStamp` pliku PE generowane.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `pIDD`  
 [out w] Wskaźnik do IMAGE_DEBUG_DIRECTORY, który wypełni moduł zapisujący symboli.  
  
 `cData`  
 [in] Element `DWORD` zawierający rozmiar danych debugowania.  
  
 `pcData`  
 [out] Wskaźnik do `DWORD` odbierająca rozmiar buforu, muszą zawierać dane debugowania.  
  
 `data`  
 [out] Wskaźnik do buforu, który jest wystarczająco duży, aby pomieścić dane debugowania do magazynu symboli.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedWriter, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

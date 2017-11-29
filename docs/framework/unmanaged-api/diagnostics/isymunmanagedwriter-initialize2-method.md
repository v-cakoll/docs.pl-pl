---
title: "ISymUnmanagedWriter::Initialize2 — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.Initialize2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::Initialize2
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize2 method [.NET Framework debugging]
- Initialize2 method [.NET Framework debugging]
ms.assetid: 93de56b6-4ae8-4cca-acdc-25a434623509
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e76543c35a717b95ae37985648986abaf16bf85d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriterinitialize2-method"></a>ISymUnmanagedWriter::Initialize2 — Metoda
Ustawienie interfejsu nadajnika metadanych, z którą ten moduł zapisujący zostanie skojarzony, a nazwa pliku wyjściowego, na którym zostanie zapisany symbole debugowania. Ta metoda umożliwia również ustawić ostatecznej lokalizacji pliku programu (PDB) bazy danych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
#### <a name="parameters"></a>Parametry  
 `emitter`  
 [in] Wskaźnik do interfejsu nadajnika metadanych.  
  
 `tempfilename`  
 [in] Wskaźnik do `WCHAR` zawierający nazwę pliku, do którego są zapisywane symbole debugowania. Jeśli nazwa pliku jest określona dla składnika zapisywania, która nie korzysta z nazw plików, ten parametr jest ignorowany.  
  
 `pIStream`  
 [in] Jeśli zostanie określona, moduł zapisujący symbol emituje symbole w danym <xref:System.Runtime.InteropServices.ComTypes.IStream> , a nie do pliku określonego w `filename` parametru. `pIStream` Parametr jest opcjonalny.  
  
 `fFullBuild`  
 [in] `true` Jeśli jest to ponownej pełnej kompilacji; `false` Jeśli jest to kompilacji przyrostowej.  
  
 `finalfilename`  
 [in] Wskaźnik do `WCHAR` oznacza to ciąg ścieżki do ostatecznego lokalizację pliku PDB.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [ISymUnmanagedWriter — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [Initialize — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)

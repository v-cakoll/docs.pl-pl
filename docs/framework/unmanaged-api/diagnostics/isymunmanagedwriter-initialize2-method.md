---
title: ISymUnmanagedWriter::Initialize2 — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize2
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize2 method [.NET Framework debugging]
- Initialize2 method [.NET Framework debugging]
ms.assetid: 93de56b6-4ae8-4cca-acdc-25a434623509
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f65262a9b9850d93e934a77f154bb625a55e1e82
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514247"
---
# <a name="isymunmanagedwriterinitialize2-method"></a>ISymUnmanagedWriter::Initialize2 — Metoda
Ustawia interfejsu nadajnika metadanych, z którym ten moduł zapisujący zostanie skojarzona i ustawia nazwę pliku wyjściowego, do którego symbole debugowania zostaną zapisane. Ta metoda umożliwia również ustawić ostateczny lokalizacja pliku bazy danych (PDB) programu.  
  
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
 [in] Wskaźnik do `WCHAR` zawierający nazwę pliku, do którego symbole debugowania są zapisywane. Jeśli nazwa pliku jest określony dla modułu zapisującego, która nie korzysta z nazw plików, ten parametr jest ignorowany.  
  
 `pIStream`  
 [in] Jeśli zostanie określony, moduł zapisujący symbol emituje symbole w danym <xref:System.Runtime.InteropServices.ComTypes.IStream> , a nie do pliku określonego w `filename` parametru. `pIStream` Parametr jest opcjonalny.  
  
 `fFullBuild`  
 [in] `true` Jeśli po ponownej pełnej kompilacji; `false` Jeśli jest to kompilacji przyrostowej.  
  
 `finalfilename`  
 [in] Wskaźnik do `WCHAR` czyli ciąg ścieżki do ostatecznego lokalizacji pliku PDB.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także
- [ISymUnmanagedWriter, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [Initialize, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)

---
title: ISymUnmanagedWriter::Initialize — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: e0ebd793-3764-4df0-8f12-0e95f60b9eae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 417cf623948d16147f9a1242d714f4df1311a314
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212053"
---
# <a name="isymunmanagedwriterinitialize-method"></a>ISymUnmanagedWriter::Initialize — Metoda
Ustawia interfejsu nadajnika metadanych, z którym ten moduł zapisujący zostanie skojarzona i ustawia nazwę pliku wyjściowego, do którego symbole debugowania zostaną zapisane.  
  
 Ta metoda może być wywoływana tylko raz, a musi zostać wywołana przed innymi metodami składnika zapisywania. Niektóre moduły zapisujące może wymagać nazwy pliku. Zawsze można jednak przekazać nazwę pliku do tej metody bez żadnych negatywny wpływ na modułów zapisujących, które nie korzystają z nazwy pliku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
## <a name="parameters"></a>Parametry  
 `emitter`  
 [in] Wskaźnik do interfejsu nadajnika metadanych.  
  
 `filename`  
 [in] Nazwa pliku, do którego symbole debugowania są zapisywane. Jeśli nazwa pliku jest określony dla modułu zapisującego, która nie korzysta z nazw plików, ten parametr jest ignorowany.  
  
 `pIStream`  
 [in] Jeśli zostanie określony, moduł zapisujący symbol zostanie wyemitowany symbole w danym <xref:System.Runtime.InteropServices.ComTypes.IStream> , a nie do pliku określonego w `filename` parametru. `pIStream` Parametr jest opcjonalny.  
  
 `fFullBuild`  
 [in] `true` Jeśli po ponownej pełnej kompilacji; `false` Jeśli jest to kompilacji przyrostowej.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedWriter — Interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [Initialize2, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)

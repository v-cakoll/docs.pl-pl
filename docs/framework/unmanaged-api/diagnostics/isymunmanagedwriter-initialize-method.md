---
title: "ISymUnmanagedWriter::Initialize — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.Initialize
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::Initialize
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: e0ebd793-3764-4df0-8f12-0e95f60b9eae
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bae368919941e6a0b234736f789320b62405a17b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriterinitialize-method"></a>ISymUnmanagedWriter::Initialize — Metoda
Ustawienie interfejsu nadajnika metadanych, z którą ten moduł zapisujący zostanie skojarzony, a nazwa pliku wyjściowego, na którym zostanie zapisany symbole debugowania.  
  
 Tę metodę można wywołać tylko raz i musi zostać wywołana przed innych metod składnika zapisywania. Niektóre moduły zapisujące może wymagać nazwy pliku. Zawsze można jednak przekazać nazwę pliku do tej metody bez żadnych negatywny wpływ na składniki zapisywania, które nie należy używać nazwy pliku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
#### <a name="parameters"></a>Parametry  
 `emitter`  
 [in] Wskaźnik do interfejsu nadajnika metadanych.  
  
 `filename`  
 [in] Nazwa pliku, do którego są zapisywane symbole debugowania. Jeśli nazwa pliku jest określona dla składnika zapisywania, która nie korzysta z nazw plików, ten parametr jest ignorowany.  
  
 `pIStream`  
 [in] Jeśli zostanie określona, moduł zapisujący symbol będzie Emituj symbole w danym <xref:System.Runtime.InteropServices.ComTypes.IStream> , a nie do pliku określonego w `filename` parametru. `pIStream` Parametr jest opcjonalny.  
  
 `fFullBuild`  
 [in] `true` Jeśli jest to ponownej pełnej kompilacji; `false` Jeśli jest to kompilacji przyrostowej.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [ISymUnmanagedWriter — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [Initialize2 — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)

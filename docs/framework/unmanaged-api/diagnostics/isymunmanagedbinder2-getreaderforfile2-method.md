---
title: "ISymUnmanagedBinder2::GetReaderForFile2 — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder2.GetReaderForFile2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder2::GetReaderForFile2
helpviewer_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2 method [.NET Framework debugging]
- GetReaderForFile2 method [.NET Framework debugging]
ms.assetid: dd92dcaf-403c-464d-a254-21594985dddd
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d232bfed801a17e1ee47dee7643ae0bf21d338e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a>ISymUnmanagedBinder2::GetReaderForFile2 — Metoda
Podany interfejs metadanych i nazwę pliku, zwraca poprawny <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interfejs, który będzie odczytywać symbole debugowania skojarzone z modułu.  
  
 Ta metoda zapewnia bardziej rozległych Wyszukaj plik programu (PDB) bazy danych niż [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
#### <a name="parameters"></a>Parametry  
 `importer`  
 [in] Wskaźnik do interfejsu importu metadanych.  
  
 `fileName`  
 [in] Wskaźnik do nazwy pliku.  
  
 `searchPath`  
 [in] Wskaźnik do ścieżki wyszukiwania.  
  
 `searchPolicy`  
 [in] Wartość [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) wyliczenia, która określa zasady, która ma być używane podczas wyszukiwania dla czytnika symboli.  
  
 `pRetVal`  
 [out] Wskaźnik, który jest ustawiony na zwracana <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interfejsu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="remarks"></a>Uwagi  
 Ta wersja metody można wyszukiwać pliku PDB w obszarach innych niż prawo obok modułu. Wyszukiwanie zasad mogą być kontrolowane przez połączenie [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md). Na przykład `AllowReferencePathAccess | AllowSymbolServerAccess` szuka pliku PDB obok pliku wykonywalnego i na serwerze symboli nie zapytanie dotyczące rejestru lub użyj ścieżki pliku wykonywalnego. Jeśli `searchPath` podano parametru, te katalogi zawsze będą wyszukiwane.  
  
## <a name="see-also"></a>Zobacz też  
 [ISymUnmanagedBinder2 — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 [GetReaderForFile — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)

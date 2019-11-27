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
ms.openlocfilehash: 041df959139a0be77f40d6aa5655ff15f93fb26f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427941"
---
# <a name="isymunmanagedwriterinitialize2-method"></a>ISymUnmanagedWriter::Initialize2 — Metoda
Ustawia interfejs emitujący metadane, z którym jest skojarzony ten składnik zapisywania i ustawia nazwę pliku wyjściowego, do którego będą zapisywane symbole debugowania. Ta metoda umożliwia również ustawienie końcowej lokalizacji pliku bazy danych programu (PDB).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
## <a name="parameters"></a>Parametry  
 `emitter`  
 podczas Wskaźnik do interfejsu emitującego metadane.  
  
 `tempfilename`  
 podczas Wskaźnik do `WCHAR`, który zawiera nazwę pliku, do którego są zapisywane symbole debugowania. Jeśli nazwa pliku jest określona dla składnika zapisywania, który nie używa nazw plików, ten parametr jest ignorowany.  
  
 `pIStream`  
 podczas Jeśli ta wartość jest określona, moduł zapisujący symboli emituje symbole do danego <xref:System.Runtime.InteropServices.ComTypes.IStream>, a nie do pliku określonego w parametrze `filename`. Parametr `pIStream` jest opcjonalny.  
  
 `fFullBuild`  
 [in] `true`, jeśli jest to pełna kompilacja; `false`, jeśli jest to kompilacja przyrostowa.  
  
 `finalfilename`  
 podczas Wskaźnik do `WCHAR`, który jest ciągiem ścieżki do ostatecznej lokalizacji pliku PDB.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedWriter, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [Initialize, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)

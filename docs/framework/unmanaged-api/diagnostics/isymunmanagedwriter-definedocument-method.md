---
title: ISymUnmanagedWriter::DefineDocument — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineDocument
helpviewer_keywords:
- ISymUnmanagedWriter::DefineDocument method [.NET Framework debugging]
- DefineDocument method [.NET Framework debugging]
ms.assetid: c3bf15b0-3250-4bbe-b9b5-c5d695289b6f
topic_type:
- apiref
ms.openlocfilehash: fdcfb0c4f9c21eb516f4196d0c8f682669468219
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615231"
---
# <a name="isymunmanagedwriterdefinedocument-method"></a>ISymUnmanagedWriter::DefineDocument — Metoda
Definiuje dokument źródłowy. Identyfikatory GUID są udostępniane dla znanych języków, dostawców i typów dokumentów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
## <a name="parameters"></a>Parametry  
 `url`  
 podczas Wskaźnik do obiektu `WCHAR` , który definiuje adres URL (Uniform Resource Locator) identyfikujący dokument.  
  
 `language`  
 podczas Wskaźnik do identyfikatora GUID, który definiuje język dokumentu.  
  
 `languageVendor`  
 podczas Wskaźnik do identyfikatora GUID, który definiuje tożsamość dostawcy dla języka dokumentu.  
  
 `documentType`  
 podczas Wskaźnik do identyfikatora GUID, który definiuje typ dokumentu.  
  
 `pRetVal`  
 określoną Wskaźnik do zwracanego interfejsu [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) .  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedWriter — Interfejs](isymunmanagedwriter-interface.md)

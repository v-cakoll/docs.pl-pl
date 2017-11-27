---
title: "ISymUnmanagedReader::UpdateSymbolStore — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.UpdateSymbolStore
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::UpdateSymbolStore
helpviewer_keywords:
- UpdateSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::UpdateSymbolStore method [.NET Framework debugging]
ms.assetid: 4a17d723-86b9-4f27-bd0d-b70c3259011c
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cfea77814069f6689f7492608548836fdafa591b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a>ISymUnmanagedReader::UpdateSymbolStore — Metoda
Aktualizuje istniejący magazyn symbol magazynu symboli delta. Ta metoda jest używana w scenariuszach edit-and-continue można zaktualizować magazynu symboli do dopasowania delty do oryginalnego przenośnego (PE) pliku wykonywalnego.  
  
> [!NOTE]
>  Należy określić tylko jeden z `filename` lub `pIStream` parametrów nie oba. Jeśli `filename` określono magazyn symbol zostanie zaktualizowany przy użyciu symboli w tym pliku. Jeśli `pIStream` określono magazyn zostanie zaktualizowany przy użyciu danych z <xref:System.Runtime.InteropServices.ComTypes.IStream>.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT UpdateSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
#### <a name="parameters"></a>Parametry  
 `filename`  
 [in] Nazwa pliku, który zawiera magazynu symboli.  
  
 `pIStream`  
 [in] Strumień pliku używany zamiast `filename` parametru.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [ISymUnmanagedReader — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

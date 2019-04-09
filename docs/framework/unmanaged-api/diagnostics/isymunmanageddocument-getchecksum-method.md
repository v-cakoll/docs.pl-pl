---
title: ISymUnmanagedDocument::GetCheckSum — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSum method [.NET Framework debugging]
- GetCheckSum method [.NET Framework debugging]
ms.assetid: 9bc881b3-e2ce-48a7-ad69-17eaaa304120
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a60bf279c143559e7410d8dfd8213d3da1d05a6d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127565"
---
# <a name="isymunmanageddocumentgetchecksum-method"></a>ISymUnmanagedDocument::GetCheckSum — Metoda
Pobiera sumy kontrolnej.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cData`  
 [in] Długość buforu, dostarczone przez `data` parametru  
  
 `pcData`  
 [out] Rozmiar i długość sumy kontrolnej, w bajtach.  
  
 `data`  
 [out] Bufor, który odbiera sumę kontrolną.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie kod błędu.  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedDocument — Interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)

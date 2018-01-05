---
title: "ISymENCUnmanagedMethod::GetSourceExtentInDocument — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymENCUnmanagedMethod.GetSourceExtentInDocument
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymENCUnmanagedMethod::GetSourceExtentInDocument
helpviewer_keywords:
- GetSourceExtentInDocument method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetSourceExtentInDocument method [.NET Framework debugging]
ms.assetid: 9c5566ab-4ec7-4b61-9753-839bb90ae78c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6116ee89cb643cc0010ef2c8a463fa131777584e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymencunmanagedmethodgetsourceextentindocument-method"></a>ISymENCUnmanagedMethod::GetSourceExtentInDocument — Metoda
Pobiera najmniejszą liczbę wierszy i uruchomić największy wiersz end dla metody w określonego dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetSourceExtentInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [out] ULONG32* pstartLine,  
    [out] ULONG32* pendLine);  
```  
  
#### <a name="parameters"></a>Parametry  
 `document`  
 [in] Wskaźnik do dokumentu.  
  
 `pstartLine`  
 [out] Wskaźnik do `ULONG32` odbierająca start wiersza.  
  
 `pendLine`  
 [out] Wskaźnik do `ULONG32` odbierająca zakończyć wiersza.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [ISymENCUnmanagedMethod, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)

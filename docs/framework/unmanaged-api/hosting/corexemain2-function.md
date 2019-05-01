---
title: _CorExeMain2 — Funkcja
ms.date: 03/30/2017
api_name:
- _CorExeMain2
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain2
helpviewer_keywords:
- _CorExeMain2 function [.NET Framework hosting]
ms.assetid: 72ea68b4-689f-4733-9416-9664b75e8892
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f968d84ae695eb1da127538ebdc5e4f55d6ebf39
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985858"
---
# <a name="corexemain2-function"></a>_CorExeMain2 — Funkcja
Uruchamia punkt wejścia w określonym kodzie mapowanym w pamięci. Ta funkcja jest wywoływana przez program ładujący systemu operacyjnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain2 (  
   [in] PBYTE           pUnmappedPE,  
   [in] DWORD           cUnmappedPE,  
   [in] __in LPWSTR     pImageNameIn,  
   [in] __in LPWSTR     pLoadersFileName,  
   [in] __in LPWSTR     pCmdLine  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pUnmappedPE`  
 [in] Wskaźnik do kodzie mapowanym w pamięci.  
  
 `cUnmappedPE`  
 [in] Liczba elementów, które `pUnmappedPE` może przechowywać.  
  
 `pImageNameIn`  
 [in] Wskaźnik na nazwę obrazu pliku wykonywalnego.  
  
 `pLoadersFileName`  
 [in] Nazwa pliku modułu ładującego.  
  
 `pCmdLine`  
 [in] Parametry wiersza polecenia, jeśli istnieje.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Statyczne funkcje globalne metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

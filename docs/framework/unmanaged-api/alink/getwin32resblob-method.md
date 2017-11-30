---
title: "GetWin32ResBlob — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.GetWin32ResBlob
api_location: alink.dll
api_type: COM
f1_keywords: GetWin32ResBlob
helpviewer_keywords: GetWin32ResBlob method
ms.assetid: 36997e04-f9f6-4254-a041-6767ac6c51d9
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9c4456757c56440463010d4adc3d3eed90dbc07a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="getwin32resblob-method"></a>GetWin32ResBlob — Metoda
Pobiera obiekt blob zasobów Win32. Tę metodę można wywołać po ustawieniu opcji zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetWin32ResBlob(  
    mdAssembly    AssemblyID,  
    mdToken       FileToken,  
    BOOL          fDll,  
    LPCWSTR       pszIconFile,  
    const void**  ppResBlob,  
    DWORD*        pcbResBlob  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametry  
 `AssemblyID`  
 Identyfikator zestawu.  
  
 `FileToken`  
 Token pliku używany do pobierania nazwy pliku do użycia podczas tworzenia zasobów Win32 wersji  
  
 `fDll`  
 Wartość TRUE, jeśli plik jest biblioteki DLL, false dla pliku EXE.  
  
 `pszIconFile`  
 Ikona opcjonalne wstawiania do obiektu blob zasobów.  
  
 `ppResBlob`  
 Odbiera zasobów obiektu blob.  
  
 `pcbResBlob`  
 Odbiera rozmiar obiektu blob.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga alink.h  
  
## <a name="see-also"></a>Zobacz też  
 [Ialink — interfejs](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [Ialink2 — interfejs](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)

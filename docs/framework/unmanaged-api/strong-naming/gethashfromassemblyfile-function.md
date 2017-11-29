---
title: "GetHashFromAssemblyFile — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetHashFromAssemblyFile
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetHashFromAssemblyFile
helpviewer_keywords: GetHashFromAssemblyFile function [.NET Framework strong naming]
ms.assetid: 751ed69f-b7ab-4e07-80de-e17ca9319b0c
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1598e4e332525f87392ae5b0ad486a735e760651
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="gethashfromassemblyfile-function"></a>GetHashFromAssemblyFile — Funkcja
Pobiera skrót określonego pliku zestawu, przy użyciu określonego algorytmu skrótu.  
  
 Ta funkcja jest przestarzała. Użyj [ICLRStrongName::GetHashFromAssemblyFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md) metody zamiast tego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szFilePath`  
 [in] Ścieżka do pliku, aby być mieszany.  
  
 `piHashAlg`  
 [w, out] Stała, który określa algorytm wyznaczania wartości skrótu. Użyj wartości zero dla domyślny algorytm skrótu.  
  
 `pbHash`  
 [out] Bufor zwrócony wyznaczania wartości skrótu.  
  
 `cchHash`  
 [in] Maksymalny rozmiar żądanej z `pbHash`.  
  
 `pchHash`  
 [out] Zwrócony rozmiar w bajtach z `pbHash`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [GetHashFromAssemblyFile — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)  
 [GetHashFromAssemblyFileW — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)  
 [ICLRStrongName — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

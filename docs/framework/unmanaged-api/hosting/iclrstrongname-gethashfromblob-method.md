---
title: "ICLRStrongName::GetHashFromBlob — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.GetHashFromBlob
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::GetHashFromBlob
helpviewer_keywords:
- ICLRStrongName::GetHashFromBlob method [.NET Framework hosting]
- GetHashFromBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: f91d0f89-f356-49ac-aafb-50fad963c13d
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: afb3614d4911b7e8b8666b1205af1c1d3d176b5d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="iclrstrongnamegethashfromblob-method"></a>ICLRStrongName::GetHashFromBlob — Metoda
Pobiera skrót zestawu pod adresem określonym pamięci, przy użyciu określonego algorytmu skrótu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetHashFromBlob (  
    [in]  BYTE    *pbBlob,  
    [in]  DWORD   cchBlob,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE    *pbHash,  
    [in]  DWORD   cchHash,  
    [out] DWORD   *pchHash  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbBlob`  
 [in] Wskaźnik do adresu blok pamięci, aby być mieszany.  
  
 `cchBlob`  
 [in] Długość, w bajtach bloku pamięci.  
  
 `piHashAlg`  
 [w, out] Stała, który określa algorytm wyznaczania wartości skrótu. Użyj wartości zero dla domyślnego algorytmu.  
  
 `pbHash`  
 [out] Bufor zwrócony wyznaczania wartości skrótu.  
  
 `cchHash`  
 [in] Maksymalny rozmiar żądanej z `pbHash`.  
  
 `pchHash`  
 [out] Rozmiar w bajtach, zwracana `pbHash`.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK`Jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje niepowodzenie (zobacz [wspólne wartości HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) lista).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRStrongName — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

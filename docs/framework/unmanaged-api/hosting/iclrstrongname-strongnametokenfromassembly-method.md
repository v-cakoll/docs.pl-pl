---
title: ICLRStrongName::StrongNameTokenFromAssembly — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromAssembly
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromAssembly method [.NET Framework hosting]
- StrongNameTokenFromAssembly method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: fc725afb-b66b-4015-aa44-1c0d1304197f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ffc1ed158caea1e3ddbc2dc1f4f828e0618c722e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656781"
---
# <a name="iclrstrongnamestrongnametokenfromassembly-method"></a>ICLRStrongName::StrongNameTokenFromAssembly — Metoda
Tworzy token silnej nazwy z określonego pliku zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `wszFilePath`  
 [in] Ścieżka do pliku wykonalnego (PE) pliku zestawu.  
  
 `ppbStrongNameToken`  
 [out] Token zwracany silnej nazwy.  
  
 `pcbStrongNameToken`  
 [out] Rozmiar w bajtach, token silnej nazwy.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).  
  
## <a name="remarks"></a>Uwagi  
 Token silna nazwa jest skrócona forma klucza publicznego. Token jest 64-bitową wartość skrótu, utworzona na podstawie klucza publicznego używany do podpisywania zestawu. Token jest częścią silnej nazwy zestawu i może zostać odczytany z metadanych zestawu.  
  
 Po utworzeniu tokenu należy wywołać [iclrstrongname::strongnamefreebuffer —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metodę, aby zwolnić alokacji pamięci.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [StrongNameTokenFromAssemblyEx, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

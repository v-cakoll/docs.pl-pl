---
title: ICLRStrongName::StrongNameCompareAssemblies — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameCompareAssemblies
helpviewer_keywords:
- ICLRStrongName::StrongNameCompareAssemblies method [.NET Framework hosting]
- StrongNameCompareAssemblies method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: b1fb356c-72cf-4aa4-8376-f291a6d97c01
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63d4b885b6968b800bc965a9be1ec6b795a42220
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59140663"
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a>ICLRStrongName::StrongNameCompareAssemblies — Metoda
Określa, czy dwa zestawy różnią się tylko ich podpisy silnej nazwy.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszAssembly1`  
 [in] Ścieżka do pierwszego zestawu.  
  
 `wszAssembly2`  
 [in] Ścieżka do drugiego zestawu.  
  
 `pdwResult`  
 [out] Jeden z następujących wartości:  
  
-   `SN_CMP_DIFFERENT` (0) — określa, że zestawy zawierają różne dane.  
  
-   `SN_CMP_IDENTICAL` (1) — określa, że zestawy są dokładnie takie same, łącznie z ich podpisy i sumy kontrolnej.  
  
-   `SN_CMP_SIGONLY` (2) — określa, że zestawy różnią się jedynie podpisu i sum kontrolnych.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="remarks"></a>Uwagi  
 Podpis silnej nazwy zestawu składa się z tekstu nazwę zestawu, wersji, kultury i token klucza publicznego.  
  
## <a name="see-also"></a>Zobacz także

- [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

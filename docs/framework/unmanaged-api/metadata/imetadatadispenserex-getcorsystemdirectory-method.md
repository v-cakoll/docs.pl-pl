---
title: IMetaDataDispenserEx::GetCORSystemDirectory — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.GetCORSystemDirectory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory
helpviewer_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory method [.NET Framework metadata]
- GetCORSystemDirectory method [.NET Framework metadata]
ms.assetid: d9e0f3b6-e106-4820-bada-5bfba34ce360
topic_type:
- apiref
ms.openlocfilehash: a76c17e663fdf6555ed878cca1b86b6a9395730e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008797"
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a>IMetaDataDispenserEx::GetCORSystemDirectory — Metoda
Pobiera katalog, który przechowuje bieżące środowisko uruchomieniowe języka wspólnego (CLR). Ta metoda jest obsługiwana tylko dla debugerów out-of-process. Jeśli wywoływana z innego składnika, zwróci E_NOTIMPL.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,
    [in]  DWORD       cchBuffer,
    [out] DWORD*      pchBuffer  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szBuffer`  
 określoną Bufor, w którym ma zostać odebrana nazwa katalogu.  
  
 `cchBuffer`  
 podczas Rozmiar, w bajtach, z `szBuffer` .  
  
 `pchBuffer`  
 określoną Liczba bajtów, które faktycznie zostały zwrócone `szBuffer` .  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataDispenserEx, interfejs](imetadatadispenserex-interface.md)
- [IMetaDataDispenser — Interfejs](imetadatadispenser-interface.md)

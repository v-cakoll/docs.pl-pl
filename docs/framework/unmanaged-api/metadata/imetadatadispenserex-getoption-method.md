---
title: IMetaDataDispenserEx::GetOption — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.GetOption
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::GetOption
helpviewer_keywords:
- GetOption method [.NET Framework metadata]
- IMetaDataDispenserEx::GetOption method [.NET Framework metadata]
ms.assetid: d7f794e5-8e25-4d65-850a-7c34fbfce87d
topic_type:
- apiref
ms.openlocfilehash: 816e2f2dc7d4d00f74f67720ee45d7b3483e57fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177719"
---
# <a name="imetadatadispenserexgetoption-method"></a>IMetaDataDispenserEx::GetOption — Metoda
Pobiera wartość określonej opcji dla bieżącego zakresu metadanych. Opcja określa sposób obsługi wywołań bieżącego zakresu metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `optionId`  
 [w] Wskaźnik do identyfikatora GUID, który określa opcję do pobrania. Zobacz sekcję Uwagi, aby uzyskać listę obsługiwanych identyfikatorów GUID.  
  
 `pValue`  
 [na zewnątrz] Wartość zwróconej opcji. Typ tej wartości będzie wariantem typu określonej opcji.  
  
## <a name="remarks"></a>Uwagi  
 Na poniższej liście przedstawiono identyfikatory GUID, które są obsługiwane dla tej metody. Opisy można znaleźć w pliku [IMetaDataDispenserEx::SetOption.](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) Jeśli `optionId` nie ma tej listy, ta `E_INVALIDARG`metoda zwraca HRESULT , wskazując niepoprawny parametr.  
  
- MetaDataCheckDuplicatesFor  
  
- MetaDataRefToDefCheck  
  
- MetaDataNotificationForTokenMovement  
  
- MetaDataSetENC  
  
- MetaDataErrorIfEmitOutOfOrder  
  
- MetaDataGenerateTCEAdapters  
  
- MetaDataLinkerOptions  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataDispenserEx, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataDispenser — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)

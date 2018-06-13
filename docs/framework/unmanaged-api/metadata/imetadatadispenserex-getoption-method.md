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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a117fcdf2ba9d37fb5483cc85fb575e5d3476794
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447677"
---
# <a name="imetadatadispenserexgetoption-method"></a>IMetaDataDispenserEx::GetOption — Metoda
Pobiera wartość określonej opcji dla bieżącego zakresu metadanych. Opcję określa sposób obsługi wywołania do bieżącego zakresu metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetOption (  
    [in]  REFGUID         optionId,   
    [out] const VARIANT   *pValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `optionId`  
 [in] Wskaźnik do identyfikatora GUID, który określa opcje, które mają zostać pobrane. Zobacz sekcję uwag listę obsługiwanych identyfikatorów GUID.  
  
 `pValue`  
 [out] Wartości zwracane opcji. Typ tej wartości będą wariant opcji określonego typu.  
  
## <a name="remarks"></a>Uwagi  
 Poniższa lista zawiera identyfikatory GUID, które są obsługiwane w przypadku tej metody. Aby uzyskać opis, zobacz [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) metody. Jeśli `optionId` jest spoza tej listy, ta metoda zwraca wartość HRESULT `E_INVALIDARG`, wskazując nieprawidłowy parametr.  
  
-   MetaDataCheckDuplicatesFor  
  
-   MetaDataRefToDefCheck  
  
-   MetaDataNotificationForTokenMovement  
  
-   MetaDataSetENC  
  
-   MetaDataErrorIfEmitOutOfOrder  
  
-   MetaDataGenerateTCEAdapters  
  
-   MetaDataLinkerOptions  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataDispenserEx, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [IMetaDataDispenser, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)

---
title: "ICeeGen::GetSectionBlock — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.GetSectionBlock
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::GetSectionBlock
helpviewer_keywords:
- GetSectionBlock method [.NET Framework metadata]
- ICeeGen::GetSectionBlock method [.NET Framework metadata]
ms.assetid: 05c78aaf-5bbd-497e-9ae2-55f4fae0c5fb
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4732eef9a47f9ea1e919bd9d855afbec18974454
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="iceegengetsectionblock-method"></a>ICeeGen::GetSectionBlock — Metoda
Pobiera blok sekcji ścieżki bazowej kodu.  
  
 Ta metoda jest przestarzała i nie powinna być używana.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,     
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);   
```  
  
#### <a name="parameters"></a>Parametry  
 `section`  
 [in] Sekcja, z którego można pobrać z bloku bazy kodu.  
  
 `len`  
 [in] Długość bloku, które mają zostać pobrane.  
  
 `align`  
 [in] Bajt względem początku sekcji, z którą ma zostać Wyrównaj do pierwszego bajtu bloku. Jest to pozycja blok w ramach sekcji.  
  
 `ppBytes`  
 [out] Wskaźnik do lokalizacji, która odbiera adres pobrane bloku.  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie `GetSectionBlock` tylko wtedy, gdy sekcja specjalne wymagania, które nie są obsługiwane za pomocą innych metod.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICeeGen — interfejs](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)

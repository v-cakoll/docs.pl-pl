---
title: "IMapToken::Map — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMapToken.Map
api_location: mscoree.dll
api_type: COM
f1_keywords: IMapToken::Map
helpviewer_keywords:
- IMapToken::Map method [.NET Framework metadata]
- Map method [.NET Framework metadata]
ms.assetid: b9b4bf2f-1098-43d6-9619-a99b4bda1940
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2e3a9701bab27764803442a3cd0c24c4e412deaf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="imaptokenmap-method"></a>IMapToken::Map — Metoda
Mapuje relacji między zestawami przy użyciu podpisów metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Map (  
    [in]  mdToken tkImp,   
    [in]  mdToken tkEmit  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `tkImp`  
 [in] Token metadanych, który reprezentuje obiekt importowany kodu.  
  
 `tkEmit`  
 [in] Token metadanych, który reprezentuje obiekt emitowany kodu.  
  
## <a name="remarks"></a>Uwagi  
 Token mapowane ponownie wystąpi podczas scalania, oryginalny token ma zakres w zakresie metadanych importowanych (źródło), a nowy token, ma zakres w zakresie metadanych emitowany (docelowy).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMapToken — interfejs](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)

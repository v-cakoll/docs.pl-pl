---
title: IMapToken::Map — Metoda
ms.date: 03/30/2017
api_name:
- IMapToken.Map
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMapToken::Map
helpviewer_keywords:
- IMapToken::Map method [.NET Framework metadata]
- Map method [.NET Framework metadata]
ms.assetid: b9b4bf2f-1098-43d6-9619-a99b4bda1940
topic_type:
- apiref
ms.openlocfilehash: 428b022ed560648f59798154d5987d382938c280
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176074"
---
# <a name="imaptokenmap-method"></a>IMapToken::Map — Metoda
Mapuje relację między zestawami przy użyciu podpisów metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tkImp`  
 [w] Token metadanych reprezentujący importowany obiekt kodu.  
  
 `tkEmit`  
 [w] Token metadanych, który reprezentuje obiekt emitowanego kodu.  
  
## <a name="remarks"></a>Uwagi  
 Gdy ponowna mapa tokenu występuje podczas scalania, oryginalny token jest objęty zakresem w zakresie metadanych importowanych (źródłowych), a nowy token jest objęty zakresem w zakresie metadanych emitowanych (docelowych).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMapToken, interfejs](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)

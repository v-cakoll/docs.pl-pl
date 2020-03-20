---
title: ICeeGen::GetSectionBlock — Metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionBlock
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionBlock
helpviewer_keywords:
- GetSectionBlock method [.NET Framework metadata]
- ICeeGen::GetSectionBlock method [.NET Framework metadata]
ms.assetid: 05c78aaf-5bbd-497e-9ae2-55f4fae0c5fb
topic_type:
- apiref
ms.openlocfilehash: a494b1aaa762549528e92ab93d18929ef73eb8da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176087"
---
# <a name="iceegengetsectionblock-method"></a>ICeeGen::GetSectionBlock — Metoda
Pobiera blok sekcji bazy kodu.  
  
 Ta metoda jest przestarzała i nie powinna być używana.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);
```  
  
## <a name="parameters"></a>Parametry  
 `section`  
 [w] Sekcja, z której ma być pobierana blokada bazy kodu.  
  
 `len`  
 [w] Długość bloku do pobrania.  
  
 `align`  
 [w] Bajt względem początku sekcji, z którym należy wyrównać pierwszy bajt bloku. Jest to położenie bloku w sekcji.  
  
 `ppBytes`  
 [na zewnątrz] Wskaźnik do lokalizacji, która odbiera adres pobranego bloku.  
  
## <a name="remarks"></a>Uwagi  
 Wywołaj `GetSectionBlock` tylko wtedy, gdy masz specjalne wymagania sekcji, które nie są obsługiwane przez inne metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICeeGen — Interfejs](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)

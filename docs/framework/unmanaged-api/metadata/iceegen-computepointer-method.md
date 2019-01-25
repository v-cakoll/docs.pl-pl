---
title: ICeeGen::ComputePointer — Metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.ComputePointer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::ComputePointer
helpviewer_keywords:
- ICeeGen::ComputePointer method [.NET Framework metadata]
- ComputePointer method [.NET Framework metadata]
ms.assetid: b6b95c04-0f2c-4fcc-a8bc-3b1dcbdba731
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 496082bbf89ceb93ba3dceef9a9222425db71784
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522417"
---
# <a name="iceegencomputepointer-method"></a>ICeeGen::ComputePointer — Metoda
Określa bufor dla sekcji określonego kodu.  
  
 Ta metoda jest przestarzała i nie powinna być używana.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,   
    [out] UCHAR        **lpBuffer  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `section`  
 [in] Sekcję kodu, dla której ma zostać zwrócone do buforu.  
  
 `RVA`  
 [in] Wirtualny adres względny metody, do których chcesz uzyskać wskaźnika.  
  
 `lpBuffer`  
 [out] Wskaźnik do buforu zwrócone.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICeeGen, interfejs](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)

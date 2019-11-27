---
title: ICeeGen::GetString — Metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetString
helpviewer_keywords:
- ICeeGen::GetString method [.NET Framework metadata]
- GetString method, ICeeGen interface [.NET Framework metadata]
ms.assetid: 7cc22562-128c-440a-9147-55ff20f173d7
topic_type:
- apiref
ms.openlocfilehash: e81ef33f4fb684cce29aa9afb756451b1e5db896
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426168"
---
# <a name="iceegengetstring-method"></a>ICeeGen::GetString — Metoda
Pobiera ciąg przechowywany w określonym względnym adresie wirtualnym.  
  
 Ta metoda jest przestarzała i nie powinna być używana.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetString (  
    [in]  ULONG      RVA,   
    [out] LPWSTR     *lpString  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `RVA`  
 podczas Względny adres wirtualny ciągu do zwrócenia.  
  
 `lpString`  
 określoną Zwrócony ciąg.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICeeGen, interfejs](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)

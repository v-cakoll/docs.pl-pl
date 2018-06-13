---
title: ICeeGen::GetSectionCreate — Metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionCreate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionCreate
helpviewer_keywords:
- ICeeGen::GetSectionCreate method [.NET Framework metadata]
- GetSectionCreate method [.NET Framework metadata]
ms.assetid: 154b2460-59ce-4874-a9f2-1b3353486ac5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 857462c380ce51994e13dab5cfe3c28bba0f38be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443342"
---
# <a name="iceegengetsectioncreate-method"></a>ICeeGen::GetSectionCreate — Metoda
Generuje i pobiera sekcji kodu przy użyciu określonej nazwy i wartości flag.  
  
 Ta metoda jest przestarzała i nie powinna być używana.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 [in] Wskaźnik do ciąg określający nazwę sekcji do utworzenia.  
  
 `flags`  
 [in] Flagi, które określają opcje.  
  
 `section`  
 [out] Wskaźnik do nowo utworzonego kodu sekcji.  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie `GetSectionCreate` tylko wtedy, gdy sekcja specjalne wymagania, które nie są obsługiwane za pomocą innych metod.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICeeGen, interfejs](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)

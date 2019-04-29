---
title: IBindingDisplay::InitializeForProcess — Metoda
ms.date: 03/30/2017
api_name:
- IBindingDisplay.InitializeForProcess
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::InitializeForProcess
helpviewer_keywords:
- IBindingDisplay::InitializeForProcess method [.NET Framework debugging]
- InitializeForProcess method [.NET Framework debugging]
ms.assetid: 59417acb-4e59-46ad-acfe-d827e6ab6078
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aa1e85751f90c34d40e88207af5c7eed2dd1bb82
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61599367"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a>IBindingDisplay::InitializeForProcess — Metoda
Inicjuje [ibindingdisplay —](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pid`  
 [in] Identyfikator procesu.  
  
## <a name="remarks"></a>Uwagi  
 Wywołuje debugera `InitializeForProcess` metody w czasie tworzenia zainicjować wyświetlania powiązania. `InitializeForProcess` musi zostać wywołana w czasie tworzenia przed innej metody w `IBindingDisplay` jest wywoływana.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** BindingDisplay.h  
  
 **Biblioteka:** BindingDisplay.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IBindingDisplay, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)

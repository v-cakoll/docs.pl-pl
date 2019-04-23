---
title: _CorExeMain — Funkcja
ms.date: 03/30/2017
api_name:
- _CorExeMain
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain
helpviewer_keywords:
- _CorExeMain function [.NET Framework hosting]
ms.assetid: 898f76e2-16f4-4a63-b7d9-dad2d3824d8a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7407db297a827004c851b904b2da8652778cb08
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59177492"
---
# <a name="corexemain-function"></a>_CorExeMain — Funkcja
Inicjuje środowisko uruchomieniowe języka wspólnego (CLR), lokalizuje zarządzany punkt wejścia w nagłówku CLR zestawu pliku wykonywalnego i rozpoczyna wykonywanie.  
  
## <a name="syntax"></a>Składnia  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana przez moduł ładujący w procesy utworzone z zarządzanych zestawów pliku wykonywalnego. Dla zestawów DLL wywołuje moduł ładujący [_cordllmain —](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) zamiast tego funkcji.  
  
 Program ładujący systemu operacyjnego wywołuje tę metodę, niezależnie od tego, w punkcie wejścia określonym w pliku obrazu.  
  
 W Windows 98, Windows ME, Windows NT i Windows 2000 `_CorExeMain` funkcja jest wywoływana, pośrednio za pośrednictwem naprawy w moduł ładujący systemu operacyjnego. We wszystkich innych wersjach systemu Windows jest wywoływana bezpośrednio przez program ładujący systemu operacyjnego.  
  
 Aby uzyskać dodatkowe informacje, zobacz sekcję Uwagi w [_corvalidateimage —](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) tematu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Statyczne funkcje globalne metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

---
title: "_CorExeMain — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _CorExeMain
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: _CorExeMain
helpviewer_keywords: _CorExeMain function [.NET Framework hosting]
ms.assetid: 898f76e2-16f4-4a63-b7d9-dad2d3824d8a
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8c341d578a45d72804d9ac33e2aefe513fd33922
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="corexemain-function"></a>_CorExeMain — Funkcja
Inicjuje środowisko uruchomieniowe języka wspólnego (CLR), lokalizuje zarządzany punkt wejścia w nagłówku CLR zestawu pliku wykonywalnego i rozpoczyna się wykonanie.  
  
## <a name="syntax"></a>Składnia  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana przez moduł ładujący w procesy utworzone z zarządzanych zestawów pliku wykonywalnego. Dla zestawów DLL wywołuje moduł ładujący [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) zamiast tego działania.  
  
 Moduł ładujący systemu operacyjnego wywołuje tę metodę, niezależnie od punkt wejścia określony w pliku obrazu.  
  
 W Windows 98, Windows ME, Windows NT i system Windows 2000 `_CorExeMain` funkcja jest wywoływana bezpośrednio za pomocą naprawy w modułu ładującego systemu operacyjnego. We wszystkich innych wersjach systemu Windows jest ona wywoływana bezpośrednio przez moduł ładujący systemu operacyjnego.  
  
 Aby uzyskać dodatkowe informacje, zobacz sekcję uwag w [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) tematu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Statyczne funkcje globalne metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

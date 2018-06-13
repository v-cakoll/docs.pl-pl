---
title: _CorDllMain — Funkcja
ms.date: 03/30/2017
api_name:
- _CorDllMain
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorDllMain
helpviewer_keywords:
- _CorDllMain function [.NET Framework hosting]
ms.assetid: bc7b51cf-39d3-48ec-a5cb-2f179fbefff8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5d541f834e829305fa2b091c45d0dc8f387bb55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431673"
---
# <a name="cordllmain-function"></a>_CorDllMain — Funkcja
Inicjuje środowisko uruchomieniowe języka wspólnego (CLR), lokalizuje zarządzany punkt wejścia w nagłówku CLR zestawu biblioteki DLL i rozpoczęciu wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hInst`  
 [in] Dojście wystąpienia załadować modułu.  
  
 `dwReason`  
 [in] Wskazuje, dlaczego jest wywoływana funkcja punktu wejścia biblioteki DLL. Ten parametr może mieć jedną z następujących wartości: DLL_PROCESS_ATTACH, DLL_THREAD_ATTACH, DLL_THREAD_ATTACH lub komunikat DLL_PROCESS_DETACH. Aby uzyskać opis tych wartości, zobacz `DllMain` dokumentacji zestawu SDK platformy.  
  
 `lpReserved`  
 [in] Nieużywane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca `true` w przypadku powodzenia i `false` w przypadku wystąpienia błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana przez moduł ładujący systemu operacyjnego dla zestawów biblioteki DLL. Dla pliku wykonywalnego zestawów wywołuje moduł ładujący [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) zamiast tego działania.  
  
 Moduł ładujący systemu operacyjnego wywołuje tę metodę, niezależnie od punkt wejścia określony w pliku DLL.  
  
 W Windows 98, Windows ME, Windows NT i system Windows 2000 `_CorDllMain` funkcja jest wywoływana bezpośrednio za pomocą fixupin modułu ładującego systemu operacyjnego. We wszystkich innych wersjach systemu Windows jest ona wywoływana bezpośrednio przez moduł ładujący systemu operacyjnego.  
  
 Aby uzyskać dodatkowe informacje, zobacz sekcję uwag w [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) tematu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Statyczne funkcje globalne metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

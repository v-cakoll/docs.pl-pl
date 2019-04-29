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
ms.openlocfilehash: c509f475d5bf0105ece9791ee3e51d21c298a31f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666930"
---
# <a name="cordllmain-function"></a>\_CorDllMain Function

Inicjuje środowisko uruchomieniowe języka wspólnego (CLR), lokalizuje zarządzany punkt wejścia w nagłówku CLR zestawu biblioteki DLL i rozpoczyna wykonywanie.  
  
## <a name="syntax"></a>Składnia  
  
```  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `hInst`  
 [in] Uchwyt wystąpienia załadowanym module.  
  
 `dwReason`  
 [in] Wskazuje, dlaczego jest wywoływana funkcja punktu wejścia biblioteki DLL. Ten parametr może być jedną z następujących wartości: Biblioteki DLL\_PROCESS_ATTACH, biblioteki DLL\_wątku\_ATTACH, biblioteki DLL\_wątku\_ATTACH lub DLL\_procesu\_ODŁĄCZANIA. Aby uzyskać opis tych wartości, zobacz `DllMain` dokumentacji w zestawie SDK platformy.  
  
 `lpReserved`  
 [in] Nieużywane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca `true` w celu osiągnięcia sukcesu i `false` w przypadku wystąpienia błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana przez program ładujący systemu operacyjnego dla zestawów DLL. Dla pliku wykonywalnego zestawów wywołuje moduł ładujący [ \_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) zamiast tego funkcji.  
  
 Program ładujący systemu operacyjnego wywołuje tę metodę, niezależnie od tego punktu wejścia, określone w pliku DLL.  
  
`_CorDllMain` Funkcja jest wywoływana bezpośrednio przez program ładujący systemu operacyjnego.
  
 Aby uzyskać dodatkowe informacje, zobacz sekcję Uwagi w [ \_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) tematu.  
  
## <a name="requirements"></a>Wymagania  

 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Statyczne funkcje globalne metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

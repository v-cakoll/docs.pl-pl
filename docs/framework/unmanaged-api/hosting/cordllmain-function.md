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
ms.openlocfilehash: f60f159ab4770023cee7123b39109040243e1ccd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136966"
---
# <a name="_cordllmain-function"></a>\_funkcja CorDllMain

Inicjuje środowisko uruchomieniowe języka wspólnego (CLR), lokalizuje zarządzany punkt wejścia w nagłówku CLR zestawu DLL i rozpoczyna wykonywanie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `hInst`  
 podczas Dojście wystąpienia załadowanego modułu.  
  
 `dwReason`  
 podczas Wskazuje, dlaczego funkcja punktu wejścia biblioteki DLL jest wywoływana. Ten parametr może być jedną z następujących wartości: DLL\_PROCESS_ATTACH, DLL\_wątku\_ATTACH, DLL\_wątku\_ATTACH, lub\_proces\_odłączania. Opisy tych wartości można znaleźć w dokumentacji `DllMain` w zestawie SDK platformy.  
  
 `lpReserved`  
 podczas Przestrzeń.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca `true` dla sukcesu i `false` w przypadku wystąpienia błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana przez program ładujący systemu operacyjnego dla zestawów bibliotek DLL. W przypadku zestawów wykonywalnych moduł ładujący wywołuje [\_funkcję CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) .  
  
 Moduł ładujący systemu operacyjnego wywołuje tę metodę niezależnie od punktu wejścia określonego w pliku DLL.  
  
Funkcja `_CorDllMain` jest wywoływana bezpośrednio przez program ładujący systemu operacyjnego.
  
 Aby uzyskać dodatkowe informacje, zobacz sekcję Uwagi w temacie [\_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) .  
  
## <a name="requirements"></a>Wymagania  

 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Statyczne funkcje globalne metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

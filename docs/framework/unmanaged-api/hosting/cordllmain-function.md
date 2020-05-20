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
ms.openlocfilehash: 3b2322f708afed08172f87e843c225aa9c60d9d3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616609"
---
# <a name="_cordllmain-function"></a>\_CorDllMain, funkcja

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
 podczas Wskazuje, dlaczego funkcja punktu wejścia biblioteki DLL jest wywoływana. Ten parametr może mieć jedną z następujących wartości: DLL PROCESS_ATTACH, dołączania do \_ \_ wątku dll \_ , \_ \_ dołączania wątku dll lub \_ \_ odłączania procesu biblioteki DLL. Opisy tych wartości można znaleźć `DllMain` w dokumentacji zestawu Platform SDK.  
  
 `lpReserved`  
 podczas Przestrzeń.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca `true` sukces i w `false` przypadku wystąpienia błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana przez program ładujący systemu operacyjnego dla zestawów bibliotek DLL. W przypadku zestawów wykonywalnych moduł ładujący wywołuje funkcję [ \_ CorExeMain](corexemain-function.md) .  
  
 Moduł ładujący systemu operacyjnego wywołuje tę metodę niezależnie od punktu wejścia określonego w pliku DLL.  
  
`_CorDllMain`Funkcja jest wywoływana bezpośrednio przez program ładujący systemu operacyjnego.
  
 Aby uzyskać dodatkowe informacje, zobacz sekcję Uwagi w temacie [ \_ CorValidateImage](corvalidateimage-function.md) .  
  
## <a name="requirements"></a>Wymagania  

 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Statyczne funkcje globalne metadanych](../metadata/metadata-global-static-functions.md)

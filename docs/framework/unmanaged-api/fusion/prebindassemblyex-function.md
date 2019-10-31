---
title: PreBindAssemblyEx — Funkcja
ms.date: 03/30/2017
api_name:
- PreBindAssemblyEx
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- PreBindAssemblyEx
helpviewer_keywords:
- PreBindAssemblyEx function [.NET Framework fusion]
ms.assetid: bd285233-a4a2-4b52-bbca-0025a60e4864
topic_type:
- apiref
ms.openlocfilehash: db3ba3380d1fc30a8f34683618b5cc326d7d1906
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123058"
---
# <a name="prebindassemblyex-function"></a>PreBindAssemblyEx — Funkcja
Pobiera nazwę wyświetlaną dla zestawu.  
  
 Ta funkcja obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT PreBindAssemblyEx (  
    [in]  IApplicationContext *pAppCtx,  
    [in]  IAssemblyName       *pName,  
    [in]  IAssembly           *pAsmParent,  
    [in]  LPCWSTR             pwzRuntimeVersion,  
    [out] IAssemblyName       **ppNamePostPolicy,  
    [in]  LPVOID              pvReserved  
 );  
```  
  
## <a name="parameters"></a>Parametry  
 `pAppCtx`  
 podczas Identyfikuje kontekst aplikacji.  
  
 `pName`  
 podczas Identyfikuje nazwę zestawu.  
  
 `pAsmParent`  
 podczas Identyfikuje zestaw nadrzędny. Ten parametr jest ignorowany.  
  
 `pwzRuntimeVersion`  
 podczas Identyfikuje wersję środowiska uruchomieniowego.  
  
 `ppNamePostPolicy`  
 określoną Zawiera nazwę wyświetlaną po wprowadzeniu zasad.  
  
 `pvReserved`  
 podczas Zarezerwowane do użytku w przyszłości. `pvReserved` musi być odwołaniem o wartości null.  
  
## <a name="remarks"></a>Uwagi  
 Parametr danych wyjściowych `ppNamePostPolicy` jest ustawiany tylko wtedy, gdy funkcja zwraca wartość HRESULT FUSION_E_REF_DEF_MISMATCH. W przeciwnym razie ma wartość null.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Łączenie statycznych funkcji globalnych](fusion-global-static-functions.md)

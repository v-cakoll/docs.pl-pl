---
title: CreateInstallReferenceEnum — Funkcja
ms.date: 03/30/2017
api_name:
- CreateInstallReferenceEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstallReference
helpviewer_keywords:
- CreateInstallReference function [.NET Framework fusion]
ms.assetid: 80dbbbf8-54fc-4894-b74a-0179d3201083
topic_type:
- apiref
ms.openlocfilehash: f089769f854bad5d3e572e0307734e06e72ca89c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108564"
---
# <a name="createinstallreferenceenum-function"></a>CreateInstallReferenceEnum — Funkcja
Pobiera wskaźnik do wystąpienia [IInstallReferenceEnum](iinstallreferenceenum-interface.md) , które reprezentuje listę odwołań aplikacji do określonego zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
## <a name="parameters"></a>Parametry  
 `ppRefEnum`  
 określoną Zwrócony wskaźnik `IInstallReferenceEnum`.  
  
 `pName`  
 podczas [IAssemblyName](iassemblyname-interface.md) , który identyfikuje zestaw, dla którego mają zostać wyliczone odwołania.  
  
 `dwFlags`  
 podczas Flagi wpływające na zachowanie modułu wyliczającego.  
  
 `pvReserved`  
 podczas Zarezerwowane do użytku w przyszłości. `pvReserved` musi być odwołaniem o wartości null.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion. h  
  
 **Biblioteka:** Fusion. dll i mscorwks. dll. Aby upewnić się, że docelowa wersja .NET Framework, należy użyć pliku Fusion. dll zamiast Mscorwks. dll.  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IInstallReferenceEnum, interfejs](iinstallreferenceenum-interface.md)
- [IAssemblyName, interfejs](iassemblyname-interface.md)
- [Łączenie statycznych funkcji globalnych](fusion-global-static-functions.md)

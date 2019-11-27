---
title: GetALinkMessageDll — Funkcja
ms.date: 03/30/2017
api_name:
- GetALinkMessageDll
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- GetALinkMessageDll
helpviewer_keywords:
- Alink API, GetALinkMessageDll function
- GetALinkMessageDll function
ms.assetid: 67985a22-88a2-4c54-8d99-4bcde9d6213e
topic_type:
- apiref
ms.openlocfilehash: 63719d0c6e13768e9dc7ed80e52e2a293e32a8a1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449345"
---
# <a name="getalinkmessagedll-function"></a>GetALinkMessageDll — Funkcja
Umożliwia znalezienie i załadowanie biblioteki DLL komunikatów. Zwraca wartość 0, jeśli nie można odnaleźć lub załadować biblioteki DLL komunikatu. Biblioteka DLL komunikatów powinna znajdować się w podkatalogu, którego nazwa jest IDENTYFIKATORem języka lub w bieżącym katalogu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** Alink. h  
  
 **Biblioteka**: Alink. dll  
  
## <a name="see-also"></a>Zobacz także

- [Al.exe (konsolidator zestawów)](../../tools/al-exe-assembly-linker.md)

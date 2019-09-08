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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 323e53c45a26d5703548ebe9863978f6d3929f0b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787479"
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

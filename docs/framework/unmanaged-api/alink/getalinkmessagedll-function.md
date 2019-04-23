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
ms.openlocfilehash: edd83e62b08aa7892c01577cd8c46f9d965c0894
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59163023"
---
# <a name="getalinkmessagedll-function"></a>GetALinkMessageDll — Funkcja
Umożliwia znalezienie i ładuje Biblioteka DLL komunikatu. Zwraca wartość 0, jeśli biblioteka DLL komunikatu nie można się lub załadowane. Biblioteka DLL komunikatu powinna być w podkatalogu, której nazwa to identyfikator języka lub w bieżącym katalogu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** alink.h  
  
 **Biblioteka**: alink.dll  
  
## <a name="see-also"></a>Zobacz także

- [Al.exe (konsolidator zestawów)](../../../../docs/framework/tools/al-exe-assembly-linker.md)

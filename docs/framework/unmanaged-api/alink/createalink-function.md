---
title: CreateALink — Funkcja
ms.date: 03/30/2017
api_name:
- CreateALink
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- CreateALink
helpviewer_keywords:
- CreateALink function
- Alink API, CreateALink function
ms.assetid: fc73bcb9-6af6-44d8-bc39-2f4400325dae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 24f7e2d5a547b78ceb4808feaf581c6f49807cf7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787620"
---
# <a name="createalink-function"></a>CreateALink — Funkcja
Tworzy wystąpienie konsolidatora zestawu i ustawia wskaźnik do określonego interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`riid`|Nazwa fizyczna jednego z interfejsów konsolidatora zestawu.|  
|`ppInterface`|Lokalizacja po pomyślnym zakończeniu zawiera wskaźnik do `riid` interfejsu.|  
  
## <a name="requirements"></a>Wymagania  
 **Biblioteka**: Alink. dll  
  
## <a name="see-also"></a>Zobacz także

- [Al.exe (konsolidator zestawów)](../../tools/al-exe-assembly-linker.md)

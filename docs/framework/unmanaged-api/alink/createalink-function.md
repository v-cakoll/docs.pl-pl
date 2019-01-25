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
ms.openlocfilehash: f809395de68b596f769f9396da8668bf296b1aa2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54675044"
---
# <a name="createalink-function"></a>CreateALink — Funkcja
Tworzy wystąpienie programu Assembly Linker i ustawia wskaźnik do określonego interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`riid`|Nazwa fizyczna jednego z interfejsów Assembly Linker.|  
|`ppInterface`|Lokalizację zawierającą od pomyślnego zakończenia wskaźnika do `riid` interfejsu.|  
  
## <a name="requirements"></a>Wymagania  
 **Biblioteka**: alink.dll  
  
## <a name="see-also"></a>Zobacz także
- [Al.exe (konsolidator zestawów)](../../../../docs/framework/tools/al-exe-assembly-linker.md)

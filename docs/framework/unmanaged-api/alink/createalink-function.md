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
ms.openlocfilehash: 993848711f41c9e03b969a3c611982a5c8bc860d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742218"
---
# <a name="createalink-function"></a>CreateALink — Funkcja
Tworzy wystąpienie programu Assembly Linker i ustawia wskaźnik do określonego interfejsu.  
  
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
|`riid`|Nazwa fizyczna jednego z interfejsów Assembly Linker.|  
|`ppInterface`|Lokalizację zawierającą od pomyślnego zakończenia wskaźnika do `riid` interfejsu.|  
  
## <a name="requirements"></a>Wymagania  
 **Biblioteka**: alink.dll  
  
## <a name="see-also"></a>Zobacz także

- [Al.exe (konsolidator zestawów)](../../../../docs/framework/tools/al-exe-assembly-linker.md)

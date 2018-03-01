---
title: "CreateALink — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 54a5afd8ee42fa122f3e18415be0b1d06c2f9302
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="createalink-function"></a>CreateALink — Funkcja
Tworzy wystąpienie Assembly Linker i ustawia wskaźnik do określonego interfejsu.  
  
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
|`ppInterface`|Lokalizacji zawierającej po pomyślnym ukończeniu wskaźnik do `riid` interfejsu.|  
  
## <a name="requirements"></a>Wymagania  
 **Biblioteka**: alink.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Al.exe (konsolidator zestawów)](../../../../docs/framework/tools/al-exe-assembly-linker.md)

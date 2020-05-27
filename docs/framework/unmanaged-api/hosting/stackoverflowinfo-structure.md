---
title: StackOverflowInfo — Struktura
ms.date: 03/30/2017
api_name:
- StackOverflowInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowInfo
helpviewer_keywords:
- StackOverflowInfo structure [.NET Framework hosting]
ms.assetid: 519389f2-0217-436c-99d4-93a76ebce5b5
topic_type:
- apiref
ms.openlocfilehash: 941093b9a0856c2b716ba359c854473f3c9ea26a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006522"
---
# <a name="stackoverflowinfo-structure"></a>StackOverflowInfo — Struktura
Przechowuje typ przepełnienia, który wystąpił, i informacje o wyjątku, który został zgłoszony z powodu przepełnienia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`soType`|Wartość wyliczenia [StackOverflowType —](stackoverflowtype-enumeration.md) , która określa typ przepełnienia.|  
|`pExceptionInfo`|Wskaźnik do `EXCEPTION_POINTERS` obiektu Win32, który zawiera rekord wyjątku z niezależnym od maszyny opisem wyjątku i rekordu kontekstu z opisem zależnym od maszyny w momencie wystąpienia wyjątku.|  
  
## <a name="remarks"></a>Uwagi  
 `StackOverflowInfo`Obiekt jest przesyłany do metody [IActionOnCLREvent:: OnEvent](iactiononclrevent-onevent-method.md) dla `Event_StackOverflow` zdarzeń.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. idl  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Hosting, struktury](hosting-structures.md)

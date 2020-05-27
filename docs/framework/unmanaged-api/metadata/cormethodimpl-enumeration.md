---
title: CorMethodImpl — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorMethodImpl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodImpl
helpviewer_keywords:
- CorMethodImpl enumeration [.NET Framework metadata]
ms.assetid: ffbb3caf-20da-4a4b-8983-77376e72b990
topic_type:
- apiref
ms.openlocfilehash: b32e8f0b03ef6d550c384f3d932cc295a7270028
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007666"
---
# <a name="cormethodimpl-enumeration"></a>CorMethodImpl — Wyliczenie
Zawiera wartości opisujące funkcje implementacji metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum CorMethodImpl {  
  
    miCodeTypeMask      =   0x0003,  
    miIL                =   0x0000,  
    miNative            =   0x0001,  
    miOPTIL             =   0x0002,  
    miRuntime           =   0x0003,  
  
    miManagedMask       =   0x0004,  
    miUnmanaged         =   0x0004,  
    miManaged           =   0x0000,  
  
    miForwardRef        =   0x0010,  
    miPreserveSig       =   0x0080,  
  
    miInternalCall      =   0x1000,  
    miSynchronized      =   0x0020,  
    miNoInlining        =   0x0008,  
    miAggressiveInlining =  0x0100,  
    miNoOptimization     =  0x0040,  
    miMaxMethodImplVal  =   0xffff  
  
} CorMethodImpl;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`miCodeTypeMask`|Flagi opisujące typ kodu.|  
|`miIL`|Określa, że implementacja metody to język pośredni (MSIL) firmy Microsoft.|  
|`miNative`|Określa, że implementacja metody jest natywna.|  
|`miOPTIL`|Określa, że implementacja metody to OPTI.|  
|`miRuntime`|Określa, że implementacja metody jest dostarczana przez środowisko uruchomieniowe języka wspólnego.|  
|`miManagedMask`|Flagi wskazujące, czy kod jest zarządzany lub niezarządzany.|  
|`miUnmanaged`|Określa, że implementacja metody jest niezarządzana.|  
|`miManaged`|Określa, że implementacja metody jest zarządzana.|  
|`miForwardRef`|Określa, że metoda jest zdefiniowana. Ta flaga jest używana głównie w scenariuszach scalania.|  
|`miPreserveSig`|Określa, że podpis metody nie może być zniekształcona dla konwersji HRESULT.|  
|`miInternalCall`|Zarezerwowane do użytku wewnętrznego przez środowisko uruchomieniowe języka wspólnego.|  
|`miSynchronized`|Określa, że metoda jest jednowątkowa za pomocą jej treści.|  
|`miNoInlining`|Określa, że metoda nie może być wbudowana.|  
|`miAggressiveInlining`|Określa, że metoda powinna być przedkreślona, jeśli to możliwe.|  
|`miNoOptimization`|Określa, że metoda nie powinna być zoptymalizowana.|  
|`miMaxMethodImplVal`|Maksymalna prawidłowa wartość elementu `CorMethodImpl` .|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr. h  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Wyliczenia metadanych](metadata-enumerations.md)

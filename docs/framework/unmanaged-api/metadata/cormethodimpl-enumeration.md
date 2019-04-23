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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2138dd32cf39db7b7c8989ba5827178d1a1e46c7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59117238"
---
# <a name="cormethodimpl-enumeration"></a>CorMethodImpl — Wyliczenie
Zawiera wartości, które opisano funkcje implementacji metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`miCodeTypeMask`|Flagi, które opisują typ kodu.|  
|`miIL`|Określa, że implementacja metody języka Microsoft intermediate language (MSIL).|  
|`miNative`|Określa, że implementacja metody natywnej.|  
|`miOPTIL`|Określa, że implementacja metody OPTIL.|  
|`miRuntime`|Określa, że implementacja metody jest świadczona przez środowisko uruchomieniowe języka wspólnego.|  
|`miManagedMask`|Flagi, które wskazują, czy kod jest zarządzany lub niezarządzany.|  
|`miUnmanaged`|Określa, że implementacja metody niezarządzanego.|  
|`miManaged`|Określa, że implementacja metody jest zarządzana.|  
|`miForwardRef`|Określa, że metoda jest zdefiniowana. Ta flaga jest używana głównie w scenariuszach scalania.|  
|`miPreserveSig`|Określa, że podpis metody nie zniekształcone konwersji HRESULT.|  
|`miInternalCall`|Zarezerwowane do użytku wewnętrznego przez środowisko uruchomieniowe języka wspólnego.|  
|`miSynchronized`|Określa, że metoda jest jednowątkowym za pośrednictwem jej treści.|  
|`miNoInlining`|Określa, że metoda nie może być śródwierszowa.|  
|`miAggressiveInlining`|Określa, że metoda powinna być śródwierszowa, jeśli jest to możliwe.|  
|`miNoOptimization`|Określa metody nie powinny być zoptymalizowany.|  
|`miMaxMethodImplVal`|Maksymalna prawidłowa wartość dla `CorMethodImpl`.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

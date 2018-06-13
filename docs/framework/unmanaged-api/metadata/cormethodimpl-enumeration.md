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
ms.openlocfilehash: 4bb91423b2eaeda7d945cf14553609fd33ce9b0c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443492"
---
# <a name="cormethodimpl-enumeration"></a>CorMethodImpl — Wyliczenie
Zawiera wartości, które opisują funkcji w implementacji metody.  
  
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
|`miCodeTypeMask`|Flagi opisujące typ kodu.|  
|`miIL`|Określa, że implementacja metody język pośredni firmy Microsoft (MSIL).|  
|`miNative`|Określa, że implementacja metody natywnej.|  
|`miOPTIL`|Określa, że implementacja metody OPTIL.|  
|`miRuntime`|Określa, że implementacja metody są dostarczane przez środowisko uruchomieniowe języka wspólnego.|  
|`miManagedMask`|Flagi, które wskazują, czy kod jest zarządzane lub niezarządzane.|  
|`miUnmanaged`|Określa, że implementacja metody niezarządzane.|  
|`miManaged`|Określa, że jest zarządzana w implementacji metody.|  
|`miForwardRef`|Określa, że metoda jest zdefiniowana. Ta flaga jest wykorzystywana głównie w przypadku scenariuszy scalania.|  
|`miPreserveSig`|Określa, że podpis metody nie zniekształcone konwersji HRESULT.|  
|`miInternalCall`|Zarezerwowane do użytku wewnętrznego przez środowisko uruchomieniowe języka wspólnego.|  
|`miSynchronized`|Określa, że metoda jest jednowątkowy za pośrednictwem jego treści.|  
|`miNoInlining`|Określa, że metoda nie może być wbudowane.|  
|`miAggressiveInlining`|Określa, że metoda powinna być wbudowane, jeśli to możliwe.|  
|`miNoOptimization`|Określa, że metoda nie może zostać zoptymalizowana.|  
|`miMaxMethodImplVal`|Maksymalna prawidłowa wartość dla `CorMethodImpl`.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

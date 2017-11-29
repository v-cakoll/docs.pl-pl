---
title: "CorMethodImpl — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorMethodImpl
api_location: mscoree.dll
api_type: COM
f1_keywords: CorMethodImpl
helpviewer_keywords: CorMethodImpl enumeration [.NET Framework metadata]
ms.assetid: ffbb3caf-20da-4a4b-8983-77376e72b990
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 85ee55c0d4ec0d3fb8c18dff570afefeb2eaf25e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

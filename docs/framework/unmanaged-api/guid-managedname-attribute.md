---
title: GUID_ManagedName — Atrybut
ms.date: 03/30/2017
api_name:
- GUID_ManagedName
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GUID_ManagedName
helpviewer_keywords:
- GUID_ManagedName attribute
ms.assetid: 11e18095-e444-47bc-aff6-b887ac5dc01e
topic_type:
- apiref
ms.openlocfilehash: 9d30c8fe71a0dfff7de9bb2f43b325cbb8016a23
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123036"
---
# <a name="guid_managedname-attribute"></a>GUID_ManagedName — Atrybut
Definiuje niestandardowy atrybut interfejsu, który określa nazwę zarządzanej przestrzeni nazw dla biblioteki modelu obiektów składnika (COM).  
  
## <a name="syntax"></a>Składnia  
  
```idl
[  
   custom(GUID_ManagedName, value)  
]  
```  
  
## <a name="parameters"></a>Parametry  
 `value`  
 Nazwa zarządzanej przestrzeni nazw dla biblioteki.  
  
## <a name="definition"></a>Definicja  
 `GUID_ManagedName` jest zdefiniowany w cor. h w następujący sposób:  
  
```cpp
// {0F21F359-AB84-41e8-9A78-36D110E6D2F9}  
EXTERN_GUID(GUID_ManagedName, 0xf21f359, 0xab84, 0x41e8, 0x9a, 0x78, 0x36, 0xd1, 0x10, 0xe6, 0xd2, 0xf9);  
```  
  
## <a name="remarks"></a>Uwagi  
 Niestandardowy atrybut interfejsu definiuje metadane dla obiektu w bibliotece typów.  
  
 Użyj <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> lub <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> do pobrania nazwy zarządzanej z atrybutu.  
  
 Aby uzyskać więcej informacji, zobacz [atrybuty interfejsu](/cpp/windows/attributes/interface-attributes) w dokumentacji C++ Visual Reference.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia definicję biblioteki przy użyciu atrybutu `GUID_ManagedName`.  
  
```idl
[  
   ...  
   custom(GUID_ManagedName, Microsoft.VisualStudio.CommandBars.dll")  
]  
library Microsoft_VisualStudio_CommandBars  
{  
   ...  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** Cor. h

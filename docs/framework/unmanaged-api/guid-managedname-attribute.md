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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 48ad6e4d1d03d8362123e65f16907880b18893f9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496394"
---
# <a name="guidmanagedname-attribute"></a>GUID_ManagedName — Atrybut
Określa atrybut niestandardowy interfejs, który określa nazwę przestrzeni nazw zarządzanych bibliotekę składników object model (COM).  
  
## <a name="syntax"></a>Składnia  
  
```  
[  
   custom(GUID_ManagedName, value)  
]  
```  
  
## <a name="parameters"></a>Parametry  
 `value`  
 Nazwa przestrzeni nazw zarządzanych dla biblioteki.  
  
## <a name="definition"></a>Definicja  
 `GUID_ManagedName` zdefiniowano w Cor.h w następujący sposób:  
  
```  
// {0F21F359-AB84-41e8-9A78-36D110E6D2F9}  
EXTERN_GUID(GUID_ManagedName, 0xf21f359, 0xab84, 0x41e8, 0x9a, 0x78, 0x36, 0xd1, 0x10, 0xe6, 0xd2, 0xf9);  
```  
  
## <a name="remarks"></a>Uwagi  
 Atrybut niestandardowy interfejs definiuje metadanych dla obiektu w bibliotece typów.  
  
 Użyj <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> lub <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> pobrać nazwy zarządzanych z atrybutu.  
  
 Aby uzyskać więcej informacji, zobacz [atrybuty interfejsu](/cpp/windows/interface-attributes) dokumentację referencyjną w programie Visual C++.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono definicję biblioteki za pomocą `GUID_ManagedName` atrybutu.  
  
```  
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
 **Nagłówek:** COR.h

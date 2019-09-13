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
ms.openlocfilehash: f14d00f17a61576a50e26d3cbcf734a10ed3c03a
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895016"
---
# <a name="guid_managedname-attribute"></a><span data-ttu-id="14a3a-102">GUID_ManagedName — Atrybut</span><span class="sxs-lookup"><span data-stu-id="14a3a-102">GUID_ManagedName Attribute</span></span>
<span data-ttu-id="14a3a-103">Definiuje niestandardowy atrybut interfejsu, który określa nazwę zarządzanej przestrzeni nazw dla biblioteki modelu obiektów składnika (COM).</span><span class="sxs-lookup"><span data-stu-id="14a3a-103">Defines a custom interface attribute that specifies the managed namespace name for a component object model (COM) library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14a3a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="14a3a-104">Syntax</span></span>  
  
```idl
[  
   custom(GUID_ManagedName, value)  
]  
```  
  
## <a name="parameters"></a><span data-ttu-id="14a3a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="14a3a-105">Parameters</span></span>  
 `value`  
 <span data-ttu-id="14a3a-106">Nazwa zarządzanej przestrzeni nazw dla biblioteki.</span><span class="sxs-lookup"><span data-stu-id="14a3a-106">The managed namespace name for the library.</span></span>  
  
## <a name="definition"></a><span data-ttu-id="14a3a-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="14a3a-107">Definition</span></span>  
 <span data-ttu-id="14a3a-108">`GUID_ManagedName`jest zdefiniowany w cor. h w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="14a3a-108">`GUID_ManagedName` is defined in Cor.h as follows:</span></span>  
  
```cpp
// {0F21F359-AB84-41e8-9A78-36D110E6D2F9}  
EXTERN_GUID(GUID_ManagedName, 0xf21f359, 0xab84, 0x41e8, 0x9a, 0x78, 0x36, 0xd1, 0x10, 0xe6, 0xd2, 0xf9);  
```  
  
## <a name="remarks"></a><span data-ttu-id="14a3a-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="14a3a-109">Remarks</span></span>  
 <span data-ttu-id="14a3a-110">Niestandardowy atrybut interfejsu definiuje metadane dla obiektu w bibliotece typów.</span><span class="sxs-lookup"><span data-stu-id="14a3a-110">A custom interface attribute defines metadata for an object in the type library.</span></span>  
  
 <span data-ttu-id="14a3a-111">Użyj <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> lub<xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> , aby pobrać nazwę zarządzaną z atrybutu.</span><span class="sxs-lookup"><span data-stu-id="14a3a-111">Use <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> or <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> to retrieve the managed name from the attribute.</span></span>  
  
 <span data-ttu-id="14a3a-112">Aby uzyskać więcej informacji, zobacz [atrybuty interfejsu](/cpp/windows/attributes/interface-attributes) w dokumentacji C++ Visual Reference.</span><span class="sxs-lookup"><span data-stu-id="14a3a-112">For more information, see [Interface Attributes](/cpp/windows/attributes/interface-attributes) in the Visual C++ reference documentation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14a3a-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="14a3a-113">Example</span></span>  
 <span data-ttu-id="14a3a-114">Poniższy przykład przedstawia definicję biblioteki przy użyciu `GUID_ManagedName` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="14a3a-114">The following example shows a library definition using the `GUID_ManagedName` attribute.</span></span>  
  
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
  
## <a name="requirements"></a><span data-ttu-id="14a3a-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="14a3a-115">Requirements</span></span>  
 <span data-ttu-id="14a3a-116">**Nagłówki** Cor. h</span><span class="sxs-lookup"><span data-stu-id="14a3a-116">**Header:** Cor.h</span></span>

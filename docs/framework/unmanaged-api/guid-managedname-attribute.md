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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777913"
---
# <a name="guidmanagedname-attribute"></a><span data-ttu-id="ed1a6-102">GUID_ManagedName — Atrybut</span><span class="sxs-lookup"><span data-stu-id="ed1a6-102">GUID_ManagedName Attribute</span></span>
<span data-ttu-id="ed1a6-103">Określa atrybut niestandardowy interfejs, który określa nazwę przestrzeni nazw zarządzanych bibliotekę składników object model (COM).</span><span class="sxs-lookup"><span data-stu-id="ed1a6-103">Defines a custom interface attribute that specifies the managed namespace name for a component object model (COM) library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed1a6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ed1a6-104">Syntax</span></span>  
  
```  
[  
   custom(GUID_ManagedName, value)  
]  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed1a6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ed1a6-105">Parameters</span></span>  
 `value`  
 <span data-ttu-id="ed1a6-106">Nazwa przestrzeni nazw zarządzanych dla biblioteki.</span><span class="sxs-lookup"><span data-stu-id="ed1a6-106">The managed namespace name for the library.</span></span>  
  
## <a name="definition"></a><span data-ttu-id="ed1a6-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="ed1a6-107">Definition</span></span>  
 <span data-ttu-id="ed1a6-108">`GUID_ManagedName` zdefiniowano w Cor.h w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ed1a6-108">`GUID_ManagedName` is defined in Cor.h as follows:</span></span>  
  
```  
// {0F21F359-AB84-41e8-9A78-36D110E6D2F9}  
EXTERN_GUID(GUID_ManagedName, 0xf21f359, 0xab84, 0x41e8, 0x9a, 0x78, 0x36, 0xd1, 0x10, 0xe6, 0xd2, 0xf9);  
```  
  
## <a name="remarks"></a><span data-ttu-id="ed1a6-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ed1a6-109">Remarks</span></span>  
 <span data-ttu-id="ed1a6-110">Atrybut niestandardowy interfejs definiuje metadanych dla obiektu w bibliotece typów.</span><span class="sxs-lookup"><span data-stu-id="ed1a6-110">A custom interface attribute defines metadata for an object in the type library.</span></span>  
  
 <span data-ttu-id="ed1a6-111">Użyj <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> lub <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> pobrać nazwy zarządzanych z atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ed1a6-111">Use <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> or <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> to retrieve the managed name from the attribute.</span></span>  
  
 <span data-ttu-id="ed1a6-112">Aby uzyskać więcej informacji, zobacz [atrybuty interfejsu](/cpp/windows/interface-attributes) dokumentację referencyjną w programie Visual C++.</span><span class="sxs-lookup"><span data-stu-id="ed1a6-112">For more information, see [Interface Attributes](/cpp/windows/interface-attributes) in the Visual C++ reference documentation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed1a6-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="ed1a6-113">Example</span></span>  
 <span data-ttu-id="ed1a6-114">W poniższym przykładzie przedstawiono definicję biblioteki za pomocą `GUID_ManagedName` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ed1a6-114">The following example shows a library definition using the `GUID_ManagedName` attribute.</span></span>  
  
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
  
## <a name="requirements"></a><span data-ttu-id="ed1a6-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ed1a6-115">Requirements</span></span>  
 <span data-ttu-id="ed1a6-116">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="ed1a6-116">**Header:** Cor.h</span></span>

---
title: "CorNativeLinkType — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorNativeLinkType
api_location: mscoree.dll
api_type: COM
f1_keywords: CorNativeLinkType
helpviewer_keywords: CorNativeLinkType enumeration [.NET Framework metadata]
ms.assetid: 4f86ff37-2dab-4e64-819a-76b3bfe828ff
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b8da034590bc5e0b2cbd9456d9d5b4ef4970f259
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="a94ca-102">CorNativeLinkType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a94ca-102">CorNativeLinkType Enumeration</span></span>
<span data-ttu-id="a94ca-103">Zawiera wartości, które wskazują na typ połączone w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="a94ca-103">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a94ca-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a94ca-104">Syntax</span></span>  
  
```  
typedef enum   
{  
    nltNone       = 1,  
    nltAnsi       = 2,  
    nltUnicode    = 3,  
    nltAuto       = 4,  
    nltOle        = 5,  
    nltMaxValue   = 7  
} CorNativeLinkType;  
```  
  
## <a name="members"></a><span data-ttu-id="a94ca-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a94ca-105">Members</span></span>  
  
|<span data-ttu-id="a94ca-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a94ca-106">Member</span></span>|<span data-ttu-id="a94ca-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a94ca-107">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="a94ca-108">Wskazuje, że słowa kluczowe są nieokreślone.</span><span class="sxs-lookup"><span data-stu-id="a94ca-108">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="a94ca-109">Wskazuje, że zostanie określone słowo kluczowe ANSI.</span><span class="sxs-lookup"><span data-stu-id="a94ca-109">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="a94ca-110">Wskazuje, że określono Unicode — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="a94ca-110">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="a94ca-111">Wskazuje, że określono auto — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="a94ca-111">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="a94ca-112">Wskazuje, że zostanie określone słowo kluczowe OLE.</span><span class="sxs-lookup"><span data-stu-id="a94ca-112">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="a94ca-113">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="a94ca-113">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a94ca-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a94ca-114">Requirements</span></span>  
 <span data-ttu-id="a94ca-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a94ca-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a94ca-116">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a94ca-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a94ca-117">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a94ca-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a94ca-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a94ca-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a94ca-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a94ca-119">See Also</span></span>  
 [<span data-ttu-id="a94ca-120">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="a94ca-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

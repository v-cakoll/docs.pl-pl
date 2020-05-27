---
title: CorNativeLinkType — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorNativeLinkType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkType
helpviewer_keywords:
- CorNativeLinkType enumeration [.NET Framework metadata]
ms.assetid: 4f86ff37-2dab-4e64-819a-76b3bfe828ff
topic_type:
- apiref
ms.openlocfilehash: 29f2401e2e3faccae05ca5249fcd7d9e89aacb46
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007614"
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="3779e-102">CorNativeLinkType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="3779e-102">CorNativeLinkType Enumeration</span></span>
<span data-ttu-id="3779e-103">Dostarcza wartości, które wskazują typ połączony w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="3779e-103">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3779e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3779e-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="3779e-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="3779e-105">Members</span></span>  
  
|<span data-ttu-id="3779e-106">Członek</span><span class="sxs-lookup"><span data-stu-id="3779e-106">Member</span></span>|<span data-ttu-id="3779e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3779e-107">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="3779e-108">Wskazuje, że nie określono żadnego ze słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="3779e-108">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="3779e-109">Wskazuje, że jest określone słowo kluczowe ANSI.</span><span class="sxs-lookup"><span data-stu-id="3779e-109">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="3779e-110">Wskazuje, że określono słowo kluczowe Unicode</span><span class="sxs-lookup"><span data-stu-id="3779e-110">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="3779e-111">Wskazuje, że jest określone słowo kluczowe New.</span><span class="sxs-lookup"><span data-stu-id="3779e-111">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="3779e-112">Wskazuje, że określono słowo kluczowe OLE.</span><span class="sxs-lookup"><span data-stu-id="3779e-112">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="3779e-113">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="3779e-113">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3779e-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3779e-114">Requirements</span></span>  
 <span data-ttu-id="3779e-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3779e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3779e-116">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3779e-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3779e-117">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3779e-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3779e-118">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3779e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3779e-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3779e-119">See also</span></span>

- [<span data-ttu-id="3779e-120">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="3779e-120">Metadata Enumerations</span></span>](metadata-enumerations.md)

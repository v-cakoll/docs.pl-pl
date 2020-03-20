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
ms.openlocfilehash: 0b613ebacdff82a29fdbc3f4caa0f2b8bb5d3f6a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176165"
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="fccfa-102">CorNativeLinkType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fccfa-102">CorNativeLinkType Enumeration</span></span>
<span data-ttu-id="fccfa-103">Zawiera wartości wskazujące typ połączony w kodzie macierzystym.</span><span class="sxs-lookup"><span data-stu-id="fccfa-103">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fccfa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fccfa-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="fccfa-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="fccfa-105">Members</span></span>  
  
|<span data-ttu-id="fccfa-106">Członek</span><span class="sxs-lookup"><span data-stu-id="fccfa-106">Member</span></span>|<span data-ttu-id="fccfa-107">Opis</span><span class="sxs-lookup"><span data-stu-id="fccfa-107">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="fccfa-108">Wskazuje, że żadne ze słów kluczowych nie są określone.</span><span class="sxs-lookup"><span data-stu-id="fccfa-108">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="fccfa-109">Wskazuje, że określono słowo kluczowe ANSI.</span><span class="sxs-lookup"><span data-stu-id="fccfa-109">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="fccfa-110">Wskazuje, że określono słowo kluczowe Unicode</span><span class="sxs-lookup"><span data-stu-id="fccfa-110">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="fccfa-111">Wskazuje, że określono automatyczne słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="fccfa-111">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="fccfa-112">Wskazuje, że określono słowo kluczowe OLE.</span><span class="sxs-lookup"><span data-stu-id="fccfa-112">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="fccfa-113">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="fccfa-113">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fccfa-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fccfa-114">Requirements</span></span>  
 <span data-ttu-id="fccfa-115">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fccfa-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fccfa-116">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="fccfa-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fccfa-117">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fccfa-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fccfa-118">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fccfa-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fccfa-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fccfa-119">See also</span></span>

- [<span data-ttu-id="fccfa-120">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="fccfa-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

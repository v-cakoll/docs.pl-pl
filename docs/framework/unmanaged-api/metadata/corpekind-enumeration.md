---
title: CorPEKind — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPEKind
helpviewer_keywords:
- CorPEKind enumeration [.NET Framework metadata]
ms.assetid: 22dc6dea-b1b9-4982-a730-a022d586b117
topic_type:
- apiref
ms.openlocfilehash: 8b6eab8156f72847eb6dd3369950f9b46a3fc877
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007562"
---
# <a name="corpekind-enumeration"></a><span data-ttu-id="3f3f7-102">CorPEKind — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="3f3f7-102">CorPEKind Enumeration</span></span>
<span data-ttu-id="3f3f7-103">Zawiera wartości opisujące przenośny plik wykonywalny (PE), który jest zwracany przez wywołanie [IMetaDataImport2:: GetPEKind —](imetadataimport2-getpekind-method.md).</span><span class="sxs-lookup"><span data-stu-id="3f3f7-103">Contains values that describe a portable executable (PE) file, as returned from a call to [IMetaDataImport2::GetPEKind](imetadataimport2-getpekind-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f3f7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3f3f7-104">Syntax</span></span>  
  
```cpp  
typedef enum CorPEKind {  
  
    peNot           = 0x00000000,  
    peILonly        = 0x00000001,  
    pe32BitRequired = 0x00000002,  
    pe32Plus        = 0x00000004,  
    pe32Unmanaged   = 0x00000008,  
    pe32BitPreferred= 0x00000010  
  
} CorPEKind;  
```  
  
## <a name="members"></a><span data-ttu-id="3f3f7-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="3f3f7-105">Members</span></span>  
  
|<span data-ttu-id="3f3f7-106">Członek</span><span class="sxs-lookup"><span data-stu-id="3f3f7-106">Member</span></span>|<span data-ttu-id="3f3f7-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3f3f7-107">Description</span></span>|  
|------------|-----------------|  
|`peNot`|<span data-ttu-id="3f3f7-108">Wskazuje, że nie jest to plik PE.</span><span class="sxs-lookup"><span data-stu-id="3f3f7-108">Indicates that this is not a PE file.</span></span>|  
|`peILOnly`|<span data-ttu-id="3f3f7-109">Wskazuje, że ten plik PE zawiera tylko kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="3f3f7-109">Indicates that this PE file contains only managed code.</span></span>|  
|`pe32BitRequired`|<span data-ttu-id="3f3f7-110">Wskazuje, że ten plik PE wykonuje wywołania Win32.</span><span class="sxs-lookup"><span data-stu-id="3f3f7-110">Indicates that this PE file makes Win32 calls.</span></span>|  
|`pe32Plus`|<span data-ttu-id="3f3f7-111">Wskazuje, że ten plik PE działa na platformie 64-bitowej.</span><span class="sxs-lookup"><span data-stu-id="3f3f7-111">Indicates that this PE file runs on a 64-bit platform.</span></span>|  
|`pe32Unmanaged`|<span data-ttu-id="3f3f7-112">Wskazuje, że ten plik PE jest kodem natywnym.</span><span class="sxs-lookup"><span data-stu-id="3f3f7-112">Indicates that this PE file is native code.</span></span>|  
|<span data-ttu-id="3f3f7-113">pe32BitPreferred</span><span class="sxs-lookup"><span data-stu-id="3f3f7-113">pe32BitPreferred</span></span>|<span data-ttu-id="3f3f7-114">Wskazuje, że ten plik PE jest niezależny od platformy i preferowany do załadowania w środowisku 32-bitowym.</span><span class="sxs-lookup"><span data-stu-id="3f3f7-114">Indicates that this PE file is platform-neutral and prefers to be loaded in a 32-bit environment.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f3f7-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3f3f7-115">Remarks</span></span>  
 <span data-ttu-id="3f3f7-116">Te wartości mogą być używane w kombinacjach bitowych.</span><span class="sxs-lookup"><span data-stu-id="3f3f7-116">These values can be used in bitwise combinations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f3f7-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3f3f7-117">Requirements</span></span>  
 <span data-ttu-id="3f3f7-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f3f7-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f3f7-119">**Nagłówek:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="3f3f7-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="3f3f7-120">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f3f7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f3f7-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3f3f7-121">See also</span></span>

- [<span data-ttu-id="3f3f7-122">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="3f3f7-122">Metadata Enumerations</span></span>](metadata-enumerations.md)

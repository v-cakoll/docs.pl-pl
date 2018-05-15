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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b5869eb16bd768d58a6f27a83f2d8d51914a8aed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="corpekind-enumeration"></a><span data-ttu-id="f7add-102">CorPEKind — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="f7add-102">CorPEKind Enumeration</span></span>
<span data-ttu-id="f7add-103">Zawiera wartości, które opisują pliku przenośny plik wykonywalny (PE), ponieważ zwracany po wywołaniu [IMetaDataImport2::GetPEKind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md).</span><span class="sxs-lookup"><span data-stu-id="f7add-103">Contains values that describe a portable executable (PE) file, as returned from a call to [IMetaDataImport2::GetPEKind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7add-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f7add-104">Syntax</span></span>  
  
```  
typedef enum CorPEKind {  
  
    peNot           = 0x00000000,  
    peILonly        = 0x00000001,  
    pe32BitRequired = 0x00000002,  
    pe32Plus        = 0x00000004,  
    pe32Unmanaged   = 0x00000008,  
    pe32BitPreferred= 0x00000010  
  
} CorPEKind;  
```  
  
## <a name="members"></a><span data-ttu-id="f7add-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="f7add-105">Members</span></span>  
  
|<span data-ttu-id="f7add-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="f7add-106">Member</span></span>|<span data-ttu-id="f7add-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f7add-107">Description</span></span>|  
|------------|-----------------|  
|`peNot`|<span data-ttu-id="f7add-108">Wskazuje, że nie jest plikiem PE.</span><span class="sxs-lookup"><span data-stu-id="f7add-108">Indicates that this is not a PE file.</span></span>|  
|`peILOnly`|<span data-ttu-id="f7add-109">Wskazuje, czy ten plik PE zawiera tylko kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="f7add-109">Indicates that this PE file contains only managed code.</span></span>|  
|`pe32BitRequired`|<span data-ttu-id="f7add-110">Wskazuje, czy ten plik PE wywołań Win32.</span><span class="sxs-lookup"><span data-stu-id="f7add-110">Indicates that this PE file makes Win32 calls.</span></span>|  
|`pe32Plus`|<span data-ttu-id="f7add-111">Wskazuje, czy ten plik PE jest uruchamiana na 64-bitowej platformy.</span><span class="sxs-lookup"><span data-stu-id="f7add-111">Indicates that this PE file runs on a 64-bit platform.</span></span>|  
|`pe32Unmanaged`|<span data-ttu-id="f7add-112">Wskazuje, że ten plik PE jest kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="f7add-112">Indicates that this PE file is native code.</span></span>|  
|<span data-ttu-id="f7add-113">pe32BitPreferred</span><span class="sxs-lookup"><span data-stu-id="f7add-113">pe32BitPreferred</span></span>|<span data-ttu-id="f7add-114">Wskazuje, czy ten plik PE jest niezależny od platformy i preferuje do załadowania w środowisku 32-bitowym.</span><span class="sxs-lookup"><span data-stu-id="f7add-114">Indicates that this PE file is platform-neutral and prefers to be loaded in a 32-bit environment.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7add-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f7add-115">Remarks</span></span>  
 <span data-ttu-id="f7add-116">Można używać tych wartości bitowe kombinacji.</span><span class="sxs-lookup"><span data-stu-id="f7add-116">These values can be used in bitwise combinations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7add-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f7add-117">Requirements</span></span>  
 <span data-ttu-id="f7add-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7add-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7add-119">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="f7add-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="f7add-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7add-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7add-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f7add-121">See Also</span></span>  
 [<span data-ttu-id="f7add-122">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="f7add-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

---
title: "CorPEKind — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorPEKind
api_location: mscoree.dll
api_type: COM
f1_keywords: CorPEKind
helpviewer_keywords: CorPEKind enumeration [.NET Framework metadata]
ms.assetid: 22dc6dea-b1b9-4982-a730-a022d586b117
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 06e28a7e926d888c7c9274900ba90ac990fbb0e5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="corpekind-enumeration"></a><span data-ttu-id="d7332-102">CorPEKind — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="d7332-102">CorPEKind Enumeration</span></span>
<span data-ttu-id="d7332-103">Zawiera wartości, które opisują pliku przenośny plik wykonywalny (PE), ponieważ zwracany po wywołaniu [IMetaDataImport2::GetPEKind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md).</span><span class="sxs-lookup"><span data-stu-id="d7332-103">Contains values that describe a portable executable (PE) file, as returned from a call to [IMetaDataImport2::GetPEKind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7332-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d7332-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="d7332-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d7332-105">Members</span></span>  
  
|<span data-ttu-id="d7332-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="d7332-106">Member</span></span>|<span data-ttu-id="d7332-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d7332-107">Description</span></span>|  
|------------|-----------------|  
|`peNot`|<span data-ttu-id="d7332-108">Wskazuje, że nie jest plikiem PE.</span><span class="sxs-lookup"><span data-stu-id="d7332-108">Indicates that this is not a PE file.</span></span>|  
|`peILOnly`|<span data-ttu-id="d7332-109">Wskazuje, czy ten plik PE zawiera tylko kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="d7332-109">Indicates that this PE file contains only managed code.</span></span>|  
|`pe32BitRequired`|<span data-ttu-id="d7332-110">Wskazuje, czy ten plik PE wywołań Win32.</span><span class="sxs-lookup"><span data-stu-id="d7332-110">Indicates that this PE file makes Win32 calls.</span></span>|  
|`pe32Plus`|<span data-ttu-id="d7332-111">Wskazuje, czy ten plik PE jest uruchamiana na 64-bitowej platformy.</span><span class="sxs-lookup"><span data-stu-id="d7332-111">Indicates that this PE file runs on a 64-bit platform.</span></span>|  
|`pe32Unmanaged`|<span data-ttu-id="d7332-112">Wskazuje, że ten plik PE jest kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="d7332-112">Indicates that this PE file is native code.</span></span>|  
|<span data-ttu-id="d7332-113">pe32BitPreferred</span><span class="sxs-lookup"><span data-stu-id="d7332-113">pe32BitPreferred</span></span>|<span data-ttu-id="d7332-114">Wskazuje, czy ten plik PE jest niezależny od platformy i preferuje do załadowania w środowisku 32-bitowym.</span><span class="sxs-lookup"><span data-stu-id="d7332-114">Indicates that this PE file is platform-neutral and prefers to be loaded in a 32-bit environment.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7332-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d7332-115">Remarks</span></span>  
 <span data-ttu-id="d7332-116">Można używać tych wartości bitowe kombinacji.</span><span class="sxs-lookup"><span data-stu-id="d7332-116">These values can be used in bitwise combinations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7332-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d7332-117">Requirements</span></span>  
 <span data-ttu-id="d7332-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7332-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7332-119">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="d7332-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d7332-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7332-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7332-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d7332-121">See Also</span></span>  
 [<span data-ttu-id="d7332-122">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="d7332-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

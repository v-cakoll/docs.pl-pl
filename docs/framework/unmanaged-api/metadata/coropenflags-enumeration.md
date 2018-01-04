---
title: "CorOpenFlags — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorOpenFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: CorOpenFlags
helpviewer_keywords: CorOpenFlags enumeration [.NET Framework metadata]
ms.assetid: e27a83b5-2698-4996-9032-1e0fed8b91ca
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 39645de71913baeaa39524e1cae081de9cac3442
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="coropenflags-enumeration"></a><span data-ttu-id="89ecd-102">CorOpenFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="89ecd-102">CorOpenFlags Enumeration</span></span>
<span data-ttu-id="89ecd-103">Zawiera wartości flag, które kontrolują zachowanie metadanych podczas otwierania plików manifestu.</span><span class="sxs-lookup"><span data-stu-id="89ecd-103">Contains flag values that control metadata behavior upon opening manifest files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89ecd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="89ecd-104">Syntax</span></span>  
  
```  
typedef enum CorOpenFlags  
{  
    ofRead              =   0x00000000,  
    ofWrite             =   0x00000001,  
    ofReadWriteMask     =   0x00000001,  
    ofCopyMemory        =   0x00000002,  
    ofCacheImage        =   0x00000004,  
    ofManifestMetadata  =   0x00000008,  
    ofReadOnly          =   0x00000010,  
    ofTakeOwnership     =   0x00000020,  
    ofCacheImage        =   0x00000004,  
    ofNoTypeLib         =   0x00000080,  
    ofNoTransform       =   0x00001000,  
    ofReserved1         =   0x00000100,  
    ofReserved2         =   0x00000200,  
    ofReserved          =   0xffffff40  
} CorOpenFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="89ecd-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="89ecd-105">Members</span></span>  
  
|<span data-ttu-id="89ecd-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="89ecd-106">Member</span></span>|<span data-ttu-id="89ecd-107">Opis</span><span class="sxs-lookup"><span data-stu-id="89ecd-107">Description</span></span>|  
|------------|-----------------|  
|`ofRead`|<span data-ttu-id="89ecd-108">Wskazuje, że plik powinien zostać otwarty tylko odczyt.</span><span class="sxs-lookup"><span data-stu-id="89ecd-108">Indicates that the file should be opened for reading only.</span></span>|  
|`ofWrite`|<span data-ttu-id="89ecd-109">Wskazuje, że plik powinien zostać otwarty do zapisu.</span><span class="sxs-lookup"><span data-stu-id="89ecd-109">Indicates that the file should be opened for writing.</span></span><br /><br /> <span data-ttu-id="89ecd-110">Jeśli używasz `ofWrite` Flaga podczas otwierania pliku winmd, należy również przekazać `ofNoTransform` flagi.</span><span class="sxs-lookup"><span data-stu-id="89ecd-110">If you are using the `ofWrite` flag when opening a .winmd file, you should also pass the `ofNoTransform` flag.</span></span>|  
|`ofReadWriteMask`|<span data-ttu-id="89ecd-111">Maska do odczytu i zapisu.</span><span class="sxs-lookup"><span data-stu-id="89ecd-111">A mask for reading and writing.</span></span>|  
|`ofCopyMemory`|<span data-ttu-id="89ecd-112">Wskazuje, że można odczytać pliku do pamięci.</span><span class="sxs-lookup"><span data-stu-id="89ecd-112">Indicates that the file should be read into memory.</span></span> <span data-ttu-id="89ecd-113">Metadane należy korzystać z własnej kopii.</span><span class="sxs-lookup"><span data-stu-id="89ecd-113">Metadata should maintain its own copy.</span></span>|  
|`ofCacheImage`|<span data-ttu-id="89ecd-114">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="89ecd-114">Obsolete.</span></span> <span data-ttu-id="89ecd-115">Ta flaga jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="89ecd-115">This flag is ignored.</span></span>|  
|`ofManifestMetadata`|<span data-ttu-id="89ecd-116">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="89ecd-116">Obsolete.</span></span> <span data-ttu-id="89ecd-117">Ta flaga jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="89ecd-117">This flag is ignored.</span></span>|  
|`ofReadOnly`|<span data-ttu-id="89ecd-118">Wskazuje, że plik powinien zostać otwarty do odczytu i że wywołanie `QueryInterface` dla [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) nie można dokonać korekty.</span><span class="sxs-lookup"><span data-stu-id="89ecd-118">Indicates that the file should be opened for reading, and that a call to `QueryInterface` for an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) cannot be made.</span></span>|  
|`ofTakeOwnership`|<span data-ttu-id="89ecd-119">Wskazuje, że pamięć został przydzielony przy użyciu wywołania [CoTaskMemAlloc](http://msdn.microsoft.com/en-us/c4cb588d-9482-4f90-a92e-75b604540d5c) i zostanie zwolniona w metadanych.</span><span class="sxs-lookup"><span data-stu-id="89ecd-119">Indicates that the memory was allocated using a call to [CoTaskMemAlloc](http://msdn.microsoft.com/en-us/c4cb588d-9482-4f90-a92e-75b604540d5c) and will be freed by the metadata.</span></span>|  
|`ofNoTypeLib`|<span data-ttu-id="89ecd-120">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="89ecd-120">Obsolete.</span></span> <span data-ttu-id="89ecd-121">Ta flaga jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="89ecd-121">This flag is ignored.</span></span>|  
|`ofNoTransform`|<span data-ttu-id="89ecd-122">Wskazuje, należy wyłączyć automatyczne transformacje plików winmd.</span><span class="sxs-lookup"><span data-stu-id="89ecd-122">Indicates that automatic transforms of .winmd files should be disabled.</span></span> <span data-ttu-id="89ecd-123">Innymi słowy można wyłączyć projekcji typu środowiska wykonawczego systemu Windows, aby typ .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="89ecd-123">In other words, the projection of a Windows Runtime type to a .NET Framework type should be disabled.</span></span> <span data-ttu-id="89ecd-124">Aby uzyskać więcej informacji, zobacz [Underneath maską .NET i środowiska wykonawczego systemu Windows](http://msdn.microsoft.com/magazine/jj651569.aspx).</span><span class="sxs-lookup"><span data-stu-id="89ecd-124">For more information, see [Underneath the Hood with .NET and the Windows Runtime](http://msdn.microsoft.com/magazine/jj651569.aspx).</span></span>|  
|`ofReserved1`|<span data-ttu-id="89ecd-125">Zarezerwowany do użytku wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="89ecd-125">Reserved for internal use.</span></span>|  
|`ofReserved2`|<span data-ttu-id="89ecd-126">Zarezerwowany do użytku wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="89ecd-126">Reserved for internal use.</span></span>|  
|`ofReserved`|<span data-ttu-id="89ecd-127">Zarezerwowany do użytku wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="89ecd-127">Reserved for internal use.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="89ecd-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="89ecd-128">Requirements</span></span>  
 <span data-ttu-id="89ecd-129">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89ecd-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89ecd-130">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="89ecd-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="89ecd-131">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89ecd-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89ecd-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="89ecd-132">See Also</span></span>  
 [<span data-ttu-id="89ecd-133">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="89ecd-133">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

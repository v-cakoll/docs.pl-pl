---
title: CorOpenFlags — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorOpenFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorOpenFlags
helpviewer_keywords:
- CorOpenFlags enumeration [.NET Framework metadata]
ms.assetid: e27a83b5-2698-4996-9032-1e0fed8b91ca
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c08b1f6be41de63886115e5aed6bcad901658bb5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509223"
---
# <a name="coropenflags-enumeration"></a><span data-ttu-id="aba29-102">CorOpenFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="aba29-102">CorOpenFlags Enumeration</span></span>
<span data-ttu-id="aba29-103">Zawiera wartości flagi, które kontrolują zachowanie metadanych podczas otwierania plików manifestu.</span><span class="sxs-lookup"><span data-stu-id="aba29-103">Contains flag values that control metadata behavior upon opening manifest files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aba29-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aba29-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="aba29-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="aba29-105">Members</span></span>  
  
|<span data-ttu-id="aba29-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="aba29-106">Member</span></span>|<span data-ttu-id="aba29-107">Opis</span><span class="sxs-lookup"><span data-stu-id="aba29-107">Description</span></span>|  
|------------|-----------------|  
|`ofRead`|<span data-ttu-id="aba29-108">Wskazuje, czy można otworzyć pliku do odczytu tylko.</span><span class="sxs-lookup"><span data-stu-id="aba29-108">Indicates that the file should be opened for reading only.</span></span>|  
|`ofWrite`|<span data-ttu-id="aba29-109">Wskazuje, że plik powinien zostać otwarty do zapisu.</span><span class="sxs-lookup"><span data-stu-id="aba29-109">Indicates that the file should be opened for writing.</span></span><br /><br /> <span data-ttu-id="aba29-110">Jeśli używasz `ofWrite` Flaga podczas otwierania pliku winmd, należy także przekazać `ofNoTransform` flagi.</span><span class="sxs-lookup"><span data-stu-id="aba29-110">If you are using the `ofWrite` flag when opening a .winmd file, you should also pass the `ofNoTransform` flag.</span></span>|  
|`ofReadWriteMask`|<span data-ttu-id="aba29-111">Maska do odczytu i zapisu.</span><span class="sxs-lookup"><span data-stu-id="aba29-111">A mask for reading and writing.</span></span>|  
|`ofCopyMemory`|<span data-ttu-id="aba29-112">Wskazuje, że można odczytać pliku do pamięci.</span><span class="sxs-lookup"><span data-stu-id="aba29-112">Indicates that the file should be read into memory.</span></span> <span data-ttu-id="aba29-113">Metadane należy zachować własną kopię.</span><span class="sxs-lookup"><span data-stu-id="aba29-113">Metadata should maintain its own copy.</span></span>|  
|`ofCacheImage`|<span data-ttu-id="aba29-114">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="aba29-114">Obsolete.</span></span> <span data-ttu-id="aba29-115">Ta flaga jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="aba29-115">This flag is ignored.</span></span>|  
|`ofManifestMetadata`|<span data-ttu-id="aba29-116">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="aba29-116">Obsolete.</span></span> <span data-ttu-id="aba29-117">Ta flaga jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="aba29-117">This flag is ignored.</span></span>|  
|`ofReadOnly`|<span data-ttu-id="aba29-118">Wskazuje, że dla odczytu, które można otworzyć pliku wywołanie `QueryInterface` dla [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) nie może zostać wykonana.</span><span class="sxs-lookup"><span data-stu-id="aba29-118">Indicates that the file should be opened for reading, and that a call to `QueryInterface` for an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) cannot be made.</span></span>|  
|`ofTakeOwnership`|<span data-ttu-id="aba29-119">Wskazuje, że pamięć została przydzielona za pomocą wywołania [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) i zostanie zwolniona w metadanych.</span><span class="sxs-lookup"><span data-stu-id="aba29-119">Indicates that the memory was allocated using a call to [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) and will be freed by the metadata.</span></span>|  
|`ofNoTypeLib`|<span data-ttu-id="aba29-120">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="aba29-120">Obsolete.</span></span> <span data-ttu-id="aba29-121">Ta flaga jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="aba29-121">This flag is ignored.</span></span>|  
|`ofNoTransform`|<span data-ttu-id="aba29-122">Wskazuje, należy wyłączyć automatyczne transformacje plików winmd.</span><span class="sxs-lookup"><span data-stu-id="aba29-122">Indicates that automatic transforms of .winmd files should be disabled.</span></span> <span data-ttu-id="aba29-123">Innymi słowy należy wyłączyć projekcji typu środowiska wykonawczego Windows, aby typ .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aba29-123">In other words, the projection of a Windows Runtime type to a .NET Framework type should be disabled.</span></span> <span data-ttu-id="aba29-124">Aby uzyskać więcej informacji, zobacz [poniżej składniki przy użyciu platformy .NET i środowiska wykonawczego Windows](https://msdn.microsoft.com/magazine/jj651569.aspx).</span><span class="sxs-lookup"><span data-stu-id="aba29-124">For more information, see [Underneath the Hood with .NET and the Windows Runtime](https://msdn.microsoft.com/magazine/jj651569.aspx).</span></span>|  
|`ofReserved1`|<span data-ttu-id="aba29-125">Zarezerwowane do użytku wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="aba29-125">Reserved for internal use.</span></span>|  
|`ofReserved2`|<span data-ttu-id="aba29-126">Zarezerwowane do użytku wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="aba29-126">Reserved for internal use.</span></span>|  
|`ofReserved`|<span data-ttu-id="aba29-127">Zarezerwowane do użytku wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="aba29-127">Reserved for internal use.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aba29-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aba29-128">Requirements</span></span>  
 <span data-ttu-id="aba29-129">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aba29-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aba29-130">**Nagłówek:** sekcję CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="aba29-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="aba29-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aba29-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aba29-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aba29-132">See Also</span></span>  
 [<span data-ttu-id="aba29-133">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="aba29-133">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

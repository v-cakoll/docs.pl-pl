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
ms.openlocfilehash: ad582fc2fd1bd1d2fc9d5a0d483fdb3a51309a10
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436506"
---
# <a name="coropenflags-enumeration"></a><span data-ttu-id="69558-102">CorOpenFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="69558-102">CorOpenFlags Enumeration</span></span>
<span data-ttu-id="69558-103">Zawiera wartości flag kontrolujące zachowanie metadanych podczas otwierania plików manifestu.</span><span class="sxs-lookup"><span data-stu-id="69558-103">Contains flag values that control metadata behavior upon opening manifest files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69558-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="69558-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="69558-105">Members</span><span class="sxs-lookup"><span data-stu-id="69558-105">Members</span></span>  
  
|<span data-ttu-id="69558-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="69558-106">Member</span></span>|<span data-ttu-id="69558-107">Opis</span><span class="sxs-lookup"><span data-stu-id="69558-107">Description</span></span>|  
|------------|-----------------|  
|`ofRead`|<span data-ttu-id="69558-108">Wskazuje, że plik powinien być otwarty tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="69558-108">Indicates that the file should be opened for reading only.</span></span>|  
|`ofWrite`|<span data-ttu-id="69558-109">Wskazuje, że plik powinien być otwarty do zapisu.</span><span class="sxs-lookup"><span data-stu-id="69558-109">Indicates that the file should be opened for writing.</span></span><br /><br /> <span data-ttu-id="69558-110">Jeśli używasz flagi `ofWrite` podczas otwierania pliku winmd, należy również przekazać flagę `ofNoTransform`.</span><span class="sxs-lookup"><span data-stu-id="69558-110">If you are using the `ofWrite` flag when opening a .winmd file, you should also pass the `ofNoTransform` flag.</span></span>|  
|`ofReadWriteMask`|<span data-ttu-id="69558-111">Maska do odczytu i zapisu.</span><span class="sxs-lookup"><span data-stu-id="69558-111">A mask for reading and writing.</span></span>|  
|`ofCopyMemory`|<span data-ttu-id="69558-112">Wskazuje, że plik powinien być odczytywany do pamięci.</span><span class="sxs-lookup"><span data-stu-id="69558-112">Indicates that the file should be read into memory.</span></span> <span data-ttu-id="69558-113">Metadane powinny zachować własną kopię.</span><span class="sxs-lookup"><span data-stu-id="69558-113">Metadata should maintain its own copy.</span></span>|  
|`ofCacheImage`|<span data-ttu-id="69558-114">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="69558-114">Obsolete.</span></span> <span data-ttu-id="69558-115">Ta flaga jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="69558-115">This flag is ignored.</span></span>|  
|`ofManifestMetadata`|<span data-ttu-id="69558-116">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="69558-116">Obsolete.</span></span> <span data-ttu-id="69558-117">Ta flaga jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="69558-117">This flag is ignored.</span></span>|  
|`ofReadOnly`|<span data-ttu-id="69558-118">Wskazuje, że plik powinien być otwarty do odczytu i że nie można wykonać wywołania `QueryInterface` dla [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="69558-118">Indicates that the file should be opened for reading, and that a call to `QueryInterface` for an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) cannot be made.</span></span>|  
|`ofTakeOwnership`|<span data-ttu-id="69558-119">Wskazuje, że pamięć została przypisana przy użyciu wywołania do [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) i zostanie zwolniona z metadanych.</span><span class="sxs-lookup"><span data-stu-id="69558-119">Indicates that the memory was allocated using a call to [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) and will be freed by the metadata.</span></span>|  
|`ofNoTypeLib`|<span data-ttu-id="69558-120">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="69558-120">Obsolete.</span></span> <span data-ttu-id="69558-121">Ta flaga jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="69558-121">This flag is ignored.</span></span>|  
|`ofNoTransform`|<span data-ttu-id="69558-122">Wskazuje, że należy wyłączyć automatyczne transformacje plików WinMD.</span><span class="sxs-lookup"><span data-stu-id="69558-122">Indicates that automatic transforms of .winmd files should be disabled.</span></span> <span data-ttu-id="69558-123">Innymi słowy, projekcja typu środowisko wykonawcze systemu Windows do typu .NET Framework powinna być wyłączona.</span><span class="sxs-lookup"><span data-stu-id="69558-123">In other words, the projection of a Windows Runtime type to a .NET Framework type should be disabled.</span></span> <span data-ttu-id="69558-124">Aby uzyskać więcej informacji, zobacz [środowisko wykonawcze systemu Windows i środowisko CLR poniżej wystawcy z platformą .NET i środowisko wykonawcze systemu Windows](https://docs.microsoft.com/archive/msdn-magazine/2012/windows-8-special-issue/windows-runtime-and-the-clr-underneath-the-hood-with-net-and-the-windows-runtime).</span><span class="sxs-lookup"><span data-stu-id="69558-124">For more information, see [Windows Runtime and the CLR - Underneath the Hood with .NET and the Windows Runtime](https://docs.microsoft.com/archive/msdn-magazine/2012/windows-8-special-issue/windows-runtime-and-the-clr-underneath-the-hood-with-net-and-the-windows-runtime).</span></span>|  
|`ofReserved1`|<span data-ttu-id="69558-125">Przeznaczone do użytku wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="69558-125">Reserved for internal use.</span></span>|  
|`ofReserved2`|<span data-ttu-id="69558-126">Przeznaczone do użytku wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="69558-126">Reserved for internal use.</span></span>|  
|`ofReserved`|<span data-ttu-id="69558-127">Przeznaczone do użytku wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="69558-127">Reserved for internal use.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="69558-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="69558-128">Requirements</span></span>  
 <span data-ttu-id="69558-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69558-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69558-130">**Nagłówek:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="69558-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="69558-131">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69558-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69558-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="69558-132">See also</span></span>

- [<span data-ttu-id="69558-133">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="69558-133">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

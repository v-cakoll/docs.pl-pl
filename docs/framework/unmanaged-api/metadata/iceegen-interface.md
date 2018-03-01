---
title: "ICeeGen — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICeeGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen
helpviewer_keywords:
- ICeeGen interface [.NET Framework metadata]
ms.assetid: 383d20b0-efe9-4e71-8fb8-1186b2e7d0c0
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 73af58ac55fd22e5b4f19f715cb0b1a137a640a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iceegen-interface"></a><span data-ttu-id="12bc2-102">ICeeGen — Interfejs</span><span class="sxs-lookup"><span data-stu-id="12bc2-102">ICeeGen Interface</span></span>
<span data-ttu-id="12bc2-103">Udostępnia metody dla kompilacji dynamicznej kodu.</span><span class="sxs-lookup"><span data-stu-id="12bc2-103">Provides methods for dynamic code compilation.</span></span>  
  
 <span data-ttu-id="12bc2-104">Ten interfejs jest przestarzały i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="12bc2-104">This interface is obsolete and should not be used.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="12bc2-105">Metody</span><span class="sxs-lookup"><span data-stu-id="12bc2-105">Methods</span></span>  
  
|<span data-ttu-id="12bc2-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="12bc2-106">Method</span></span>|<span data-ttu-id="12bc2-107">Opis</span><span class="sxs-lookup"><span data-stu-id="12bc2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="12bc2-108">AddSectionReloc, metoda</span><span class="sxs-lookup"><span data-stu-id="12bc2-108">AddSectionReloc Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)|<span data-ttu-id="12bc2-109">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="12bc2-109">Obsolete.</span></span> <span data-ttu-id="12bc2-110">Dodaje instrukcję .reloc do ścieżki bazowej kodu.</span><span class="sxs-lookup"><span data-stu-id="12bc2-110">Adds a .reloc instruction to the code base.</span></span>|  
|[<span data-ttu-id="12bc2-111">AllocateMethodBuffer, metoda</span><span class="sxs-lookup"><span data-stu-id="12bc2-111">AllocateMethodBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-allocatemethodbuffer-method.md)|<span data-ttu-id="12bc2-112">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="12bc2-112">Obsolete.</span></span> <span data-ttu-id="12bc2-113">Tworzy buforu o określonym rozmiarze metody i pobiera adres względny wirtualnej metody.</span><span class="sxs-lookup"><span data-stu-id="12bc2-113">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>|  
|[<span data-ttu-id="12bc2-114">ComputePointer, metoda</span><span class="sxs-lookup"><span data-stu-id="12bc2-114">ComputePointer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-computepointer-method.md)|<span data-ttu-id="12bc2-115">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="12bc2-115">Obsolete.</span></span> <span data-ttu-id="12bc2-116">Określa bufor dla określonego kodu sekcji.</span><span class="sxs-lookup"><span data-stu-id="12bc2-116">Determines the buffer for the specified code section.</span></span>|  
|[<span data-ttu-id="12bc2-117">EmitString, metoda</span><span class="sxs-lookup"><span data-stu-id="12bc2-117">EmitString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-emitstring-method.md)|<span data-ttu-id="12bc2-118">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="12bc2-118">Obsolete.</span></span> <span data-ttu-id="12bc2-119">Emituje określonego ciągu w bazie kodu.</span><span class="sxs-lookup"><span data-stu-id="12bc2-119">Emits the specified string into the code base.</span></span>|  
|[<span data-ttu-id="12bc2-120">GenerateCeeFile, metoda</span><span class="sxs-lookup"><span data-stu-id="12bc2-120">GenerateCeeFile Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceefile-method.md)|<span data-ttu-id="12bc2-121">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="12bc2-121">Obsolete.</span></span> <span data-ttu-id="12bc2-122">Generuje plik bazowej kodu, który zawiera kod podstawowy załadowanych obecnie do tego `ICeeGen`.</span><span class="sxs-lookup"><span data-stu-id="12bc2-122">Generates a code-base file that contains the code base currently loaded into this `ICeeGen`.</span></span>|  
|[<span data-ttu-id="12bc2-123">GenerateCeeMemoryImage, metoda</span><span class="sxs-lookup"><span data-stu-id="12bc2-123">GenerateCeeMemoryImage Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceememoryimage-method.md)|<span data-ttu-id="12bc2-124">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="12bc2-124">Obsolete.</span></span> <span data-ttu-id="12bc2-125">Generuje obrazu w pamięci dla ścieżki bazowej kodu.</span><span class="sxs-lookup"><span data-stu-id="12bc2-125">Generates an image in memory for the code base.</span></span>|  
|[<span data-ttu-id="12bc2-126">GetIlSection, metoda</span><span class="sxs-lookup"><span data-stu-id="12bc2-126">GetIlSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getilsection-method.md)|<span data-ttu-id="12bc2-127">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="12bc2-127">Obsolete.</span></span> <span data-ttu-id="12bc2-128">Pobiera część bazy kodu języka pośredniego odwołuje się określony uchwyt.</span><span class="sxs-lookup"><span data-stu-id="12bc2-128">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>|  
|[<span data-ttu-id="12bc2-129">GetIMapTokenIface, metoda</span><span class="sxs-lookup"><span data-stu-id="12bc2-129">GetIMapTokenIface Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getimaptokeniface-method.md)|<span data-ttu-id="12bc2-130">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="12bc2-130">Obsolete.</span></span> <span data-ttu-id="12bc2-131">Pobiera interfejs odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="12bc2-131">Gets the interface referenced by the specified token.</span></span>|  
|[<span data-ttu-id="12bc2-132">GetMethodBuffer, metoda</span><span class="sxs-lookup"><span data-stu-id="12bc2-132">GetMethodBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getmethodbuffer-method.md)|<span data-ttu-id="12bc2-133">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="12bc2-133">Obsolete.</span></span> <span data-ttu-id="12bc2-134">Pobiera odpowiedni rozmiar buforu dla metody pod określonym adresem wirtualnego względną.</span><span class="sxs-lookup"><span data-stu-id="12bc2-134">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>|  
|[<span data-ttu-id="12bc2-135">GetSectionBlock, metoda</span><span class="sxs-lookup"><span data-stu-id="12bc2-135">GetSectionBlock Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectionblock-method.md)|<span data-ttu-id="12bc2-136">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="12bc2-136">Obsolete.</span></span> <span data-ttu-id="12bc2-137">Pobiera blok sekcji ścieżki bazowej kodu.</span><span class="sxs-lookup"><span data-stu-id="12bc2-137">Gets a section block of the code base.</span></span>|  
|[<span data-ttu-id="12bc2-138">GetSectionCreate, metoda</span><span class="sxs-lookup"><span data-stu-id="12bc2-138">GetSectionCreate Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectioncreate-method.md)|<span data-ttu-id="12bc2-139">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="12bc2-139">Obsolete.</span></span> <span data-ttu-id="12bc2-140">Generuje i pobiera sekcji kodu przy użyciu określonej nazwy i wartości flag.</span><span class="sxs-lookup"><span data-stu-id="12bc2-140">Generates and gets a code section using the specified name and flag values.</span></span>|  
|[<span data-ttu-id="12bc2-141">GetSectionDataLen, metoda</span><span class="sxs-lookup"><span data-stu-id="12bc2-141">GetSectionDataLen Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectiondatalen-method.md)|<span data-ttu-id="12bc2-142">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="12bc2-142">Obsolete.</span></span> <span data-ttu-id="12bc2-143">Pobiera długość określonej sekcji.</span><span class="sxs-lookup"><span data-stu-id="12bc2-143">Gets the length of the specified section.</span></span>|  
|[<span data-ttu-id="12bc2-144">GetString, metoda</span><span class="sxs-lookup"><span data-stu-id="12bc2-144">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstring-method.md)|<span data-ttu-id="12bc2-145">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="12bc2-145">Obsolete.</span></span> <span data-ttu-id="12bc2-146">Pobiera ciąg przechowywanych na określony wirtualny adres względny.</span><span class="sxs-lookup"><span data-stu-id="12bc2-146">Gets the string stored at the specified relative virtual address.</span></span>|  
|[<span data-ttu-id="12bc2-147">GetStringSection, metoda</span><span class="sxs-lookup"><span data-stu-id="12bc2-147">GetStringSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstringsection-method.md)|<span data-ttu-id="12bc2-148">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="12bc2-148">Obsolete.</span></span> <span data-ttu-id="12bc2-149">Pobiera reprezentację ciągu sekcji kod odwołuje się określony uchwyt.</span><span class="sxs-lookup"><span data-stu-id="12bc2-149">Gets a string representation of the code section referenced by the specified handle.</span></span>|  
|[<span data-ttu-id="12bc2-150">TruncateSection, metoda</span><span class="sxs-lookup"><span data-stu-id="12bc2-150">TruncateSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-truncatesection-method.md)|<span data-ttu-id="12bc2-151">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="12bc2-151">Obsolete.</span></span> <span data-ttu-id="12bc2-152">Obcina sekcji określonego kodu przez określony czas.</span><span class="sxs-lookup"><span data-stu-id="12bc2-152">Truncates the specified code section by the specified length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="12bc2-153">Wymagania</span><span class="sxs-lookup"><span data-stu-id="12bc2-153">Requirements</span></span>  
 <span data-ttu-id="12bc2-154">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12bc2-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12bc2-155">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="12bc2-155">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="12bc2-156">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="12bc2-156">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="12bc2-157">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12bc2-157">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12bc2-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="12bc2-158">See Also</span></span>  
 [<span data-ttu-id="12bc2-159">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="12bc2-159">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)

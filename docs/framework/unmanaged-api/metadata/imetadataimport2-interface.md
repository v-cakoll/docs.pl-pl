---
title: "IMetaDataImport2 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2
helpviewer_keywords: IMetaDataImport2 interface [.NET Framework metadata]
ms.assetid: d39b2b87-ba53-4771-ae53-952a68452511
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1b00879f1d22d49e5f0dc3bdb072e0545feda68d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2-interface"></a><span data-ttu-id="49661-102">IMetaDataImport2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="49661-102">IMetaDataImport2 Interface</span></span>
<span data-ttu-id="49661-103">Rozszerza [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interfejsu możliwości pracy z typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="49661-103">Extends the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface to provide the capability of working with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="49661-104">Metody</span><span class="sxs-lookup"><span data-stu-id="49661-104">Methods</span></span>  
  
|<span data-ttu-id="49661-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="49661-105">Method</span></span>|<span data-ttu-id="49661-106">Opis</span><span class="sxs-lookup"><span data-stu-id="49661-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="49661-107">EnumGenericParamConstraints — metoda</span><span class="sxs-lookup"><span data-stu-id="49661-107">EnumGenericParamConstraints Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparamconstraints-method.md)|<span data-ttu-id="49661-108">Pobiera moduł wyliczający dla tablicy ograniczenia parametru ogólnego skojarzone z parametru ogólnego reprezentowany przez określony token.</span><span class="sxs-lookup"><span data-stu-id="49661-108">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="49661-109">EnumGenericParams — metoda</span><span class="sxs-lookup"><span data-stu-id="49661-109">EnumGenericParams Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)|<span data-ttu-id="49661-110">Pobiera moduł wyliczający dla tablicy parametrów ogólnych tokenów skojarzone z określonym TypeDef lub MethodDef token.</span><span class="sxs-lookup"><span data-stu-id="49661-110">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>|  
|[<span data-ttu-id="49661-111">EnumMethodSpecs — metoda</span><span class="sxs-lookup"><span data-stu-id="49661-111">EnumMethodSpecs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enummethodspecs-method.md)|<span data-ttu-id="49661-112">Pobiera moduł wyliczający dla tablicy tokenów MethodSpec skojarzone z określonym MethodDef lub MemberRef token.</span><span class="sxs-lookup"><span data-stu-id="49661-112">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>|  
|[<span data-ttu-id="49661-113">GetGenericParamConstraintProps — metoda</span><span class="sxs-lookup"><span data-stu-id="49661-113">GetGenericParamConstraintProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamconstraintprops-method.md)|<span data-ttu-id="49661-114">Pobiera metadane skojarzone z ograniczenia parametru ogólnego reprezentowany przez ograniczenie określony token.</span><span class="sxs-lookup"><span data-stu-id="49661-114">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>|  
|[<span data-ttu-id="49661-115">GetGenericParamProps — metoda</span><span class="sxs-lookup"><span data-stu-id="49661-115">GetGenericParamProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamprops-method.md)|<span data-ttu-id="49661-116">Pobiera metadane skojarzone z parametru ogólnego reprezentowany przez określony token.</span><span class="sxs-lookup"><span data-stu-id="49661-116">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="49661-117">GetMethodSpecProps — metoda</span><span class="sxs-lookup"><span data-stu-id="49661-117">GetMethodSpecProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getmethodspecprops-method.md)|<span data-ttu-id="49661-118">Pobiera token podpisu metadanych metody odwołuje się określony element MethodSpec.</span><span class="sxs-lookup"><span data-stu-id="49661-118">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>|  
|[<span data-ttu-id="49661-119">GetPEKind — metoda</span><span class="sxs-lookup"><span data-stu-id="49661-119">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)|<span data-ttu-id="49661-120">Pobiera wartość identyfikujący rodzaj kod przenośny plik wykonywalny (PE) pliku, zwykle plik DLL ani EXE, zdefiniowany w bieżącym zakresie metadanych</span><span class="sxs-lookup"><span data-stu-id="49661-120">Gets a value identifying the nature of the code in a portable executable (PE) file, typically a DLL or EXE file, defined in the current metadata scope</span></span>|  
|[<span data-ttu-id="49661-121">GetVersionString — metoda</span><span class="sxs-lookup"><span data-stu-id="49661-121">GetVersionString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getversionstring-method.md)|<span data-ttu-id="49661-122">Pobiera numer wersji środowiska uruchomieniowego, który został użyty do budowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="49661-122">Gets the version number of the runtime that was used to build the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="49661-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="49661-123">Requirements</span></span>  
 <span data-ttu-id="49661-124">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49661-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49661-125">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="49661-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="49661-126">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="49661-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="49661-127">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49661-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49661-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="49661-128">See Also</span></span>  
 <xref:System.Reflection.PortableExecutableKinds>  
 [<span data-ttu-id="49661-129">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="49661-129">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="49661-130">IMetaDataImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="49661-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)

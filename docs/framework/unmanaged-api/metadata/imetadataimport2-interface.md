---
title: IMetaDataImport2 — Interfejs
ms.date: 03/30/2017
api_name:
- IMetaDataImport2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2
helpviewer_keywords:
- IMetaDataImport2 interface [.NET Framework metadata]
ms.assetid: d39b2b87-ba53-4771-ae53-952a68452511
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6717c48fca14f2200f783a984594388ef3b29c15
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211936"
---
# <a name="imetadataimport2-interface"></a><span data-ttu-id="82214-102">IMetaDataImport2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="82214-102">IMetaDataImport2 Interface</span></span>
<span data-ttu-id="82214-103">Rozszerza [imetadataimport —](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interfejsu, aby zapewnić możliwość pracy z typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="82214-103">Extends the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface to provide the capability of working with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="82214-104">Metody</span><span class="sxs-lookup"><span data-stu-id="82214-104">Methods</span></span>  
  
|<span data-ttu-id="82214-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="82214-105">Method</span></span>|<span data-ttu-id="82214-106">Opis</span><span class="sxs-lookup"><span data-stu-id="82214-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="82214-107">EnumGenericParamConstraints, metoda</span><span class="sxs-lookup"><span data-stu-id="82214-107">EnumGenericParamConstraints Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparamconstraints-method.md)|<span data-ttu-id="82214-108">Pobiera moduł wyliczający dla tablicy ograniczenia parametru ogólnego skojarzone z parametru ogólnego, reprezentowane przez określony token.</span><span class="sxs-lookup"><span data-stu-id="82214-108">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="82214-109">EnumGenericParams, metoda</span><span class="sxs-lookup"><span data-stu-id="82214-109">EnumGenericParams Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)|<span data-ttu-id="82214-110">Pobiera moduł wyliczający dla tablic, tokeny parametrów ogólnych skojarzone z określonego typu lub MethodDef token.</span><span class="sxs-lookup"><span data-stu-id="82214-110">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>|  
|[<span data-ttu-id="82214-111">EnumMethodSpecs, metoda</span><span class="sxs-lookup"><span data-stu-id="82214-111">EnumMethodSpecs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enummethodspecs-method.md)|<span data-ttu-id="82214-112">Pobiera moduł wyliczający dla tablicy tokenów MethodSpec skojarzone z określonym MethodDef lub MemberRef tokenu.</span><span class="sxs-lookup"><span data-stu-id="82214-112">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>|  
|[<span data-ttu-id="82214-113">GetGenericParamConstraintProps, metoda</span><span class="sxs-lookup"><span data-stu-id="82214-113">GetGenericParamConstraintProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamconstraintprops-method.md)|<span data-ttu-id="82214-114">Pobiera metadane skojarzone z ograniczenia parametru ogólnego, reprezentowane przez ograniczenie określonego tokenu.</span><span class="sxs-lookup"><span data-stu-id="82214-114">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>|  
|[<span data-ttu-id="82214-115">GetGenericParamProps, metoda</span><span class="sxs-lookup"><span data-stu-id="82214-115">GetGenericParamProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamprops-method.md)|<span data-ttu-id="82214-116">Pobiera metadane skojarzone z parametru ogólnego, reprezentowane przez określony token.</span><span class="sxs-lookup"><span data-stu-id="82214-116">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="82214-117">GetMethodSpecProps, metoda</span><span class="sxs-lookup"><span data-stu-id="82214-117">GetMethodSpecProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getmethodspecprops-method.md)|<span data-ttu-id="82214-118">Sygnatura metadanych metody odwołuje się określona MethodSpec pobiera token.</span><span class="sxs-lookup"><span data-stu-id="82214-118">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>|  
|[<span data-ttu-id="82214-119">GetPEKind, metoda</span><span class="sxs-lookup"><span data-stu-id="82214-119">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)|<span data-ttu-id="82214-120">Pobiera wartość identyfikujący rodzaj kodu w przenośnym pliku wykonywalnym (PE) pliku, zazwyczaj pliku DLL lub EXE, zdefiniowana w bieżącym zakresie metadanych</span><span class="sxs-lookup"><span data-stu-id="82214-120">Gets a value identifying the nature of the code in a portable executable (PE) file, typically a DLL or EXE file, defined in the current metadata scope</span></span>|  
|[<span data-ttu-id="82214-121">GetVersionString, metoda</span><span class="sxs-lookup"><span data-stu-id="82214-121">GetVersionString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getversionstring-method.md)|<span data-ttu-id="82214-122">Pobiera numer wersji środowiska uruchomieniowego, który został użyty do tworzenia zestawu.</span><span class="sxs-lookup"><span data-stu-id="82214-122">Gets the version number of the runtime that was used to build the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="82214-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="82214-123">Requirements</span></span>  
 <span data-ttu-id="82214-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82214-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82214-125">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="82214-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="82214-126">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="82214-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="82214-127">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="82214-127">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="82214-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="82214-128">See also</span></span>

- <xref:System.Reflection.PortableExecutableKinds>
- [<span data-ttu-id="82214-129">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="82214-129">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="82214-130">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="82214-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)

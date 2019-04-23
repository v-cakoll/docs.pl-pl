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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59211936"
---
# <a name="imetadataimport2-interface"></a><span data-ttu-id="020e9-102">IMetaDataImport2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="020e9-102">IMetaDataImport2 Interface</span></span>
<span data-ttu-id="020e9-103">Rozszerza [imetadataimport —](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interfejsu, aby zapewnić możliwość pracy z typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="020e9-103">Extends the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface to provide the capability of working with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="020e9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="020e9-104">Methods</span></span>  
  
|<span data-ttu-id="020e9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="020e9-105">Method</span></span>|<span data-ttu-id="020e9-106">Opis</span><span class="sxs-lookup"><span data-stu-id="020e9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="020e9-107">EnumGenericParamConstraints, metoda</span><span class="sxs-lookup"><span data-stu-id="020e9-107">EnumGenericParamConstraints Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparamconstraints-method.md)|<span data-ttu-id="020e9-108">Pobiera moduł wyliczający dla tablicy ograniczenia parametru ogólnego skojarzone z parametru ogólnego, reprezentowane przez określony token.</span><span class="sxs-lookup"><span data-stu-id="020e9-108">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="020e9-109">EnumGenericParams, metoda</span><span class="sxs-lookup"><span data-stu-id="020e9-109">EnumGenericParams Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)|<span data-ttu-id="020e9-110">Pobiera moduł wyliczający dla tablic, tokeny parametrów ogólnych skojarzone z określonego typu lub MethodDef token.</span><span class="sxs-lookup"><span data-stu-id="020e9-110">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>|  
|[<span data-ttu-id="020e9-111">EnumMethodSpecs, metoda</span><span class="sxs-lookup"><span data-stu-id="020e9-111">EnumMethodSpecs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enummethodspecs-method.md)|<span data-ttu-id="020e9-112">Pobiera moduł wyliczający dla tablicy tokenów MethodSpec skojarzone z określonym MethodDef lub MemberRef tokenu.</span><span class="sxs-lookup"><span data-stu-id="020e9-112">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>|  
|[<span data-ttu-id="020e9-113">GetGenericParamConstraintProps, metoda</span><span class="sxs-lookup"><span data-stu-id="020e9-113">GetGenericParamConstraintProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamconstraintprops-method.md)|<span data-ttu-id="020e9-114">Pobiera metadane skojarzone z ograniczenia parametru ogólnego, reprezentowane przez ograniczenie określonego tokenu.</span><span class="sxs-lookup"><span data-stu-id="020e9-114">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>|  
|[<span data-ttu-id="020e9-115">GetGenericParamProps, metoda</span><span class="sxs-lookup"><span data-stu-id="020e9-115">GetGenericParamProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamprops-method.md)|<span data-ttu-id="020e9-116">Pobiera metadane skojarzone z parametru ogólnego, reprezentowane przez określony token.</span><span class="sxs-lookup"><span data-stu-id="020e9-116">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="020e9-117">GetMethodSpecProps, metoda</span><span class="sxs-lookup"><span data-stu-id="020e9-117">GetMethodSpecProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getmethodspecprops-method.md)|<span data-ttu-id="020e9-118">Sygnatura metadanych metody odwołuje się określona MethodSpec pobiera token.</span><span class="sxs-lookup"><span data-stu-id="020e9-118">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>|  
|[<span data-ttu-id="020e9-119">GetPEKind, metoda</span><span class="sxs-lookup"><span data-stu-id="020e9-119">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)|<span data-ttu-id="020e9-120">Pobiera wartość identyfikujący rodzaj kodu w przenośnym pliku wykonywalnym (PE) pliku, zazwyczaj pliku DLL lub EXE, zdefiniowana w bieżącym zakresie metadanych</span><span class="sxs-lookup"><span data-stu-id="020e9-120">Gets a value identifying the nature of the code in a portable executable (PE) file, typically a DLL or EXE file, defined in the current metadata scope</span></span>|  
|[<span data-ttu-id="020e9-121">GetVersionString, metoda</span><span class="sxs-lookup"><span data-stu-id="020e9-121">GetVersionString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getversionstring-method.md)|<span data-ttu-id="020e9-122">Pobiera numer wersji środowiska uruchomieniowego, który został użyty do tworzenia zestawu.</span><span class="sxs-lookup"><span data-stu-id="020e9-122">Gets the version number of the runtime that was used to build the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="020e9-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="020e9-123">Requirements</span></span>  
 <span data-ttu-id="020e9-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="020e9-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="020e9-125">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="020e9-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="020e9-126">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="020e9-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="020e9-127">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="020e9-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="020e9-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="020e9-128">See also</span></span>

- <xref:System.Reflection.PortableExecutableKinds>
- [<span data-ttu-id="020e9-129">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="020e9-129">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="020e9-130">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="020e9-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)

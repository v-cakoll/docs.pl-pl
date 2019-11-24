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
ms.openlocfilehash: 0fd7915ef46899bdce8312bc6e8a466167e26382
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429212"
---
# <a name="imetadataimport2-interface"></a><span data-ttu-id="2b12f-102">IMetaDataImport2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2b12f-102">IMetaDataImport2 Interface</span></span>
<span data-ttu-id="2b12f-103">Extends the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface to provide the capability of working with generic types.</span><span class="sxs-lookup"><span data-stu-id="2b12f-103">Extends the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface to provide the capability of working with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2b12f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2b12f-104">Methods</span></span>  
  
|<span data-ttu-id="2b12f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2b12f-105">Method</span></span>|<span data-ttu-id="2b12f-106">Opis</span><span class="sxs-lookup"><span data-stu-id="2b12f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2b12f-107">EnumGenericParamConstraints, metoda</span><span class="sxs-lookup"><span data-stu-id="2b12f-107">EnumGenericParamConstraints Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparamconstraints-method.md)|<span data-ttu-id="2b12f-108">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span><span class="sxs-lookup"><span data-stu-id="2b12f-108">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="2b12f-109">EnumGenericParams, metoda</span><span class="sxs-lookup"><span data-stu-id="2b12f-109">EnumGenericParams Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)|<span data-ttu-id="2b12f-110">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span><span class="sxs-lookup"><span data-stu-id="2b12f-110">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>|  
|[<span data-ttu-id="2b12f-111">EnumMethodSpecs, metoda</span><span class="sxs-lookup"><span data-stu-id="2b12f-111">EnumMethodSpecs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enummethodspecs-method.md)|<span data-ttu-id="2b12f-112">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span><span class="sxs-lookup"><span data-stu-id="2b12f-112">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>|  
|[<span data-ttu-id="2b12f-113">GetGenericParamConstraintProps, metoda</span><span class="sxs-lookup"><span data-stu-id="2b12f-113">GetGenericParamConstraintProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamconstraintprops-method.md)|<span data-ttu-id="2b12f-114">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span><span class="sxs-lookup"><span data-stu-id="2b12f-114">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>|  
|[<span data-ttu-id="2b12f-115">GetGenericParamProps, metoda</span><span class="sxs-lookup"><span data-stu-id="2b12f-115">GetGenericParamProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamprops-method.md)|<span data-ttu-id="2b12f-116">Gets the metadata associated with the generic parameter represented by the specified token.</span><span class="sxs-lookup"><span data-stu-id="2b12f-116">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="2b12f-117">GetMethodSpecProps, metoda</span><span class="sxs-lookup"><span data-stu-id="2b12f-117">GetMethodSpecProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getmethodspecprops-method.md)|<span data-ttu-id="2b12f-118">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span><span class="sxs-lookup"><span data-stu-id="2b12f-118">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>|  
|[<span data-ttu-id="2b12f-119">GetPEKind, metoda</span><span class="sxs-lookup"><span data-stu-id="2b12f-119">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)|<span data-ttu-id="2b12f-120">Gets a value identifying the nature of the code in a portable executable (PE) file, typically a DLL or EXE file, defined in the current metadata scope</span><span class="sxs-lookup"><span data-stu-id="2b12f-120">Gets a value identifying the nature of the code in a portable executable (PE) file, typically a DLL or EXE file, defined in the current metadata scope</span></span>|  
|[<span data-ttu-id="2b12f-121">GetVersionString, metoda</span><span class="sxs-lookup"><span data-stu-id="2b12f-121">GetVersionString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getversionstring-method.md)|<span data-ttu-id="2b12f-122">Gets the version number of the runtime that was used to build the assembly.</span><span class="sxs-lookup"><span data-stu-id="2b12f-122">Gets the version number of the runtime that was used to build the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2b12f-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2b12f-123">Requirements</span></span>  
 <span data-ttu-id="2b12f-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b12f-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b12f-125">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2b12f-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2b12f-126">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2b12f-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2b12f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b12f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b12f-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2b12f-128">See also</span></span>

- <xref:System.Reflection.PortableExecutableKinds>
- [<span data-ttu-id="2b12f-129">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="2b12f-129">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="2b12f-130">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="2b12f-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)

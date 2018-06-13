---
title: CorNativeType — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorNativeType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeType
helpviewer_keywords:
- CorNativeType enumeration [.NET Framework metadata]
ms.assetid: e47a72f1-9609-48ed-bb34-97170d7f6890
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b28fe8e8fd8b602a01b6358f46f60cdf792ced0d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448628"
---
# <a name="cornativetype-enumeration"></a><span data-ttu-id="8fe87-102">CorNativeType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8fe87-102">CorNativeType Enumeration</span></span>
<span data-ttu-id="8fe87-103">Zawiera wartości, które opisują typy natywne niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="8fe87-103">Contains values that describe native unmanaged types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fe87-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8fe87-104">Syntax</span></span>  
  
```  
typedef enum CorNativeType {  
  
    NATIVE_TYPE_END                  = 0x0,  
    NATIVE_TYPE_VOID                 = 0x1,  
    NATIVE_TYPE_BOOLEAN              = 0x2,  
    NATIVE_TYPE_I1                   = 0x3,  
    NATIVE_TYPE_U1                   = 0x4,  
    NATIVE_TYPE_I2                   = 0x5,  
    NATIVE_TYPE_U2                   = 0x6,  
    NATIVE_TYPE_I4                   = 0x7,  
    NATIVE_TYPE_U4                   = 0x8,  
    NATIVE_TYPE_I8                   = 0x9,  
    NATIVE_TYPE_U8                   = 0xa,  
    NATIVE_TYPE_R4                   = 0xb,  
    NATIVE_TYPE_R8                   = 0xc,  
    NATIVE_TYPE_SYSCHAR              = 0xd,  
    NATIVE_TYPE_VARIANT              = 0xe,  
    NATIVE_TYPE_CURRENCY             = 0xf,  
    NATIVE_TYPE_PTR                  = 0x10,  
  
    NATIVE_TYPE_DECIMAL              = 0x11,  
    NATIVE_TYPE_DATE                 = 0x12,  
    NATIVE_TYPE_BSTR                 = 0x13,  
    NATIVE_TYPE_LPSTR                = 0x14,  
    NATIVE_TYPE_LPWSTR               = 0x15,  
    NATIVE_TYPE_LPTSTR               = 0x16,  
    NATIVE_TYPE_FIXEDSYSSTRING       = 0x17,  
    NATIVE_TYPE_OBJECTREF            = 0x18,  
    NATIVE_TYPE_IUNKNOWN             = 0x19,  
    NATIVE_TYPE_IDISPATCH            = 0x1a,  
    NATIVE_TYPE_STRUCT               = 0x1b,  
    NATIVE_TYPE_INTF                 = 0x1c,  
    NATIVE_TYPE_SAFEARRAY            = 0x1d,  
    NATIVE_TYPE_FIXEDARRAY           = 0x1e,  
    NATIVE_TYPE_INT                  = 0x1f,  
    NATIVE_TYPE_UINT                 = 0x20,  
  
    NATIVE_TYPE_NESTEDSTRUCT         = 0x21,  
    NATIVE_TYPE_BYVALSTR             = 0x22,  
    NATIVE_TYPE_ANSIBSTR             = 0x23,  
    NATIVE_TYPE_TBSTR                = 0x24,  
    NATIVE_TYPE_VARIANTBOOL          = 0x25,  
    NATIVE_TYPE_FUNC                 = 0x26,  
  
    NATIVE_TYPE_ASANY                = 0x28,  
    NATIVE_TYPE_ARRAY                = 0x2a,  
    NATIVE_TYPE_LPSTRUCT             = 0x2b,  
    NATIVE_TYPE_CUSTOMMARSHALER      = 0x2c,  
    NATIVE_TYPE_IINSPECTABLE         = 0x2e,  
    NATIVE_TYPE_HSTRING              = 0x2f,  
  
    NATIVE_TYPE_ERROR                = 0x2d,   
  
    NATIVE_TYPE_MAX                  = 0x50  
  
} CorNativeType;  
```  
  
## <a name="members"></a><span data-ttu-id="8fe87-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="8fe87-105">Members</span></span>  
  
|<span data-ttu-id="8fe87-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="8fe87-106">Member</span></span>|<span data-ttu-id="8fe87-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8fe87-107">Description</span></span>|  
|------------|-----------------|  
|`NATIVE_TYPE_END`|<span data-ttu-id="8fe87-108">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="8fe87-108">Obsolete.</span></span>|  
|`NATIVE_TYPE_VOID`|<span data-ttu-id="8fe87-109">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="8fe87-109">Obsolete.</span></span>|  
|`NATIVE_TYPE_BOOLEAN`|<span data-ttu-id="8fe87-110">Wartość logiczna 4-bajtowych, gdzie wartość TRUE jest różna od zera i FALSE wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="8fe87-110">A 4-byte Boolean value, where TRUE is non-zero and FALSE is zero.</span></span>|  
|`NATIVE_TYPE_I1`|<span data-ttu-id="8fe87-111">Wartość całkowita 8-bitowa.</span><span class="sxs-lookup"><span data-stu-id="8fe87-111">A signed 8-bit integer value.</span></span>|  
|`NATIVE_TYPE_U1`|<span data-ttu-id="8fe87-112">Niepodpisane 8-bitową liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="8fe87-112">An unsigned 8-bit integer value.</span></span>|  
|`NATIVE_TYPE_I2`|<span data-ttu-id="8fe87-113">Wartość całkowita 16-bitowych.</span><span class="sxs-lookup"><span data-stu-id="8fe87-113">A signed 16-bit integer value.</span></span>|  
|`NATIVE_TYPE_U2`|<span data-ttu-id="8fe87-114">Niepodpisane 16-bitową liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="8fe87-114">An unsigned 16-bit integer value.</span></span>|  
|`NATIVE_TYPE_I4`|<span data-ttu-id="8fe87-115">Wartość całkowita 32-bitowa.</span><span class="sxs-lookup"><span data-stu-id="8fe87-115">A signed 32-bit integer value.</span></span>|  
|`NATIVE_TYPE_U4`|<span data-ttu-id="8fe87-116">Wartość liczby całkowitej bez znaku 32-bitowych.</span><span class="sxs-lookup"><span data-stu-id="8fe87-116">An unsigned 32-bit integer value.</span></span>|  
|`NATIVE_TYPE_I8`|<span data-ttu-id="8fe87-117">Wartość całkowita 64-bitowa.</span><span class="sxs-lookup"><span data-stu-id="8fe87-117">A signed 64-bit integer value.</span></span>|  
|`NATIVE_TYPE_U8`|<span data-ttu-id="8fe87-118">Wartość liczby całkowitej bez znaku 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="8fe87-118">An unsigned 64-bit integer value.</span></span>|  
|`NATIVE_TYPE_R4`|<span data-ttu-id="8fe87-119">4-bajtowych liczb zmiennoprzecinkowych wartość liczbową.</span><span class="sxs-lookup"><span data-stu-id="8fe87-119">A 4-byte floating-point numeric value.</span></span>|  
|`NATIVE_TYPE_R8`|<span data-ttu-id="8fe87-120">8-bajtowych liczb zmiennoprzecinkowych wartość liczbowa.</span><span class="sxs-lookup"><span data-stu-id="8fe87-120">An 8-byte floating-point numeric value.</span></span>|  
|`NATIVE_TYPE_SYSCHAR`|<span data-ttu-id="8fe87-121">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="8fe87-121">Obsolete.</span></span>|  
|`NATIVE_TYPE_VARIANT`|<span data-ttu-id="8fe87-122">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="8fe87-122">Obsolete.</span></span>|  
|`NATIVE_TYPE_CURRENCY`|<span data-ttu-id="8fe87-123">Typ liczbowy COM, umożliwiająca zarządzanej <xref:System.Decimal> typu.</span><span class="sxs-lookup"><span data-stu-id="8fe87-123">A numeric COM type that corresponds to the managed <xref:System.Decimal> type.</span></span>|  
|`NATIVE_TYPE_PTR`|<span data-ttu-id="8fe87-124">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="8fe87-124">Obsolete.</span></span>|  
|`NATIVE_TYPE_DECIMAL`|<span data-ttu-id="8fe87-125">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="8fe87-125">Obsolete.</span></span>|  
|`NATIVE_TYPE_DATE`|<span data-ttu-id="8fe87-126">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="8fe87-126">Obsolete.</span></span>|  
|`NATIVE_TYPE_BSTR`|<span data-ttu-id="8fe87-127">COM Interop.</span><span class="sxs-lookup"><span data-stu-id="8fe87-127">COM Interop.</span></span>|  
|`NATIVE_TYPE_LPSTR`|<span data-ttu-id="8fe87-128">Wartość ciągu LPSTR.</span><span class="sxs-lookup"><span data-stu-id="8fe87-128">An LPSTR string value.</span></span>|  
|`NATIVE_TYPE_LPWSTR`|<span data-ttu-id="8fe87-129">Wartość ciągu LPWSTR.</span><span class="sxs-lookup"><span data-stu-id="8fe87-129">An LPWSTR string value.</span></span>|  
|`NATIVE_TYPE_LPTSTR`|<span data-ttu-id="8fe87-130">Wartość ciągu LPTSTR.</span><span class="sxs-lookup"><span data-stu-id="8fe87-130">An LPTSTR string value.</span></span>|  
|`NATIVE_TYPE_FIXEDSYSSTRING`|<span data-ttu-id="8fe87-131">Wartość ciągu o stałej, zdefiniowane przez system.</span><span class="sxs-lookup"><span data-stu-id="8fe87-131">A fixed, system-defined string value.</span></span>|  
|`NATIVE_TYPE_OBJECTREF`|<span data-ttu-id="8fe87-132">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="8fe87-132">Obsolete.</span></span>|  
|`NATIVE_TYPE_IUNKNOWN`|<span data-ttu-id="8fe87-133">COM Interop.</span><span class="sxs-lookup"><span data-stu-id="8fe87-133">COM Interop.</span></span>|  
|`NATIVE_TYPE_IDISPATCH`|<span data-ttu-id="8fe87-134">COM Interop.</span><span class="sxs-lookup"><span data-stu-id="8fe87-134">COM Interop.</span></span>|  
|`NATIVE_TYPE_STRUCT`|<span data-ttu-id="8fe87-135">Wartość native struktury.</span><span class="sxs-lookup"><span data-stu-id="8fe87-135">A native structure value.</span></span>|  
|`NATIVE_TYPE_INTF`|<span data-ttu-id="8fe87-136">COM Interop.</span><span class="sxs-lookup"><span data-stu-id="8fe87-136">COM Interop.</span></span>|  
|`NATIVE_TYPE_SAFEARRAY`|<span data-ttu-id="8fe87-137">COM Interop.</span><span class="sxs-lookup"><span data-stu-id="8fe87-137">COM Interop.</span></span>|  
|`NATIVE_TYPE_FIXEDARRAY`|<span data-ttu-id="8fe87-138">Wartość stałej długości tablicy.</span><span class="sxs-lookup"><span data-stu-id="8fe87-138">A fixed-length array value.</span></span>|  
|`NATIVE_TYPE_INT`|<span data-ttu-id="8fe87-139">Wartość native 16-bitową liczbę całkowitą ze znakiem.</span><span class="sxs-lookup"><span data-stu-id="8fe87-139">A native 16-bit signed integer value.</span></span>|  
|`NATIVE_TYPE_UINT`|<span data-ttu-id="8fe87-140">Wartość native liczbę całkowitą bez znaku 16-bitowych.</span><span class="sxs-lookup"><span data-stu-id="8fe87-140">A native 16-bit unsigned integer value.</span></span>|  
|`NATIVE_TYPE_NESTEDSTRUCT`|<span data-ttu-id="8fe87-141">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="8fe87-141">Obsolete.</span></span><br /><br /> <span data-ttu-id="8fe87-142">Użyj NATIVE_TYPE_STRUCT.</span><span class="sxs-lookup"><span data-stu-id="8fe87-142">Use NATIVE_TYPE_STRUCT.</span></span>|  
|`NATIVE_TYPE_BYVALSTR`|<span data-ttu-id="8fe87-143">COM Interop.</span><span class="sxs-lookup"><span data-stu-id="8fe87-143">COM Interop.</span></span>|  
|`NATIVE_TYPE_ANSIBSTR`|<span data-ttu-id="8fe87-144">COM Interop.</span><span class="sxs-lookup"><span data-stu-id="8fe87-144">COM Interop.</span></span>|  
|`NATIVE_TYPE_TBSTR`|<span data-ttu-id="8fe87-145">COM Interop.</span><span class="sxs-lookup"><span data-stu-id="8fe87-145">COM Interop.</span></span><br /><br /> <span data-ttu-id="8fe87-146">Wybierz, BSTR lub ANSIBSTR w zależności od platformy.</span><span class="sxs-lookup"><span data-stu-id="8fe87-146">Select BSTR or ANSIBSTR depending on the platform.</span></span>|  
|`NATIVE_TYPE_VARIANTBOOL`|<span data-ttu-id="8fe87-147">2-bajtowych wartość logiczna, której prawdziwe wynosi -1 i FAŁSZ wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="8fe87-147">A 2-byte Boolean value, where TRUE is -1 and FALSE is zero.</span></span>|  
|`NATIVE_TYPE_FUNC`|<span data-ttu-id="8fe87-148">Wskaźnik funkcji.</span><span class="sxs-lookup"><span data-stu-id="8fe87-148">A function pointer.</span></span>|  
|`NATIVE_TYPE_ASANY`|<span data-ttu-id="8fe87-149">Odwołanie do dowolnego typu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="8fe87-149">A reference to any native type.</span></span>|  
|`NATIVE_TYPE_ARRAY`|<span data-ttu-id="8fe87-150">Odwołanie do tablicy z elementami członkowskimi nieokreślonego typu.</span><span class="sxs-lookup"><span data-stu-id="8fe87-150">A reference to an array with members of an unspecified type.</span></span>|  
|`NATIVE_TYPE_LPSTRUCT`|<span data-ttu-id="8fe87-151">32-bitową liczbę całkowitą wskaźnik do struktury.</span><span class="sxs-lookup"><span data-stu-id="8fe87-151">A 32-bit integer pointer to a structure.</span></span>|  
|`NATIVE_TYPE_CUSTOMMARSHALER`|<span data-ttu-id="8fe87-152">Organizator niestandardowy typ macierzysty.</span><span class="sxs-lookup"><span data-stu-id="8fe87-152">A custom marshaler native type.</span></span><br /><br /> <span data-ttu-id="8fe87-153">To musi następować ciąg o następującym formacie: "organizator nazwa/0Custom typ macierzysty typ nazwy/0Optional pliku cookie/0" lub "{natywnego typu GUID} / organizatora 0Custom wpisz nazwę/0Optional pliku cookie/0"</span><span class="sxs-lookup"><span data-stu-id="8fe87-153">This must be followed by a string of the following format: "Native type name/0Custom marshaler type name/0Optional cookie/0" or "{Native type GUID}/0Custom marshaler type name/0Optional cookie/0"</span></span>|  
|`NATIVE_TYPE_ERROR`|<span data-ttu-id="8fe87-154">COM Interop.</span><span class="sxs-lookup"><span data-stu-id="8fe87-154">COM Interop.</span></span><br /><br /> <span data-ttu-id="8fe87-155">Z ELEMENT_TYPE_I4 VT_HRESULT mapuje tego typu.</span><span class="sxs-lookup"><span data-stu-id="8fe87-155">With ELEMENT_TYPE_I4 this type maps to VT_HRESULT.</span></span>|  
|`NATIVE_TYPE_IINSPECTABLE`|<span data-ttu-id="8fe87-156">Natywny `IInspectable` typu.</span><span class="sxs-lookup"><span data-stu-id="8fe87-156">A native `IInspectable` type.</span></span>|  
|`NATIVE_TYPE_HSTRING`|<span data-ttu-id="8fe87-157">Natywny `HString`.</span><span class="sxs-lookup"><span data-stu-id="8fe87-157">A native `HString`.</span></span>|  
|`NATIVE_TYPE_MAX`|<span data-ttu-id="8fe87-158">Określono nieprawidłową wartość.</span><span class="sxs-lookup"><span data-stu-id="8fe87-158">An invalid value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8fe87-159">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8fe87-159">Requirements</span></span>  
 <span data-ttu-id="8fe87-160">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fe87-160">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fe87-161">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="8fe87-161">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="8fe87-162">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fe87-162">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fe87-163">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8fe87-163">See Also</span></span>  
 <xref:System.Runtime.InteropServices.UnmanagedType>  
 [<span data-ttu-id="8fe87-164">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="8fe87-164">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

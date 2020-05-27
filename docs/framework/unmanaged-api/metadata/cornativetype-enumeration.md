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
ms.openlocfilehash: dd97c479f12e7bdb015b39a802b398ca2b0bcd3f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007640"
---
# <a name="cornativetype-enumeration"></a><span data-ttu-id="dd950-102">CorNativeType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="dd950-102">CorNativeType Enumeration</span></span>
<span data-ttu-id="dd950-103">Zawiera wartości opisujące natywne typy niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="dd950-103">Contains values that describe native unmanaged types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd950-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dd950-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="dd950-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="dd950-105">Members</span></span>  
  
|<span data-ttu-id="dd950-106">Członek</span><span class="sxs-lookup"><span data-stu-id="dd950-106">Member</span></span>|<span data-ttu-id="dd950-107">Opis</span><span class="sxs-lookup"><span data-stu-id="dd950-107">Description</span></span>|  
|------------|-----------------|  
|`NATIVE_TYPE_END`|<span data-ttu-id="dd950-108">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="dd950-108">Obsolete.</span></span>|  
|`NATIVE_TYPE_VOID`|<span data-ttu-id="dd950-109">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="dd950-109">Obsolete.</span></span>|  
|`NATIVE_TYPE_BOOLEAN`|<span data-ttu-id="dd950-110">4-bajtowa wartość logiczna, gdzie TRUE ma wartość różną od zera, a wartość FALSE to zero.</span><span class="sxs-lookup"><span data-stu-id="dd950-110">A 4-byte Boolean value, where TRUE is non-zero and FALSE is zero.</span></span>|  
|`NATIVE_TYPE_I1`|<span data-ttu-id="dd950-111">8-bitowa liczba całkowita ze znakiem.</span><span class="sxs-lookup"><span data-stu-id="dd950-111">A signed 8-bit integer value.</span></span>|  
|`NATIVE_TYPE_U1`|<span data-ttu-id="dd950-112">8-bitowa liczba całkowita bez znaku.</span><span class="sxs-lookup"><span data-stu-id="dd950-112">An unsigned 8-bit integer value.</span></span>|  
|`NATIVE_TYPE_I2`|<span data-ttu-id="dd950-113">Wartość 16-bitowa ze znakiem.</span><span class="sxs-lookup"><span data-stu-id="dd950-113">A signed 16-bit integer value.</span></span>|  
|`NATIVE_TYPE_U2`|<span data-ttu-id="dd950-114">16-bitowa liczba całkowita bez znaku.</span><span class="sxs-lookup"><span data-stu-id="dd950-114">An unsigned 16-bit integer value.</span></span>|  
|`NATIVE_TYPE_I4`|<span data-ttu-id="dd950-115">Podpisana 32-bitowa liczba całkowita.</span><span class="sxs-lookup"><span data-stu-id="dd950-115">A signed 32-bit integer value.</span></span>|  
|`NATIVE_TYPE_U4`|<span data-ttu-id="dd950-116">Niepodpisana wartość 32-bitowa liczba całkowita.</span><span class="sxs-lookup"><span data-stu-id="dd950-116">An unsigned 32-bit integer value.</span></span>|  
|`NATIVE_TYPE_I8`|<span data-ttu-id="dd950-117">Podpisana 64-bitowa liczba całkowita.</span><span class="sxs-lookup"><span data-stu-id="dd950-117">A signed 64-bit integer value.</span></span>|  
|`NATIVE_TYPE_U8`|<span data-ttu-id="dd950-118">Niepodpisana wartość 64-bitowa liczba całkowita.</span><span class="sxs-lookup"><span data-stu-id="dd950-118">An unsigned 64-bit integer value.</span></span>|  
|`NATIVE_TYPE_R4`|<span data-ttu-id="dd950-119">4-bajtowa wartość liczbowa zmiennoprzecinkowa.</span><span class="sxs-lookup"><span data-stu-id="dd950-119">A 4-byte floating-point numeric value.</span></span>|  
|`NATIVE_TYPE_R8`|<span data-ttu-id="dd950-120">8-bajtowa wartość liczbowa zmiennoprzecinkowa.</span><span class="sxs-lookup"><span data-stu-id="dd950-120">An 8-byte floating-point numeric value.</span></span>|  
|`NATIVE_TYPE_SYSCHAR`|<span data-ttu-id="dd950-121">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="dd950-121">Obsolete.</span></span>|  
|`NATIVE_TYPE_VARIANT`|<span data-ttu-id="dd950-122">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="dd950-122">Obsolete.</span></span>|  
|`NATIVE_TYPE_CURRENCY`|<span data-ttu-id="dd950-123">Liczbowy typ COM, który odpowiada typowi zarządzanemu <xref:System.Decimal> .</span><span class="sxs-lookup"><span data-stu-id="dd950-123">A numeric COM type that corresponds to the managed <xref:System.Decimal> type.</span></span>|  
|`NATIVE_TYPE_PTR`|<span data-ttu-id="dd950-124">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="dd950-124">Obsolete.</span></span>|  
|`NATIVE_TYPE_DECIMAL`|<span data-ttu-id="dd950-125">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="dd950-125">Obsolete.</span></span>|  
|`NATIVE_TYPE_DATE`|<span data-ttu-id="dd950-126">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="dd950-126">Obsolete.</span></span>|  
|`NATIVE_TYPE_BSTR`|<span data-ttu-id="dd950-127">Międzyoperacyjność modelu COM.</span><span class="sxs-lookup"><span data-stu-id="dd950-127">COM Interop.</span></span>|  
|`NATIVE_TYPE_LPSTR`|<span data-ttu-id="dd950-128">Wartość ciągu LPSTR.</span><span class="sxs-lookup"><span data-stu-id="dd950-128">An LPSTR string value.</span></span>|  
|`NATIVE_TYPE_LPWSTR`|<span data-ttu-id="dd950-129">Wartość ciągu LPWSTR.</span><span class="sxs-lookup"><span data-stu-id="dd950-129">An LPWSTR string value.</span></span>|  
|`NATIVE_TYPE_LPTSTR`|<span data-ttu-id="dd950-130">Wartość ciągu LPTSTR.</span><span class="sxs-lookup"><span data-stu-id="dd950-130">An LPTSTR string value.</span></span>|  
|`NATIVE_TYPE_FIXEDSYSSTRING`|<span data-ttu-id="dd950-131">Stała, zdefiniowana przez system wartość ciągu.</span><span class="sxs-lookup"><span data-stu-id="dd950-131">A fixed, system-defined string value.</span></span>|  
|`NATIVE_TYPE_OBJECTREF`|<span data-ttu-id="dd950-132">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="dd950-132">Obsolete.</span></span>|  
|`NATIVE_TYPE_IUNKNOWN`|<span data-ttu-id="dd950-133">Międzyoperacyjność modelu COM.</span><span class="sxs-lookup"><span data-stu-id="dd950-133">COM Interop.</span></span>|  
|`NATIVE_TYPE_IDISPATCH`|<span data-ttu-id="dd950-134">Międzyoperacyjność modelu COM.</span><span class="sxs-lookup"><span data-stu-id="dd950-134">COM Interop.</span></span>|  
|`NATIVE_TYPE_STRUCT`|<span data-ttu-id="dd950-135">Wartość struktury natywnej.</span><span class="sxs-lookup"><span data-stu-id="dd950-135">A native structure value.</span></span>|  
|`NATIVE_TYPE_INTF`|<span data-ttu-id="dd950-136">Międzyoperacyjność modelu COM.</span><span class="sxs-lookup"><span data-stu-id="dd950-136">COM Interop.</span></span>|  
|`NATIVE_TYPE_SAFEARRAY`|<span data-ttu-id="dd950-137">Międzyoperacyjność modelu COM.</span><span class="sxs-lookup"><span data-stu-id="dd950-137">COM Interop.</span></span>|  
|`NATIVE_TYPE_FIXEDARRAY`|<span data-ttu-id="dd950-138">Wartość tablicy o stałej długości.</span><span class="sxs-lookup"><span data-stu-id="dd950-138">A fixed-length array value.</span></span>|  
|`NATIVE_TYPE_INT`|<span data-ttu-id="dd950-139">Natywna 16-bitowa liczba całkowita ze znakiem.</span><span class="sxs-lookup"><span data-stu-id="dd950-139">A native 16-bit signed integer value.</span></span>|  
|`NATIVE_TYPE_UINT`|<span data-ttu-id="dd950-140">Natywna 16-bitowa liczba całkowita bez znaku.</span><span class="sxs-lookup"><span data-stu-id="dd950-140">A native 16-bit unsigned integer value.</span></span>|  
|`NATIVE_TYPE_NESTEDSTRUCT`|<span data-ttu-id="dd950-141">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="dd950-141">Obsolete.</span></span><br /><br /> <span data-ttu-id="dd950-142">Użyj NATIVE_TYPE_STRUCT.</span><span class="sxs-lookup"><span data-stu-id="dd950-142">Use NATIVE_TYPE_STRUCT.</span></span>|  
|`NATIVE_TYPE_BYVALSTR`|<span data-ttu-id="dd950-143">Międzyoperacyjność modelu COM.</span><span class="sxs-lookup"><span data-stu-id="dd950-143">COM Interop.</span></span>|  
|`NATIVE_TYPE_ANSIBSTR`|<span data-ttu-id="dd950-144">Międzyoperacyjność modelu COM.</span><span class="sxs-lookup"><span data-stu-id="dd950-144">COM Interop.</span></span>|  
|`NATIVE_TYPE_TBSTR`|<span data-ttu-id="dd950-145">Międzyoperacyjność modelu COM.</span><span class="sxs-lookup"><span data-stu-id="dd950-145">COM Interop.</span></span><br /><br /> <span data-ttu-id="dd950-146">W zależności od platformy wybierz opcję BSTR lub ANSIBSTR.</span><span class="sxs-lookup"><span data-stu-id="dd950-146">Select BSTR or ANSIBSTR depending on the platform.</span></span>|  
|`NATIVE_TYPE_VARIANTBOOL`|<span data-ttu-id="dd950-147">Wartość 2-bajtowa wartości logicznej, gdzie TRUE to-1, a FALSE to zero.</span><span class="sxs-lookup"><span data-stu-id="dd950-147">A 2-byte Boolean value, where TRUE is -1 and FALSE is zero.</span></span>|  
|`NATIVE_TYPE_FUNC`|<span data-ttu-id="dd950-148">Wskaźnik funkcji.</span><span class="sxs-lookup"><span data-stu-id="dd950-148">A function pointer.</span></span>|  
|`NATIVE_TYPE_ASANY`|<span data-ttu-id="dd950-149">Odwołanie do dowolnego typu natywnego.</span><span class="sxs-lookup"><span data-stu-id="dd950-149">A reference to any native type.</span></span>|  
|`NATIVE_TYPE_ARRAY`|<span data-ttu-id="dd950-150">Odwołanie do tablicy z elementami członkowskimi nieokreślonego typu.</span><span class="sxs-lookup"><span data-stu-id="dd950-150">A reference to an array with members of an unspecified type.</span></span>|  
|`NATIVE_TYPE_LPSTRUCT`|<span data-ttu-id="dd950-151">32-bitowy wskaźnik liczby całkowitej do struktury.</span><span class="sxs-lookup"><span data-stu-id="dd950-151">A 32-bit integer pointer to a structure.</span></span>|  
|`NATIVE_TYPE_CUSTOMMARSHALER`|<span data-ttu-id="dd950-152">Typ natywny organizatora niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="dd950-152">A custom marshaler native type.</span></span><br /><br /> <span data-ttu-id="dd950-153">Musi to być ciąg o następującym formacie: "native type name/0Custom typ marshaler/0Optional cookie/0" lub "{native Type GUID}/0Custom typu nazwa/0Optional cookie/0"</span><span class="sxs-lookup"><span data-stu-id="dd950-153">This must be followed by a string of the following format: "Native type name/0Custom marshaler type name/0Optional cookie/0" or "{Native type GUID}/0Custom marshaler type name/0Optional cookie/0"</span></span>|  
|`NATIVE_TYPE_ERROR`|<span data-ttu-id="dd950-154">Międzyoperacyjność modelu COM.</span><span class="sxs-lookup"><span data-stu-id="dd950-154">COM Interop.</span></span><br /><br /> <span data-ttu-id="dd950-155">Dzięki ELEMENT_TYPE_I4 ten typ mapuje do VT_HRESULT.</span><span class="sxs-lookup"><span data-stu-id="dd950-155">With ELEMENT_TYPE_I4 this type maps to VT_HRESULT.</span></span>|  
|`NATIVE_TYPE_IINSPECTABLE`|<span data-ttu-id="dd950-156">Typ natywny `IInspectable` .</span><span class="sxs-lookup"><span data-stu-id="dd950-156">A native `IInspectable` type.</span></span>|  
|`NATIVE_TYPE_HSTRING`|<span data-ttu-id="dd950-157">Natywny `HString` .</span><span class="sxs-lookup"><span data-stu-id="dd950-157">A native `HString`.</span></span>|  
|`NATIVE_TYPE_MAX`|<span data-ttu-id="dd950-158">Nieprawidłowa wartość.</span><span class="sxs-lookup"><span data-stu-id="dd950-158">An invalid value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dd950-159">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dd950-159">Requirements</span></span>  
 <span data-ttu-id="dd950-160">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd950-160">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd950-161">**Nagłówek:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="dd950-161">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="dd950-162">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd950-162">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd950-163">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dd950-163">See also</span></span>

- <xref:System.Runtime.InteropServices.UnmanagedType>
- [<span data-ttu-id="dd950-164">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="dd950-164">Metadata Enumerations</span></span>](metadata-enumerations.md)

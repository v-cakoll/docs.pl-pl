---
title: StrongNameGetBlob — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlob
helpviewer_keywords:
- StrongNameGetBlob function [.NET Framework strong naming]
ms.assetid: 15d09166-be00-4696-913f-2c1fbc7ac2e1
topic_type:
- apiref
ms.openlocfilehash: e99346ecca651346b46c220a5e427cbc7f4c4697
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095015"
---
# <a name="strongnamegetblob-function"></a><span data-ttu-id="39c23-102">StrongNameGetBlob — Funkcja</span><span class="sxs-lookup"><span data-stu-id="39c23-102">StrongNameGetBlob Function</span></span>
<span data-ttu-id="39c23-103">Wypełnia określony bufor reprezentacją binarną pliku wykonywalnego pod określonym adresem.</span><span class="sxs-lookup"><span data-stu-id="39c23-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
 <span data-ttu-id="39c23-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="39c23-104">This function has been deprecated.</span></span> <span data-ttu-id="39c23-105">Zamiast tego użyj metody [ICLRStrongName:: StrongNameGetBlob —](../hosting/iclrstrongname-strongnamegetblob-method.md) .</span><span class="sxs-lookup"><span data-stu-id="39c23-105">Use the [ICLRStrongName::StrongNameGetBLob](../hosting/iclrstrongname-strongnamegetblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39c23-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="39c23-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39c23-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="39c23-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="39c23-108">podczas Prawidłowa ścieżka do pliku wykonywalnego, który ma zostać załadowany.</span><span class="sxs-lookup"><span data-stu-id="39c23-108">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="39c23-109">podczas Bufor, do którego ma zostać załadowany plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="39c23-109">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="39c23-110">[in. out] Żądany maksymalny rozmiar w bajtach `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="39c23-110">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="39c23-111">Po powrocie, rzeczywisty rozmiar w bajtach `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="39c23-111">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39c23-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="39c23-112">Return Value</span></span>  
 <span data-ttu-id="39c23-113">`true` po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="39c23-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39c23-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="39c23-114">Remarks</span></span>  
 <span data-ttu-id="39c23-115">Jeśli funkcja `StrongNameGetBlob` nie zakończy się pomyślnie, wywołaj funkcję [StrongNameErrorInfo —](strongnameerrorinfo-function.md) w celu pobrania ostatniego wygenerowanego błędu.</span><span class="sxs-lookup"><span data-stu-id="39c23-115">If the `StrongNameGetBlob` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39c23-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="39c23-116">Requirements</span></span>  
 <span data-ttu-id="39c23-117">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39c23-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39c23-118">**Nagłówek:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="39c23-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="39c23-119">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="39c23-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="39c23-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39c23-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39c23-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="39c23-121">See also</span></span>

- [<span data-ttu-id="39c23-122">StrongNameGetBlob, metoda</span><span class="sxs-lookup"><span data-stu-id="39c23-122">StrongNameGetBlob Method</span></span>](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="39c23-123">StrongNameGetBlobFromImage, metoda</span><span class="sxs-lookup"><span data-stu-id="39c23-123">StrongNameGetBlobFromImage Method</span></span>](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="39c23-124">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="39c23-124">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)

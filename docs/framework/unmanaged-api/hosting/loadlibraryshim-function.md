---
title: "LoadLibraryShim — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LoadLibraryShim
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: LoadLibraryShim
helpviewer_keywords: LoadLibraryShim function [.NET Framework hosting]
ms.assetid: 30931874-4d0e-4df1-b3d1-e425b50655d1
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c56f5a3576c505fd7b7d514e3f2d038e7f8f3ecc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="loadlibraryshim-function"></a><span data-ttu-id="37f60-102">LoadLibraryShim — Funkcja</span><span class="sxs-lookup"><span data-stu-id="37f60-102">LoadLibraryShim Function</span></span>
<span data-ttu-id="37f60-103">Ładuje określona wersja biblioteki DLL, która jest uwzględniona w pakiet redystrybucyjny programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="37f60-103">Loads a specified version of a DLL that is included in the .NET Framework redistributable package.</span></span>  
  
 <span data-ttu-id="37f60-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="37f60-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="37f60-105">Użyj [ICLRRuntimeInfo::LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="37f60-105">Use the [ICLRRuntimeInfo::LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37f60-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="37f60-106">Syntax</span></span>  
  
```  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="37f60-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="37f60-107">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="37f60-108">[in] Ciąg zakończony zerem, który reprezentuje nazwę biblioteki DLL do załadowania z biblioteki .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="37f60-108">[in] A zero-terminated string that represents the name of the DLL to be loaded from the .NET Framework library.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="37f60-109">[in] Ciąg zakończony zerem, który reprezentuje wersja biblioteki DLL do załadowania.</span><span class="sxs-lookup"><span data-stu-id="37f60-109">[in] A zero-terminated string that represents the version of the DLL to be loaded.</span></span> <span data-ttu-id="37f60-110">Jeśli `szVersion` jest null, wersja wybrany na potrzeby ładowania jest najnowsza wersja określonej biblioteki DLL, która jest mniejsza niż w wersji 4.</span><span class="sxs-lookup"><span data-stu-id="37f60-110">If `szVersion` is null, the version selected for loading is the latest version of the specified DLL that is less than version 4.</span></span> <span data-ttu-id="37f60-111">Oznacza to, że wszystkie wersje, równa lub większa niż wersja 4 są ignorowane, jeśli `szVersion` ma wartość null, a jeśli nie wcześniejszą niż wersja w wersji 4 jest zainstalowana, biblioteki DLL nie udało się załadować.</span><span class="sxs-lookup"><span data-stu-id="37f60-111">That is, all versions equal to or greater than version 4 are ignored if `szVersion` is null, and if no version less than version 4 is installed, the DLL fails to load.</span></span> <span data-ttu-id="37f60-112">Dzięki tej instalacji [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] nie wpływa na istniejące aplikacje lub składników.</span><span class="sxs-lookup"><span data-stu-id="37f60-112">This is to ensure that installation of the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] does not affect pre-existing applications or components.</span></span> <span data-ttu-id="37f60-113">Zobacz wpis [SxS wewnątrzprocesową i migracji Szybki Start](http://go.microsoft.com/fwlink/?LinkId=200329) w blogu zespołu CLR.</span><span class="sxs-lookup"><span data-stu-id="37f60-113">See the entry [In-Proc SxS and Migration Quick Start](http://go.microsoft.com/fwlink/?LinkId=200329) in the CLR team blog.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="37f60-114">Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="37f60-114">Reserved for future use.</span></span>  
  
 `phModDll`  
 <span data-ttu-id="37f60-115">[out] Wskaźnik do uchwytu modułu.</span><span class="sxs-lookup"><span data-stu-id="37f60-115">[out] A pointer to the handle of the module.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37f60-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="37f60-116">Return Value</span></span>  
 <span data-ttu-id="37f60-117">Ta metoda zwraca standardowy składnik modelu COM. kody błędów, zgodnie z definicją w pliku WinError.h oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="37f60-117">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="37f60-118">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="37f60-118">Return code</span></span>|<span data-ttu-id="37f60-119">Opis</span><span class="sxs-lookup"><span data-stu-id="37f60-119">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="37f60-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="37f60-120">S_OK</span></span>|<span data-ttu-id="37f60-121">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="37f60-121">The method completed successfully.</span></span>|  
|<span data-ttu-id="37f60-122">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="37f60-122">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="37f60-123">Ładowanie `szDllName` wymaga ładowania środowisko uruchomieniowe języka wspólnego (CLR) i wymaganej wersji aparatu CLR nie może zostać załadowany.</span><span class="sxs-lookup"><span data-stu-id="37f60-123">Loading `szDllName` requires loading the common language runtime (CLR), and the necessary version of the CLR cannot be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37f60-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="37f60-124">Remarks</span></span>  
 <span data-ttu-id="37f60-125">Ta funkcja jest używana do załadowania biblioteki dll, które znajdują się w pakiet redystrybucyjny programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="37f60-125">This function is used to load DLLs that are included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="37f60-126">Nie ładuje wygenerowaną przez użytkowników biblioteki dll.</span><span class="sxs-lookup"><span data-stu-id="37f60-126">It does not load user-generated DLLs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37f60-127">Począwszy od programu .NET Framework w wersji 2.0, ładowanie Fusion.dll powoduje, że można załadować środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="37f60-127">Beginning with the .NET Framework version 2.0, loading Fusion.dll causes the CLR to be loaded.</span></span> <span data-ttu-id="37f60-128">Jest to spowodowane funkcje w Fusion.dll są teraz otoki którego implementacje znajdują się w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="37f60-128">This is because the functions in Fusion.dll are now wrappers whose implementations are provided by the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37f60-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="37f60-129">Requirements</span></span>  
 <span data-ttu-id="37f60-130">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37f60-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37f60-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="37f60-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="37f60-132">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37f60-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37f60-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="37f60-133">See Also</span></span>  
 [<span data-ttu-id="37f60-134">Przestarzałe funkcje hostingu środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="37f60-134">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

---
title: LoadLibraryShim — Funkcja
ms.date: 03/30/2017
api_name:
- LoadLibraryShim
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LoadLibraryShim
helpviewer_keywords:
- LoadLibraryShim function [.NET Framework hosting]
ms.assetid: 30931874-4d0e-4df1-b3d1-e425b50655d1
topic_type:
- apiref
ms.openlocfilehash: 11bb220068e978dc130701e3b28ab3f421be7337
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937652"
---
# <a name="loadlibraryshim-function"></a><span data-ttu-id="67986-102">LoadLibraryShim — Funkcja</span><span class="sxs-lookup"><span data-stu-id="67986-102">LoadLibraryShim Function</span></span>
<span data-ttu-id="67986-103">Ładuje określoną wersję biblioteki DLL dołączoną do pakietu redystrybucyjnego .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="67986-103">Loads a specified version of a DLL that is included in the .NET Framework redistributable package.</span></span>  
  
 <span data-ttu-id="67986-104">Ta funkcja jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="67986-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="67986-105">Zamiast tego użyj metody [ICLRRuntimeInfo:: LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) .</span><span class="sxs-lookup"><span data-stu-id="67986-105">Use the [ICLRRuntimeInfo::LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67986-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="67986-106">Syntax</span></span>  
  
```cpp  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67986-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="67986-107">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="67986-108">podczas Ciąg zakończony zerem, który reprezentuje nazwę biblioteki DLL, która ma zostać załadowana z biblioteki .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="67986-108">[in] A zero-terminated string that represents the name of the DLL to be loaded from the .NET Framework library.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="67986-109">podczas Ciąg zakończony zerem, który reprezentuje wersję biblioteki DLL, która ma zostać załadowana.</span><span class="sxs-lookup"><span data-stu-id="67986-109">[in] A zero-terminated string that represents the version of the DLL to be loaded.</span></span> <span data-ttu-id="67986-110">Jeśli `szVersion` ma wartość null, wybrana wersja do załadowania to Najnowsza wersja określonej biblioteki DLL, która jest starsza niż wersja 4.</span><span class="sxs-lookup"><span data-stu-id="67986-110">If `szVersion` is null, the version selected for loading is the latest version of the specified DLL that is less than version 4.</span></span> <span data-ttu-id="67986-111">Oznacza to, że wszystkie wersje równe lub większe niż wersja 4 są ignorowane, jeśli `szVersion` ma wartość null, a w przypadku braku zainstalowanej wersji programu w wersji 4 nie można załadować biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="67986-111">That is, all versions equal to or greater than version 4 are ignored if `szVersion` is null, and if no version less than version 4 is installed, the DLL fails to load.</span></span> <span data-ttu-id="67986-112">Ma to na celu zapewnienie, że instalacja .NET Framework 4 nie ma wpływu na istniejące aplikacje lub składniki.</span><span class="sxs-lookup"><span data-stu-id="67986-112">This is to ensure that installation of the .NET Framework 4 does not affect pre-existing applications or components.</span></span> <span data-ttu-id="67986-113">Zapoznaj się z wpisem [w procesie SxS i szybki start migracji](https://devblogs.microsoft.com/dotnet/in-proc-sxs-and-migration-quick-start/) w blogu zespołu CLR.</span><span class="sxs-lookup"><span data-stu-id="67986-113">See the entry [In-Proc SxS and Migration Quick Start](https://devblogs.microsoft.com/dotnet/in-proc-sxs-and-migration-quick-start/) in the CLR team blog.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="67986-114">Zarezerwowany do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="67986-114">Reserved for future use.</span></span>  
  
 `phModDll`  
 <span data-ttu-id="67986-115">określoną Wskaźnik do uchwytu modułu.</span><span class="sxs-lookup"><span data-stu-id="67986-115">[out] A pointer to the handle of the module.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="67986-116">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="67986-116">Return Value</span></span>  
 <span data-ttu-id="67986-117">Ta metoda zwraca kody błędów standardowego Component Object Model (COM), jak zdefiniowano w WinError. h, oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="67986-117">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="67986-118">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="67986-118">Return code</span></span>|<span data-ttu-id="67986-119">Opis</span><span class="sxs-lookup"><span data-stu-id="67986-119">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="67986-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="67986-120">S_OK</span></span>|<span data-ttu-id="67986-121">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="67986-121">The method completed successfully.</span></span>|  
|<span data-ttu-id="67986-122">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="67986-122">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="67986-123">Ładowanie `szDllName` wymaga załadowania środowiska uruchomieniowego języka wspólnego (CLR), a niezbędna wersja środowiska CLR nie może zostać załadowana.</span><span class="sxs-lookup"><span data-stu-id="67986-123">Loading `szDllName` requires loading the common language runtime (CLR), and the necessary version of the CLR cannot be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67986-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="67986-124">Remarks</span></span>  
 <span data-ttu-id="67986-125">Ta funkcja służy do ładowania bibliotek DLL, które znajdują się w pakiecie redystrybucyjnym .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="67986-125">This function is used to load DLLs that are included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="67986-126">Nie ładuje bibliotek DLL generowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="67986-126">It does not load user-generated DLLs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="67986-127">Począwszy od .NET Framework w wersji 2,0, wczytywanie pliku Fusion. dll powoduje załadowanie środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="67986-127">Beginning with the .NET Framework version 2.0, loading Fusion.dll causes the CLR to be loaded.</span></span> <span data-ttu-id="67986-128">Jest to spowodowane tym, że funkcje w programie Fusion. dll są teraz otokami, których implementacje są udostępniane przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="67986-128">This is because the functions in Fusion.dll are now wrappers whose implementations are provided by the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67986-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="67986-129">Requirements</span></span>  
 <span data-ttu-id="67986-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67986-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67986-131">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="67986-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="67986-132">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67986-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67986-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="67986-133">See also</span></span>

- [<span data-ttu-id="67986-134">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="67986-134">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

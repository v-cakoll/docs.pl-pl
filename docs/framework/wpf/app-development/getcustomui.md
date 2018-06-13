---
title: GetCustomUI
ms.date: 03/30/2017
helpviewer_keywords:
- custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
ms.openlocfilehash: ff68c30c4e58cebb70c59352593d7b084413dce8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548649"
---
# <a name="getcustomui"></a><span data-ttu-id="b2317-102">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="b2317-102">GetCustomUI</span></span>
<span data-ttu-id="b2317-103">Metoda wywoływana przez PresentationHost.exe można pobrać niestandardowych postęp i komunikaty o błędach z hosta, jeśli zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="b2317-103">Called by PresentationHost.exe to get custom progress and error messages from the host, if implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2317-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b2317-104">Syntax</span></span>  
  
```  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b2317-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b2317-105">Parameters</span></span>  
 `pwzProgressAssemblyName`  
  
 <span data-ttu-id="b2317-106">[out] Wskaźnik do zestawu, który zawiera interfejs użytkownika postępu hosta dostarczone.</span><span class="sxs-lookup"><span data-stu-id="b2317-106">[out] A pointer to the assembly that contains the host-supplied progress user interface.</span></span>  
  
 `pwzProgressClassName`  
  
 <span data-ttu-id="b2317-107">[out] Nazwa klasy, która najlepiej jest interfejs użytkownika postępu hosta dostarczone, [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] pliku z <xref:System.Windows.Controls.Page> jest jego element najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="b2317-107">[out] The name of the class that is the host-supplied progress user interface, preferably a [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="b2317-108">Ta klasa znajduje się w zestawie, który jest określony przez `pwzProgressAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="b2317-108">This class resides in the assembly that is specified by `pwzProgressAssemblyName`.</span></span>  
  
 `pwzErrorAssemblyName`  
  
 <span data-ttu-id="b2317-109">[out] Wskaźnik do zestawu zawierającego hosta dostarczone błąd interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b2317-109">[out] A pointer to the assembly that contains the host-supplied error user interface.</span></span>  
  
 `pwzErrorClassName`  
  
 <span data-ttu-id="b2317-110">[out] Nazwa klasy, która jest użytkownikiem hosta dostarczone błąd interfejsu, najlepiej plik XAML z <xref:System.Windows.Controls.Page> jest jego element najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="b2317-110">[out] The name of the class that is the host-supplied error user interface, preferably a XAML file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="b2317-111">Ta klasa znajduje się w zestawie, który jest określony przez `pwzErrorAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="b2317-111">This class resides in the assembly that is specified by `pwzErrorAssemblyName`.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="b2317-112">Wartość właściwości/Zwracana wartość</span><span class="sxs-lookup"><span data-stu-id="b2317-112">Property Value/Return Value</span></span>  
 <span data-ttu-id="b2317-113">Wynik HRESULT: ignorowane.</span><span class="sxs-lookup"><span data-stu-id="b2317-113">HRESULT: Ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2317-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b2317-114">Remarks</span></span>  
 <span data-ttu-id="b2317-115">Aplikacja hosta może mieć określonej motyw interfejsów użytkownika firmy PresentationHost.exe domyślny może nie być zgodne.</span><span class="sxs-lookup"><span data-stu-id="b2317-115">A host application may have a specific theme that PresentationHost.exe’s default user interfaces may not conform to.</span></span> <span data-ttu-id="b2317-116">Jeśli jest to możliwe, można wdrożyć aplikacji hosta [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) do zwrócenia postęp i błąd interfejsu użytkownika do PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="b2317-116">If this is the case, the host application can implement [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) to return progress and error user interfaces to PresentationHost.exe.</span></span> <span data-ttu-id="b2317-117">Zawsze spowoduje wywołanie PresentationHost.exe [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) przed użyciem jej interfejsów użytkownika domyślnego.</span><span class="sxs-lookup"><span data-stu-id="b2317-117">PresentationHost.exe will always call [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) before using its default user interfaces.</span></span>  
  
 <span data-ttu-id="b2317-118">Ta funkcja jest wywoływana raz podczas inicjowania PresentationHost firmy.</span><span class="sxs-lookup"><span data-stu-id="b2317-118">This function is called once during PresentationHost’s initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2317-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2317-119">See Also</span></span>  
 [<span data-ttu-id="b2317-120">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="b2317-120">IWpfHostSupport</span></span>](../../../../docs/framework/wpf/app-development/iwpfhostsupport.md)

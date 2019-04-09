---
title: GetCustomUI
ms.date: 03/30/2017
helpviewer_keywords:
- custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
ms.openlocfilehash: 30084143949d2243fd310448c52e6b861505ad66
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191253"
---
# <a name="getcustomui"></a><span data-ttu-id="8eabd-102">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="8eabd-102">GetCustomUI</span></span>
<span data-ttu-id="8eabd-103">Metoda wywoływana przez PresentationHost.exe można pobrać niestandardowych postępu i komunikaty o błędach z hosta, jeśli zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="8eabd-103">Called by PresentationHost.exe to get custom progress and error messages from the host, if implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8eabd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8eabd-104">Syntax</span></span>  
  
```  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
## <a name="parameters"></a><span data-ttu-id="8eabd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8eabd-105">Parameters</span></span>  
 `pwzProgressAssemblyName`  
  
 <span data-ttu-id="8eabd-106">[out] Wskaźnik do zestawu, który zawiera interfejs użytkownika postępu dostarczone z hosta.</span><span class="sxs-lookup"><span data-stu-id="8eabd-106">[out] A pointer to the assembly that contains the host-supplied progress user interface.</span></span>  
  
 `pwzProgressClassName`  
  
 <span data-ttu-id="8eabd-107">[out] Nazwa klasy, które jest dostarczone z hosta postępu interfejsu użytkownika, najlepiej [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] plik z <xref:System.Windows.Controls.Page> jest element najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="8eabd-107">[out] The name of the class that is the host-supplied progress user interface, preferably a [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="8eabd-108">Ta klasa znajduje się w zestawie, który jest określony przez `pwzProgressAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="8eabd-108">This class resides in the assembly that is specified by `pwzProgressAssemblyName`.</span></span>  
  
 `pwzErrorAssemblyName`  
  
 <span data-ttu-id="8eabd-109">[out] Wskaźnik do zestawu, który zawiera interfejs użytkownika błędzie dostarczony przez hosta.</span><span class="sxs-lookup"><span data-stu-id="8eabd-109">[out] A pointer to the assembly that contains the host-supplied error user interface.</span></span>  
  
 `pwzErrorClassName`  
  
 <span data-ttu-id="8eabd-110">[out] Nazwa klasy, która jest użytkownikiem błędzie dostarczony host interfejsu najlepiej plik XAML z <xref:System.Windows.Controls.Page> jest element najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="8eabd-110">[out] The name of the class that is the host-supplied error user interface, preferably a XAML file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="8eabd-111">Ta klasa znajduje się w zestawie, który jest określony przez `pwzErrorAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="8eabd-111">This class resides in the assembly that is specified by `pwzErrorAssemblyName`.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="8eabd-112">Wartość właściwości/Zwracana wartość</span><span class="sxs-lookup"><span data-stu-id="8eabd-112">Property Value/Return Value</span></span>  
 <span data-ttu-id="8eabd-113">HRESULT: Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="8eabd-113">HRESULT: Ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8eabd-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8eabd-114">Remarks</span></span>  
 <span data-ttu-id="8eabd-115">Aplikacja hosta może mieć określonych motyw, który interfejsy użytkownika domyślnego PresentationHost.exe firmy nie będą zgodne z.</span><span class="sxs-lookup"><span data-stu-id="8eabd-115">A host application may have a specific theme that PresentationHost.exe’s default user interfaces may not conform to.</span></span> <span data-ttu-id="8eabd-116">Jeśli jest to możliwe, aplikacja hosta można zaimplementować [getcustomui —](getcustomui.md) do zwrotu postęp oraz błąd interfejsy użytkownika PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="8eabd-116">If this is the case, the host application can implement [GetCustomUI](getcustomui.md) to return progress and error user interfaces to PresentationHost.exe.</span></span> <span data-ttu-id="8eabd-117">Zawsze spowoduje wywołanie PresentationHost.exe [getcustomui —](getcustomui.md) przed rozpoczęciem korzystania z jego interfejsów użytkownika domyślnego.</span><span class="sxs-lookup"><span data-stu-id="8eabd-117">PresentationHost.exe will always call [GetCustomUI](getcustomui.md) before using its default user interfaces.</span></span>  
  
 <span data-ttu-id="8eabd-118">Ta funkcja jest wywoływana jeden raz podczas inicjowania PresentationHost firmy.</span><span class="sxs-lookup"><span data-stu-id="8eabd-118">This function is called once during PresentationHost’s initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eabd-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8eabd-119">See also</span></span>

- [<span data-ttu-id="8eabd-120">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="8eabd-120">IWpfHostSupport</span></span>](iwpfhostsupport.md)

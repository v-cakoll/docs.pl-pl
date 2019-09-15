---
title: GetCustomUI
ms.date: 03/30/2017
helpviewer_keywords:
- custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
ms.openlocfilehash: a9c4c9d597f5cc1b172213d49a3dd5b8f1c1f671
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991377"
---
# <a name="getcustomui"></a><span data-ttu-id="ae1ec-102">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="ae1ec-102">GetCustomUI</span></span>
<span data-ttu-id="ae1ec-103">Wywoływane przez PresentationHost. exe w celu uzyskania niestandardowych postępów i komunikatów o błędach z hosta, jeśli zostały zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="ae1ec-103">Called by PresentationHost.exe to get custom progress and error messages from the host, if implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae1ec-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ae1ec-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae1ec-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ae1ec-105">Parameters</span></span>  
 `pwzProgressAssemblyName`  
  
 <span data-ttu-id="ae1ec-106">określoną Wskaźnik do zestawu, który zawiera interfejs użytkownika postępu dostarczonego przez hosta.</span><span class="sxs-lookup"><span data-stu-id="ae1ec-106">[out] A pointer to the assembly that contains the host-supplied progress user interface.</span></span>  
  
 `pwzProgressClassName`  
  
 <span data-ttu-id="ae1ec-107">określoną Nazwa klasy, która jest interfejsem użytkownika postępu dostarczonego przez hosta, najlepiej do [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] pliku z <xref:System.Windows.Controls.Page> jest elementem najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="ae1ec-107">[out] The name of the class that is the host-supplied progress user interface, preferably a [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="ae1ec-108">Ta klasa znajduje się w zestawie, który jest określony przez `pwzProgressAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="ae1ec-108">This class resides in the assembly that is specified by `pwzProgressAssemblyName`.</span></span>  
  
 `pwzErrorAssemblyName`  
  
 <span data-ttu-id="ae1ec-109">określoną Wskaźnik do zestawu, który zawiera interfejs użytkownika o błędzie dostarczonym przez hosta.</span><span class="sxs-lookup"><span data-stu-id="ae1ec-109">[out] A pointer to the assembly that contains the host-supplied error user interface.</span></span>  
  
 `pwzErrorClassName`  
  
 <span data-ttu-id="ae1ec-110">określoną Nazwa klasy, która jest interfejsem użytkownika o błędzie dostarczonym przez hosta, najlepiej do pliku XAML z <xref:System.Windows.Controls.Page> jest jego elementem najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="ae1ec-110">[out] The name of the class that is the host-supplied error user interface, preferably a XAML file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="ae1ec-111">Ta klasa znajduje się w zestawie, który jest określony przez `pwzErrorAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="ae1ec-111">This class resides in the assembly that is specified by `pwzErrorAssemblyName`.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="ae1ec-112">Wartość właściwości/Zwracana wartość</span><span class="sxs-lookup"><span data-stu-id="ae1ec-112">Property Value/Return Value</span></span>  
 <span data-ttu-id="ae1ec-113">WYNIK Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="ae1ec-113">HRESULT: Ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae1ec-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ae1ec-114">Remarks</span></span>  
 <span data-ttu-id="ae1ec-115">Aplikacja hosta może mieć określony motyw, który PresentationHost. exe domyślne interfejsy użytkownika mogą nie być zgodne.</span><span class="sxs-lookup"><span data-stu-id="ae1ec-115">A host application may have a specific theme that PresentationHost.exe’s default user interfaces may not conform to.</span></span> <span data-ttu-id="ae1ec-116">W takim przypadku aplikacja hosta może zaimplementować [GetCustomUI](getcustomui.md) , aby zwracać interfejs użytkownika postępu i błędów do PresentationHost. exe.</span><span class="sxs-lookup"><span data-stu-id="ae1ec-116">If this is the case, the host application can implement [GetCustomUI](getcustomui.md) to return progress and error user interfaces to PresentationHost.exe.</span></span> <span data-ttu-id="ae1ec-117">PresentationHost. exe zawsze będzie wywoływał [GetCustomUI](getcustomui.md) przed użyciem jego domyślnych interfejsów użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ae1ec-117">PresentationHost.exe will always call [GetCustomUI](getcustomui.md) before using its default user interfaces.</span></span>  
  
 <span data-ttu-id="ae1ec-118">Ta funkcja jest wywoływana raz podczas inicjowania PresentationHost.</span><span class="sxs-lookup"><span data-stu-id="ae1ec-118">This function is called once during PresentationHost’s initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae1ec-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ae1ec-119">See also</span></span>

- [<span data-ttu-id="ae1ec-120">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="ae1ec-120">IWpfHostSupport</span></span>](iwpfhostsupport.md)

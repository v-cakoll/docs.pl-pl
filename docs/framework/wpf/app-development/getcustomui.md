---
title: GetCustomUI
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3f3c101ad13df9b99a2d872bac8783baed8b4b9a
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="getcustomui"></a><span data-ttu-id="434f9-102">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="434f9-102">GetCustomUI</span></span>
<span data-ttu-id="434f9-103">Metoda wywoływana przez PresentationHost.exe można pobrać niestandardowych postęp i komunikaty o błędach z hosta, jeśli zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="434f9-103">Called by PresentationHost.exe to get custom progress and error messages from the host, if implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="434f9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="434f9-104">Syntax</span></span>  
  
```  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="434f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="434f9-105">Parameters</span></span>  
 `pwzProgressAssemblyName`  
  
 <span data-ttu-id="434f9-106">[out] Wskaźnik do zestawu, który zawiera interfejs użytkownika postępu hosta dostarczone.</span><span class="sxs-lookup"><span data-stu-id="434f9-106">[out] A pointer to the assembly that contains the host-supplied progress user interface.</span></span>  
  
 `pwzProgressClassName`  
  
 <span data-ttu-id="434f9-107">[out] Nazwa klasy, która najlepiej jest interfejs użytkownika postępu hosta dostarczone, [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] pliku z <xref:System.Windows.Controls.Page> jest jego element najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="434f9-107">[out] The name of the class that is the host-supplied progress user interface, preferably a [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="434f9-108">Ta klasa znajduje się w zestawie, który jest określony przez `pwzProgressAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="434f9-108">This class resides in the assembly that is specified by `pwzProgressAssemblyName`.</span></span>  
  
 `pwzErrorAssemblyName`  
  
 <span data-ttu-id="434f9-109">[out] Wskaźnik do zestawu zawierającego hosta dostarczone błąd interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="434f9-109">[out] A pointer to the assembly that contains the host-supplied error user interface.</span></span>  
  
 `pwzErrorClassName`  
  
 <span data-ttu-id="434f9-110">[out] Nazwa klasy, która jest użytkownikiem hosta dostarczone błąd interfejsu, najlepiej plik XAML z <xref:System.Windows.Controls.Page> jest jego element najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="434f9-110">[out] The name of the class that is the host-supplied error user interface, preferably a XAML file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="434f9-111">Ta klasa znajduje się w zestawie, który jest określony przez `pwzErrorAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="434f9-111">This class resides in the assembly that is specified by `pwzErrorAssemblyName`.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="434f9-112">Wartość właściwości/Zwracana wartość</span><span class="sxs-lookup"><span data-stu-id="434f9-112">Property Value/Return Value</span></span>  
 <span data-ttu-id="434f9-113">Wynik HRESULT: ignorowane.</span><span class="sxs-lookup"><span data-stu-id="434f9-113">HRESULT: Ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="434f9-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="434f9-114">Remarks</span></span>  
 <span data-ttu-id="434f9-115">Aplikacja hosta może mieć określonej motyw interfejsów użytkownika firmy PresentationHost.exe domyślny może nie być zgodne.</span><span class="sxs-lookup"><span data-stu-id="434f9-115">A host application may have a specific theme that PresentationHost.exe’s default user interfaces may not conform to.</span></span> <span data-ttu-id="434f9-116">Jeśli jest to możliwe, można wdrożyć aplikacji hosta [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) do zwrócenia postęp i błąd interfejsu użytkownika do PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="434f9-116">If this is the case, the host application can implement [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) to return progress and error user interfaces to PresentationHost.exe.</span></span> <span data-ttu-id="434f9-117">Zawsze spowoduje wywołanie PresentationHost.exe [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) przed użyciem jej interfejsów użytkownika domyślnego.</span><span class="sxs-lookup"><span data-stu-id="434f9-117">PresentationHost.exe will always call [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) before using its default user interfaces.</span></span>  
  
 <span data-ttu-id="434f9-118">Ta funkcja jest wywoływana raz podczas inicjowania PresentationHost firmy.</span><span class="sxs-lookup"><span data-stu-id="434f9-118">This function is called once during PresentationHost’s initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="434f9-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="434f9-119">See Also</span></span>  
 [<span data-ttu-id="434f9-120">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="434f9-120">IWpfHostSupport</span></span>](../../../../docs/framework/wpf/app-development/iwpfhostsupport.md)

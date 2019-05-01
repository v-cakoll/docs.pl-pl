---
title: x:Reference — Rozszerzenie znaczników
ms.date: 03/30/2017
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
ms.openlocfilehash: 960f5c0e4192df72090c1a571dfc2fc5e3fd8ba3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938882"
---
# <a name="xreference-markup-extension"></a><span data-ttu-id="8b76b-102">x:Reference — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="8b76b-102">x:Reference Markup Extension</span></span>
<span data-ttu-id="8b76b-103">Odwołuje się do wystąpienia, która jest zadeklarowana w innym miejscu w znaczniku XAML.</span><span class="sxs-lookup"><span data-stu-id="8b76b-103">References an instance that is declared elsewhere in XAML markup.</span></span> <span data-ttu-id="8b76b-104">Odwołania, który odwołuje się do elementu `x:Name`.</span><span class="sxs-lookup"><span data-stu-id="8b76b-104">The reference refers to an element's `x:Name`.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="8b76b-105">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="8b76b-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Reference instancexName}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="8b76b-106">Użycie elementu obiektu języka XAML</span><span class="sxs-lookup"><span data-stu-id="8b76b-106">XAML Object Element Usage</span></span>  
  
```xaml  
<object>  
  <object.property>  
    <x:Reference Name="instancexName"/>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="8b76b-107">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="8b76b-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`instancexName`|<span data-ttu-id="8b76b-108">`x:Name` Wartość (lub wartość <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>— określone właściwości) wystąpienia odwołania.</span><span class="sxs-lookup"><span data-stu-id="8b76b-108">The `x:Name` value (or value of the <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-identified property) of the referenced instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b76b-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8b76b-109">Remarks</span></span>  
 <span data-ttu-id="8b76b-110">`x:Reference` zapewnia wsparcie poziomu języka XAML dla koncepcji odwołanie do elementu, który został wdrożony w przeciwnym razie określonych platform, takich jak WPF.</span><span class="sxs-lookup"><span data-stu-id="8b76b-110">`x:Reference` provides XAML language-level support for an element reference concept that was otherwise implemented in specific frameworks such as WPF.</span></span>  
  
## <a name="xreference-and-wpf"></a><span data-ttu-id="8b76b-111">x: Reference i WPF</span><span class="sxs-lookup"><span data-stu-id="8b76b-111">x:Reference and WPF</span></span>  
 <span data-ttu-id="8b76b-112">WPF i XAML 2006, odwołania do elementu są rozwiązywane przez funkcję poziomie struktury <xref:System.Windows.Data.Binding.ElementName%2A> powiązania.</span><span class="sxs-lookup"><span data-stu-id="8b76b-112">In WPF and XAML 2006, element references are addressed by the framework-level feature of <xref:System.Windows.Data.Binding.ElementName%2A> binding.</span></span> <span data-ttu-id="8b76b-113">Dla większości aplikacji WPF i scenariuszy <xref:System.Windows.Data.Binding.ElementName%2A> nadal należy używać powiązania.</span><span class="sxs-lookup"><span data-stu-id="8b76b-113">For most WPF applications and scenarios, <xref:System.Windows.Data.Binding.ElementName%2A> binding should still be used.</span></span> <span data-ttu-id="8b76b-114">Wyjątki od tej ogólne wskazówki mogą obejmować przypadki, w przypadku, gdy istnieją kontekstu danych lub inne zagadnienia zakresu, wchodzące niepraktyczne powiązanie danych oraz znaczników kompilacji nie jest zaangażowana.</span><span class="sxs-lookup"><span data-stu-id="8b76b-114">Exceptions to this general guidance might include cases where there are data context or other scoping considerations that make data binding impractical and where markup compilation is not involved.</span></span>  
  
 <span data-ttu-id="8b76b-115">`x:Reference` konstrukcja zdefiniowano w XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="8b76b-115">`x:Reference` is a construct defined in XAML 2009.</span></span> <span data-ttu-id="8b76b-116">W środowisku WPF można użyć funkcji XAML 2009, ale tylko dla XAML, który nie jest kompilowana do znaczników WPF.</span><span class="sxs-lookup"><span data-stu-id="8b76b-116">In WPF, you can use XAML 2009 features, but only for XAML that is not WPF markup-compiled.</span></span> <span data-ttu-id="8b76b-117">XAML kompilowana do znaczników i formularz BAML XAML aktualnie nie obsługuje słowa kluczowe języka XAML 2009 oraz funkcje.</span><span class="sxs-lookup"><span data-stu-id="8b76b-117">Markup-compiled XAML and the BAML form of XAML do not currently support the XAML 2009 language keywords and features.</span></span>

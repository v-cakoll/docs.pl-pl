---
title: x:Reference — Rozszerzenie znaczników
ms.date: 03/30/2017
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
ms.openlocfilehash: 960f5c0e4192df72090c1a571dfc2fc5e3fd8ba3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562248"
---
# <a name="xreference-markup-extension"></a><span data-ttu-id="5917f-102">x:Reference — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="5917f-102">x:Reference Markup Extension</span></span>
<span data-ttu-id="5917f-103">Odwołuje się do wystąpienia, która jest zadeklarowana w innym miejscu w kodzie XAML.</span><span class="sxs-lookup"><span data-stu-id="5917f-103">References an instance that is declared elsewhere in XAML markup.</span></span> <span data-ttu-id="5917f-104">Odwołanie odwołuje się do elementu `x:Name`.</span><span class="sxs-lookup"><span data-stu-id="5917f-104">The reference refers to an element's `x:Name`.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="5917f-105">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="5917f-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Reference instancexName}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="5917f-106">Użycie elementu obiektu języka XAML</span><span class="sxs-lookup"><span data-stu-id="5917f-106">XAML Object Element Usage</span></span>  
  
```xaml  
<object>  
  <object.property>  
    <x:Reference Name="instancexName"/>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="5917f-107">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="5917f-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`instancexName`|<span data-ttu-id="5917f-108">`x:Name` Wartości (lub wartość <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>— określone właściwości) wystąpienia, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="5917f-108">The `x:Name` value (or value of the <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-identified property) of the referenced instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5917f-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5917f-109">Remarks</span></span>  
 <span data-ttu-id="5917f-110">`x:Reference` zapewnia obsługę poziom języka XAML dla koncepcji odwołanie do elementu, który został wdrożony w innym przypadku określonych platform, takich jak WPF.</span><span class="sxs-lookup"><span data-stu-id="5917f-110">`x:Reference` provides XAML language-level support for an element reference concept that was otherwise implemented in specific frameworks such as WPF.</span></span>  
  
## <a name="xreference-and-wpf"></a><span data-ttu-id="5917f-111">x: Reference i WPF</span><span class="sxs-lookup"><span data-stu-id="5917f-111">x:Reference and WPF</span></span>  
 <span data-ttu-id="5917f-112">WPF i XAML 2006 odwołuje się do elementu dotyczą funkcji poziomie struktury <xref:System.Windows.Data.Binding.ElementName%2A> powiązania.</span><span class="sxs-lookup"><span data-stu-id="5917f-112">In WPF and XAML 2006, element references are addressed by the framework-level feature of <xref:System.Windows.Data.Binding.ElementName%2A> binding.</span></span> <span data-ttu-id="5917f-113">Dla większości środowisk i aplikacje WPF <xref:System.Windows.Data.Binding.ElementName%2A> powiązania nadal powinien być używany.</span><span class="sxs-lookup"><span data-stu-id="5917f-113">For most WPF applications and scenarios, <xref:System.Windows.Data.Binding.ElementName%2A> binding should still be used.</span></span> <span data-ttu-id="5917f-114">Wyjątki od tej ogólnych wytycznych mogą obejmować przypadków, w przypadku, gdy istnieją kontekstu danych lub innych kwestii zakresu, które należy niepraktyczne powiązania danych, a nie uczestniczy kompilację znaczników.</span><span class="sxs-lookup"><span data-stu-id="5917f-114">Exceptions to this general guidance might include cases where there are data context or other scoping considerations that make data binding impractical and where markup compilation is not involved.</span></span>  
  
 <span data-ttu-id="5917f-115">`x:Reference` konstrukcję jest zdefiniowany w języku XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="5917f-115">`x:Reference` is a construct defined in XAML 2009.</span></span> <span data-ttu-id="5917f-116">Na platformie WPF można użyć XAML 2009 — funkcje, ale tylko dla języka XAML, która nie jest skompilowany znaczników WPF.</span><span class="sxs-lookup"><span data-stu-id="5917f-116">In WPF, you can use XAML 2009 features, but only for XAML that is not WPF markup-compiled.</span></span> <span data-ttu-id="5917f-117">Aktualnie kompilacji znaczników XAML i BAML formę XAML nie obsługują słów kluczowych języka XAML 2009 i funkcje.</span><span class="sxs-lookup"><span data-stu-id="5917f-117">Markup-compiled XAML and the BAML form of XAML do not currently support the XAML 2009 language keywords and features.</span></span>

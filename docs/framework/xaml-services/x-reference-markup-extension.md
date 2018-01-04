---
title: "x:Reference — Rozszerzenie znaczników"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 03b63cb40e57223d5c66c03fb60780689cd6c925
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="xreference-markup-extension"></a><span data-ttu-id="b62b4-102">x:Reference — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="b62b4-102">x:Reference Markup Extension</span></span>
<span data-ttu-id="b62b4-103">Odwołuje się do wystąpienia, która jest zadeklarowana w innym miejscu w kodzie XAML.</span><span class="sxs-lookup"><span data-stu-id="b62b4-103">References an instance that is declared elsewhere in XAML markup.</span></span> <span data-ttu-id="b62b4-104">Odwołanie odwołuje się do elementu `x:Name`.</span><span class="sxs-lookup"><span data-stu-id="b62b4-104">The reference refers to an element's `x:Name`.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="b62b4-105">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="b62b4-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Reference instancexName}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="b62b4-106">Użycie elementu obiektu języka XAML</span><span class="sxs-lookup"><span data-stu-id="b62b4-106">XAML Object Element Usage</span></span>  
  
```xaml  
<object>  
  <object.property>  
    <x:Reference Name="instancexName"/>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="b62b4-107">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="b62b4-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`instancexName`|<span data-ttu-id="b62b4-108">`x:Name` Wartości (lub wartość <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>— określone właściwości) wystąpienia, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="b62b4-108">The `x:Name` value (or value of the <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-identified property) of the referenced instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b62b4-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b62b4-109">Remarks</span></span>  
 <span data-ttu-id="b62b4-110">`x:Reference`zapewnia obsługę poziom języka XAML dla koncepcji odwołanie do elementu, który został wdrożony w innym przypadku określonych platform, takich jak WPF.</span><span class="sxs-lookup"><span data-stu-id="b62b4-110">`x:Reference` provides XAML language-level support for an element reference concept that was otherwise implemented in specific frameworks such as WPF.</span></span>  
  
## <a name="xreference-and-wpf"></a><span data-ttu-id="b62b4-111">x: Reference i WPF</span><span class="sxs-lookup"><span data-stu-id="b62b4-111">x:Reference and WPF</span></span>  
 <span data-ttu-id="b62b4-112">WPF i XAML 2006 odwołuje się do elementu dotyczą funkcji poziomie struktury <xref:System.Windows.Data.Binding.ElementName%2A> powiązania.</span><span class="sxs-lookup"><span data-stu-id="b62b4-112">In WPF and XAML 2006, element references are addressed by the framework-level feature of <xref:System.Windows.Data.Binding.ElementName%2A> binding.</span></span> <span data-ttu-id="b62b4-113">Dla większości środowisk i aplikacje WPF <xref:System.Windows.Data.Binding.ElementName%2A> powiązania nadal powinien być używany.</span><span class="sxs-lookup"><span data-stu-id="b62b4-113">For most WPF applications and scenarios, <xref:System.Windows.Data.Binding.ElementName%2A> binding should still be used.</span></span> <span data-ttu-id="b62b4-114">Wyjątki od tej ogólnych wytycznych mogą obejmować przypadków, w przypadku, gdy istnieją kontekstu danych lub innych kwestii zakresu, które należy niepraktyczne powiązania danych, a nie uczestniczy kompilację znaczników.</span><span class="sxs-lookup"><span data-stu-id="b62b4-114">Exceptions to this general guidance might include cases where there are data context or other scoping considerations that make data binding impractical and where markup compilation is not involved.</span></span>  
  
 <span data-ttu-id="b62b4-115">`x:Reference`konstrukcję jest zdefiniowany w języku XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="b62b4-115">`x:Reference` is a construct defined in XAML 2009.</span></span> <span data-ttu-id="b62b4-116">Na platformie WPF można użyć XAML 2009 — funkcje, ale tylko dla języka XAML, która nie jest skompilowany znaczników WPF.</span><span class="sxs-lookup"><span data-stu-id="b62b4-116">In WPF, you can use XAML 2009 features, but only for XAML that is not WPF markup-compiled.</span></span> <span data-ttu-id="b62b4-117">Aktualnie kompilacji znaczników XAML i BAML formę XAML nie obsługują słów kluczowych języka XAML 2009 i funkcje.</span><span class="sxs-lookup"><span data-stu-id="b62b4-117">Markup-compiled XAML and the BAML form of XAML do not currently support the XAML 2009 language keywords and features.</span></span>

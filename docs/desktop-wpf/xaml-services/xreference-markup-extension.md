---
title: x:Reference — Rozszerzenie znaczników
ms.date: 03/30/2017
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
ms.openlocfilehash: f06e259893111a436e5afe2df754c3edee326d54
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071382"
---
# <a name="xreference-markup-extension"></a><span data-ttu-id="9adf7-102">x:Reference — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="9adf7-102">x:Reference Markup Extension</span></span>

<span data-ttu-id="9adf7-103">Odwołuje się do wystąpienia, które jest zadeklarowane w innym miejscu znaczników XAML.</span><span class="sxs-lookup"><span data-stu-id="9adf7-103">References an instance that is declared elsewhere in XAML markup.</span></span> <span data-ttu-id="9adf7-104">Odwołanie odnosi się do elementu `x:Name`.</span><span class="sxs-lookup"><span data-stu-id="9adf7-104">The reference refers to an element's `x:Name`.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="9adf7-105">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="9adf7-105">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Reference instancexName}" .../>
```

## <a name="xaml-object-element-usage"></a><span data-ttu-id="9adf7-106">Użycie elementu obiektu języka XAML</span><span class="sxs-lookup"><span data-stu-id="9adf7-106">XAML Object Element Usage</span></span>

```xaml
<object>
  <object.property>
    <x:Reference Name="instancexName"/>
  </object.property>
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="9adf7-107">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="9adf7-107">XAML Values</span></span>

|||
|-|-|
|`instancexName`|<span data-ttu-id="9adf7-108">Wartość `x:Name` (lub wartość <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>właściwości -identified) wystąpienia, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="9adf7-108">The `x:Name` value (or value of the <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-identified property) of the referenced instance.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9adf7-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9adf7-109">Remarks</span></span>

<span data-ttu-id="9adf7-110">`x:Reference`zapewnia obsługę na poziomie języka XAML dla koncepcji odwołania do elementu, która została w przeciwnym razie zaimplementowana w określonych ramach, takich jak WPF.</span><span class="sxs-lookup"><span data-stu-id="9adf7-110">`x:Reference` provides XAML language-level support for an element reference concept that was otherwise implemented in specific frameworks such as WPF.</span></span>

## <a name="xreference-and-wpf"></a><span data-ttu-id="9adf7-111">x:Odwołanie i WPF</span><span class="sxs-lookup"><span data-stu-id="9adf7-111">x:Reference and WPF</span></span>

<span data-ttu-id="9adf7-112">W WPF WPF I XAML 2006 odwołania do elementów są adresowane przez funkcję na poziomie struktury <xref:System.Windows.Data.Binding.ElementName%2A> powiązania.</span><span class="sxs-lookup"><span data-stu-id="9adf7-112">In WPF and XAML 2006, element references are addressed by the framework-level feature of <xref:System.Windows.Data.Binding.ElementName%2A> binding.</span></span> <span data-ttu-id="9adf7-113">W przypadku większości aplikacji i <xref:System.Windows.Data.Binding.ElementName%2A> scenariuszy WPF powiązanie powinno być nadal używane.</span><span class="sxs-lookup"><span data-stu-id="9adf7-113">For most WPF applications and scenarios, <xref:System.Windows.Data.Binding.ElementName%2A> binding should still be used.</span></span> <span data-ttu-id="9adf7-114">Wyjątki od tych ogólnych wskazówek mogą obejmować przypadki, w których istnieją kontekst danych lub inne zagadnienia dotyczące zakresu, które sprawiają, że powiązanie danych jest niepraktyczne i w których kompilacja znaczników nie jest zaangażowana.</span><span class="sxs-lookup"><span data-stu-id="9adf7-114">Exceptions to this general guidance might include cases where there are data context or other scoping considerations that make data binding impractical and where markup compilation is not involved.</span></span>

<span data-ttu-id="9adf7-115">`x:Reference`jest konstrukcją zdefiniowaną w XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="9adf7-115">`x:Reference` is a construct defined in XAML 2009.</span></span> <span data-ttu-id="9adf7-116">W WPF WPF można użyć funkcji XAML 2009, ale tylko dla XAML, który nie jest Skompilowany znaczników WPF.</span><span class="sxs-lookup"><span data-stu-id="9adf7-116">In WPF, you can use XAML 2009 features, but only for XAML that is not WPF markup-compiled.</span></span> <span data-ttu-id="9adf7-117">Markup-skompilowany XAML i BAML formie XAML obecnie nie obsługują XAML 2009 słowa kluczowe i funkcje języka.</span><span class="sxs-lookup"><span data-stu-id="9adf7-117">Markup-compiled XAML and the BAML form of XAML do not currently support the XAML 2009 language keywords and features.</span></span>

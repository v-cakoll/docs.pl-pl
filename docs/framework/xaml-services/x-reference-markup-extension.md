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
# <a name="xreference-markup-extension"></a>x:Reference — Rozszerzenie znaczników
Odwołuje się do wystąpienia, która jest zadeklarowana w innym miejscu w znaczniku XAML. Odwołania, który odwołuje się do elementu `x:Name`.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object property="{x:Reference instancexName}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>Użycie elementu obiektu języka XAML  
  
```xaml  
<object>  
  <object.property>  
    <x:Reference Name="instancexName"/>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`instancexName`|`x:Name` Wartość (lub wartość <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>— określone właściwości) wystąpienia odwołania.|  
  
## <a name="remarks"></a>Uwagi  
 `x:Reference` zapewnia wsparcie poziomu języka XAML dla koncepcji odwołanie do elementu, który został wdrożony w przeciwnym razie określonych platform, takich jak WPF.  
  
## <a name="xreference-and-wpf"></a>x: Reference i WPF  
 WPF i XAML 2006, odwołania do elementu są rozwiązywane przez funkcję poziomie struktury <xref:System.Windows.Data.Binding.ElementName%2A> powiązania. Dla większości aplikacji WPF i scenariuszy <xref:System.Windows.Data.Binding.ElementName%2A> nadal należy używać powiązania. Wyjątki od tej ogólne wskazówki mogą obejmować przypadki, w przypadku, gdy istnieją kontekstu danych lub inne zagadnienia zakresu, wchodzące niepraktyczne powiązanie danych oraz znaczników kompilacji nie jest zaangażowana.  
  
 `x:Reference` konstrukcja zdefiniowano w XAML 2009. W środowisku WPF można użyć funkcji XAML 2009, ale tylko dla XAML, który nie jest kompilowana do znaczników WPF. XAML kompilowana do znaczników i formularz BAML XAML aktualnie nie obsługuje słowa kluczowe języka XAML 2009 oraz funkcje.

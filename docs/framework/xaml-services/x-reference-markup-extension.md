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
# <a name="xreference-markup-extension"></a>x:Reference — Rozszerzenie znaczników
Odwołuje się do wystąpienia, która jest zadeklarowana w innym miejscu w kodzie XAML. Odwołanie odwołuje się do elementu `x:Name`.  
  
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
|`instancexName`|`x:Name` Wartości (lub wartość <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>— określone właściwości) wystąpienia, do którego istnieje odwołanie.|  
  
## <a name="remarks"></a>Uwagi  
 `x:Reference` zapewnia obsługę poziom języka XAML dla koncepcji odwołanie do elementu, który został wdrożony w innym przypadku określonych platform, takich jak WPF.  
  
## <a name="xreference-and-wpf"></a>x: Reference i WPF  
 WPF i XAML 2006 odwołuje się do elementu dotyczą funkcji poziomie struktury <xref:System.Windows.Data.Binding.ElementName%2A> powiązania. Dla większości środowisk i aplikacje WPF <xref:System.Windows.Data.Binding.ElementName%2A> powiązania nadal powinien być używany. Wyjątki od tej ogólnych wytycznych mogą obejmować przypadków, w przypadku, gdy istnieją kontekstu danych lub innych kwestii zakresu, które należy niepraktyczne powiązania danych, a nie uczestniczy kompilację znaczników.  
  
 `x:Reference` konstrukcję jest zdefiniowany w języku XAML 2009. Na platformie WPF można użyć XAML 2009 — funkcje, ale tylko dla języka XAML, która nie jest skompilowany znaczników WPF. Aktualnie kompilacji znaczników XAML i BAML formę XAML nie obsługują słów kluczowych języka XAML 2009 i funkcje.

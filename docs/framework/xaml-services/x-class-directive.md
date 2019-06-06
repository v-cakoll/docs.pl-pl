---
title: x:Class — dyrektywa
ms.date: 03/30/2017
f1_keywords:
- x:Class
- xClass
- Class
helpviewer_keywords:
- Class attribute in XAML [XAML Services]
- XAML [XAML Services], x:Class attribute
- x:Class attribute [XAML Services]
ms.assetid: bc4a3d8e-76e2-423e-a5d1-159a023e82ec
ms.openlocfilehash: ee94d7bf52f3fb2ea534cdb2f44d0be2cc8699eb
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2019
ms.locfileid: "66689414"
---
# <a name="xclass-directive"></a>x:Class — dyrektywa
Służy do konfigurowania kompilacji znaczników XAML do dołączenia do klas częściowych między znaczników i związane z kodem. Klasy częściowe kod jest zdefiniowany w osobnym pliku kodu w [!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)] języka, natomiast klasy częściowej znaczników jest zwykle tworzony przy generowanie kodu podczas kompilacji XAML.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```  
<object x:Class="namespace.classname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`namespace`|Opcjonalna. Określa [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] przestrzeń nazw zawierająca identyfikowane za pomocą klasy częściowej `classname`. Jeśli `namespace` określono pojedynczego znaku kropki (.) oddziela `namespace` i `classname`. Zobacz uwagi.|  
|`classname`|Wymagana. Określa [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] nazwa częściową klasą, która łączy XAML załadowane i usługi związane z kodem dla tego XAML.|  
  
## <a name="dependencies"></a>Zależności  
 `x:Class` można określić tylko dla elementu głównego produkcji XAML. `x:Class` jest nieprawidłowy dla dowolnego obiektu, który ma element nadrzędny w środowisku produkcyjnym XAML. Aby uzyskać więcej informacji, zobacz [ \[MS-XAML\] sekcji 4.3.1.6](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="remarks"></a>Uwagi  
 `namespace` Wartość może zawierać dodatkowe kropki w celu zorganizowania pokrewne obszary nazw Nazwa hierarchii, co jest typową techniką w programowaniu .NET Framework. Tylko ostatni kropki (.) w ciągu `x:Class` wartości jest interpretowany do oddzielania `namespace` i `classname.` klasy, która jest używana jako `x:Class` nie może być klasą zagnieżdżoną. Klasy zagnieżdżone nie są dozwolone, ponieważ określanie znaczenie kropki dla `x:Class` ciągów jest niejednoznaczny, jeżeli klasy zagnieżdżone są dozwolone.  
  
 W istniejących modeli, które używają programowania `x:Class`, `x:Class` jest opcjonalny w tym sensie, jest całkowicie umożliwiającego strona XAML ma nie związanym z kodem. Jednak taką możliwość interakcji z akcji kompilacji jako implementowany przez struktur, które używają XAML. `x:Class` możliwość ma również wpływ ról, że różne klasyfikacje zawartości XAML, określone w modelu aplikacji i w odpowiednich akcji kompilowania. Jeśli Twoje XAML deklaruje atrybutu obsługi zdarzeń wartości lub tworzy niestandardowe elementy, których definiowanie klas w klasie CodeBehind, musisz podać `x:Class` dyrektywy odwołania (lub [x: Subclass](x-subclass-directive.md)) do Klasa odpowiednie związanym z kodem.  
  
 Wartość `x:Class` dyrektywa musi być ciąg, który określa w pełni kwalifikowana nazwa klasy, ale bez żadnych informacji zestawu (równoważne <xref:System.Type.FullName%2A?displayProperty=nameWithType>). Dla prostej aplikacji można pominąć informacje o przestrzeni nazw CLR, jeśli również mają strukturę kodu powiązanego w ten sposób (rozpoczęcie definicji kodu na poziomie klasy).  
  
 Plik związany z kodem dla definicji strona lub aplikacja musi być w pliku kodu, który wchodzi w skład projektu, który tworzy skompilowaną aplikację i obejmuje kompilacji znaczników. Nazwa reguły dla klas CLR muszą być zgodne. Aby uzyskać więcej informacji, zobacz [wytyczne dotyczące projektowania Framework](../../standard/design-guidelines/index.md). Domyślnie klasa związanym z kodem musi być `public`; Jednakże, można zdefiniować na poziomie różny dostęp za pomocą [x: classmodifier — dyrektywa](x-classmodifier-directive.md).  
  
 Interpretacja tego `x:Class` atrybut ma zastosowanie tylko do wykonania na podstawie CLR XAML, w szczególności do usług programu .NET Framework XAML. Inne implementacje XAML, które nie są oparte na CLR, które nie korzystają z usług programu .NET Framework XAML może użyć formuły innego rozwiązania do łączenia znaczników XAML i kodu w czasie wykonywania kopii. Aby uzyskać więcej informacji na temat interpretacji bardziej ogólnych `x:Class`, zobacz [ \[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
 Na poziomie architekturę, znaczenie `x:Class` nie jest zdefiniowana w .NET Framework XAML Services. Jest to spowodowane usług programu .NET Framework XAML nie określono modelu programowania, XAML, które są połączone znaczników i kopii kodu. Zastosowań dodatkowe `x:Class` dyrektywa może być implementowana przez określonych platform, korzystające z modeli programowania lub modeli aplikacji do definiowania sposobu łączenia znaczników XAML i na podstawie CLR związane z kodem. Każdej struktury mogą mieć własne działania kompilacji, umożliwiające niektóre zachowania lub określonych składników, które muszą być zawarte w środowisku kompilacji. W ramach akcji kompilacji może być różny w zależności od określonego języka środowiska CLR, używany do związanym z kodem.  
  
## <a name="xclass-in-the-wpf-programming-model"></a>x: Class w modelu programowania WPF  
 W aplikacjach WPF i modelu aplikacji WPF `x:Class` mogą być deklarowane jako atrybutu dla każdego elementu głównego pliku XAML, który jest kompilowany (gdzie XAML znajduje się w projekcie aplikacji WPF przy użyciu `Page` Akcja kompilacji), lub < C4 > <xref:System.Windows.Application>  główny urząd certyfikacji w definicji aplikacji skompilowanej aplikacji WPF. Deklarowanie `x:Class` na element inny niż główny strony lub katalog główny aplikacji lub w pliku XAML w WPF, która nie jest kompilowana, powoduje błąd kompilacji w ramach [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)] i kompilator platformy .NET Framework 3.5 WPF XAML. Aby uzyskać informacje o innych aspektów `x:Class` obsługi na platformie WPF, zobacz [związanym z kodem i XAML w WPF](../wpf/advanced/code-behind-and-xaml-in-wpf.md).  
  
## <a name="xclass-for-windows-workflow-foundation"></a>x: Class dla programu Windows Workflow Foundation  
 Dla programu Windows Workflow Foundation `x:Class` nazwy klasy niestandardowe działanie składające się wyłącznie w XAML lub nazwy klasy częściowej strony XAML w Projektancie działanie z kodem.  
  
## <a name="silverlight-usage-notes"></a>Uwagi dotyczące użytkowania Silverlight  
 `x:Class` dla programu Silverlight jest opisane osobno. Aby uzyskać więcej informacji, zobacz [Namespace XAML (x:) Funkcje języka (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Zobacz także

- [x:Subclass, dyrektywa](x-subclass-directive.md)
- [Klasy XAML i niestandardowe dla WPF](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [x:ClassModifier, dyrektywa](x-classmodifier-directive.md)
- [Typy migrowane z WPF do System.Xaml](types-migrated-from-wpf-to-system-xaml.md)

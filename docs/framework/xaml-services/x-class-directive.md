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
ms.openlocfilehash: 7e6a2379640d2556b553d14d20398a0a14931393
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566811"
---
# <a name="xclass-directive"></a>x:Class — dyrektywa
Konfiguruje kompilację znaczników XAML, aby dołączyć klasy częściowe między znaczników i związane z kodem. Klasy częściowe kod jest zdefiniowany w osobnym pliku kodu w [!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)] języka, podczas gdy klasy częściowej znaczników jest zwykle tworzony przy generowania kodu podczas kompilacji XAML.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```  
<object x:Class="namespace.classname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`namespace`|Opcjonalna. Określa [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] przestrzeń nazw zawiera klasy częściowej identyfikowane przez `classname`. Jeśli `namespace` określono kropkę (.) oddziela `namespace` i `classname`. Zobacz uwagi.|  
|`classname`|Wymagana. Określa [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] nazwa częściowej klasy, która łączy załadować XAML i z kodem dla tego języka XAML.|  
  
## <a name="dependencies"></a>Zależności  
 `x:Class` można określić tylko dla elementu głównego XAML produkcji. `x:Class` jest nieprawidłowy w każdym obiekcie, który ma element nadrzędny w środowisku produkcyjnym XAML. Aby uzyskać więcej informacji, zobacz [ \[MS XAML\] sekcji 4.3.1.6](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="remarks"></a>Uwagi  
 `namespace` Wartość może zawierać dodatkowe punkty organizowania pokrewne przestrzeni nazw w hierarchii nazwa czyli technikę typowe w programowaniu .NET Framework. Tylko ostatni kropki (.) w ciągu `x:Class` wartości jest interpretowany do oddzielania `namespace` i `classname.` klasy, która jest używana jako `x:Class` nie może być klasą zagnieżdżoną. Klasy zagnieżdżone nie są dozwolone, ponieważ określanie znaczenie kropkami dla `x:Class` ciągów jest niejednoznaczny, jeśli klasy zagnieżdżone są dozwolone.  
  
 W istniejących programowania modeli, które używają `x:Class`, `x:Class` jest opcjonalna w tym sensie, jest całkowicie nieprawidłowe strona XAML ma nie kodem. Jednak taką możliwość interakcji z akcji kompilacji zaimplementowanego przez platformy, które używają XAML. `x:Class` możliwość również ma wpływ ról, że różne klasyfikacje zawartości XAML, określony w modelu aplikacji i w polu kompilacji akcje. Jeśli Twoje XAML deklaruje atrybutu obsługi zdarzeń wartości lub tworzy elementy niestandardowe, gdzie klasy definiującej znajdują się w klasie związanej z kodem, musisz podać `x:Class` dyrektywy odwołania (lub [x: Subclass](../../../docs/framework/xaml-services/x-subclass-directive.md)) do odpowiedniej klasy dla związane z kodem.  
  
 Wartość `x:Class` dyrektywa musi być ciągiem, który określa w pełni kwalifikowana nazwa klasy, ale bez żadnych informacji o zestawie (odpowiednikiem <xref:System.Type.FullName%2A?displayProperty=nameWithType>). W przypadku prostego aplikacji informacji przestrzeń nazw CLR można pominąć, jeśli CodeBehind składa się również w ten sposób (kod rozpocznie definicji na poziomie klasy).  
  
 Plik CodeBehind dla definicji strony lub aplikacji musi być w pliku kodu, który jest częścią projektu, który tworzy skompilowanej aplikacji i obejmuje kompilację znaczników. Wykonaj regułami dotyczącymi nazw dla klasy CLR. Aby uzyskać więcej informacji, zobacz [zaleceń dotyczących projektowania Framework](../../../docs/standard/design-guidelines/index.md). Domyślnie klasy związane z kodem musi być `public`, jednak można zdefiniować na poziomie różnych dostępu za pomocą [x: classmodifier — dyrektywa](../../../docs/framework/xaml-services/x-classmodifier-directive.md).  
  
 Ta interpretacja `x:Class` atrybut dotyczy tylko do wdrożenia na podstawie CLR XAML, w szczególności usług .NET Framework XAML. Implementacje XAML, które nie są oparte na CLR, które nie korzystają z usług .NET Framework XAML może używać formuły innego rozwiązania do łączenia XAML znaczników i kodu w czasie wykonywania kopii. Aby uzyskać więcej informacji na temat interpretacji bardziej ogólne `x:Class`, zobacz [ \[MS XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
 Na poziomie architekturę, znaczenie `x:Class` jest niezdefiniowana w usługach programu .NET Framework XAML. Jest to spowodowane usług .NET Framework XAML nie został określony model programowania, przez które XAML znaczników i tworzenie kopii kodu są połączone. Dodatkowe zastosowań `x:Class` dyrektywa może być zaimplementowany przez określonych struktur, co umożliwia definiowanie sposobu łączenia znaczników XAML i środowiska CLR na podstawie kodem modele programowania i modeli aplikacji. Każdy framework może mieć własną akcji kompilacji, które udostępnia niektóre działania lub określone składniki, które muszą być zawarte w środowisku kompilacji. W ramach akcji kompilacji mogą być też inne w zależności od określonego języka środowiska CLR używanej do kodu powiązanego.  
  
## <a name="xclass-in-the-wpf-programming-model"></a>x: Class w modelu programowania WPF  
 W aplikacji WPF i modelem aplikacji WPF `x:Class` mogą być deklarowane jako atrybut dla każdego elementu, który jest elementem głównym pliku XAML i jest kompilowany (gdzie XAML znajduje się w projekcie aplikacji WPF z `Page` Akcja kompilacji), lub < C4 > <xref:System.Windows.Application>  głównego definicji aplikacji skompilowanej aplikacji WPF. Deklarowanie `x:Class` elementu innego niż strony głównej lub katalog główny aplikacji lub pliku WPF XAML, który nie jest skompilowany, powoduje błąd kompilacji w obszarze [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)] i [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] kompilatora WPF XAML. Aby uzyskać informacje o innych aspektów `x:Class` obsługi na platformie WPF, zobacz [CodeBehind i języka XAML w WPF](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).  
  
## <a name="xclass-for-windows-workflow-foundation"></a>x: Class dla programu Windows Workflow Foundation  
 Dla programu Windows Workflow Foundation `x:Class` nazwy klasy niestandardowe działanie składające się wyłącznie w języku XAML, lub nazwy klasy częściowej strony XAML Designer działanie z kodem.  
  
## <a name="silverlight-usage-notes"></a>Uwagi dotyczące użycia programu Silverlight  
 `x:Class` dla programu Silverlight jest udokumentowany oddzielnie. Aby uzyskać więcej informacji, zobacz [Namespace XAML (x:) Funkcje języka (platformy Silverlight)](http://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Zobacz też  
 [x:Subclass, dyrektywa](../../../docs/framework/xaml-services/x-subclass-directive.md)  
 [Klasy XAML i niestandardowe dla WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)  
 [x:ClassModifier, dyrektywa](../../../docs/framework/xaml-services/x-classmodifier-directive.md)  
 [Typy migrowane z WPF do System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)

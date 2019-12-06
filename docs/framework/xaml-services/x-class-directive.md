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
ms.openlocfilehash: d6baa6d8eb3a6d3520fb1549e2182f27ca52c36a
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837249"
---
# <a name="xclass-directive"></a>x:Class — dyrektywa
Konfiguruje kompilację znaczników XAML, aby dołączyć klasy częściowe między adiustacją i kodem. Klasa fragmentu kodu jest definiowana w osobnym pliku kodu w języku Common Language Specification (CLS), natomiast Klasa fragmentu znaczników jest zazwyczaj tworzona przez generowanie kodu podczas kompilacji XAML.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object x:Class="namespace.classname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`namespace`|Opcjonalny. Określa przestrzeń nazw CLR, która zawiera klasę częściową identyfikowaną przez `classname`. Jeśli `namespace` jest określony, kropka (.) oddziela `namespace` i `classname`. Zobacz uwagi.|  
|`classname`|Wymagany. Określa nazwę CLR klasy częściowej, która łączy załadowany kod XAML i związany z kodem dla tego języka XAML.|  
  
## <a name="dependencies"></a>Zależności  
 `x:Class` można określić tylko w elemencie głównym produkcji XAML. `x:Class` jest nieprawidłowy dla każdego obiektu, który ma element nadrzędny w środowisku produkcyjnym XAML. Aby uzyskać więcej informacji, zobacz [sekcję\[MS-XAML\] sekcji 4.3.1.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
## <a name="remarks"></a>Uwagi  
 Wartość `namespace` może zawierać dodatkowe kropki do organizowania powiązanych przestrzeni nazw w hierarchie nazw, które są typową techniką w programowaniu .NET Framework. Tylko Ostatnia kropka w ciągu `x:Class` wartości jest interpretowana do oddzielenia `namespace` i `classname.` Klasa, która jest używana jako `x:Class` nie może być klasą zagnieżdżoną. Klasy zagnieżdżone są niedozwolone, ponieważ określenie znaczenia kropek dla ciągów `x:Class` jest niejednoznaczne, jeśli zagnieżdżone klasy są dozwolone.  
  
 W istniejących modelach programowania, które używają `x:Class`, `x:Class` jest opcjonalne w sensie, że jest całkowicie prawidłowy, aby mieć stronę XAML, która nie zawiera kodu. Jednak ta funkcja współdziała z akcjami kompilacji zaimplementowanymi przez platformy, które używają języka XAML. na `x:Class` ma także wpływ role, które różne klasyfikacje zawartości w języku XAML mają w modelu aplikacji i w odpowiednich akcjach kompilacji. Jeśli kod XAML deklaruje wartości atrybutów obsługi zdarzeń lub tworzy wystąpienia elementów niestandardowych, w których klasy definiujące znajdują się w klasie związanej z kodem, należy podać odwołanie do dyrektywy `x:Class` (lub [x:Subclass —](x-subclass-directive.md)) do odpowiedniej klasy dla kodu.  
  
 Wartość dyrektywy `x:Class` musi być ciągiem, który określa w pełni kwalifikowaną nazwę klasy, ale nie zawiera żadnych informacji o zestawie (równoważnych <xref:System.Type.FullName%2A?displayProperty=nameWithType>). W przypadku prostych aplikacji można pominąć informacje o przestrzeni nazw środowiska CLR, jeśli kod źródłowy jest również strukturalny w ten sposób (definicja kodu jest uruchamiana na poziomie klasy).  
  
 Plik związany z kodem dla definicji strony lub aplikacji musi znajdować się w pliku kodu, który jest zawarty w projekcie, który tworzy skompilowaną aplikację i obejmuje kompilację znaczników. Należy przestrzegać reguł nazw dla klas CLR. Aby uzyskać więcej informacji, zobacz [Framework — wskazówki dotyczące projektowania](../../standard/design-guidelines/index.md). Domyślnie Klasa z kodem musi być `public`; można jednak zdefiniować go na innym poziomie dostępu przy użyciu [dyrektywy x:ClassModifier —](x-classmodifier-directive.md).  
  
 Ta interpretacja atrybutu `x:Class` ma zastosowanie tylko do implementacji języka XAML opartego na środowisku CLR, w szczególności do .NET Framework usług XAML. Inne implementacje języka XAML, które nie są oparte na środowisku CLR i nie używają .NET Framework usług XAML, mogą korzystać z innej formuły rozpoznawania kodu w celu łączenia znaczników XAML i wykonywania kopii zapasowych w czasie wykonywania. Aby uzyskać więcej informacji na temat bardziej ogólnych interpretacji `x:Class`, zobacz [\[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
 Na określonym poziomie architektury znaczenie `x:Class` nie jest zdefiniowane w .NET Framework usługach XAML. Jest to spowodowane tym, że usługi XAML .NET Framework nie określają modelu programowania, za pomocą którego znaczniki XAML i kod zapasowy są połączone. Dodatkowe zastosowania dyrektywy `x:Class` mogą być implementowane przez konkretne struktury, które używają modeli programowania lub modeli aplikacji do definiowania sposobu łączenia znaczników XAML i kodu CLR. Każda struktura może mieć własne akcje kompilacji, które umożliwiają zachowanie niektórych zachowań lub określonych składników, które muszą być zawarte w środowisku kompilacji. W ramach struktury akcje kompilacji mogą się różnić w zależności od konkretnego języka CLR, który jest używany w kodzie.  
  
## <a name="xclass-in-the-wpf-programming-model"></a>x:Class w modelu programowania WPF  
 W aplikacjach WPF i modelu aplikacji WPF, `x:Class` może być zadeklarowany jako atrybut dla każdego elementu, który jest elementem głównym pliku XAML i jest kompilowany (gdzie kod XAML jest zawarty w projekcie aplikacji WPF z `Page` akcją kompilacji) lub <xref:System.Windows.Application> głównym w definicji aplikacji skompilowanej aplikacji WPF. Deklarowanie `x:Class` w elemencie innym niż katalog główny lub katalog główny strony lub w pliku XAML WPF, który nie jest kompilowany, powoduje błąd czasu kompilacji w ramach kompilatora .NET Framework 3,0 i .NET Framework 3,5 WPF XAML. Aby uzyskać informacje na temat innych aspektów obsługi `x:Class` w WPF, zobacz [kod w kodzie i XAML w WPF](../wpf/advanced/code-behind-and-xaml-in-wpf.md).  
  
## <a name="xclass-for-windows-workflow-foundation"></a>x:Class Windows Workflow Foundation  
 W przypadku Windows Workflow Foundation `x:Class` nazwy klasy działania niestandardowego składającego się całkowicie z języka XAML lub nazwy klasy częściowej strony XAML dla projektanta działań z kodem.  
  
## <a name="silverlight-usage-notes"></a>Uwagi dotyczące użytkowania Silverlight  
 `x:Class` dla Silverlight jest opisane osobno. Aby uzyskać więcej informacji, zobacz [przestrzeń nazw XAML (x:) Funkcje języka (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).  
  
## <a name="see-also"></a>Zobacz także

- [x:Subclass, dyrektywa](x-subclass-directive.md)
- [Klasy XAML i niestandardowe dla WPF](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [x:ClassModifier, dyrektywa](x-classmodifier-directive.md)
- [Typy migrowane z WPF do System.Xaml](types-migrated-from-wpf-to-system-xaml.md)

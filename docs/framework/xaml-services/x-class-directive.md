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
ms.openlocfilehash: 563802be655e0cb66c9a2735a64da9d7723c2a43
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401524"
---
# <a name="xclass-directive"></a>x:Class — dyrektywa
Konfiguruje kompilację znaczników XAML, aby dołączyć klasy częściowe między adiustacją i kodem. Klasa fragmentu kodu jest definiowana w osobnym pliku kodu w języku Common Language Specification (CLS), natomiast Klasa fragmentu znaczników jest zazwyczaj tworzona przez generowanie kodu podczas kompilacji XAML.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```  
<object x:Class="namespace.classname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`namespace`|Opcjonalny. Określa przestrzeń nazw CLR, która zawiera klasę częściową identyfikowaną przez `classname`. Jeśli `namespace` jest określony, kropka (.) `namespace` oddziela i `classname`. Zobacz uwagi.|  
|`classname`|Wymagane. Określa nazwę CLR klasy częściowej, która łączy załadowany kod XAML i związany z kodem dla tego języka XAML.|  
  
## <a name="dependencies"></a>Zależności  
 `x:Class`można określić tylko dla elementu głównego w środowisku produkcyjnym XAML. `x:Class`jest nieprawidłowy dla każdego obiektu, który ma element nadrzędny w środowisku produkcyjnym XAML. Aby uzyskać więcej informacji, zobacz [ \[sekcję MS\] -XAML 4.3.1.6](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="remarks"></a>Uwagi  
 `namespace` Wartość może zawierać dodatkowe kropki do organizowania powiązanych przestrzeni nazw w hierarchie nazw, które są powszechną techniką w .NET Framework programowaniu. Tylko Ostatnia kropka `x:Class` w ciągu wartości jest interpretowana jako oddzielona `namespace` , a `classname.` Klasa, która jest używana `x:Class` jako nie może być klasą zagnieżdżoną. Klasy zagnieżdżone są niedozwolone, ponieważ określenie znaczenia kropek dla `x:Class` ciągów jest niejednoznaczne, jeśli zagnieżdżone klasy są dozwolone.  
  
 W istniejących modelach programowania, które `x:Class`używają `x:Class` , jest opcjonalne w sensie, że jest całkowicie prawidłowy, aby mieć stronę XAML, która nie zawiera kodu. Jednak ta funkcja współdziała z akcjami kompilacji zaimplementowanymi przez platformy, które używają języka XAML. `x:Class`na możliwość ma także wpływ na role, które różne klasyfikacje zawartości w języku XAML mają w modelu aplikacji i w odpowiednich akcjach kompilacji. Jeśli kod XAML deklaruje wartości atrybutów obsługi zdarzeń lub tworzy wystąpienia elementów niestandardowych, w których klasy definiujące znajdują się w klasie związanej z kodem, należy `x:Class` podać odwołanie do dyrektywy (lub [x:Subclass —](x-subclass-directive.md)) do odpowiedniej klasy dla związane z kodem.  
  
 Wartość `x:Class` dyrektywy musi być ciągiem, który określa w pełni kwalifikowaną nazwę klasy, ale nie zawiera żadnych informacji o zestawie (równoważnych <xref:System.Type.FullName%2A?displayProperty=nameWithType>). W przypadku prostych aplikacji można pominąć informacje o przestrzeni nazw środowiska CLR, jeśli kod źródłowy jest również strukturalny w ten sposób (definicja kodu jest uruchamiana na poziomie klasy).  
  
 Plik związany z kodem dla definicji strony lub aplikacji musi znajdować się w pliku kodu, który jest zawarty w projekcie, który tworzy skompilowaną aplikację i obejmuje kompilację znaczników. Należy przestrzegać reguł nazw dla klas CLR. Aby uzyskać więcej informacji, zobacz [Framework — wskazówki dotyczące projektowania](../../standard/design-guidelines/index.md). Domyślnie Klasa z kodem musi być `public`, ale można ją zdefiniować na innym poziomie dostępu za pomocą [dyrektywy x:ClassModifier —](x-classmodifier-directive.md).  
  
 Ta interpretacja `x:Class` atrybutu dotyczy tylko implementacji języka XAML opartego na środowisku CLR, w szczególności w przypadku .NET Framework usług XAML. Inne implementacje języka XAML, które nie są oparte na środowisku CLR i nie używają .NET Framework usług XAML, mogą korzystać z innej formuły rozpoznawania kodu w celu łączenia znaczników XAML i wykonywania kopii zapasowych w czasie wykonywania. Aby uzyskać więcej informacji na temat bardziej ogólnych interpretacji `x:Class`, zobacz [ \[MS-XAML.\]](https://go.microsoft.com/fwlink/?LinkId=114525)  
  
 W przypadku określonego poziomu architektury znaczenie `x:Class` jest niezdefiniowane w .NET Framework usługach XAML. Jest to spowodowane tym, że usługi XAML .NET Framework nie określają modelu programowania, za pomocą którego znaczniki XAML i kod zapasowy są połączone. Dodatkowe zastosowania `x:Class` dyrektywy mogą być implementowane przez konkretne struktury, które używają modeli programowania lub modeli aplikacji do definiowania sposobu łączenia znaczników XAML i kodu opartego na środowisku CLR. Każda struktura może mieć własne akcje kompilacji, które umożliwiają zachowanie niektórych zachowań lub określonych składników, które muszą być zawarte w środowisku kompilacji. W ramach struktury akcje kompilacji mogą się różnić w zależności od konkretnego języka CLR, który jest używany w kodzie.  
  
## <a name="xclass-in-the-wpf-programming-model"></a>x:Class w modelu programowania WPF  
 W aplikacjach WPF i modelu `x:Class` aplikacji WPF można zadeklarować jako atrybut dla dowolnego elementu, który jest elementem głównym pliku XAML i jest kompilowany (gdzie kod XAML jest zawarty w projekcie aplikacji WPF z `Page` akcją kompilacji) lub dla < > <xref:System.Windows.Application> C4 w definicji aplikacji skompilowanej aplikacji WPF. Deklarowanie `x:Class` dla elementu innego niż katalog główny lub katalog główny strony, lub w pliku XAML WPF, który nie jest kompilowany, powoduje błąd czasu kompilacji w ramach kompilatora .NET Framework 3,0 i .NET Framework 3,5 WPF XAML. Aby uzyskać informacje na temat innych `x:Class` aspektów obsługi w WPF, zobacz sekcję [kod i XAML w WPF](../wpf/advanced/code-behind-and-xaml-in-wpf.md).  
  
## <a name="xclass-for-windows-workflow-foundation"></a>x:Class Windows Workflow Foundation  
 W przypadku Windows Workflow Foundation `x:Class` nazwa klasy działania niestandardowego składa się w całości w języku XAML lub nazwa klasy częściowej strony XAML dla projektanta działań z kodem.  
  
## <a name="silverlight-usage-notes"></a>Uwagi dotyczące użycia programu Silverlight  
 `x:Class`program Silverlight jest udokumentowany osobno. Aby uzyskać więcej informacji, [Zobacz Przestrzeń nazw XAML (x:) Funkcje języka (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Zobacz także

- [x:Subclass, dyrektywa](x-subclass-directive.md)
- [Klasy XAML i niestandardowe dla WPF](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [x:ClassModifier, dyrektywa](x-classmodifier-directive.md)
- [Typy migrowane z WPF do System.Xaml](types-migrated-from-wpf-to-system-xaml.md)

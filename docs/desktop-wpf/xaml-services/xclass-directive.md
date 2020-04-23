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
ms.openlocfilehash: f589fa70c2ee1c56544fa0f0152990478aa3761f
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072040"
---
# <a name="xclass-directive"></a>x:Class — dyrektywa
Konfiguruje kompilację znaczników XAML, aby dołączyć do klas częściowych między znacznikami a kodem. Klasa częściowa kodu jest zdefiniowana w oddzielnym pliku kodu w języku specyfikacji języka wspólnego (CLS), podczas gdy klasa częściowa znaczników jest zwykle tworzona przez generowanie kodu podczas kompilacji XAML.

## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML

```xaml
<object x:Class="namespace.classname"...>
  ...
</object>
```

## <a name="xaml-values"></a>Wartości XAML

|||
|-|-|
|`namespace`|Element opcjonalny. Określa obszar nazw CLR zawierający klasę częściową identyfikowaną przez `classname`program . Jeśli `namespace` jest określony, kropka (.) oddziela `namespace` i `classname`. Zobacz uwagi.|
|`classname`|Wymagany. Określa nazwę CLR klasy częściowej, która łączy załadowany kod XAML i kod dla tego kodu XAML.|

## <a name="dependencies"></a>Zależności

`x:Class`można określić tylko w elemencie głównym produkcji XAML. `x:Class`jest nieprawidłowy dla każdego obiektu, który ma element nadrzędny w produkcji XAML. Aby uzyskać więcej informacji, zobacz [ \[rozdział 4.3.1.6 ms-XAML\] ](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

## <a name="remarks"></a>Uwagi

Wartość `namespace` może zawierać dodatkowe kropki do organizowania powiązanych obszarów nazw w hierarchie nazw, co jest powszechną techniką w programowaniu .NET. Tylko ostatnia kropka w `x:Class` ciągu wartości jest `namespace` `classname.` interpretowana do oddzielenia i Klasa, która jest używana jako `x:Class` nie może być klasą zagnieżdżoną. Klasy zagnieżdżone nie są dozwolone, `x:Class` ponieważ określenie znaczenia kropek dla ciągów jest niejednoznaczne, jeśli zagnieżdżone klasy są dozwolone.

W istniejących modelach `x:Class` `x:Class` programowania, które używają , jest opcjonalne w tym sensie, że jest całkowicie prawidłowy, aby mieć stronę XAML, która nie ma posuń kodu. Jednak ta funkcja współdziała z akcjami kompilacji zaimplementowanymi przez struktury korzystające z XAML. `x:Class`na możliwości mają również wpływ role, które różne klasyfikacje zawartości określonej w języku XAML mają w modelu aplikacji i w odpowiednich akcjach kompilacji. Jeśli xaml deklaruje wartości atrybutów obsługi zdarzeń lub wystąpienia elementów niestandardowych, gdzie klasy definiujące znajdują `x:Class` się w klasie związanej z kodem, należy podać odwołanie do dyrektywy (lub [x:Podklasa)](xsubclass-directive.md)do odpowiedniej klasy dla klasy związanej z kodem.

Wartość `x:Class` dyrektywy musi być ciągiem, który określa w pełni kwalifikowaną nazwę klasy, <xref:System.Type.FullName%2A?displayProperty=nameWithType>ale bez żadnych informacji o zestawie (równoważnych ). W przypadku prostych aplikacji można pominąć informacje o przestrzeni nazw CLR, jeśli pozorowany kod jest również skonstruowany w ten sposób (definicja kodu rozpoczyna się na poziomie klasy).

Plik związany z kodem dla definicji strony lub aplikacji musi znajdować się w pliku kodu, który jest dołączony jako część projektu, który tworzy skompilowaną aplikację i obejmuje kompilację znaczników. Należy przestrzegać reguł nazw dla klas CLR. Aby uzyskać więcej informacji, zobacz [Wytyczne dotyczące projektowania ram](../../../api/index.md). Domyślnie klasa zakodowa musi `public`być; można jednak zdefiniować go na innym poziomie dostępu przy użyciu [x:ClassModifier Dyrektywy](xclassmodifier-directive.md).

Ta interpretacja `x:Class` atrybutu ma zastosowanie tylko do implementacji XAML opartej na programie CLR, w szczególności do usług .NET XAML Services. Inne implementacje XAML, które nie są oparte na programie CLR i które nie korzystają z usług .NET XAML, mogą używać innej formuły rozpoznawania do łączenia znaczników XAML i tworzenia kodu wykonawczego. Aby uzyskać więcej informacji na `x:Class`temat bardziej ogólnych interpretacji , zobacz [ \[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

Na pewnym poziomie architektury znaczenie `x:Class` jest niezdefiniowane w usługach .NET XAML. Dzieje się tak, ponieważ usługi .NET XAML services nie określają modelu programowania, za pomocą którego są połączone znaczniki XAML i kod zapasowy. Dodatkowe zastosowania `x:Class` dyrektywy mogą być implementowane przez określone struktury, które używają modeli programowania lub modeli aplikacji do definiowania sposobu łączenia znaczników XAML i związanych z kodem opartym na programie CLR. Każda struktura może mieć własne akcje kompilacji, które umożliwiają niektóre zachowanie lub określonych składników, które muszą być uwzględnione w środowisku kompilacji. W ramach akcje kompilacji mogą się również różnić w zależności od określonego języka CLR, który jest używany dla kodu.

## <a name="xclass-in-the-wpf-programming-model"></a>x:Klasa w modelu programowania WPF

W aplikacjach WPF i modelu `x:Class` aplikacji WPF, mogą być zadeklarowane jako atrybut dla dowolnego elementu, który jest głównym pliku XAML i jest `Page` kompilowany (gdzie <xref:System.Windows.Application> XAML znajduje się w projekcie aplikacji WPF z akcji kompilacji) lub dla katalogu głównego w definicji aplikacji skompilowaną aplikację WPF. Deklarowanie `x:Class` na element inny niż strona główna lub główny aplikacji lub w pliku WPF XAML, który nie jest skompilowany, powoduje błąd w czasie kompilacji w ramach .NET Framework 3.0 i .NET Framework 3.5 WPF XAML kompilatora. Aby uzyskać informacje `x:Class` na temat innych aspektów obsługi w WPF, zobacz [Code-Behind i XAML w WPF](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).

## <a name="xclass-for-windows-workflow-foundation"></a>x:Klasa dla fundacji przepływu pracy systemu Windows
W przypadku programu `x:Class` Windows Workflow Foundation nazwy klasy działania niestandardowego składającego się w całości z XAML lub nazwy częściowej klasy strony XAML dla projektanta działań z kodem.

## <a name="silverlight-usage-notes"></a>Uwagi dotyczące użycia programu Silverlight

`x:Class`dla programu Silverlight jest dokumentowany oddzielnie. Aby uzyskać więcej informacji, zobacz [obszar nazw XAML (x:) Funkcje językowe (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).

## <a name="see-also"></a>Zobacz też

- [x:Subclass — dyrektywa](xsubclass-directive.md)
- [Klasy XAML i niestandardowe dla WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [x:ClassModifier — dyrektywa](xclassmodifier-directive.md)
- [Typy migrowane z WPF do System.Xaml](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)

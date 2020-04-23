---
title: x:Subclass — dyrektywa
ms.date: 03/30/2017
f1_keywords:
- Subclass
- xSubclass
- x:Subclass
helpviewer_keywords:
- x:Subclass attribute [XAML Services]
- XAML [XAML Services], x:Subclass attribute
- Subclass attribute in XAML [XAML Services]
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
ms.openlocfilehash: e85e0fb5a0e1a865ed84a93767f8152a115bbe5f
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071368"
---
# <a name="xsubclass-directive"></a>x:Subclass — dyrektywa

Modyfikuje zachowanie kompilacji znaczników `x:Class` XAML, gdy jest również podany. Zamiast tworzenia klasy częściowej, która `x:Class`jest oparta na , pod warunkiem `x:Class` jest tworzony jako klasa pośrednia, a następnie pod warunkiem, że klasa pochodna ma być oparta na `x:Class`.

## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML

```xaml
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">
   ...
</object>
```

## <a name="xaml-values"></a>Wartości XAML

|||
|-|-|
|`namespace`|Element opcjonalny. Określa obszar nazw CLR `classname`zawierający plik . Jeśli `namespace` jest określony, kropka (.) oddziela `namespace` i `classname`.|
|`classname`|Wymagany. Określa nazwę CLR klasy częściowej, która łączy załadowany kod XAML i kod dla tego kodu XAML. Zobacz uwagi.|
|`subclassNamespace`|Element opcjonalny. Może się `namespace` różnić od tego, czy każdy obszar nazw może rozwiązać inny. Określa obszar nazw CLR `subclassName`zawierający plik . Jeśli `subclassName` jest określony, kropka (.) oddziela `subclassNamespace` i `subclassName`.|
|`subclassName`|Wymagany. Określa nazwę CLR podklasy.|

## <a name="dependencies"></a>Zależności

[x:Dyrektywa klasy](xclass-directive.md) musi być również podana na tym samym obiekcie, a ten obiekt musi być głównym elementem produkcji XAML.

## <a name="remarks"></a>Uwagi

`x:Subclass`użycie jest przeznaczone głównie dla języków, które nie obsługują deklaracji klasy częściowej.

Klasa używana jako `x:Subclass` klasa nie może być `x:Subclass` klasą zagnieżdżoną i musi odwoływać się do obiektu głównego, jak wyjaśniono w sekcji "Zależności".

W przeciwnym razie znaczenie `x:Subclass` koncepcyjne jest niezdefiniowane przez implementację usług .NET XAML. Dzieje się tak, ponieważ zachowanie usług .NET XAML services nie określa ogólnego modelu programowania, za pomocą którego są połączone znaczniki XAML i kod zapasowy. Implementacje dalszych pojęć `x:Class` związanych z i `x:Subclass` są wykonywane przez określone struktury, które używają modeli programowania lub modeli aplikacji do definiowania sposobu łączenia znaczników XAML, skompilowanych znaczników i opartych na programie CLR związanych z kodem. Każda struktura może mieć własne akcje kompilacji, które umożliwiają niektóre zachowanie lub określonych składników, które muszą być uwzględnione w środowisku kompilacji. W ramach akcje kompilacji mogą się również różnić w zależności od określonego języka CLR, który jest używany dla kodu.

## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF

`x:Subclass`może znajdować się na stronie <xref:System.Windows.Application> głównej lub na katalogu `x:Class`głównym w definicji aplikacji, która już ma . Deklarowanie `x:Subclass` na dowolny element inny niż strona lub katalog `x:Class` główny aplikacji lub określenie go tam, gdzie nie istnieje, powoduje błąd w czasie kompilacji.

Tworzenie klas pochodnych, które `x:Subclass` działają poprawnie dla scenariusza jest dość skomplikowane. Może być konieczne zbadanie plików pośrednich (pliki .g utworzone w folderze obj projektu przez kompilację znaczników, z nazwami zawierającymi nazwy plików .xaml). Te pliki pośrednie mogą pomóc w określeniu pochodzenia niektórych konstrukcji programowania w połączonych klas częściowych w skompilowaną aplikację.

Programy obsługi zdarzeń w klasie `internal override` pochodnej muszą być (w`Friend Overrides` programie Microsoft Visual Basic) w celu zastąpienia wycinków dla programów obsługi utworzonych w klasie pośredniej podczas kompilacji. W przeciwnym razie implementacje klasy pochodnej ukryć (cień) implementacji klasy pośredniej i pośrednich obsługi klasy nie są wywoływane.

Podczas definiowania `x:Class` `x:Subclass`zarówno i , nie trzeba podać żadnej implementacji `x:Class`dla klasy, do której odwołuje się . Wystarczy nadać mu nazwę za `x:Class` pośrednictwem atrybutu, tak aby kompilator ma pewne wskazówki dla klasy, która tworzy w plikach pośrednich (kompilator nie wybiera domyślnej nazwy w tym przypadku). Można dać `x:Class` klasie implementacji; jednak nie jest to typowy scenariusz `x:Class` `x:Subclass`do korzystania zarówno i .

## <a name="see-also"></a>Zobacz też

- [x:Class — dyrektywa](xclass-directive.md)
- [Klasy XAML i niestandardowe dla WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)

---
title: x:TypeArguments — dyrektywa
ms.date: 03/30/2017
f1_keywords:
- x:TypeArguments
- xTypeArguments
- TypeArguments
helpviewer_keywords:
- x:TypeArguments attribute [XAML Services]
- TypeArguments attribute in XAML [XAML Services]
- XAML [XAML Services], x:TypeArguments attribute
ms.assetid: 86561058-d393-4a44-b5c3-993a4513ea74
ms.openlocfilehash: 69da9329f140121b66c71d4cf2e99e9d14a1b207
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071354"
---
# <a name="xtypearguments-directive"></a>x:TypeArguments — dyrektywa

Przekazuje argumenty typu ograniczające rodzajowy do konstruktora typu ogólnego.

## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML

```xaml
<object x:TypeArguments="typeString" .../>
```

## <a name="xaml-values"></a>Wartości XAML

|||
|-|-|
|`object`|Deklaracja elementu obiektu typu XAML, który jest wspierany przez typ ogólny CLR. Jeśli `object` odwołuje się do typu XAML, który nie pochodzi `object` z domyślnego obszaru nazw XAML, `object` wymaga prefiksu, aby wskazać obszar nazw XAML, gdzie istnieje.|
|`typeString`|Ciąg, który deklaruje jedną lub więcej nazw typów XAML jako ciągi, który dostarcza argumenty typu dla typu ogólnego CLR. Zobacz Uwagi, aby uzyskać dodatkowe uwagi składniowe.|

## <a name="remarks"></a>Uwagi

W większości przypadków typy XAML, które są `typeString` używane jako element informacji w ciągu są poprzedzone. Typowe typy ograniczeń ogólnych CLR <xref:System.Int32> (na przykład i) <xref:System.String>pochodzą z bibliotek klas podstawowych CLR. Te biblioteki nie są mapowane do typowych domyślnych obszarów nazw XAML specyficznych dla struktury i dlatego wymagają mapowania prefiksów dla użycia XAML.

Można określić więcej niż jedną nazwę typu XAML za pomocą ogranicznika przecinka.

Jeśli same ograniczenia ogólne używają typów ogólnych, argumenty typu zagnieżdżonego mogą być zawarte w nawiasach ().

Należy zauważyć, `x:TypeArguments` że ta definicja jest specyficzna dla usług .NET XAML i przy użyciu kopii clr. Definicję na poziomie języka można znaleźć w [ \[sekcji MS-XAML\] 5.3.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

## <a name="usage-examples"></a>Przykłady użycia

W poniższych przykładach załóżmy, że następujące definicje przestrzeni nazw XAML są zadeklarowane:

```xaml
xmlns:sys="clr-namespace:System;assembly=mscorlib"
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"
```

### <a name="liststring"></a>>\<ciągu listy

`<scg:List x:TypeArguments="sys:String" ...>`wystąpienia nowego <xref:System.Collections.Generic.List%601> z argumentem <xref:System.String> typu.

### <a name="dictionarystringstring"></a>Ciąg\<słownika,Ciąg>

`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>`wystąpienia nowego <xref:System.Collections.Generic.Dictionary%602> z dwoma <xref:System.String> argumentami typu.

### <a name="queuekeyvaluepairstringstring"></a>Kolejka<Ciąg KeyValuePair,\<Ciąg>>

`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>`<xref:System.Collections.Generic.Queue%601> wystąpienia nowego, który ma ograniczenie <xref:System.Collections.Generic.KeyValuePair%602> z argumentami <xref:System.String> typu <xref:System.String>ograniczenia wewnętrznego i .

## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a>XAML 2006 i WPF Ogólne użycie XAML

W przypadku użycia XAML 2006 i XAML używanego w aplikacjach `x:TypeArguments` WPF istnieją następujące ograniczenia dotyczące ogólnych użycia typu z XAML w ogóle:

- Tylko element główny pliku XAML może obsługiwać ogólne użycie XAML, które odwołuje się do typu ogólnego.

- Element główny musi być mapowana do typu ogólnego z co najmniej jednym argumentem typu. Może to być na przykład <xref:System.Windows.Navigation.PageFunction%601>. Funkcje strony są podstawowym scenariuszem obsługi użycia ogólnego XAML w WPF.

- Element główny XAML element obiektu dla ogólnego musi `x:Class`również zadeklarować klasę częściową przy użyciu . Jest to prawdą, nawet jeśli definiowanie akcji kompilacji WPF.

- `x:TypeArguments`nie można odwoływać się do zagnieżdżonych ograniczeń ogólnych.

## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a>XAML 2009 lub XAML 2006 bez zależności WPF 3.0 lub WPF 3.5

W usługach .NET XAML dla XAML 2006 lub XAML 2009 ograniczenia związane z WPF ogólne użycie XAML są złagodzone. Można utworzyć wystąpienie elementu obiektu ogólnego w dowolnym miejscu w znacznikach XAML, które może obsługiwać system typu kopii zapasowej i model obiektu.

Jeśli używasz XAML 2009 zamiast mapowania typów podstawowych CLR w celu uzyskania typów XAML dla pierwotnych języków wspólnych, można użyć [wbudowanych typów dla wspólnych elementów pierwotnych języka XAML](types-for-primitives.md) jako elementów informacyjnych w `typeString`pliku . Na przykład można zadeklarować następujące (mapowania prefiksów nie są wyświetlane, ale x jest przestrzenią nazw XAML języka XAML dla XAML 2009):

```xaml
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>
```

W WPF I podczas kierowania .NET Framework 4 lub .NET Core 3.0 (lub nowsze), `x:TypeArguments` można użyć funkcji XAML 2009 wraz z, ale tylko dla luźnego XAML (XAML, który nie jest skompilowany znaczników). Markup-skompilowany XAML dla WPF i BAML formie XAML obecnie nie obsługują XAML 2009 słów kluczowych i funkcji. Jeśli chcesz oznaczyć skompilować XAML, należy działać zgodnie z ograniczeniami opisanymi w [XAML 2006 i WPF Generic XAML usages](#xaml-2006-and-wpf-generic-xaml-usages) sekcji. BAML jest obsługiwany tylko w .NET Framework.

## <a name="see-also"></a>Zobacz też

- [x:Class — dyrektywa](xclass-directive.md)
- [x:Type — Rozszerzenie znaczników](xtype-markup-extension.md)
- [Typy wbudowane dla wspólnych elementów podstawowych języka XAML](types-for-primitives.md)
- [Typy ogólne w XAML](generics.md)

---
title: Właściwości zależności
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
ms.openlocfilehash: e1372b75cb6501f8bc3fec913364e9d80157ad83
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741723"
---
# <a name="dependency-properties"></a>Właściwości zależności
Właściwość zależności (DP) to zwykła właściwość, która przechowuje jej wartość w magazynie właściwości, zamiast przechowywać ją w zmiennej typu (pole), na przykład.

 Właściwość dołączona zależność jest rodzajem właściwości zależności modelowanym jako statyczne metody get i Set reprezentujące "właściwości" opisujące relacje między obiektami i ich kontenerami (np. położenie obiektu `Button` w kontenerze `Panel`).

 ✔️ zapewnić właściwości zależności, jeśli potrzebujesz właściwości do obsługi funkcji WPF, takich jak style, wyzwalacze, powiązanie danych, animacje, zasoby dynamiczne i dziedziczenie.

## <a name="dependency-property-design"></a>Projekt właściwości zależności
 ✔️ dziedziczyć po <xref:System.Windows.DependencyObject>lub jednym z jego podtypów podczas implementowania właściwości zależności. Typ zapewnia bardzo wydajną implementację magazynu właściwości i automatycznie obsługuje powiązanie danych WPF.

 ✔️ zapewnić zwykłą Właściwość środowiska CLR i publiczne statyczne pole tylko do odczytu przechowujące wystąpienie <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> dla każdej właściwości zależności.

 ✔️ Implementowanie właściwości zależności przez wywoływanie metod wystąpienia <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> i <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.

 ✔️ Nadaj nazwę statycznemu polu właściwości zależności za pomocą sufiksu nazwy właściwości z "Property".

 ❌ nie ustawiaj domyślnych wartości właściwości zależności jawnie w kodzie; Zamiast tego należy je ustawić w metadanych.

 Jeśli jawnie ustawisz właściwość domyślną, można zapobiec ustawianiu tej właściwości przez niejawne środki, takie jak style.

 ❌ nie należy umieszczać kodu w odniesieniu do właściwości, innym niż standardowy kod w celu uzyskania dostępu do pola statycznego.

 Ten kod nie zostanie wykonany, jeśli właściwość jest ustawiona w sposób niejawny, na przykład w stylu, ponieważ style używa pola statycznego bezpośrednio.

 ❌ nie używać właściwości zależności do przechowywania zabezpieczonych danych. Nawet prywatne właściwości zależności są dostępne publicznie.

## <a name="attached-dependency-property-design"></a>Projekt właściwości dołączonej zależności
 Właściwości zależności opisane w poprzedniej sekcji reprezentują właściwości wewnętrzne typu deklarującego; na przykład właściwość `Text` jest właściwością `TextButton`, która deklaruje ją. Szczególnym rodzajem właściwości zależności jest dołączona właściwość zależności.

 Klasycznym przykładem dołączonej właściwości jest właściwość <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType>. Właściwość reprezentuje położenie kolumny przycisku (nie siatki), ale ma zastosowanie tylko wtedy, gdy przycisk jest zawarty w siatce i dlatego jest "dołączony" do przycisków według siatki.

```xaml
<Grid>
    <Grid.ColumnDefinitions>
        <ColumnDefinition />
        <ColumnDefinition />
    </Grid.ColumnDefinitions>

    <Button Grid.Column="0">Click</Button>
    <Button Grid.Column="1">Clack</Button>
</Grid>
```

 Definicja dołączonej właściwości wygląda głównie podobnie jak w przypadku właściwości zależności regularnej, z tą różnicą, że metody dostępu są reprezentowane za pomocą statycznych metod get i set:

```csharp
public class Grid {

    public static int GetColumn(DependencyObject obj) {
        return (int)obj.GetValue(ColumnProperty);
    }

    public static void SetColumn(DependencyObject obj, int value) {
        obj.SetValue(ColumnProperty,value);
    }

    public static readonly DependencyProperty ColumnProperty =
        DependencyProperty.RegisterAttached(
            "Column",
            typeof(int),
            typeof(Grid)
    );
}
```

## <a name="dependency-property-validation"></a>Walidacja właściwości zależności
 Właściwości często implementują to, co jest nazywane walidacją. Logika walidacji jest wykonywana, gdy podejmowana jest próba zmiany wartości właściwości.

 Metody dostępu właściwości zależności nie mogą zawierać dowolnego kodu weryfikacyjnego. Zamiast tego należy określić logikę walidacji właściwości zależności podczas rejestracji właściwości.

 ❌ nie należy umieszczać logiki walidacji właściwości zależności we właściwościach dostępu. Zamiast tego należy przekazać wywołanie zwrotne walidacji do metody `DependencyProperty.Register`.

## <a name="dependency-property-change-notifications"></a>Powiadomienia o zmianie właściwości zależności
 ❌ nie zaimplementować logiki powiadomień o zmianach we właściwościach dostępu zależności. Właściwości zależności mają wbudowaną funkcję powiadomień o zmianach, która musi być używana przez dostarczenie wywołania zwrotnego powiadomienia o zmianie do <xref:System.Windows.PropertyMetadata>.

## <a name="dependency-property-value-coercion"></a>Wymuszone przekształcenie wartości właściwości zależności
 Wymuszanie właściwości odbywa się, gdy wartość określona dla metody ustawiającej właściwość jest modyfikowana przez metodę ustawiającą przed faktycznym zmodyfikowaniem magazynu właściwości.

 ❌ nie implementuje logiki przymusu we właściwościach dostępu zależności.

 Właściwości zależności mają wbudowaną funkcję przymusu i mogą być używane przez dostarczenie wywołania zwrotnego przekształcenia do `PropertyMetadata`.

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Często używane wzorce projektowe](../../../docs/standard/design-guidelines/common-design-patterns.md)

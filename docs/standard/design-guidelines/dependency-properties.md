---
title: Właściwości zależności
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
ms.openlocfilehash: 476ef1bb1ac5ec1f551979c64a41cbae55c554bc
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280260"
---
# <a name="dependency-properties"></a>Właściwości zależności
Właściwość zależności (DP) to zwykła właściwość, która przechowuje jej wartość w magazynie właściwości, zamiast przechowywać ją w zmiennej typu (pole), na przykład.

 Właściwość dołączona zależność jest rodzajem właściwości zależności modelowanym jako statyczne metody get i Set reprezentujące "właściwości" opisujące relacje między obiektami i ich kontenerami (np. pozycja `Button` obiektu w `Panel` kontenerze).

 ✔️ zapewnić właściwości zależności, jeśli potrzebujesz właściwości do obsługi funkcji WPF, takich jak style, wyzwalacze, powiązanie danych, animacje, zasoby dynamiczne i dziedziczenie.

## <a name="dependency-property-design"></a>Projekt właściwości zależności
 ✔️ dziedziczyć po <xref:System.Windows.DependencyObject> lub jeden z jego podtypów podczas implementowania właściwości zależności. Typ zapewnia bardzo wydajną implementację magazynu właściwości i automatycznie obsługuje powiązanie danych WPF.

 ✔️ zapewnić zwykłą Właściwość środowiska CLR i publiczne statyczne pole tylko do odczytu przechowujące wystąpienie <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> dla każdej właściwości zależności.

 ✔️ Implementowanie właściwości zależności przez wywoływanie metod wystąpień <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> i <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType> .

 ✔️ Nadaj nazwę statycznemu polu właściwości zależności za pomocą sufiksu nazwy właściwości z "Property".

 ❌NIE ustawiaj domyślnych wartości właściwości zależności jawnie w kodzie; Zamiast tego należy je ustawić w metadanych.

 Jeśli jawnie ustawisz właściwość domyślną, można zapobiec ustawianiu tej właściwości przez niejawne środki, takie jak style.

 ❌NIE należy umieszczać kodu w odniesieniu do właściwości, innym niż standardowy kod, aby uzyskać dostęp do pola statycznego.

 Ten kod nie zostanie wykonany, jeśli właściwość jest ustawiona w sposób niejawny, na przykład w stylu, ponieważ style używa pola statycznego bezpośrednio.

 ❌NIE należy używać właściwości zależności do przechowywania zabezpieczonych danych. Nawet prywatne właściwości zależności są dostępne publicznie.

## <a name="attached-dependency-property-design"></a>Projekt właściwości dołączonej zależności
 Właściwości zależności opisane w poprzedniej sekcji reprezentują właściwości wewnętrzne typu deklarującego; na przykład `Text` Właściwość jest właściwością `TextButton` , która deklaruje ją. Szczególnym rodzajem właściwości zależności jest dołączona właściwość zależności.

 Klasycznym przykładem dołączonej właściwości jest <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> Właściwość. Właściwość reprezentuje położenie kolumny przycisku (nie siatki), ale ma zastosowanie tylko wtedy, gdy przycisk jest zawarty w siatce i dlatego jest "dołączony" do przycisków według siatki.

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

 ❌NIE należy umieszczać logiki walidacji właściwości zależności we właściwościach dostępu. Zamiast tego należy przekazać wywołanie zwrotne walidacji do `DependencyProperty.Register` metody.

## <a name="dependency-property-change-notifications"></a>Powiadomienia o zmianie właściwości zależności
 ❌NIE implementuje logiki powiadomień o zmianach we właściwościach dostępu zależności. Właściwości zależności mają wbudowaną funkcję powiadomień o zmianach, która musi być używana przez dostarczenie wywołania zwrotnego powiadomienia o zmianie <xref:System.Windows.PropertyMetadata> .

## <a name="dependency-property-value-coercion"></a>Wymuszone przekształcenie wartości właściwości zależności
 Wymuszanie właściwości odbywa się, gdy wartość określona dla metody ustawiającej właściwość jest modyfikowana przez metodę ustawiającą przed faktycznym zmodyfikowaniem magazynu właściwości.

 ❌NIE Wdrażaj logiki przekształcenia we właściwościach dostępu zależności.

 Właściwości zależności mają wbudowaną funkcję przymusu i mogą być używane przez dostarczenie wywołania zwrotnego przekształcenia do elementu `PropertyMetadata` .

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Wskazówki dotyczące projektowania struktury](index.md)
- [Typowe wzorce projektowe](common-design-patterns.md)

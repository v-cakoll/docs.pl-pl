---
ms.openlocfilehash: 35fc4782ebbba33f5fc6668712af9d89d00cafe9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614973"
---
### <a name="wpf-changing-a-primary-key-when-displaying-ado-data-in-a-masterdetail-scenario"></a>WPF zmiana klucza podstawowego podczas wyświetlania danych ADO w scenariuszu głównym/szczegółowym

#### <a name="details"></a>Szczegóły

Załóżmy, że istnieje kolekcja ADO elementów typu `Order` , z relacją o nazwie OrderDetails, &quot; &quot; która odnosi się do kolekcji elementów typu `Detail` za pośrednictwem klucza podstawowego &quot; IDZamówienia &quot; . W aplikacji WPF można powiązać formant listy z danymi szczegółowymi dotyczącymi danej kolejności:

```xaml
<ListBox ItemsSource="{Binding Path=OrderDetails}" >
```

gdzie DataContext jest `Order` . WPF Pobiera wartość `OrderDetails` właściwości-kolekcji D wszystkich `Detail` elementów, które `OrderID` pasują do `OrderID` elementu głównego. Zmiana klucza podstawowego elementu głównego jest zachowaniem `OrderID` . Obiekt ADO automatycznie zmienia `OrderID` każdy z rekordów, których dotyczy ten rekord w kolekcji szczegóły (a mianowicie skopiowane do kolekcji D).  Ale co się dzieje z D?

- Stare zachowanie: Kolekcja D została wyczyszczona. Element główny *nie zgłasza powiadomienia* o zmianie dla właściwości `OrderDetails` . Element ListBox nadal używa kolekcji D, która jest teraz pusta.
- Nowe zachowanie: Kolekcja D nie została zmieniona. Każdy z elementów zgłasza powiadomienie o zmianie dla `OrderID` właściwości. Element ListBox nadal używa kolekcji D i wyświetla szczegóły z nowym `OrderID` . WPF implementuje nowe zachowanie przez utworzenie kolekcji D w inny sposób: przez wywołanie metody ADO <xref:System.Data.DataRowView.CreateChildView(System.Data.DataRelation,System.Boolean)?displayProperty=nameWithType> z `followParent` argumentem ustawionym na `true` .

#### <a name="suggestion"></a>Sugestia

Aplikacja pobiera nowe zachowanie przy użyciu następującego przełącznika AppContext.

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Data.DoNotUseFollowParentWhenBindingToADODataRelation=false"/>
  </runtime>
</configuration>
```

Ustawienie domyślne przełącznika `true` (stare zachowanie) dla aplikacji przeznaczonych dla platformy .NET 4.7.1 lub nowszych oraz do `false` (nowe zachowanie) dla aplikacji przeznaczonych dla platformy .NET 4.7.2 lub nowszej.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4.7.2       |
| Typ    | Przekierowanie |
